# Especificação do motor de decisão — GiroCerto

## Estado desta especificação

Documento de referência para o protótipo. A versão atual usa **regras locais e dados demonstrativos**. Não existe integração real com ERP/WMS nem modelo de IA em produção.

O objetivo é demonstrar como uma futura inteligência prescritiva organizaria dados, justificaria uma recomendação e geraria uma tarefa operacional.

## Entradas mínimas

| Campo | Significado |
|---|---|
| `currentStock` | Quantidade física atual |
| `avgDailySales` | Venda média diária estimada |
| `daysToExpire` | Dias restantes até o vencimento |
| `unitPrice` | Preço atual de venda |
| `costPrice` | Custo unitário |
| `unitOfMeasure` | Unidade ou quilograma |
| `foodSafetyStatus` | Condição sanitária e elegibilidade para venda/doação |
| `targetStoreDemand` | Demanda estimada em outra unidade, quando houver |

## Métricas derivadas

```text
diasNecessarios = estoqueAtual / vendaMediaDiaria
demandaAteVencimento = vendaMediaDiaria × diasAteVencer
sobraEstimada = máximo(0, estoqueAtual − demandaAteVencimento)
margemAtual = (precoVenda − custo) / precoVenda
valorTotalExposto = estoqueAtual × precoVenda
perdaProvavelSemAcao = sobraEstimada × precoVenda
precoComDesconto = precoVenda × (1 − desconto / 100)
receitaRecuperavel = unidadesRecuperadas × precoComDesconto
```

É importante separar **valor total exposto** de **perda provável**. Eles não representam a mesma coisa.

## Ordem corrigida das regras

A ordem abaixo evita que uma regra de desconto impeça uma regra mais urgente de transferência ou doação.

1. **Validar dados e segurança alimentar.** Item vencido ou impróprio não pode ser vendido nem doado para consumo humano.
2. **Manter exposição** quando o giro natural absorve o estoque antes do vencimento.
3. **Doação rastreada** quando resta até um dia, existe sobra estimada, o item está apto e a operação cumpre as exigências sanitárias.
4. **Transferir unidade** quando restam até dois dias, existe excesso muito acima da demanda local e outra unidade pode absorvê-lo dentro da janela logística.
5. **Aplicar desconto gradual** quando restam até três dias, existe sobra e a margem comporta o desconto.
6. **Montar sacola oferta** quando restam até três dias, existe sobra e a margem é insuficiente para o markdown individual, assumindo recuperação parcial de valor.
7. **Revisão humana** quando os dados são insuficientes ou mais de uma saída apresenta risco semelhante.

## Pseudocódigo do protótipo

```javascript
function recommend(item) {
  validateRequiredData(item);

  if (item.foodSafetyStatus !== "SAFE") {
    return { actionType: "BLOCK_AND_REVIEW" };
  }

  const demandUntilExpiry = item.avgDailySales * item.daysToExpire;
  const expectedExcess = Math.max(0, item.currentStock - demandUntilExpiry);
  const daysNeeded = item.currentStock / Math.max(item.avgDailySales, 0.1);

  if (daysNeeded <= item.daysToExpire) {
    return { actionType: "MANTER_EXPOSICAO" };
  }

  if (item.daysToExpire <= 1 && expectedExcess > 0 && item.donationEligible) {
    return { actionType: "ENVIAR_DOACAO_ESG", requiresHumanApproval: true };
  }

  if (
    item.daysToExpire <= 2 &&
    item.currentStock > item.avgDailySales * item.daysToExpire * 3 &&
    item.targetStoreDemand > 0
  ) {
    return { actionType: "TRANSFERIR_UNIDADE", requiresHumanApproval: true };
  }

  if (item.daysToExpire <= 3 && expectedExcess > 0) {
    return item.currentMarginPercent >= 20
      ? { actionType: "APLICAR_DESCONTO_GRADUAL" }
      : { actionType: "MONTAR_SACOLA_OFERTA" };
  }

  return { actionType: "REVIEW_REQUIRED", requiresHumanApproval: true };
}
```

## Tipos de dados de referência

```typescript
export type DecisionType =
  | "APLICAR_DESCONTO_GRADUAL"
  | "MONTAR_SACOLA_OFERTA"
  | "TRANSFERIR_UNIDADE"
  | "ENVIAR_DOACAO_ESG"
  | "MANTER_EXPOSICAO"
  | "BLOCK_AND_REVIEW"
  | "REVIEW_REQUIRED";

export interface ProductItem {
  id: string;
  sku: string;
  name: string;
  category: string;
  unitPrice: number;
  costPrice: number;
  currentStock: number;
  unitOfMeasure: "UN" | "KG";
  expirationDate: string;
  daysToExpire: number;
  avgDailySales: number;
  currentMarginPercent: number;
  foodSafetyStatus: "SAFE" | "REVIEW" | "UNSAFE";
  donationEligible: boolean;
  targetStoreDemand?: number;
}

export interface Recommendation {
  actionType: DecisionType;
  title: string;
  description: string;
  suggestedDiscountPercent?: number;
  targetLocation?: string;
  executionDeadline: string;
  requiresHumanApproval: boolean;
  justificationFactors: {
    daysNeeded: number;
    expectedExcess: number;
    marginAfterDiscountPercent?: number;
    totalValueExposed: number;
    probableLossWithoutAction: number;
    dataQuality: "HIGH" | "MEDIUM" | "LOW";
  };
  impactSimulation: {
    recoverableRevenue: number;
    wastePreventedKg: number;
    co2ReductionKg?: number;
    assumptions: string[];
  };
}

export interface TaskDirective {
  taskId: string;
  assignedRole: string;
  instructionText: string;
  status: "PENDING" | "IN_PROGRESS" | "COMPLETED";
}
```

## Revisão dos dados demonstrativos recebidos

### Queijo mussarela fatiado 200 g

Com 45 unidades, venda média de 4 unidades/dia e três dias de validade:

- demanda estimada até o vencimento: **12 unidades**;
- sobra estimada: **33 unidades**;
- valor total exposto: **R$ 652,50**;
- perda provável sem ação: **R$ 478,50**;
- preço com 30% de desconto: **R$ 10,15**;
- receita recuperável sobre as 33 unidades excedentes: **R$ 334,95**;
- massa excedente potencialmente preservada: **6,6 kg**.

O valor de R$ 456,75 corresponde à venda das 45 unidades com desconto, não apenas das 33 unidades que provavelmente sobrariam. Ambos os números podem ser usados, desde que o rótulo deixe clara a premissa.

### Iogurte natural integral 170 g

Com 80 unidades, venda média de 8 unidades/dia e dois dias de validade:

- demanda estimada até o vencimento: **16 unidades**;
- sobra estimada: **64 unidades**;
- valor total exposto: **R$ 336,00**;
- perda provável sem ação: **R$ 268,80**;
- preço unitário com 45% de desconto: **R$ 2,31**;
- receita recuperável sobre as 64 unidades excedentes: **R$ 147,84**;
- massa excedente potencialmente preservada: **10,88 kg**.

Um kit com cinco unidades por R$ 11,55 fica abaixo do custo agregado de R$ 15,75. Portanto, deve ser apresentado como **recuperação parcial para evitar perda total**, não como preservação de margem ou recuperação integral do custo.

## CO₂ e impacto ambiental

O CO₂ evitado não pode ser derivado apenas de peso e preço. Uma versão real precisaria de fatores de emissão por categoria, origem metodológica, limites do cálculo e versão do fator.

No protótipo:

- mostrar os valores como **estimativa demonstrativa**;
- não alegar precisão científica;
- registrar a fórmula e a fonte antes de usar o indicador em produção.

## Exemplo de tarefa operacional

Para o cenário do queijo, a recomendação pode terminar em uma orientação demonstrativa como:

```text
Responsável: Operador do Setor de Perecíveis
Prazo: hoje até 15h30
Ação: imprimir etiquetas com 30% de desconto, aplicar o preço de R$ 10,15
e mover 20 unidades para a Ilha Promocional 02.
Estado: pendente de confirmação
```

A tarefa melhora o valor percebido porque mostra que o GiroCerto não termina na análise. No protótipo, a confirmação é apenas visual e não envia instruções reais.

## Aplicação nas três telas aprovadas

A proposta recebida descrevia um dashboard único. Para respeitar a regra da AppJam e preservar a narrativa, seus blocos ficam distribuídos sem criar uma quarta tela:

| Bloco proposto | Destino no fluxo aprovado |
|---|---|
| Barra de KPIs | Tela Hoje |
| Filtros de urgência e margem | Tela Prioridades, como Should |
| Card do item prioritário | Seleção na tela Prioridades |
| Explicabilidade e recomendação | Tela Decisão |
| Simulador antes/depois | Tela Decisão |
| Tarefa para operador | Confirmação da tela Decisão, como Should |

### 1. Hoje

- KPIs agregados demonstrativos;
- uma evidência curta da ABRAS no conteúdo expansível “Como chegamos nisso?”;
- mensagem de que a priorização usa regras locais demonstrativas.

### 2. Prioridades

- pelo menos três itens ordenados;
- prazo, estoque, giro e valor recuperável;
- filtros são Should, não um novo painel.

### 3. Decisão

- ação recomendada;
- fatores explicáveis;
- comparação antes/depois;
- ajuste de desconto;
- instrução curta para o operador;
- confirmação da ação demonstrativa.

## MoSCoW desta ampliação

### Must

- manter exatamente três telas em um HTML;
- distinguir dados reais de mercado, dados demonstrativos e resultados de terceiros;
- explicar ao menos uma recomendação com estoque, giro, validade e margem;
- manter o fluxo risco → recomendação → impacto → confirmação;
- bloquear qualquer interpretação de doação de produto vencido ou impróprio;
- manter o aplicativo funcional sem ERP, backend ou internet.

### Should

- documentar as quatro saídas de decisão;
- mostrar a instrução operacional para o responsável;
- usar dois cenários de dados recalculados;
- apresentar uma evidência ABRAS no pitch;
- manter rastreabilidade das premissas da simulação.

### Could

- implementar filtros por urgência e margem;
- permitir escolher entre desconto, sacola, transferência e doação;
- mostrar CO₂ quando houver fator de emissão documentado;
- simular aprovação automática conforme alçada.

### Won't have for now

- integração real com ERP/WMS;
- modelo de IA externo;
- doação automática;
- cálculo fiscal ou jurídico automático;
- envio real de tarefa a funcionário;
- afirmação de que o protótipo produz os resultados dos benchmarks.
