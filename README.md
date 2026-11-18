# Roadcast 🚦

### Previsão de Ocorrência de Sinistros em Rodovias Federais Brasileiras com Técnicas de Machine Learning

O **Roadcast** é um projeto desenvolvido como parte do Trabalho de Conclusão de Curso (TCC) da graduação em Ciência de Dados para Negócios da Universidade Federal da Paraíba (UFPB).

A pesquisa investiga a aplicação de técnicas de *Machine Learning* na previsão da ocorrência diária de sinistros de trânsito em rodovias federais brasileiras, utilizando dados históricos disponibilizados pela Polícia Rodoviária Federal (PRF).

## 🎓 Sobre o Projeto

Os sinistros de trânsito representam um importante desafio para a segurança viária, tornando relevante o desenvolvimento de abordagens analíticas capazes de identificar padrões associados à sua ocorrência.

Nesse contexto, o Roadcast investiga a capacidade de modelos preditivos de estimar a ocorrência de sinistros a partir de informações históricas e temporais.

O problema foi estruturado como uma tarefa de **classificação binária**, na qual cada observação representa uma combinação de Unidade Federativa (UF), Rodovia Federal (BR) e dia.

A variável-alvo possui duas classes:

- **Classe 1 — Ocorrência:** registro de pelo menos um sinistro na combinação UF × BR durante o dia analisado.
- **Classe 0 — Não ocorrência registrada:** ausência de registros de sinistros na combinação UF × BR durante o dia analisado.

A unidade de análise adotada é, portanto, **UF × BR × dia**.

O estudo busca avaliar o desempenho de diferentes abordagens preditivas, investigar a contribuição dos atributos utilizados e compreender as limitações dos modelos em diferentes contextos de frequência de sinistros.

O projeto não pretende prever a localização exata, a gravidade ou a quantidade de sinistros, mas estimar a probabilidade de ocorrência de pelo menos um registro diário na unidade espacial considerada.

## 🎯 Objetivos

### Objetivo geral

Investigar a aplicação de técnicas de *Machine Learning* na previsão da ocorrência diária de sinistros de trânsito em rodovias federais brasileiras, a partir de dados históricos da Polícia Rodoviária Federal.

### Objetivos específicos

- Obter, consolidar e preparar dados históricos de sinistros de trânsito registrados pela PRF.
- Investigar a distribuição temporal e espacial dos registros e sua adequação ao problema preditivo.
- Construir uma base analítica diária contemplando períodos com e sem sinistros registrados.
- Desenvolver atributos temporais e históricos, respeitando a disponibilidade das informações anteriores ao dia previsto.
- Implementar e comparar diferentes abordagens de classificação binária.
- Avaliar o desempenho preditivo utilizando métricas apropriadas e divisão cronológica dos dados.
- Investigar a importância dos atributos e as diferenças de desempenho entre rodovias.
- Analisar as limitações dos modelos e possíveis estratégias de melhoria.

## 📊 Fontes de Dados

A principal fonte de dados do Roadcast é a base pública de sinistros da **Polícia Rodoviária Federal (PRF)**, na modalidade de registros agrupados por ocorrência.

Foram utilizados dados referentes ao período de **2017 a 2025**, inicialmente consolidados em uma base com **632.713 registros de sinistros**.

Após os procedimentos de preparação, foi construída uma base diária com as seguintes características:

| Característica | Quantidade |
|---|---:|
| Combinações UF × BR | 230 |
| Período de modelagem | 2018–2025 |
| Observações diárias | 672.060 |
| Dias com sinistros registrados | 228.575 (34,01%) |
| Dias sem sinistros registrados | 443.485 (65,99%) |

As 230 combinações UF × BR foram definidas com base nas unidades observadas em 2017, utilizado também para fornecer informações históricas necessárias à construção dos atributos iniciais.

A ausência de registros em determinada combinação UF × BR e dia é interpretada como ausência de sinistros **registrados na base utilizada**, não constituindo necessariamente uma confirmação de que nenhum evento ocorreu.

**Fontes oficiais:**

- [Dados Abertos da PRF](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf)
- [Dicionário de Acidentes da PRF](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dicionario-acidentes)

## 🧪 Metodologia

O desenvolvimento experimental foi organizado nas seguintes etapas:

1. **Aquisição e consolidação dos dados:** integração dos arquivos anuais da PRF, padronização de campos e análise de consistência.
2. **Análise exploratória:** investigação da distribuição dos registros, das características das rodovias e da qualidade das informações disponíveis.
3. **Construção da base analítica:** definição das combinações UF × BR e criação de um painel diário com a variável-alvo binária.
4. **Engenharia de atributos:** construção de variáveis temporais e históricas utilizando informações disponíveis antes do dia previsto.
5. **Desenvolvimento dos modelos:** implementação de abordagens de referência e algoritmos de classificação.
6. **Avaliação temporal:** treinamento, validação, escolha de limiares e avaliação em períodos cronologicamente posteriores.
7. **Interpretação dos resultados:** análise das métricas, importância dos atributos e desempenho por rodovia.
8. **Experimento complementar:** investigação de limiares adaptativos para rodovias com diferentes frequências históricas de sinistros.

### Engenharia de atributos

Os modelos utilizam informações relacionadas a:

- Unidade Federativa e rodovia federal;
- Ano, mês, dia da semana, dia do ano e trimestre;
- Indicadores de finais de semana e feriados nacionais;
- Quantidade de sinistros registrados nos últimos 7, 14 e 30 dias;
- Quantidade de dias com sinistros registrados nessas mesmas janelas;
- Indicadores de ocorrência em dias anteriores.

Os atributos históricos foram construídos utilizando informações anteriores ao dia previsto, com o objetivo de evitar vazamento temporal de informações.

### Modelos avaliados

Foram implementadas três abordagens:

| Modelo | Descrição |
|---|---|
| Baseline histórico | Estimativa baseada na proporção de dias com sinistros registrados nos últimos 30 dias |
| Regressão Logística | Modelo linear de classificação utilizado como referência |
| XGBoost | Algoritmo de *gradient boosting* baseado em árvores de decisão |

### Divisão temporal

Para respeitar a natureza temporal do problema, foi adotada uma divisão cronológica:

| Conjunto | Período | Observações |
|---|---|---:|
| Treinamento | 2018–2023 | 503.930 |
| Validação | 2024 | 84.180 |
| Teste | 2025 | 83.950 |

O conjunto de treinamento foi utilizado para ajustar os modelos, enquanto a validação permitiu comparar abordagens e selecionar os limiares de classificação.

O conjunto de teste de 2025 foi utilizado na avaliação final dos modelos originais.

### Métricas de avaliação

Foram consideradas as seguintes métricas:

- Average Precision (AP);
- ROC-AUC;
- Precisão (*precision*);
- Revocação (*recall*);
- F1-score;
- F2-score;
- Matriz de confusão.

A Average Precision foi calculada utilizando a implementação `average_precision_score` do Scikit-learn.

O **F2-score** foi utilizado como critério para selecionar os limiares de classificação, atribuindo maior importância à revocação, considerando o interesse em reduzir a quantidade de dias com sinistros não identificados.

## 📈 Resultados

Os resultados obtidos no conjunto de teste de **2025** foram:

| Modelo | AP | ROC-AUC | Precisão | Revocação | F1-score | F2-score |
|---|---:|---:|---:|---:|---:|---:|
| Baseline histórico | 0,8121 | 0,8789 | 52,62% | **92,61%** | 0,6711 | 0,8039 |
| Regressão Logística | 0,8261 | 0,8812 | 53,59% | 92,60% | 0,6789 | **0,8083** |
| XGBoost | **0,8285** | **0,8833** | **53,97%** | 92,25% | **0,6810** | 0,8079 |

O XGBoost apresentou os maiores valores de Average Precision, ROC-AUC, precisão e F1-score.

A Regressão Logística obteve o maior F2-score, embora a diferença em relação ao XGBoost tenha sido pequena.

O baseline histórico também apresentou desempenho competitivo, evidenciando a relevância das informações sobre ocorrências anteriores.

### Resultados do XGBoost

O XGBoost foi mantido como principal referência para as análises detalhadas, utilizando o limiar de classificação de **0,17**, selecionado na validação de 2024.

No conjunto de teste de 2025, foram obtidos:

| Resultado | Quantidade |
|---|---:|
| Verdadeiros positivos | 26.985 |
| Falsos positivos | 23.011 |
| Falsos negativos | 2.267 |
| Verdadeiros negativos | 31.687 |

O modelo identificou corretamente **26.985 dos 29.252 dias com sinistros registrados**, correspondendo a uma revocação global de **92,25%**.

Entretanto, esse desempenho agregado não representa necessariamente a capacidade preditiva em todas as rodovias analisadas.

### Importância dos atributos

A análise de importância dos atributos do XGBoost indicou maior contribuição das variáveis relacionadas ao histórico recente de sinistros, especialmente:

- Quantidade de sinistros nos últimos 30 dias;
- Quantidade de sinistros nos últimos 14 dias;
- Quantidade de dias com sinistros nos últimos 30 dias.

Esses resultados reforçam a relevância do comportamento histórico das ocorrências para a capacidade preditiva do modelo.

A importância dos atributos representa sua contribuição para o funcionamento do modelo e não estabelece relações de causalidade.

## 🔎 Análise Complementar

### Desempenho por frequência de sinistros

A avaliação individual das combinações UF × BR revelou diferenças importantes de desempenho.

No teste de 2025, as combinações foram agrupadas retrospectivamente de acordo com a frequência observada de dias com sinistros:

| Frequência de ocorrência | Revocação agregada |
|---|---:|
| Muito baixa (0–10%) | 5,64% |
| Baixa (10–30%) | 70,27% |
| Moderada (30–60%) | 99,48% |
| Alta (60–100%) | 100,00% |

Embora o modelo tenha alcançado revocação global superior a 92%, apresentou desempenho substancialmente inferior nas rodovias com sinistros pouco frequentes.

As combinações com frequência de até 30% concentraram **2.230 dos 2.267 falsos negativos**, correspondendo a aproximadamente 98,37% dos dias positivos não identificados.

Essa análise evidencia a importância de investigar o desempenho dos modelos além das métricas globais.

### Experimento com limiares adaptativos

Diante da heterogeneidade observada, foi realizado um experimento complementar para investigar a utilização de diferentes limiares de classificação conforme a frequência histórica de sinistros de cada combinação UF × BR.

As faixas históricas foram definidas com dados de treinamento de 2018 a 2023, e as configurações foram comparadas utilizando a validação de 2024.

Os resultados demonstraram que limiares menores conseguem aumentar a revocação nas rodovias de menor frequência, mas também provocam crescimento significativo na quantidade de falsos positivos.

Nenhuma das 25 configurações adaptativas avaliadas apresentou F2-score global superior ao limiar original de 0,17 na validação.

Por esse motivo, os limiares adaptativos foram mantidos como um experimento complementar, sem substituir a configuração principal do XGBoost.

## 🤖 Tecnologias

O projeto foi desenvolvido utilizando ferramentas e bibliotecas do ecossistema Python:

- **Python:** processamento de dados e desenvolvimento dos experimentos;
- **Pandas e NumPy:** manipulação, transformação e análise de dados;
- **Scikit-learn:** pré-processamento, modelagem e avaliação;
- **XGBoost:** implementação do modelo baseado em *gradient boosting*;
- **Holidays:** identificação de feriados nacionais;
- **Jupyter Notebook:** execução e documentação dos experimentos;
- **VS Code:** ambiente de desenvolvimento;
- **Git e GitHub:** versionamento e disponibilização do projeto.

## 📁 Estrutura do Repositório

```text
Roadcast/
├── data/
│   └── ...                  # Dados utilizados localmente
├── notebooks/
│   └── roadcast_pipeline.ipynb       # Notebook completo do projeto
├── src/                     # Diretório reservado para código-fonte
├── LICENSE
├── README.md
├── requirements.txt
└── .gitignore
```

O notebook `notebooks/roadcast_pipeline.ipynb` contém as etapas de preparação dos dados, construção da base analítica, engenharia de atributos, treinamento, avaliação e experimentos complementares.

Os arquivos CSV utilizados no desenvolvimento são provenientes dos dados abertos da PRF. Sua inclusão no repositório depende das configurações de versionamento e das limitações de tamanho do GitHub.

## ⚠️ Considerações e Limitações

O Roadcast possui finalidade acadêmica e investigativa, não constituindo um sistema operacional de prevenção de sinistros ou gerenciamento de tráfego.

Entre as principais limitações do estudo estão:

- A ausência de registros na PRF não garante a inexistência de sinistros em determinado dia.
- A unidade espacial UF × BR não permite identificar o local exato de uma possível ocorrência.
- O modelo não incorpora diretamente informações sobre volume de tráfego, extensão das rodovias ou condições meteorológicas detalhadas.
- A seleção das combinações UF × BR com base nos registros de 2017 limita a abrangência das unidades analisadas.
- O desempenho é heterogêneo, especialmente nas rodovias com baixa frequência de sinistros registrados.
- A utilização operacional dos atributos históricos dependeria da disponibilidade e atualização dos registros da PRF antes do momento da previsão.

Os resultados devem ser interpretados como associações preditivas, sem estabelecer relações de causalidade entre os atributos utilizados e a ocorrência de sinistros.

A avaliação realizada é retrospectiva e não representa uma validação operacional de um sistema de alertas em tempo real.

## 🎓 Contexto Acadêmico

- **Curso:** Ciência de Dados para Negócios
- **Instituição:** Universidade Federal da Paraíba (UFPB)
- **Modalidade:** Trabalho de Conclusão de Curso — Relato Monográfico
- **Área de pesquisa:** Ciência de Dados, Aprendizado de Máquina e Segurança Viária

### Status do Projeto

A etapa experimental do Roadcast foi concluída, contemplando preparação dos dados, desenvolvimento dos modelos, avaliação temporal e investigação das limitações identificadas.

O projeto encontra-se na fase de **redação da monografia em LaTeX, utilizando o Overleaf**.

---

*Roadcast — Ciência de Dados aplicada à compreensão e à previsão de sinistros de trânsito.*