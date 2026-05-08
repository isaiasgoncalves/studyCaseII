# Projeto: studyCaseII (Case Charles River - Hipótese Capital)

## Visão Geral do Projeto
Este projeto é um estudo de caso para o processo seletivo da Charles River, focado em **Data Science aplicado ao Asset Management**. O objetivo é estimar a trajetória de valor de uma empresa de capital fechado do setor de petróleo (ativa em exploração e produção) utilizando proxies de mercado (`OLEO3` e `FUEL3`).

A gestão do fundo multimercado da Hipótese Capital precisa de ferramentas para preencher as lacunas entre as marcações semestrais independentes, lidando com o desafio de reconciliar dinâmicas de mercado líquido com ativos ilíquidos.

### Principais Desafios
- **Reconciliação:** Ajustar trajetórias quando os proxies e o ativo divergem (ex: proxies sobem, ativo cai).
- **Projeção Ex Ante:** Estimativa em tempo real após a última marcação conhecida.
- **Trajetória Ex Post:** Reconstrução histórica "real" entre dois pontos fixos de marcação.

### Tecnologias e Ferramentas
- **Linguagem:** Python 3.
- **Bibliotecas:** `pandas` (séries temporais), `numpy` (cálculos matemáticos), `matplotlib`/`seaborn` (visualizações).
- **Entregáveis:** Notebooks funcionais, ferramenta de consulta por data e apresentação de slides.

### Estrutura de Dados
- `data/proxies.csv`: Preços diários de OLEO3 e FUEL3 (Jun/2021 a Jun/2026).
- `data/marcacoes.csv`: 11 marcações semestrais (M1 a M11).

## Restrições do Agente
- **Proteção de Arquivos:** NÃO edite o arquivo `instructions.md` sob nenhuma circunstância.
- **Consistência:** As estimativas devem partir rigorosamente dos valores de marcação nas datas especificadas.
