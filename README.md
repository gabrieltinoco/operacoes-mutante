# Laboratório: Teste de Mutação com a "Calculadora Mutante"

Bem-vindo ao trabalho prático de Teste de Mutação. O objetivo deste projeto é usar a ferramenta StrykerJS para avaliar e fortalecer uma suíte de testes que, à primeira vista, parece boa.

## Contexto

Este repositório contém uma biblioteca de cálculos simples. A suíte inicial em `test/operacoes.test.js` foi projetada para ter alta **cobertura de código**, mas esconde fraquezas que só o **teste de mutação** pode revelar. Foram adicionados casos de borda para fortalecer as asserções.

Sua missão é atuar como um engenheiro de qualidade para encontrar essas fraquezas e escrever testes mais robustos para corrigi-las.

## Tarefas

1.  **Prepare o ambiente:** Clone o repositório e rode `npm install`.
2.  **Análise Inicial:**
    - Rode `npm test` para ver os testes passando.
    - Rode `npm run coverage` para gerar os percentuais de cobertura.
3.  **Análise de Mutação:**
    - Configure o StrykerJS (`npx stryker init`).
    - Execute a análise com `npm run mutate` (equivalente a `npx stryker run`).
    - Abra o relatório HTML e analise os **mutantes que sobreviveram**.
4.  **Aprimore os Testes:**
    - Para cada mutante sobrevivente, entenda por que ele não foi "morto".
    - Adicione novos testes em `__tests__/operacoes.test.js` focados em asserções mais específicas para matar esses mutantes.
5.  **Validação Final:**
    - Rode o Stryker novamente e verifique se sua pontuação de mutação aumentou, idealmente para mais de 95%.

## Resultados desta execução

| Métrica | Inicial | Após o reforço |
| --- | ---: | ---: |
| Testes Jest aprovados | 50/50 | 59/59 |
| Statements | 85,41% | 100% |
| Branches | 58,82% | 100% |
| Funções | 100% | 100% |
| Linhas | 98,64% | 100% |
| Mutation score | 73,71% | 99,01% |

Na análise inicial do Stryker, houve 44 mutantes sobreviventes, 8 timeouts e 12 mutantes sem cobertura. Na análise final, 196 mutantes foram mortos, 2 sobreviveram e 5 tiveram timeout; os sobreviventes são mutações equivalentes nos limites do `clamp` (`<` para `<=` e `>` para `>=`), pois não alteram o valor retornado quando a entrada é exatamente o limite. Os relatórios HTML inicial e final estão em `reports/mutation/`.

O relatório escrito está em `reports/Relatorio-Teste-de-Mutacao.pdf`
