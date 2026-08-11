# Direção visual — Transformação

## Estado

Aprovada pela usuária em 11/08/2026.

O nome “Jam” continua provisório. Esta direção descreve a experiência visual, não a marca definitiva.

## Conceito visual

A interface deve representar uma transformação clara:

> risco visível → decisão compreensível → valor recuperado

O início da experiência usa tons quentes para comunicar urgência. Conforme o usuário avança e toma uma decisão, a interface migra para tons positivos, mostrando oportunidade financeira e redução de desperdício.

## Sensação desejada

- Moderna, segura e otimista.
- Tecnológica sem parecer complicada.
- Próxima do universo de alimentos e supermercados.
- Visualmente marcante durante uma apresentação curta.
- Mais narrativa do que painel administrativo.

## Paleta provisória

| Papel | Cor | Uso sugerido |
|---|---|---|
| Base clara | `#F7F5EF` | Fundo principal acolhedor |
| Texto principal | `#17211D` | Títulos, números e conteúdo importante |
| Risco | `#C7472F` | Perda potencial e urgência crítica |
| Atenção | `#B87800` | Prazo curto e oportunidade que exige ação |
| Transformação | `#0D6770` | Inteligência, transição e controles |
| Recuperação | `#18794E` | Valor recuperado e desperdício evitado |
| Superfície | `#FFFFFF` | Cartões e áreas de leitura |

As cores devem ser verificadas em contexto para garantir contraste. Vermelho e verde não podem ser os únicos meios de transmitir estado; usar também textos, ícones e rótulos.

## Tipografia

- Fonte sem serifa, moderna e altamente legível.
- Números de impacto grandes e com peso forte.
- Textos curtos; evitar parágrafos dentro do fluxo principal.
- Usar fontes do sistema no primeiro protótipo para reduzir dependências externas.

## Comportamento por página

### 1. Hoje

- Começa com uma área de risco em tom quente.
- Destaca o valor que ainda pode ser recuperado, não apenas a perda.
- Usa uma linha, arco ou fluxo visual indicando que existe uma transformação possível.
- Chamada principal conduz para a maior oportunidade do dia.

### 2. Prioridades

- Cartões organizados por oportunidade, evitando aparência de planilha.
- Cada cartão mostra urgência, prazo e valor recuperável.
- O item principal deve parecer selecionado pela inteligência do sistema.
- Tons quentes aparecem apenas onde exigem atenção.

### 3. Decisão

- Concentra o momento de encantamento.
- O estado inicial mostra risco em vermelho/laranja.
- A simulação movimenta os números e a composição em direção ao verde.
- A comparação antes/depois deve ser compreendida sem explicação oral.
- A confirmação encerra com valor recuperado e desperdício evitado.

## Movimento e transições

- Animações curtas e suaves, usadas para explicar transformação.
- Contadores podem evoluir do valor em risco para o valor recuperável.
- A mudança de cor deve acompanhar a mudança de estado.
- Evitar animações decorativas que atrasem a demonstração.
- Respeitar a preferência do navegador por movimento reduzido.

## Elemento visual principal

O elemento memorável será a transformação de impacto:

```text
ANTES                         DEPOIS
R$ 1.240 em risco   →         R$ 860 recuperáveis
52 kg em risco      →         38 kg preservados
```

Esse elemento deve ser maior e mais marcante que gráficos, menus ou listas.

## Evitar

- Aparência de ERP ou planilha convencional.
- Excesso de gráficos pequenos.
- Fundo completamente verde desde o início, pois elimina a sensação de transformação.
- Visual futurista genérico com neon e muitos efeitos.
- Ícones sem texto ou significados ambíguos.
- Fotografias decorativas que disputem atenção com os números.

## Critério de aprovação do protótipo

Uma pessoa que veja apenas as três telas deve entender:

1. existe uma perda urgente;
2. o sistema encontrou uma oportunidade;
3. uma decisão transforma o resultado;
4. há benefício financeiro e ambiental.
