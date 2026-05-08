# Planejamento de Execução: Case Study Hipótese Capital

Este planejamento detalha os passos técnicos para cumprir as três fases do case, focando na precisão dos cálculos financeiros e na usabilidade das ferramentas solicitadas.

## Fluxo de Trabalho e Tarefas

### 1. Preparação dos Dados (Fundação)
- [ ] **Carregamento:** Ler `proxies.csv` e `marcacoes.csv`.
- [ ] **Tratamento Temporal:** Converter datas e garantir que ambos os datasets compartilhem o mesmo calendário de dias úteis.
- [ ] **Cálculo de Retornos:** Gerar retornos diários logarítmicos ou percentuais para as proxies.

### 2. Fase 1: Projeção Ex Ante (fase_1.ipynb)
*Objetivo: Estimar o valor pós-M10 (30/12/2025) usando média simples dos retornos de OLEO3 e FUEL3.*
- [ ] **Implementação da Lógica:** Criar a série de retornos médios (50% OLEO3, 50% FUEL3).
- [ ] **Acumulação:** Partir do valor de M10 (397,14) e aplicar os retornos acumulados dia a dia.
- [ ] **Criação da Ferramenta:** Função `estimar_valor_ex_ante(data)` que retorna o valor exato para qualquer input após M10.
- [ ] **Análise Crítica:** Documentar limitações (ex: falta de prêmio de risco, volatilidade não capturada).

### 3. Fase 2: Reestimativa Ex Post (fase_2.ipynb)
*Objetivo: Conectar M10 a M11 (325,66) preservando a volatilidade das proxies, apesar da queda do ativo.*
- [ ] **Cálculo do Gap:** Identificar a diferença entre a projeção baseada puramente em proxies e o valor real de M11.
- [ ] **Método de Ajuste:** Implementar uma técnica de "fração de ajuste" ou "drift corretivo" distribuído ao longo do semestre.
- [ ] **Criação da Ferramenta:** Função `estimar_valor_ex_post(data)` para consulta entre M10 e M11.
- [ ] **Reflexão Quantitativa:** Explicar como o "gap" foi distribuído (linearmente nos retornos vs. ajuste no preço final).

### 4. Fase 3: Visualização Comparativa (fase_3.ipynb)
*Objetivo: Comparar a "expectativa" (Ex Ante) com a "realidade" (Ex Post).*
- [ ] **Gráfico Integrado:** Plotar M1 a M11 como pontos, e as duas trajetórias entre M10 e M11.
- [ ] **Análise de Divergência:** Plotar o gráfico de resíduos (Ex Ante - Ex Post) ao longo do tempo.
- [ ] **Insights:** Identificar o ponto de inflexão onde o problema de captação (específico da empresa) começou a pesar mais que o setor.

### 5. Finalização e Documentação
- [ ] **Apresentação:** Criar o PPT com a defesa das decisões técnicas e trade-offs.
- [ ] **Repositório:** Garantir commits progressivos e README claro.

## Cronograma Sugerido (Urgente - Hoje)
1. **Próxima hora:** Finalizar Fase 1 e ferramenta de input.
2. **Segunda hora:** Resolver o desafio matemático da Fase 2 (Ajuste Ex Post).
3. **Terceira hora:** Visualizações e reflexões analíticas.
