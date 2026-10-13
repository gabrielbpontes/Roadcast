# Roadcast 🚦
### Previsão da Ocorrência de Sinistros em Rodovias Federais Brasileiras com Machine Learning

O **Roadcast** é um projeto desenvolvido como parte do Trabalho de Conclusão de Curso (TCC) da graduação em Ciência de Dados para Negócios da Universidade Federal da Paraíba (UFPB). A pesquisa investiga a aplicação de técnicas de *Machine Learning* na previsão da ocorrência de sinistros de trânsito em trechos de rodovias federais brasileiras, utilizando dados históricos e características espaciais e temporais.

## 🎓 Sobre o Projeto

Os sinistros de trânsito representam um importante desafio para a segurança viária, tornando relevante o desenvolvimento de abordagens analíticas capazes de identificar padrões relacionados à sua ocorrência.

Nesse contexto, o projeto propõe utilizar técnicas de Ciência de Dados e Aprendizado de Máquina para investigar a capacidade de modelos preditivos de estimar a ocorrência de sinistros em determinados trechos rodoviários e períodos de tempo.

A pesquisa estrutura o problema como uma tarefa de classificação binária, na qual cada observação representa um trecho rodoviário em determinado período:

- **Classe 1 — Ocorrência:** registro de pelo menos um sinistro no trecho durante o período analisado.
- **Classe 0 — Não ocorrência registrada:** ausência de registros de sinistros no trecho durante o período analisado.

O estudo busca avaliar o desempenho dos modelos e compreender quais características espaciais, temporais e viárias apresentam relevância para as previsões.

## 🎯 Objetivos

### Objetivo geral

Investigar a aplicação de técnicas de *Machine Learning* na previsão da ocorrência de sinistros de trânsito em trechos de rodovias federais brasileiras, a partir de dados históricos e de características relevantes do contexto rodoviário.

### Objetivos específicos

- Obter, organizar e preparar dados históricos de sinistros de trânsito.
- Caracterizar os padrões espaciais e temporais das ocorrências.
- Construir uma base analítica que represente períodos com e sem sinistros registrados.
- Desenvolver e comparar modelos de classificação para a previsão de ocorrência.
- Avaliar o desempenho preditivo por meio de métricas adequadas ao problema.
- Interpretar as variáveis relevantes para as previsões e discutir os resultados à luz da literatura científica.

## 📊 Fontes de Dados

A principal fonte de dados é a base de dados abertos da Polícia Rodoviária Federal (PRF), que disponibiliza registros de sinistros ocorridos em rodovias federais brasileiras.

Fontes complementares podem ser utilizadas para incorporar informações sobre características da infraestrutura rodoviária, volume de tráfego e condições meteorológicas, conforme sua relevância para o problema de pesquisa.

Os dados são submetidos a procedimentos de preparação, tratamento e análise, visando garantir sua consistência e adequação às etapas de modelagem.

- [Dados Abertos da PRF](https://www.gov.br/prf/pt-br/acesso-a-informacao/dados-abertos/dados-abertos-da-prf)
- [Departamento Nacional de Infraestrutura de Transportes (DNIT)](https://www.gov.br/dnit/pt-br)
- [Instituto Nacional de Meteorologia (INMET)](https://portal.inmet.gov.br/)

## 🧪 Metodologia

O desenvolvimento da pesquisa compreende as seguintes etapas:

1. **Aquisição e preparação dos dados:** obtenção, integração, tratamento e organização das bases utilizadas.
2. **Análise exploratória:** investigação da distribuição dos registros e dos padrões espaciais e temporais dos sinistros.
3. **Construção da base analítica:** definição das unidades de análise e da variável-alvo, contemplando trechos e períodos com e sem sinistros registrados.
4. **Engenharia de atributos:** criação e seleção de variáveis preditoras relevantes, respeitando a disponibilidade das informações no momento da previsão.
5. **Desenvolvimento dos modelos:** treinamento e comparação de abordagens de classificação, incluindo modelos de referência e algoritmos de Aprendizado de Máquina.
6. **Avaliação dos modelos:** análise do desempenho preditivo por meio de métricas apropriadas, com estratégias de validação temporal.
7. **Interpretação e discussão dos resultados:** identificação de padrões relevantes, análise das contribuições das variáveis e discussão das limitações e implicações dos resultados.

## 🤖 Tecnologias

O projeto utiliza ferramentas e bibliotecas do ecossistema de Ciência de Dados e Aprendizado de Máquina, incluindo:

- **Python** — processamento e análise de dados, desenvolvimento dos modelos e experimentação.
- **Pandas e NumPy** — manipulação de dados e operações numéricas.
- **Scikit-learn** — preparação de dados, treinamento, comparação e avaliação dos modelos.
- **XGBoost** — implementação de modelos de *gradient boosting*, quando aplicável à estratégia de modelagem.
- **Matplotlib e Seaborn** — visualização e análise exploratória.
- **Jupyter Notebook** — documentação e execução de análises experimentais.
- **Git e GitHub** — versionamento e organização do código.

## 📁 Estrutura do Repositório

A organização do repositório busca separar os dados, as análises exploratórias, o código-fonte e os resultados produzidos ao longo da pesquisa.

```text
roadcast/
├── data/
│   ├── raw/
│   ├── processed/
│   └── README.md
├── notebooks/
├── src/
├── reports/
├── requirements.txt
├── .gitignore
└── README.md
```

- `data/raw/`: dados originais, quando permitido armazená-los localmente.
- `data/processed/`: dados tratados e preparados para análise.
- `notebooks/`: notebooks de exploração, experimentação e avaliação.
- `src/`: módulos reutilizáveis para processamento, engenharia de atributos e modelagem.
- `reports/`: relatórios, gráficos e materiais complementares da pesquisa.
- `requirements.txt`: dependências necessárias para reproduzir o ambiente Python.
- `.gitignore`: arquivos e diretórios que não devem ser versionados.

Os conjuntos de dados não são necessariamente armazenados no GitHub. Sua disponibilização segue as condições de uso, as limitações de tamanho e as boas práticas de versionamento.

## 📈 Avaliação e Interpretação

A avaliação dos modelos considera métricas compatíveis com a classificação binária e com a possível distribuição desbalanceada das classes, incluindo precisão (*precision*), revocação (*recall*), F1-score e área sob a curva Precisão-Revocação (PR-AUC).

A validação temporal permite avaliar o comportamento dos modelos em períodos posteriores aos utilizados no treinamento. Quando aplicável, técnicas de interpretabilidade auxiliam na investigação das variáveis relevantes para as previsões.

## ⚠️ Considerações e Limitações

O Roadcast possui finalidade acadêmica e investigativa, não constituindo um sistema operacional de prevenção de sinistros ou de gerenciamento de tráfego.

A ausência de registros em determinado trecho e período é interpretada como ausência de sinistros registrados na base utilizada, não sendo necessariamente uma confirmação de que nenhum evento ocorreu.

Os resultados são interpretados em termos de padrões e associações preditivas, sem estabelecer relações de causalidade entre as variáveis analisadas e a ocorrência de sinistros.

## 🎓 Contexto Acadêmico

- **Curso:** Ciência de Dados para Negócios
- **Instituição:** Universidade Federal da Paraíba (UFPB)
- **Trabalho:** Trabalho de Conclusão de Curso (TCC)
- **Área de pesquisa:** Ciência de Dados, Aprendizado de Máquina e Segurança Viária

---

*Roadcast — Ciência de Dados aplicada à compreensão e à previsão de sinistros de trânsito.*
