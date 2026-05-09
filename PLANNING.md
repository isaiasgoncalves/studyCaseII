# Planejamento de Execução: Case Study Hipótese Capital

## 1. Fase 1: Projeção Ex Ante (CONCLUÍDO ✅)
*Objetivo: Estimar o valor diário da empresa após M10 usando proxies de mercado.*

### Atividades Realizadas:
- **Tratamento de Dados:** Importação de CSVs, conversão de tipos e indexação temporal (`datetime`).
- **Engenharia de Atributos:** 
    - Cálculo de **Retornos Simples** individuais para `OLEO3` e `FUEL3`.
    - Cálculo do **Retorno do Portfólio (50/50)** via média aritmética dos retornos simples (representando rebalanceamento diário).
    - Conversão para **Retorno Logarítmico** para garantir **aditividade temporal** e evitar o viés de capitalização.
- **Modelagem:** 
    - Acumulação via `cumsum()` e aplicação da fórmula $V_{M10} \cdot e^{\sum r_{log}}$.
    - Identificação de Gap: Projeção estimou **511.39** vs Realidade de **325.66** na M11.
- **Ferramenta:** Implementação da função `return_marker_estimate` com lógica **AsOf** para tratar fins de semana e feriados.
- **Análise Crítica:** Discussão sobre Choques Idiosincráticos (atraso na captação) vs Fatores Sistêmicos (setor de petróleo).

---

## 2. Fase 2: Reestimativa Ex Post (PRÓXIMO PASSO 🚀)
*Objetivo: Criar a trajetória "real" que conecta M10 a M11, ajustando a divergência observada.*

### Tarefas Planejadas:
- [ ] **Cálculo do Erro Logarítmico Total:** Diferença entre $\ln(M_{11}/M_{10})$ e a soma dos retornos das proxies.
- [ ] **Distribuição do Drift:** Calcular o ajuste diário constante ($\alpha = \text{Erro Total} / \text{Dias Úteis}$) para "puxar" a curva para o valor real.
- [ ] **Implementação da Curva Ajustada:** Aplicar o drift aos retornos diários e gerar a nova série de preços.
- [ ] **Ferramenta Ex Post:** Criar função de consulta específica para o período M10-M11.
- [ ] **Validação:** Garantir que o valor final no dia da M11 seja exatamente **325.66**.

---

## 3. Fase 3: Visualização Comparativa
*Objetivo: Mostrar o gap entre Expectativa (Fase 1) e Realidade (Fase 2).*

### Tarefas Planejadas:
- [ ] **Gráfico de Trajetórias:** Plotar as duas curvas sobrepostas.
- [ ] **Gráfico de Divergência:** Série temporal do resíduo (Ex Ante - Ex Post).
- [ ] **Análise de Inflexão:** Identificar visualmente quando os problemas de captação começaram a descolar a empresa do setor.

---

## Cronograma (Hoje)
- **Fase 1:** 100% concluída.
- **Fase 2:** Início imediato (Matemática de Ancoragem).
- **Fase 3:** Finalização e Slides.
