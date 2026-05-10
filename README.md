# Case II - Análise Quantitativa - Hipótese Capital

Este repositório contém a resolução do estudo de caso focado em **Data Science aplicado ao Asset Management**. O objetivo principal é a modelagem da trajetória de valor de uma empresa de capital fechado do setor de Exploração e Produção (E&P) de Petróleo, utilizando proxies de mercado líquido para preencher lacunas de marcação.

## Contexto do Problema

A gestão de ativos ilíquidos (Private Equity/Private Credit) enfrenta o desafio de atualizar o valor de ativos que possuem apenas marcações semestrais independentes. Para garantir uma visão em tempo real do portfólio, utilizamos proxies líquidos (`OLEO3` e `FUEL3`) para estimar a trajetória do ativo entre e após as janelas de marcação oficial.

## Metodologia e Estrutura

O projeto foi dividido em três fases lógicas, representadas pelos notebooks:

### 1. Fase 1: Projeção *Ex Ante* (`fase_1.ipynb`)
*   **Objetivo:** Projetar o valor do ativo a partir da última marcação conhecida ($M_{10}$).
*   **Técnica:** Utilização de **Log-Retornos** médios das proxies.
*   **Diferencial:** Justificativa matemática para o uso de log-retornos visando evitar o viés de capitalização e garantir a aditividade dos retornos no tempo.

### 2. Fase 2: Trajetória *Ex Post* (`fase_2.ipynb`)
*   **Objetivo:** Reconstruir a trajetória histórica entre duas marcações fixas ($M_{10}$ e $M_{11}$), garantindo ancoragem nos dois pontos.
*   **Técnica:** Introdução de um **Fator de Drift ($\alpha$)** calculado analiticamente para reconciliar a divergência entre proxies e a avaliação independente, sem distorcer a volatilidade diária.

### 3. Fase 3: Reconciliação e Análise (`fase_3.ipynb`)
*   **Objetivo:** Comparar as trajetórias projetadas vs. realizadas e analisar a decomposição da divergência.
*   **Visualização:** Gráficos comparativos com foco em clareza para tomada de decisão gerencial.

## Estrutura de diretórios

```text
├── assets/             # Gráficos e exportações visuais
├── data/               # Datasets (proxies.csv e marcacoes.csv)
├── docs/               # Planejamento e suporte à apresentação
├── fase_1.ipynb        # Modelagem Ex Ante
├── fase_2.ipynb        # Modelagem Ex Post (Ancoragem)
├── fase_3.ipynb        # Comparativo e Visualização Final
└── GEMINI.md           # Notas de desenvolvimento
```

## Como Executar

1.  Certifique-se de ter o Python 3.10+ instalado.
2.  Instale as dependências necessárias:
    ```bash
    pip install pandas numpy matplotlib seaborn
    ```
3.  Execute os notebooks na ordem numérica (`fase_1` -> `fase_2` -> `fase_3`).

## Resultados Principais

*   **Preservação de Dinâmica:** O modelo *Ex Post* conseguiu manter os "picos e vales" do setor de petróleo (capturados pelas proxies) enquanto convergiu exatamente para o valor de fechamento auditado.
*   **Ferramenta de Consulta:** O código permite a consulta do valor estimado para qualquer data intermediária, facilitando o reporte de performance intra-semestral.

---
