# Trabalho Final Pratico - Python & Pandas

## Tema 1: Desempenho Academico de Estudantes

Este trabalho analisa a base **Student Performance Dataset**, disponivel no UCI Machine Learning Repository. A ideia principal e entender quais fatores aparecem associados ao desempenho final dos estudantes.

A base usada foi `student-por.csv`, com dados da disciplina de Portugues. Ela tem **649 registros** e **33 colunas**, entao atende aos requisitos minimos definidos no enunciado.

## Arquivos

- `projeto_final.ipynb`: notebook com codigo, tabelas, graficos e interpretacoes.
- `student-por.csv`: base de dados usada na analise.
- `README.md`: explicacao do projeto e instrucoes de execucao.

## Fonte dos dados

Fonte: UCI Machine Learning Repository  
Dataset: Student Performance  
Link: https://archive.ics.uci.edu/dataset/320/student+performance

A base contem informacoes de estudantes portugueses do ensino medio. Entre as variaveis estao as notas `G1`, `G2` e `G3`, tempo de estudo, faltas, apoio familiar, consumo de alcool, historico de reprovacoes e escolaridade dos pais.

A variavel principal do trabalho e `G3`, que representa a nota final do estudante em uma escala de 0 a 20.

## Como executar

1. Abra a pasta do projeto:

```text
C:\Users\paulo\OneDrive\Documentos\Estudos\Novas_Tecnologias\Projeto_Final_Novas_Tecnologias
```

2. Instale as bibliotecas usadas no notebook:

```bash
pip install numpy pandas matplotlib seaborn ipython jupyter notebook
```

3. Abra `projeto_final.ipynb` no PyCharm, Jupyter Notebook, JupyterLab ou Google Colab.

4. Confira se `student-por.csv` esta na mesma pasta do notebook.

5. Execute as celulas em ordem.

O CSV usa ponto e virgula como separador. Por isso, a leitura da base foi feita assim:

```python
from pathlib import Path
import pandas as pd

BASE_DIR = Path.cwd()
ARQUIVO_DADOS = BASE_DIR / 'student-por.csv'
df_raw = pd.read_csv(ARQUIVO_DADOS, sep=';', encoding='utf-8')
```

## Organizacao do notebook

O notebook segue esta ordem:

1. Configuracao do ambiente
2. Carregamento dos dados
3. Compreensao inicial da base
4. Dicionario de dados
5. Limpeza e tratamento
6. Criacao de novas colunas
7. Deteccao de outliers com IQR
8. Resposta das 8 perguntas-guia
9. Correlacao e mapa de calor
10. Graficos obrigatorios
11. Interpretacao estatistica
12. Indicadores sinteticos
13. Conclusoes e limitacoes

## Perguntas da analise

1. Qual e a relacao entre tempo de estudo semanal (`studytime`) e nota final (`G3`)?
2. Estudantes com reprovacoes anteriores (`failures > 0`) tem desempenho inferior?
3. O apoio educacional da familia (`famsup`) influencia a aprovacao?
4. Existe diferenca de desempenho entre escolas e entre sexos?
5. Como o consumo de alcool (`Dalc`, `Walc`) se relaciona com a nota final?
6. Como criar um indice de risco academico?
7. Quais variaveis tem maior correlacao com `G3`?
8. Como fica a nota media por escola e escolaridade dos pais?

## Tecnicas usadas

O notebook inclui as tecnicas pedidas no enunciado:

- leitura com `pd.read_csv()`;
- inspecao com `info()` e `describe()`;
- tratamento com `isna()`, `fillna()`, `dropna()` e `drop_duplicates()`;
- padronizacao de texto com `str.strip()`, `str.lower()` e `str.upper()`;
- criacao de data com `pd.to_datetime()`;
- agrupamentos com `groupby()` e `agg()`;
- tabela cruzada com `pd.crosstab()`;
- colunas derivadas com `np.where()`, `np.select()`, `pd.cut()`, `pd.qcut()` e `apply(lambda)`;
- tabela dinamica com `pd.pivot_table()`;
- matriz de correlacao com `df.corr()`;
- outliers com metodo IQR.

## Graficos

Foram criados os 7 tipos de graficos solicitados:

- barras;
- histograma;
- dispersao;
- linha;
- box plot;
- mapa de calor;
- barras empilhadas.

Todos os graficos possuem titulo, rotulos nos eixos e uma interpretacao logo depois.

## Principais resultados

- A media geral de `G3` foi **11.91**.
- A taxa de aprovacao foi **84.59%**.
- Estudantes sem reprovacao anterior tiveram media **12.51**.
- Estudantes com reprovacao anterior tiveram media **8.59**.
- O tempo de estudo apresentou tendencia positiva: o menor nivel teve media **10.84**, enquanto o nivel 3 chegou a **13.23**.
- O consumo de alcool teve correlacao negativa fraca com a nota final.
- As maiores correlacoes com `G3` foram `G2`, `media_parcial` e `G1`.
- O grupo de risco academico alto teve media **8.39** e aprovacao de **41.73%**.

## Observacoes

A base nao possui uma coluna de data real. Para demonstrar `pd.to_datetime()`, foi criada a coluna `data_processamento`.

O indice de risco academico nao usa diretamente `G3`. Ele usa `G1`, `G2`, faltas, reprovacoes anteriores, tempo de estudo e consumo medio de alcool. Assim, a analise evita usar a propria nota final como parte do criterio de risco.

## Limitacoes

Os dados sao observacionais. Isso significa que a analise mostra associacoes, mas nao prova causa e efeito. Alem disso, os dados representam estudantes de um contexto especifico em Portugal, entao os resultados nao devem ser generalizados para todos os estudantes.
