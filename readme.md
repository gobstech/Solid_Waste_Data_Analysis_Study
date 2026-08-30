# Solid_Waste_Data_Analysis_Study

Estudo estatístico descritivo sobre dados de resíduos sólidos do município de São Paulo — PUC-Campinas,
Escola Politécnica, Engenharia de Computação, disciplina de Estatística e Análise de Dados.

[Português](#português) · [English](#english)

---

# Português

## Contexto

Um grupo de pesquisadores da cidade de São Paulo deseja, a partir dos dados sobre resíduos sólidos
reunidos em uma tabela disponibilizada pela prefeitura, analisá-los para propor meios mais eficientes
de gerenciamento de lixo nas futuras políticas públicas da cidade.

O interesse não é meramente descritivo: a análise deve subsidiar decisões de destinação no contexto da
**transição energética**, definindo qual parcela do resíduo deve ser encaminhada a biodigestores e a
unidades de compostagem e qual apresenta características adequadas à incineração com recuperação de
energia. Essa decisão depende de duas propriedades físico-químicas do material: o **teor de umidade**,
que condiciona a rota biológica, e o **poder calorífico**, que condiciona a rota térmica. Como a água
não contribui para a liberação de energia e ainda consome parte do calor gerado na vaporização,
encaminhar resíduo úmido a um incinerador — ou resíduo seco a um biodigestor — significa desperdiçar
capacidade instalada e recursos públicos.

A proposta está em consonância com a Política Nacional de Resíduos Sólidos (Lei nº 12.305/2010) e com
o Plano de Gestão Integrada de Resíduos Sólidos (PGIRS) do município.

O contexto completo, com problema de pesquisa e objetivos, está em
[aux_docs/context.md](aux_docs/context.md).

## Base de dados

A base é o arquivo [tables/Solid_waste_pt.xlsx](tables/Solid_waste_pt.xlsx), com os registros de
caracterização de resíduos sólidos disponibilizados pela prefeitura. Cada linha corresponde a uma
amostra caracterizada em laboratório. A planilha reúne 11 variáveis; esta etapa do projeto analisa 3
delas, com **n = 290** observações.

| Variável (planilha) | Descrição | Unidade | Classificação |
| --- | --- | --- | --- |
| `Origem_Residuo` | Setor gerador da amostra | Categoria | Qualitativa nominal |
| `Umidade_Residuo_pct` | Percentual de água na massa da amostra | % | Quantitativa contínua |
| `Poder_Calorifico_MJkg` | Energia liberada pela combustão de 1 kg | MJ/kg | Quantitativa contínua |

## Principais resultados

- **Origem do resíduo** — predominância residencial: 143 amostras (49,31%); moda = Residencial.
- **Teor de umidade** — média 37,01%, mediana 32,30%, faixa de 2,0% a 81,6%. A distribuição é
  nitidamente **bimodal** (um grupo seco, entre 2% e 20%, e um grupo úmido, entre 55% e 75%), de modo
  que a média isolada descreve um resíduo que quase não existe na amostra.
- **Poder calorífico** — média 12,24 MJ/kg, mediana 11,95 MJ/kg, faixa de 1,0 a 26,3 MJ/kg.

A leitura completa dos resultados está no relatório em [docs/](docs/).

## Estrutura de pastas

```
solid_waste_Data_Analysis_Study/
├── src/                                # Notebooks da análise (um por variável)
│   ├── quali_var1.ipynb                # Origem do resíduo: frequências, barras, setores, moda
│   ├── quant1_graficos_e_medidas.ipynb # Teor de umidade: classes, histogramas, média/moda/mediana
│   ├── quant2_graficos_e_medidas.ipynb # Poder calorífico: classes, histogramas, média/moda/mediana
│   ├── quali_var_test.ipynb            # Rascunho da análise qualitativa
│   └── quali_var_test.py               # Versão .py do rascunho
├── tables/                             # Base de dados analisada
│   └── Solid_waste_pt.xlsx             # 11 variáveis, n = 290 observações
├── docs/                               # Entregas e documentação do projeto
│   ├── Relatorio_Grupo1.pdf                      # Relatório final (versão entregue)
│   ├── Estatistica_Projeto_1_Relatorio.1.1.docx  # Relatório em formato editável
│   └── descrição_datasets.pdf                    # Descrição dos datasets da disciplina
├── aux_src/                            # Material de apoio de código (referência, fora da análise)
│   ├── notebooks/                      # Notebooks de exemplo de distribuições de frequência
│   │   ├── 1_Tab_varquali.ipynb            # tabela de variável qualitativa
│   │   ├── 2_Tab_vardiscreta.ipynb         # tabela de variável quantitativa discreta
│   │   ├── 3_Tab_varcontinua_classes.ipynb # tabela de variável contínua agrupada em classes
│   │   ├── varqual.ipynb
│   │   └── varquants.ipynb
│   └── python_files/                   # Versões .py dos notebooks de apoio
│       └── varqual.py
├── aux_docs/                           # Material de apoio de documentação
│   ├── context.md                                  # contexto, problema de pesquisa e variáveis
│   ├── 2-Python - Distribuições de Frequência.pdf  # material teórico da disciplina
│   ├── dados_projeto1.xlsx                         # dados de exemplo
│   └── exemplo tabela.xlsx                         # tabela de exemplo
└── readme.md
```

## Instalação

Pré-requisito: Python 3.10 ou superior.

1. Clone o repositório:

```bash
git clone https://github.com/gobstech/Solid_Waste_Data_Analysis_Study.git
```

2. Entre na pasta do projeto:

```bash
cd Solid_Waste_Data_Analysis_Study
```

3. Crie e ative um ambiente virtual.

Windows (PowerShell):

```bash
python -m venv .venv; .\.venv\Scripts\Activate.ps1
```

Linux / macOS:

```bash
python3 -m venv .venv && source .venv/bin/activate
```

4. Instale as dependências:

```bash
pip install pandas matplotlib seaborn openpyxl jupyter
```

> `openpyxl` é necessário para que o `pandas` leia os arquivos `.xlsx` da pasta `tables/`.

## Como executar

Os notebooks de `src/` carregam a planilha pelo caminho relativo `./Solid_waste_pt.xlsx`, como no
Google Colab. Antes de executá-los localmente, copie a base para dentro de `src/`:

```bash
cp tables/Solid_waste_pt.xlsx src/
```

Em seguida, abra os notebooks de uma destas formas:

- **Localmente**, com o ambiente virtual ativado:

```bash
jupyter notebook src
```

- **No Visual Studio Code**, abrindo o notebook e selecionando o interpretador do ambiente virtual
  `.venv` como kernel.
- **No Google Colab**, enviando o arquivo `.ipynb` desejado e fazendo o upload de
  `tables/Solid_waste_pt.xlsx` na seção *Files*.

Cada notebook é independente e cobre uma variável: leitura da base, distribuições de frequência,
gráficos e medidas de tendência central.

## Documentos do projeto

- [docs/Relatorio_Grupo1.pdf](docs/Relatorio_Grupo1.pdf) — relatório final entregue, com resumo,
  metodologia, resultados, discussão, conclusão e apêndices.
- [docs/Estatistica_Projeto_1_Relatorio.1.1.docx](docs/Estatistica_Projeto_1_Relatorio.1.1.docx) —
  mesma versão em formato editável.
- [docs/descrição_datasets.pdf](docs/descrição_datasets.pdf) — descrição dos datasets oferecidos na
  disciplina.

## Autores

Enzo Marchi Romera · Gabriel de Oliveira Baptista · Leonardo de Moura Gomes Machado ·
Renan Henrique Martin de Souza

Orientação: Prof.ª Dr.ª Maria Beatriz Ferreira Leite — PUC-Campinas, agosto de 2026.

---

# English

## Context

A group of researchers from the city of São Paulo intends to analyze the solid waste data gathered in
a table published by the city government, in order to propose more efficient waste management
approaches for the city's future public policies.

The interest is not merely descriptive: the analysis is meant to support disposal decisions in the
context of the **energy transition**, determining which fraction of the waste should be directed to
biodigesters and composting facilities and which is suitable for incineration with energy recovery.
That decision depends on two physicochemical properties of the material: **moisture content**, which
governs the biological route, and **calorific value**, which governs the thermal route. Since water
contributes no energy and consumes part of the heat generated during vaporization, sending wet waste
to an incinerator — or dry waste to a biodigester — wastes installed capacity and public funds.

The study is aligned with the Brazilian National Solid Waste Policy (Law 12.305/2010) and with the
municipal Integrated Solid Waste Management Plan (PGIRS).

The full context, including the research problem and objectives, is in
[aux_docs/context.md](aux_docs/context.md) (in Portuguese).

## Dataset

The dataset is [tables/Solid_waste_pt.xlsx](tables/Solid_waste_pt.xlsx), containing the solid waste
characterization records published by the city government. Each row is one laboratory-characterized
sample. The spreadsheet holds 11 variables; this stage of the project analyzes 3 of them, with
**n = 290** observations.

| Variable (spreadsheet) | Description | Unit | Classification |
| --- | --- | --- | --- |
| `Origem_Residuo` | Generating sector of the sample | Category | Nominal qualitative |
| `Umidade_Residuo_pct` | Water percentage in the sample mass | % | Continuous quantitative |
| `Poder_Calorifico_MJkg` | Energy released by burning 1 kg | MJ/kg | Continuous quantitative |

## Key results

- **Waste origin** — residential waste predominates: 143 samples (49.31%); mode = Residential.
- **Moisture content** — mean 37.01%, median 32.30%, range 2.0% to 81.6%. The distribution is clearly
  **bimodal** (a dry group between 2% and 20%, and a wet group between 55% and 75%), so the mean alone
  describes a waste profile that barely exists in the sample.
- **Calorific value** — mean 12.24 MJ/kg, median 11.95 MJ/kg, range 1.0 to 26.3 MJ/kg.

The full discussion of results is in the report under [docs/](docs/) (in Portuguese).

## Folder structure

```
solid_waste_Data_Analysis_Study/
├── src/                                # Analysis notebooks (one per variable)
│   ├── quali_var1.ipynb                # Waste origin: frequencies, bar/pie charts, mode
│   ├── quant1_graficos_e_medidas.ipynb # Moisture: class intervals, histograms, mean/mode/median
│   ├── quant2_graficos_e_medidas.ipynb # Calorific value: classes, histograms, mean/mode/median
│   ├── quali_var_test.ipynb            # Draft of the qualitative analysis
│   └── quali_var_test.py               # .py version of the draft
├── tables/                             # Dataset under analysis
│   └── Solid_waste_pt.xlsx             # 11 variables, n = 290 observations
├── docs/                               # Project deliverables and documentation
│   ├── Relatorio_Grupo1.pdf                      # Final report (submitted version)
│   ├── Estatistica_Projeto_1_Relatorio.1.1.docx  # Report in editable format
│   └── descrição_datasets.pdf                    # Description of the course datasets
├── aux_src/                            # Supporting code material (reference, not the analysis)
│   ├── notebooks/                      # Example notebooks on frequency distributions
│   │   ├── 1_Tab_varquali.ipynb            # qualitative variable table
│   │   ├── 2_Tab_vardiscreta.ipynb         # discrete quantitative variable table
│   │   ├── 3_Tab_varcontinua_classes.ipynb # continuous variable grouped into classes
│   │   ├── varqual.ipynb
│   │   └── varquants.ipynb
│   └── python_files/                   # .py versions of the supporting notebooks
│       └── varqual.py
├── aux_docs/                           # Supporting documentation material
│   ├── context.md                                  # context, research problem and variables
│   ├── 2-Python - Distribuições de Frequência.pdf  # course theory material
│   ├── dados_projeto1.xlsx                         # sample data
│   └── exemplo tabela.xlsx                         # sample table
└── readme.md
```

## Installation

Requirement: Python 3.10 or newer.

1. Clone the repository:

```bash
git clone https://github.com/gobstech/Solid_Waste_Data_Analysis_Study.git
```

2. Enter the project folder:

```bash
cd Solid_Waste_Data_Analysis_Study
```

3. Create and activate a virtual environment.

Windows (PowerShell):

```bash
python -m venv .venv; .\.venv\Scripts\Activate.ps1
```

Linux / macOS:

```bash
python3 -m venv .venv && source .venv/bin/activate
```

4. Install the dependencies:

```bash
pip install pandas matplotlib seaborn openpyxl jupyter
```

> `openpyxl` is required for `pandas` to read the `.xlsx` files in `tables/`.

## Running the project

The notebooks in `src/` load the spreadsheet from the relative path `./Solid_waste_pt.xlsx`, as they
do on Google Colab. Before running them locally, copy the dataset into `src/`:

```bash
cp tables/Solid_waste_pt.xlsx src/
```

Then open the notebooks in one of these ways:

- **Locally**, with the virtual environment activated:

```bash
jupyter notebook src
```

- **In Visual Studio Code**, opening the notebook and selecting the `.venv` interpreter as the kernel.
- **On Google Colab**, uploading the desired `.ipynb` file and `tables/Solid_waste_pt.xlsx` in the
  *Files* section.

Each notebook is self-contained and covers one variable: reading the dataset, frequency
distributions, charts and measures of central tendency.

## Project documents

- [docs/Relatorio_Grupo1.pdf](docs/Relatorio_Grupo1.pdf) — final submitted report, with abstract,
  methodology, results, discussion, conclusion and appendices.
- [docs/Estatistica_Projeto_1_Relatorio.1.1.docx](docs/Estatistica_Projeto_1_Relatorio.1.1.docx) —
  the same version in editable format.
- [docs/descrição_datasets.pdf](docs/descrição_datasets.pdf) — description of the course datasets.

## Authors

Enzo Marchi Romera · Gabriel de Oliveira Baptista · Leonardo de Moura Gomes Machado ·
Renan Henrique Martin de Souza

Advisor: Prof. Dr. Maria Beatriz Ferreira Leite — PUC-Campinas, August 2026.
