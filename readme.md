# Solid_Waste_Data_Analysis_Study

[Português](#português) · [English](#english)

---

# Português

## Contexto

Um grupo de pesquisadores da cidade de São Paulo deseja, a partir dos dados sobre resíduos sólidos
reunidos em uma tabela disponibilizada pela prefeitura, analisá-los para propor meios mais eficientes
de gerenciamento de lixo nas futuras políticas públicas da cidade.

Para isso, os dados foram organizados em variáveis qualitativas e quantitativas:

**Qualitativas**

- Região da cidade onde foi feita a coleta
- Tipo de resíduo
- Origem do resíduo (setor gerador)
- Método de destinação

**Quantitativas**

- Massa coletada (kg)
- Densidade aparente do resíduo (in natura) (kg/m³)
- Teor de umidade (%)
- Distância até destinação (km)
- Custo da coleta / transporte (R$/ton)
- Índice de reciclabilidade (%)
- Poder calorífico (poder de aproveitamento) (MJ/kg)

A análise é conduzida sobre um subconjunto dessas variáveis (1 qualitativa e 2 quantitativas),
utilizando Python, Google Colab, Visual Studio Code e Excel.

O detalhamento completo do contexto está em [aux_docs/context.md](aux_docs/context.md).

## Estrutura de pastas

```
solid_waste_Data_Analysis_Study/
├── src/                    # Código da análise do projeto
├── tables/                 # Base de dados analisada
│   └── Solid_waste_pt.xlsx
├── docs/                   # Documentação do projeto
│   └── descrição_datasets.pdf
├── aux_src/                # Material de apoio de código (referência, não faz parte da análise)
│   ├── notebooks/          # Notebooks de exemplo de distribuições de frequência
│   │   ├── 1_Tab_varquali.ipynb            # tabela de variável qualitativa
│   │   ├── 2_Tab_vardiscreta.ipynb         # tabela de variável quantitativa discreta
│   │   ├── 3_Tab_varcontinua_classes.ipynb # tabela de variável contínua agrupada em classes
│   │   ├── varqual.ipynb
│   │   └── varquants.ipynb
│   └── python_files/       # Versões .py dos notebooks de apoio
│       └── varqual.py
├── aux_docs/               # Material de apoio de documentação
│   ├── context.md                                  # contexto e variáveis do estudo
│   ├── 2-Python - Distribuições de Frequência.pdf  # material teórico
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
pip install pandas numpy openpyxl matplotlib jupyter
```

> `openpyxl` é necessário para que o `pandas` leia os arquivos `.xlsx` da pasta `tables/`.

## Como executar

Os notebooks podem ser abertos de duas formas:

- **Localmente**, com o ambiente virtual ativado:

```bash
jupyter notebook
```

- **No Google Colab**, enviando o arquivo `.ipynb` desejado e fazendo o upload da planilha
  correspondente da pasta `tables/`.

No Visual Studio Code, basta abrir o notebook e selecionar o interpretador do ambiente virtual
`.venv` como kernel.

---

# English

## Context

A group of researchers from the city of São Paulo intends to analyze the solid waste data gathered in
a table published by the city government, in order to propose more efficient waste management
approaches for the city's future public policies.

To that end, the data was organized into qualitative and quantitative variables:

**Qualitative**

- City region where the collection took place
- Waste type
- Waste origin (generating sector)
- Disposal method

**Quantitative**

- Collected mass (kg)
- Apparent density of the waste (as collected) (kg/m³)
- Moisture content (%)
- Distance to disposal site (km)
- Collection / transport cost (R$/ton)
- Recyclability index (%)
- Calorific value (energy recovery potential) (MJ/kg)

The analysis is carried out on a subset of these variables (1 qualitative and 2 quantitative), using
Python, Google Colab, Visual Studio Code and Excel.

The full context description is available in [aux_docs/context.md](aux_docs/context.md) (in
Portuguese).

## Folder structure

```
solid_waste_Data_Analysis_Study/
├── src/                    # Project analysis code
├── tables/                 # Dataset under analysis
│   └── Solid_waste_pt.xlsx
├── docs/                   # Project documentation
│   └── descrição_datasets.pdf
├── aux_src/                # Supporting code material (reference only, not part of the analysis)
│   ├── notebooks/          # Example notebooks on frequency distributions
│   │   ├── 1_Tab_varquali.ipynb            # qualitative variable table
│   │   ├── 2_Tab_vardiscreta.ipynb         # discrete quantitative variable table
│   │   ├── 3_Tab_varcontinua_classes.ipynb # continuous variable grouped into classes
│   │   ├── varqual.ipynb
│   │   └── varquants.ipynb
│   └── python_files/       # .py versions of the supporting notebooks
│       └── varqual.py
├── aux_docs/               # Supporting documentation material
│   ├── context.md                                  # study context and variables
│   ├── 2-Python - Distribuições de Frequência.pdf  # theory material
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
pip install pandas numpy openpyxl matplotlib jupyter
```

> `openpyxl` is required for `pandas` to read the `.xlsx` files in `tables/`.

## Running the project

The notebooks can be opened in two ways:

- **Locally**, with the virtual environment activated:

```bash
jupyter notebook
```

- **On Google Colab**, by uploading the desired `.ipynb` file along with the corresponding
  spreadsheet from `tables/`.

In Visual Studio Code, open the notebook and select the `.venv` virtual environment interpreter as
the kernel.
