# Briefing operacional — AppJam Expoagas

## O desafio em uma frase

Demonstrar, em três páginas, uma solução simples e inovadora para um problema real de supermercados ou dos participantes da Expoagas.

## Entrega exigida pelo material

- Microaplicativo com exatamente três páginas.
- Uma única página HTML, com JavaScript moderno quando necessário.
- Repositório no GitHub e aplicação publicada no GitHub Pages.
- Links do repositório e da aplicação.
- Nome e e-mail legíveis de cada integrante.
- Equipe de até cinco participantes.
- Entrega final confirmada para quarta-feira, **12/08/2026, até 23h59**, por Google Forms.
- O formulário pede uma breve proposta, uma URL do trabalho e nome/e-mail dos integrantes.

## Pontuação

| Critério | Pontos | O que precisamos demonstrar |
|---|---:|---|
| Resolução de problema do setor | 30 | Problema claro, relevante, útil e com valor percebido |
| Aderência a temas estratégicos | 20 | Conexão real e consistente com um ou mais temas |
| Experiência do usuário | 15 | Interface intuitiva, navegação simples e boa organização |
| Criatividade e inovação | 15 | Abordagem diferenciada e adequada ao problema |
| Identidade visual e comunicação | 10 | Aparência coerente, legível e apresentação convincente |
| Qualidade técnica | 10 | Aplicação funcional, sem erros e publicada corretamente |

Os primeiros critérios de desempate são problema do setor, aderência aos temas, identidade visual e qualidade técnica.

## Nome definitivo: GiroCerto

GiroCerto comunica o principal valor do produto: colocar cada item na ação certa e no momento certo para preservar margem e evitar desperdício.

### Problema

Produtos próximos do vencimento podem virar perda financeira, desperdício e trabalho operacional. A equipe da loja precisa decidir rapidamente quais itens priorizar e que ação tomar.

### Solução

Um assistente visual que organiza os produtos por urgência, sugere uma ação e simula o impacto da decisão. O protótipo usa dados fictícios e regras locais, o que permite uma demonstração confiável sem backend.

### Por que esta é a melhor aposta

- O problema é fácil de entender em poucos segundos.
- Conecta vários temas sem forçar a narrativa: analytics, indicadores, supply chain, automação, ESG, economia brasileira e IA aplicada ao varejo.
- Permite um fluxo completo com apenas três telas.
- O valor pode ser mostrado com números antes/depois.
- É viável construir rapidamente e ainda deixar espaço para uma identidade visual forte.

### As três páginas

1. **Visão do dia** — resumo de itens críticos, perda potencial e valor que pode ser recuperado.
2. **Prioridades** — produtos ordenados por urgência, com filtros simples.
3. **Plano de ação** — recomendação, ajuste de desconto e impacto estimado da ação.

### História da demonstração

“A líder de perecíveis vê que há uma perda potencial hoje, encontra o item mais urgente, simula uma remarcação e confirma uma ação que reduz desperdício e recupera margem. O gerente geral acompanha o impacto consolidado.”

## Escopo MoSCoW do primeiro protótipo

### Must have — sem isso não há entrega

- Exatamente três páginas dentro de uma única página HTML.
- Navegação funcionando entre Hoje, Prioridades e Decisão.
- Uma visão do dia com dados fictícios plausíveis.
- Pelo menos três produtos na lista de prioridades.
- Um fluxo completo: selecionar o produto, simular a ação e mostrar o impacto.
- Botões principais funcionando e nenhum erro visível durante a demonstração.
- Layout utilizável em celular e computador.
- Uso eficiente do espaço em telas largas e identidade cromática coerente para apresentação.
- Explicação curta do problema, da solução, do público e dos temas estratégicos.
- Uma evidência real do setor com fonte, sem misturar benchmark e resultado do protótipo.
- Identificação dos integrantes com nome e e-mail.
- Repositório organizado e versão final publicada no GitHub Pages.
- Links do repositório e da aplicação verificados antes da entrega.

### Should have — importante depois dos Must

- Filtro por urgência ou categoria na lista de prioridades.
- Comparação visual de perda potencial antes e depois da ação.
- Ajuste do percentual de desconto na simulação.
- Estados visuais claros para produto crítico, em atenção e controlado.
- Roteiro de apresentação de 60 a 90 segundos.
- Instrução operacional curta para o responsável pela ação.

### Could have — somente se houver tempo seguro

- Microanimações e transições entre páginas.
- Mais produtos e categorias demonstrativas.
- Alternativas de ação, como oferta, reposicionamento e doação.
- Pequeno gráfico de tendência semanal.
- Modo escuro ou personalização visual.
- Mensagem de confirmação mais elaborada após a ação.
- Indicador de CO₂ com fator de emissão e premissas documentadas.

### Won't have for now — fora desta versão

- Login e perfis.
- Banco de dados ou backend.
- Integração real com estoque ou ERP.
- Integração real com modelo de IA.
- Notificações reais.
- Cadastro e edição completa de produtos.
- Relatórios avançados.
- Aplicativo móvel nativo.
- Processamento de pagamentos ou dados pessoais de clientes.
- Doação, aprovação, tarefa ou benefício fiscal executados de verdade.

Um item Should ou Could nunca deve atrasar um Must. Mudanças de categoria precisam ser aprovadas e registradas.

## Alternativas para o grupo avaliar

| Ideia | Problema e fluxo | Pontos fortes | Risco principal |
|---|---|---|---|
| **MatchExpo** | Conecta necessidades de supermercados aos expositores e monta uma agenda | Muito ligado ao evento e fácil de apresentar | Problema menos recorrente fora da feira |
| **FilaFluxo** | Prevê horários de pico e sugere abertura de caixas/equipe | Problema real, visual e mensurável | Previsão pode parecer pouco crível sem explicar os dados |
| **Ruptura Zero** | Prioriza risco de falta de produtos e sugere reposição | Muito relevante para supply chain | Tema comum; exige diferenciação visual e narrativa |

## Organização sugerida do grupo

Para até cinco pessoas:

1. Produto e apresentação: problema, escopo, decisões e pitch.
2. UX e conteúdo: fluxo, textos e validação com usuários.
3. Identidade e interface: cores, componentes e acabamento visual.
4. Desenvolvimento: HTML, CSS, JavaScript e responsividade.
5. Qualidade e entrega: testes, GitHub Pages, links e checklist.

Em grupos menores, produto pode acumular apresentação; UX pode acumular interface; desenvolvimento pode acumular qualidade.

## Sequência recomendada

### Primeiro checkpoint

1. Confirmar problema, público e aplicação do nome GiroCerto.
2. Aprovar as três páginas e o fluxo de demonstração.
3. Revisar e aprovar a classificação MoSCoW.
4. Montar o esqueleto navegável.
5. Completar todos os Must possíveis, começando pelo caso de ponta a ponta.
6. Preparar uma apresentação de 60 a 90 segundos.

### Depois do checkpoint

1. Ajustar os Must com o feedback recebido.
2. Completar e verificar todos os Must.
3. Executar os Should por ordem de valor para a apresentação.
4. Considerar os Could somente se o prazo estiver seguro.
5. Revisar todos os critérios da banca.
6. Publicar, testar os links e fechar a entrega.

## Perguntas ainda abertas

- O repositório será renomeado para `girocerto-appjam-2026`?
- Quais papéis cada integrante assumirá na finalização e apresentação?
- Quais itens Should ainda cabem com segurança antes da publicação?
