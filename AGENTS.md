# Instruções dos agentes — AppJam UniRitter

## Objetivo do projeto

- Ajudar o grupo a conceber, prototipar e entregar um microaplicativo para a Expoagas/AppJam.
- Priorizar uma demonstração curta, funcional e convincente; não tentar construir um produto completo.
- Usar `docs/BRIEFING_E_PLANO.md` como fonte resumida dos requisitos da competição.
- Usar `docs/CONCEITO_GIROCERTO.md` como proposta atual de produto.
- Usar `docs/PESQUISA_E_BENCHMARKS.md` para fatos, fontes e limitações de mercado.
- Usar `docs/ESPECIFICACAO_DECISAO.md` para regras, cálculos e dados demonstrativos.
- Registrar escolhas e aprovações em `docs/DECISOES.md`.

Ao citar números, distinguir sempre: dado setorial validado, resultado divulgado por terceiro e simulação do protótipo. Não apresentar benefício fiscal, resultado ambiental ou desempenho comercial como garantido.

## Forma de colaboração com a usuária

- Comunicar em português claro, com pouca linguagem técnica.
- Começar cada etapa informando o resultado esperado e as decisões em aberto.
- Fazer perguntas quando faltar informação que altere tema, público, escopo, prazo, identidade ou tecnologia.
- Quando a dúvida não alterar materialmente o resultado, declarar uma suposição razoável e continuar.
- Apresentar no máximo três alternativas quando houver uma decisão; recomendar uma delas com justificativa.
- Dividir o trabalho em entregas pequenas e revisáveis. Mostrar o que mudou e como conferir.
- Não considerar silêncio como aprovação para decisões importantes.

## Aprovações obrigatórias

Pedir aprovação antes de:

1. Fixar ou trocar o problema, público principal ou tema do projeto.
2. Fixar o escopo das três páginas e o fluxo principal da demonstração.
3. Definir nome, identidade visual ou mensagem principal como versão final.
4. Adicionar dependência de produção, serviço pago, API externa, login ou coleta de dados pessoais.
5. Remover funcionalidades combinadas ou fazer uma mudança ampla de arquitetura.
6. Criar commit, enviar alterações ao GitHub, publicar no GitHub Pages ou submeter a entrega.
7. Apagar arquivos, sobrescrever trabalho do grupo ou executar uma ação de difícil reversão.

Leitura, análise, documentação, pequenos protótipos locais, testes e correções reversíveis podem ser feitos sem nova aprovação, desde que respeitem o escopo aprovado.

## Requisitos que não podem ser esquecidos

- Entregar um microaplicativo com exatamente três páginas/telas claramente identificáveis.
- Entregar tudo em uma única página HTML, podendo usar JavaScript moderno para alternar as telas.
- Publicar no GitHub Pages.
- Manter o repositório no GitHub organizado e pronto para avaliação.
- Informar o link do repositório, o link da aplicação e a identificação legível dos integrantes, com nome e e-mail.
- Equipe com no máximo cinco participantes.
- Entrega final confirmada para quarta-feira, 12/08/2026, até 23h59, pelo Google Forms indicado em `docs/ENTREGA.md`.
- Garantir que o protótipo não dependa de backend ou API externa para funcionar na apresentação, salvo aprovação explícita.

## Prioridade guiada pela avaliação

Trabalhar nesta ordem:

1. Problema real do setor e valor percebido — 30 pontos.
2. Conexão consistente com temas estratégicos — 20 pontos.
3. Experiência simples, intuitiva e fácil de demonstrar — 15 pontos.
4. Criatividade e diferenciação — 15 pontos.
5. Identidade visual e comunicação — 10 pontos.
6. Qualidade técnica e publicação correta — 10 pontos.

Em caso de conflito, preservar primeiro a clareza do problema e o fluxo funcional. Evitar efeitos visuais ou recursos que aumentem o risco sem melhorar a demonstração.

## Escopo aprovado

- Nome definitivo aprovado: **GiroCerto**.
- Conceito aprovado: um assistente de decisão para reduzir perdas de produtos próximos do vencimento em supermercados.
- Público principal: líder ou encarregado de perecíveis e prevenção de perdas.
- Público secundário: gerente geral da loja, interessado no resultado consolidado.
- Proposta de valor: indicar os itens mais urgentes e sugerir uma ação simples — remarcação, oferta, reposicionamento ou doação — mostrando impacto estimado.
- Tema principal: IA aplicada ao varejo.
- Temas complementares: Analytics, Gestão por Indicadores, Supply Chain e ESG.
- As sugestões podem ser simuladas com regras locais e dados fictícios; não alegar que há IA real se não houver integração de modelo.
- Páginas aprovadas:
  1. **Visão do dia:** perdas evitáveis, itens críticos e impacto estimado.
  2. **Prioridades:** lista filtrável de produtos próximos do vencimento.
  3. **Plano de ação:** simulação da recomendação e confirmação da ação.
- Fluxo de demonstração: identificar um risco na visão do dia, abrir o item prioritário, simular uma ação e mostrar o impacto.
- Não trocar o nome definitivo sem nova aprovação da usuária e do grupo.

## Método de desenvolvimento

1. **Alinhamento:** confirmar problema, público, integrantes, prazo e responsável por cada parte.
2. **Escopo:** escrever uma frase do problema, uma frase da solução, três telas e um único fluxo principal; classificar todas as funcionalidades com MoSCoW.
3. **Protótipo inicial:** criar navegação entre as três telas e completar primeiro o fluxo central com dados fictícios.
4. **Validação:** conferir cada critério da banca, uso em celular e computador, textos, estados vazios e erros visíveis.
5. **Polimento:** identidade visual, apresentação, roteiro de demonstração e revisão do código.
6. **Entrega:** somente após aprovação, publicar, conferir links e integrantes e preencher o Google Forms; nunca pressionar “Enviar” sem autorização final da usuária.

## Priorização obrigatória com MoSCoW

Todo pedido, funcionalidade ou melhoria deve entrar em uma destas categorias:

- **Must have:** indispensável para cumprir as regras, executar o fluxo principal ou apresentar o projeto. Sem isso, a entrega não está pronta.
- **Should have:** importante e valioso, mas a demonstração ainda funciona sem isso. Fazer somente depois de todos os Must.
- **Could have:** melhoria desejável de acabamento ou diferenciação. Fazer apenas se houver tempo seguro.
- **Won't have for now:** explicitamente fora desta versão. Registrar para evitar que volte ao escopo durante o desenvolvimento.

Regras de aplicação:

- Concluir e verificar todos os Must antes de iniciar itens Should.
- Não iniciar itens Could enquanto existir Must incompleto ou com erro.
- Qualquer mudança que promova ou rebaixe um item entre categorias precisa ser registrada em `docs/DECISOES.md`.
- Se surgir um novo Must, informar o impacto no prazo e indicar o que precisa sair ou ser rebaixado.
- Tratar os requisitos obrigatórios da AppJam como Must, sem negociação.
- Revisar a lista MoSCoW no início e no fim de cada etapa.

## Limites de escopo

- Preferir HTML, CSS e JavaScript simples enquanto o grupo não aprovar outra pilha.
- Não criar autenticação, painel administrativo, banco de dados ou backend para o primeiro protótipo.
- Não integrar IA apenas para usar a palavra “IA”; o benefício deve aparecer no fluxo.
- Não aumentar o número de telas. Modais e estados internos devem continuar pertencendo a uma das três páginas.
- Congelar o MVP assim que todos os Must estiverem funcionais; ideias adicionais entram como Could ou Won't for now.

## Qualidade e verificação

- Toda ação principal da demonstração precisa funcionar sem recarregar a página ou depender da internet, exceto o carregamento pelo GitHub Pages.
- Não deixar botões principais sem efeito.
- Usar dados fictícios plausíveis e marcá-los como demonstração quando necessário.
- Conferir legibilidade, contraste, navegação por teclado básica e layout responsivo.
- Antes de declarar uma etapa concluída, revisar o resultado contra os requisitos e registrar pendências reais.
- Nunca afirmar que testes, publicação ou integrações foram concluídos sem verificá-los.

## Trabalho em grupo e uso de agentes

- Manter uma pessoa responsável por cada arquivo ou área quando houver trabalho simultâneo.
- Não permitir que dois agentes editem o mesmo arquivo ao mesmo tempo.
- Só usar subagentes ou trabalho paralelo quando a usuária pedir, e preferir tarefas independentes como pesquisa, revisão e testes.
- O agente principal consolida os resultados e apresenta uma única recomendação ao grupo.
- Não substituir decisões do grupo por decisões automáticas do agente.

## Formato das atualizações

Ao terminar uma etapa, informar:

- o que ficou pronto;
- o que foi verificado;
- o que ainda falta;
- qual é a próxima decisão que precisa de aprovação.
