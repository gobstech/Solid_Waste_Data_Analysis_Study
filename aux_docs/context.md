# Contexto do projeto

> Fonte: seção **1 INTRODUÇÃO** e capítulo **2 PROCEDIMENTOS METODOLÓGICOS** do relatório
> [`docs/Relatorio_Grupo1.pdf`](../docs/Relatorio_Grupo1.pdf).

## Contexto da pesquisa

Um grupo de pesquisadores da cidade de São Paulo deseja, a partir dos dados sobre resíduos sólidos
reunidos em uma tabela disponibilizada pela prefeitura, analisá-los para propor meios mais eficientes
de gerenciamento de lixo nas futuras políticas públicas da cidade.

O interesse não é meramente descritivo: a análise deve subsidiar decisões de destinação no contexto
da **transição energética**, definindo qual parcela do resíduo gerado na cidade deve ser encaminhada
a biodigestores e a unidades de compostagem e qual parcela apresenta características adequadas à
incineração com recuperação de energia.

A proposta está em consonância com a Política Nacional de Resíduos Sólidos (Lei nº 12.305, de 2 de
agosto de 2010) e com os instrumentos de planejamento municipal, entre os quais o Plano de Gestão
Integrada de Resíduos Sólidos (PGIRS). A existência de marcos legais, contudo, não assegura por si só
a eficiência do gerenciamento: essa eficiência depende também das características dos resíduos
efetivamente gerados e das condições em que se apresentam.

A decisão de destinação depende diretamente de duas propriedades físico-químicas do material:

- **Teor de umidade** — condiciona a rota biológica: frações com elevado conteúdo de água e de
  matéria orgânica são as que melhor respondem à biodigestão anaeróbia e à compostagem.
- **Poder calorífico** — condiciona a rota térmica: apenas frações capazes de liberar energia
  suficiente na combustão justificam, técnica e economicamente, a recuperação energética.

As duas propriedades são interdependentes, pois a água presente no resíduo não contribui para a
liberação de energia e ainda consome parte do calor gerado na vaporização. Encaminhar resíduo úmido a
um incinerador, ou resíduo seco a um biodigestor, significa desperdiçar capacidade instalada e
recursos públicos.

## Problema de pesquisa

De que forma os recursos da estatística descritiva permitem transformar os registros brutos da base
de resíduos sólidos do município em informação capaz de orientar a triagem entre as rotas de
destinação disponíveis, considerando o perfil das amostras coletadas e a possível relação entre o
teor de umidade e o poder calorífico do material?

## Objetivos

**Geral** — apresentar uma análise descritiva estruturada da base de dados de resíduos sólidos,
demonstrando a importância da estatística como instrumento de apoio à interpretação e à tomada de
decisão em políticas públicas.

**Específicos**

1. Identificar e classificar corretamente as variáveis relevantes;
2. Organizar os dados em distribuições de frequência absoluta, relativa e acumulada;
3. Representar graficamente cada variável por meio do gráfico adequado ao seu tipo;
4. Calcular e interpretar as medidas de tendência central de cada variável, indicando sempre a
   respectiva unidade de medida;
5. Discutir os resultados obtidos, apontando limitações e preparando o estudo de correlação entre as
   variáveis quantitativas, previsto para a etapa seguinte do projeto.

## Base de dados

A base utilizada é o arquivo [`tables/Solid_waste_pt.xlsx`](../tables/Solid_waste_pt.xlsx), planilha
com os registros de caracterização de resíduos sólidos do município de São Paulo disponibilizados
pela prefeitura. Cada observação corresponde a uma amostra de resíduo caracterizada em laboratório.
A planilha reúne **11 variáveis**, das quais **3** foram selecionadas para esta etapa, com
**n = 290** observações.

### Variáveis disponíveis na planilha

**Qualitativas**

- `Regiao_Coleta` — região da cidade onde foi feita a coleta
- `Tipo_Residuo` — tipo de resíduo
- `Origem_Residuo` — origem do resíduo (setor gerador)
- `Metodo_Destinacao` — método de destinação

**Quantitativas**

- `Massa_Coletada_kg` — massa coletada (kg)
- `Densidade_Residuo_kgm3` — densidade aparente do resíduo (in natura) (kg/m³)
- `Umidade_Residuo_pct` — teor de umidade (%)
- `Distancia_Destinacao_km` — distância até destinação (km)
- `Custo_Coleta_Transporte_RS_ton` — custo da coleta / transporte (R$/ton)
- `Indice_Reciclabilidade_pct` — índice de reciclabilidade (%)
- `Poder_Calorifico_MJkg` — poder calorífico (MJ/kg)

### Variáveis selecionadas para a análise

| Variável (planilha) | Descrição | Unidade | Classificação |
| --- | --- | --- | --- |
| `Origem_Residuo` | Setor gerador da amostra de resíduo | Categoria (sem unidade métrica) | Qualitativa nominal |
| `Umidade_Residuo_pct` | Percentual de água contido na massa da amostra | Porcentagem (%) | Quantitativa contínua |
| `Poder_Calorifico_MJkg` | Energia liberada pela combustão de 1 kg da amostra | Megajoule por quilograma (MJ/kg) | Quantitativa contínua |

`Origem_Residuo` é nominal porque suas quatro categorias — Residencial, Comercial, Industrial e
Serviços de Saúde — apenas identificam grupos, sem ordem ou hierarquia natural. `Umidade_Residuo_pct`
e `Poder_Calorifico_MJkg` são contínuas porque podem assumir qualquer valor real dentro do intervalo
de medição, limitadas apenas pela precisão do instrumento.

### Justificativa da escolha

Umidade e poder calorífico foram selecionados porque entre eles existe uma relação física conhecida e
teoricamente esperada — espera-se relação inversa —, o que permitirá um estudo consistente de
correlação na etapa seguinte. `Origem_Residuo` foi escolhida como **variável de estratificação**:
permite verificar se o perfil observado no conjunto se mantém quando as amostras são separadas por
setor gerador, além de informar a própria composição da amostra.

## Ferramentas utilizadas

Todo o processamento foi realizado em **Python**, em ambiente **Google Colab**, com as bibliotecas
**pandas** (leitura da planilha, distribuições de frequência e medidas resumo), **matplotlib** e
**seaborn** (representações gráficas). Também foram utilizados **Visual Studio Code** e **Excel**.
Foram elaborados três notebooks independentes, um para cada variável.
