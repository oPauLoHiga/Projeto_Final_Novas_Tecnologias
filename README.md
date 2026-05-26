# Trabalho Final Pratico - Python & Pandas

## Tema 1: Desempenho Academico de Estudantes

Este projeto apresenta uma analise exploratoria da base **Student Performance Dataset**, do UCI Machine Learning Repository. O objetivo e investigar fatores associados ao desempenho academico de estudantes, usando Python, Pandas e visualizacoes estatisticas.

A base principal utilizada foi `student-por.csv`, referente ao desempenho em Portugues, pois ela possui 649 registros e atende ao requisito minimo do trabalho. A base `student-mat.csv`, referente a Matematica, foi usada apenas como comparacao complementar.

## Arquivos do projeto

- `projeto_final.ipynb`: notebook principal com todo o codigo, graficos, tabelas e interpretacoes.
- `student-por.csv`: base principal da analise, com 649 registros e 33 colunas.
- `student-mat.csv`: base complementar, usada para comparacao final entre disciplinas.
- `README.md`: instrucoes para executar e entender o projeto.

## Base de dados

Fonte: UCI Machine Learning Repository  
Dataset: Student Performance  
Link: https://archive.ics.uci.edu/dataset/320/student+performance

A base contem informacoes de estudantes portugueses do ensino medio, incluindo notas em tres periodos (`G1`, `G2`, `G3`), tempo de estudo, faltas, apoio familiar, consumo de alcool, historico de reprovacoes e dados familiares.

A variavel principal da analise e `G3`, que representa a nota final do estudante em escala de 0 a 20.

## Bibliotecas utilizadas

O notebook utiliza as seguintes bibliotecas:

```python
import numpy
import pandas as pd
import matplotlib
import seaborn
import IPython
```

Para executar em ambiente local, instale as dependencias com:

```bash
pip install numpy pandas matplotlib seaborn ipython jupyter notebook
```

No Google Colab, essas bibliotecas normalmente ja estao disponiveis.

## Como executar no PyCharm

1. Abra a pasta do projeto no PyCharm:

```text
C:\Users\paulo\OneDrive\Documentos\Estudos\Novas_Tecnologias\Projeto_Final_Novas_Tecnologias
```

2. Configure um interpretador Python para o projeto. Recomenda-se usar Python 3.11 ou superior com as bibliotecas instaladas.

3. Instale as dependencias pelo terminal do PyCharm:

```bash
pip install numpy pandas matplotlib seaborn ipython jupyter notebook
```

4. Abra o arquivo `projeto_final.ipynb`.

5. Garanta que os arquivos `student-por.csv` e `student-mat.csv` estejam na mesma pasta do notebook.

6. Execute as celulas em ordem, do inicio ao fim. No PyCharm, tambem e possivel usar a opcao de executar todas as celulas do notebook.

## Como executar em Jupyter ou Google Colab

1. Abra o arquivo `projeto_final.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab.
2. Garanta que os arquivos `student-por.csv` e `student-mat.csv` estejam na mesma pasta do notebook.
3. Execute as celulas em ordem, do inicio ao fim.
4. Use a opcao `Run all` para verificar se o notebook executa completamente sem erros.

O carregamento da base no notebook usa Pandas. Se voce testar esse trecho separado no PyCharm, use o exemplo completo abaixo para evitar erro de `pd` nao definido:

```python
from pathlib import Path
import pandas as pd

BASE_DIR = Path.cwd()
df_raw = pd.read_csv(BASE_DIR / 'student-por.csv', sep=';', encoding='utf-8')
df_mat = pd.read_csv(BASE_DIR / 'student-mat.csv', sep=';', encoding='utf-8')
```

Se aparecer erro de arquivo nao encontrado, confira se o terminal/kernel do PyCharm esta executando dentro da pasta do projeto. O separador `sep=';'` e obrigatorio porque os arquivos CSV desta base nao usam virgula como separador.

## Estrutura do notebook

O notebook esta organizado nas seguintes secoes:

1. Configuracao do ambiente
2. Carregamento dos dados
3. Compreensao inicial da base
4. Dicionario de dados
5. Limpeza e tratamento
6. Transformacao e criacao de indicadores derivados
7. Outliers com metodo IQR
8. Analise das 8 perguntas-guia
9. Analise de correlacao e mapa de calor
10. Visualizacoes obrigatorias
11. Interpretacao estatistica
12. Indicadores sinteticos
13. Comparacao opcional com Matematica
14. Conclusoes e limitacoes

## Perguntas respondidas

O notebook responde as 8 perguntas-guia do Tema 1:

1. Qual e a relacao entre tempo de estudo semanal (`studytime`) e nota final (`G3`)?
2. Estudantes que ja reprovaram antes (`failures > 0`) tem desempenho inferior?
3. O apoio educacional da familia (`famsup`) influencia a aprovacao final?
4. Existe diferenca de desempenho entre escolas (`school`) e entre sexos (`sex`)?
5. Como o consumo de alcool (`Dalc`, `Walc`) se correlaciona com a nota final?
6. Como criar um indice de risco academico combinando notas parciais, faltas e reprovacoes anteriores?
7. Quais variaveis tem maior correlacao positiva e negativa com `G3`?
8. Como construir uma tabela pivo de nota media por escola e nivel educacional dos pais?

## Tecnicas obrigatorias demonstradas

O notebook inclui as tecnicas exigidas nas orientacoes:

- `pd.read_csv()` com `sep=';'`
- `df.info()` e `df.describe()`
- `isna()`, `fillna()` e `dropna()`
- `drop_duplicates()`
- `str.strip()`, `str.lower()` e `str.upper()`
- `pd.to_datetime()`
- `groupby()` com `agg()`
- `pd.crosstab()`
- `np.where()` e `np.select()`
- `pd.cut()` e `pd.qcut()`
- `pd.pivot_table()`
- `df.corr()`
- Metodo IQR para outliers em duas colunas
- `df.apply(lambda)`
- Groupby multinivel com multiplas metricas

## Graficos obrigatorios

O notebook tambem inclui os 7 tipos de graficos solicitados:

- Grafico de barras
- Histograma
- Grafico de dispersao
- Grafico de linha
- Box plot
- Mapa de calor de correlacao
- Barras empilhadas

Todos os graficos possuem titulo, rotulos nos eixos e interpretacao em Markdown logo apos a celula de codigo.

## Indicadores criados

Foram criados indicadores e variaveis derivadas, incluindo:

- `aprovado`
- `teve_reprovacao`
- `alcool_total`
- `media_parcial`
- `faixa_faltas`
- `faixa_etaria`
- `educ_pais_media`
- `nivel_educ_pais`
- `quartil_media_parcial`
- `perfil_estudo`
- `score_risco`
- `risco_academico`

## Principais resultados

Alguns resultados encontrados na analise:

- A media geral de `G3` foi 11.91.
- A taxa de aprovacao foi 84.59%.
- Estudantes sem reprovacao anterior tiveram media 12.51 em `G3`.
- Estudantes com reprovacao anterior tiveram media 8.59 em `G3`.
- O tempo de estudo apresentou tendencia positiva: estudantes no menor nivel de estudo tiveram media 10.84, enquanto o nivel 3 chegou a media 13.23.
- O consumo de alcool teve correlacao negativa fraca com a nota final.
- As maiores correlacoes com `G3` foram `G2`, `media_parcial` e `G1`.
- O grupo de risco academico alto teve media 8.39 e aprovacao de 41.73%.

## Observacoes importantes

A base nao possui coluna de data real. Por isso, a coluna `data_processamento` foi criada apenas para demonstrar o uso de `pd.to_datetime()`, conforme solicitado nas orientacoes tecnicas.

O indice de risco academico nao usa diretamente `G3`, porque `G3` e a variavel final que esta sendo analisada. Para evitar uma analise circular, o indice usa `G1`, `G2`, faltas, reprovacoes anteriores, tempo de estudo e consumo medio de alcool.

## Limitacoes

Os dados sao observacionais, portanto a analise identifica associacoes, mas nao prova causalidade. Alem disso, a base representa estudantes de um contexto especifico em Portugal, o que limita a generalizacao para outros paises ou realidades escolares.

## Autor

Projeto desenvolvido para a disciplina de Inteligencia Artificial / Ciencia de Dados, como trabalho final pratico de Python e Pandas.
