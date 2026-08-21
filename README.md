# Pandas

## 1. Estruturas fundamentais: Series, DataFrame e Index
| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| pd.Series([1, 2, 3]) | Series | Cria uma Series |
| pd.Series([1,2,3], index=['a','b','c']) | Series | Cria Series com índice personalizado |
| pd.DataFrame({...}) | DataFrame | Cria DataFrame |
| pd.DataFrame([[1,2],[3,4]]) | DataFrame | Cria DataFrame a partir de listas |
| pd.DataFrame(data, columns=[...]) | DataFrame | Define nomes das colunas |
| pd.DataFrame(data, index=[...]) | DataFrame | Define índices |
| pd.Index([1,2,3]) | Index | Cria índice simples |
| pd.Index(['a','b','c']) | Index | Cria índice textual |
| pd.MultiIndex.from_arrays(...) | Index | Cria MultiIndex a partir de arrays |
| pd.MultiIndex.from_tuples(...) | Index | Cria MultiIndex a partir de tuplas |
| pd.MultiIndex.from_product(...) | Index | Cria combinação cartesiana de níveis |
| df.index | DataFrame / Index | Acessa índice |
| df.columns | DataFrame / Index | Acessa nomes das colunas |
| s.index | Series / Index | Acessa índice da Series |
| s.name | Series | Acessa nome da Series |
| df.shape | DataFrame | Retorna (linhas, colunas) |
| df.size | DataFrame | Número total de elementos |
| df.ndim | DataFrame / Series | Número de dimensões |
| df.values | DataFrame | Retorna valores como array |
| s.values | Series | Retorna valores como array |
| df.to_numpy() | DataFrame | Converte para NumPy |
| s.to_numpy() | Series | Converte para NumPy |

## 2. Inspeção de dados
Instrução	Estrutura	Descrição
df.head()	DataFrame	Primeiras 5 linhas
df.head(10)	DataFrame	Primeiras 10 linhas
df.tail()	DataFrame	Últimas 5 linhas
df.tail(10)	DataFrame	Últimas 10 linhas
df.sample()	DataFrame	Amostra aleatória
df.sample(10)	DataFrame	10 registros aleatórios
df.info()	DataFrame	Estrutura, tipos e valores não nulos
df.describe()	DataFrame	Estatísticas descritivas numéricas
df.describe(include='all')	DataFrame	Estatísticas de todas as colunas
df.describe(include='object')	DataFrame	Estatísticas de texto/categorias
df.dtypes	DataFrame	Tipos das colunas
df.astype(...)	DataFrame / Series	Converte tipos
df.nunique()	DataFrame / Series	Número de valores únicos
df.unique()	Series	Valores únicos
df.value_counts()	Series	Frequência dos valores
df.is_unique	Series / Index	Verifica unicidade
df.index.is_unique	Index	Verifica se índice é único
df.empty	DataFrame / Series	Verifica se está vazio
df.memory_usage()	DataFrame	Memória utilizada
df.memory_usage(deep=True)	DataFrame	Memória detalhada
df.select_dtypes(...)	DataFrame	Seleciona colunas por tipo
df.columns	DataFrame	Lista nomes das colunas
df.index	DataFrame	Visualiza índice
df.axes	DataFrame	Retorna eixos
df.keys()	DataFrame	Retorna colunas
df.count()	DataFrame / Series	Conta valores não nulos
df.isna().sum()	DataFrame	Conta valores ausentes
df.duplicated().sum()	DataFrame	Conta duplicidades
df.corr()	DataFrame	Correlação entre variáveis numéricas
df.cov()	DataFrame	Covariância
df.rank()	DataFrame / Series	Calcula ranking
4. Seleção de dados
DataFrame
Instrução	Estrutura	Descrição
df['coluna']	DataFrame	Seleciona uma coluna como Series
df[['col1','col2']]	DataFrame	Seleciona várias colunas
df.loc[...]	DataFrame / Series	Seleção por rótulo
df.iloc[...]	DataFrame / Series	Seleção por posição
df.at[...]	DataFrame / Series	Acessa uma célula por rótulo
df.iat[...]	DataFrame / Series	Acessa uma célula por posição
df.loc[:, 'coluna']	DataFrame	Seleciona coluna por nome
df.loc[0:10, ['a','b']]	DataFrame	Linhas e colunas por rótulo
df.iloc[0:10, 0:2]	DataFrame	Linhas e colunas por posição
df.filter(items=[...])	DataFrame	Seleciona colunas/linhas específicas
df.filter(like='sales')	DataFrame	Seleciona nomes contendo texto
df.filter(regex='^sales')	DataFrame	Seleção usando expressão regular
Series
Instrução	Estrutura	Descrição
s[0]	Series	Acesso por índice
s.iloc[0]	Series	Acesso posicional
s.loc['A']	Series	Acesso por rótulo
s.iloc[0:5]	Series	Fatiamento posicional
s.loc['A':'D']	Series	Fatiamento por rótulo
5. Filtragem de dados
Instrução	Estrutura	Descrição
df[df['idade'] > 18]	DataFrame	Filtra condição
df[df['cidade'] == 'Recife']	DataFrame	Igualdade
df[df['valor'] != 0]	DataFrame	Diferente
df[df['valor'] >= 100]	DataFrame	Maior ou igual
df[df['valor'] <= 100]	DataFrame	Menor ou igual
df[(df['idade'] > 18) & (df['idade'] < 60)]	DataFrame	AND
`df[(df['cidade']=='Recife')	(df['cidade']=='Olinda')]`	DataFrame
df[~(df['status']=='Cancelado')]	DataFrame	NOT
df['cidade'].isin([...])	Series	Verifica pertencimento
df['idade'].between(18, 60)	Series	Intervalo
df['nome'].str.contains('ana')	Series	Procura texto
df['nome'].str.startswith('A')	Series	Começa com
df['nome'].str.endswith('a')	Series	Termina com
df.query("idade > 18")	DataFrame	Filtragem com expressão
df.query("cidade == 'Recife'")	DataFrame	Query textual
df.nlargest(10, 'valor')	DataFrame	10 maiores valores
df.nsmallest(10, 'valor')	DataFrame	10 menores valores
6. Ordenação
Instrução	Estrutura	Descrição
df.sort_values('valor')	DataFrame	Ordena coluna
df.sort_values('valor', ascending=False)	DataFrame	Ordem decrescente
df.sort_values(['cidade','valor'])	DataFrame	Ordena por várias colunas
df.sort_values(['cidade','valor'], ascending=[True,False])	DataFrame	Ordem diferente por coluna
df.sort_index()	DataFrame / Series	Ordena pelo índice
df.sort_index(ascending=False)	DataFrame / Series	Índice decrescente
s.sort_values()	Series	Ordena valores
s.sort_index()	Series	Ordena índice
df.nlargest(5, 'valor')	DataFrame	Maiores registros
df.nsmallest(5, 'valor')	DataFrame	Menores registros
7. Índice simples
Instrução	Estrutura	Descrição
df.index	Index	Obtém índice
df.index.name	Index	Obtém nome
df.index.names	Index	Obtém nomes dos níveis
df.set_index('id')	DataFrame	Define coluna como índice
df.reset_index()	DataFrame	Converte índice em coluna
df.reset_index(drop=True)	DataFrame	Remove índice
df.rename_axis('id')	DataFrame / Index	Renomeia eixo
df.reindex([...])	DataFrame	Reindexa
df.reindex(columns=[...])	DataFrame	Reordena/reindexa colunas
df.index.tolist()	Index	Converte índice em lista
df.index.unique()	Index	Índices únicos
df.index.duplicated()	Index	Detecta índices duplicados
df.index.is_monotonic_increasing	Index	Verifica ordenação crescente
df.index.is_monotonic_decreasing	Index	Verifica ordenação decrescente
8. MultiIndex / índice hierárquico
Instrução	Estrutura	Descrição
pd.MultiIndex.from_tuples(...)	Index	Cria índice hierárquico
pd.MultiIndex.from_arrays(...)	Index	Cria níveis a partir de arrays
pd.MultiIndex.from_product(...)	Index	Produto cartesiano
df.set_index(['estado','cidade'])	DataFrame	Cria MultiIndex
df.reset_index()	DataFrame	Remove MultiIndex
df.index.levels	MultiIndex	Lista níveis
df.index.codes	MultiIndex	Códigos dos níveis
df.index.names	MultiIndex	Nomes dos níveis
df.xs('PE', level='estado')	DataFrame	Seleciona nível específico
df.loc['PE']	DataFrame	Seleciona primeiro nível
df.loc[('PE','Recife')]	DataFrame	Seleciona combinação
df.swaplevel()	DataFrame	Troca níveis
df.reorder_levels(...)	DataFrame	Reorganiza níveis
df.sort_index()	DataFrame	Ordena MultiIndex
df.droplevel(...)	DataFrame / Index	Remove nível
df.unstack()	DataFrame	Transforma nível em coluna
df.stack()	DataFrame	Transforma colunas em índice
9. Operações com índices
Instrução	Estrutura	Descrição
df.set_index()	DataFrame	Define índice
df.reset_index()	DataFrame	Redefine índice
df.reindex()	DataFrame / Series	Reindexação
df.rename_axis()	DataFrame / Series	Renomeia índice/eixo
df.sort_index()	DataFrame / Series	Ordena índice
df.index.union(other)	Index	União
df.index.intersection(other)	Index	Interseção
df.index.difference(other)	Index	Diferença
df.index.symmetric_difference(other)	Index	Diferença simétrica
df.index.isin([...])	Index	Verifica pertencimento
df.index.duplicated()	Index	Detecta duplicidade
df.index.drop_duplicates()	Index	Remove índices duplicados
df.index.rename('novo')	Index	Renomeia índice
df.index.astype(...)	Index	Converte tipo
10. Valores ausentes
Instrução	Estrutura	Descrição
df.isna()	DataFrame	Detecta ausentes
df.isnull()	DataFrame	Alias de isna()
df.notna()	DataFrame	Detecta não nulos
df.isna().sum()	DataFrame	Quantidade de ausentes
df.dropna()	DataFrame / Series	Remove registros com NA
df.dropna(axis=1)	DataFrame	Remove colunas com NA
df.dropna(subset=['coluna'])	DataFrame	Remove NA de colunas específicas
df.dropna(how='all')	DataFrame	Remove somente linhas totalmente vazias
df.fillna(0)	DataFrame / Series	Substitui NA
df.fillna({'idade':0})	DataFrame	Valor específico por coluna
df.ffill()	DataFrame / Series	Propaga valor anterior
df.bfill()	DataFrame / Series	Propaga próximo valor
df.interpolate()	DataFrame / Series	Interpolação
df.replace(np.nan, 0)	DataFrame / Series	Substituição
df.isna().mean()	DataFrame	Percentual de NA
11. Operações com colunas
Instrução	Estrutura	Descrição
df['nova'] = ...	DataFrame	Cria coluna
df.assign(nova=...)	DataFrame	Cria colunas
df.insert(...)	DataFrame	Insere coluna em posição
df.drop(columns=['x'])	DataFrame	Remove coluna
df.rename(columns={'x':'y'})	DataFrame	Renomeia coluna
df.columns = [...]	DataFrame	Redefine nomes
df.columns.str.lower()	Index	Coloca nomes em minúsculo
df.columns.str.upper()	Index	Coloca nomes em maiúsculo
df.columns.str.strip()	Index	Remove espaços
df.columns.str.replace(...)	Index	Substitui caracteres
df.pop('coluna')	DataFrame	Remove e retorna coluna
df.filter(regex=...)	DataFrame	Seleciona colunas por padrão
df.select_dtypes(...)	DataFrame	Seleciona por tipo
12. Operadores de colunas
Instrução	Estrutura	Descrição
df['a'] + df['b']	DataFrame / Series	Soma
df['a'] - df['b']	DataFrame / Series	Subtração
df['a'] * df['b']	DataFrame / Series	Multiplicação
df['a'] / df['b']	DataFrame / Series	Divisão
df['a'] // df['b']	Series	Divisão inteira
df['a'] % df['b']	Series	Módulo
df['a'] ** 2	Series	Potência
df['a'].abs()	Series	Valor absoluto
df['a'].round(2)	Series	Arredondamento
df['a'].clip(0,100)	Series	Limita valores
df['a'].add(df['b'])	Series	Soma
df['a'].sub(df['b'])	Series	Subtração
df['a'].mul(df['b'])	Series	Multiplicação
df['a'].div(df['b'])	Series	Divisão
df.eval('total = preco * quantidade')	DataFrame	Operações com expressão
13. Operações matemáticas e estatísticas
Instrução	Estrutura	Descrição
df.sum()	DataFrame / Series	Soma
df.mean()	DataFrame / Series	Média
df.median()	DataFrame / Series	Mediana
df.mode()	DataFrame / Series	Moda
df.min()	DataFrame / Series	Mínimo
df.max()	DataFrame / Series	Máximo
df.std()	DataFrame / Series	Desvio padrão
df.var()	DataFrame / Series	Variância
df.sem()	DataFrame / Series	Erro padrão
df.skew()	DataFrame / Series	Assimetria
df.kurt()	DataFrame / Series	Curtose
df.quantile(0.25)	DataFrame / Series	Percentil
df.cumsum()	DataFrame / Series	Soma acumulada
df.cumprod()	DataFrame / Series	Produto acumulado
df.cummin()	DataFrame / Series	Mínimo acumulado
df.cummax()	DataFrame / Series	Máximo acumulado
df.pct_change()	Series / DataFrame	Variação percentual
14. Agregação de dados
Instrução	Estrutura	Descrição
df.sum()	DataFrame / Series	Soma
df.mean()	DataFrame / Series	Média
df.count()	DataFrame / Series	Contagem
df.min()	DataFrame / Series	Mínimo
df.max()	DataFrame / Series	Máximo
df.agg('sum')	DataFrame / Series	Agregação
df.agg(['sum','mean','max'])	DataFrame	Múltiplas agregações
df.agg({'vendas':'sum','preco':'mean'})	DataFrame	Agregações diferentes
s.agg(...)	Series	Agregação da Series
df.value_counts()	DataFrame / Series	Frequência
df.nunique()	DataFrame / Series	Quantidade de distintos
15. Agrupamento — groupby
Instrução	Estrutura	Descrição
df.groupby('categoria')	DataFrame	Agrupa por coluna
df.groupby(['estado','cidade'])	DataFrame	Agrupamento múltiplo
df.groupby('categoria').sum()	DataFrame	Soma por grupo
df.groupby('categoria').mean()	DataFrame	Média por grupo
df.groupby('categoria').count()	DataFrame	Contagem
df.groupby('categoria').size()	DataFrame	Tamanho dos grupos
df.groupby('categoria').agg(...)	DataFrame	Agregações múltiplas
df.groupby('categoria').transform(...)	DataFrame	Transforma mantendo tamanho
df.groupby('categoria').filter(...)	DataFrame	Filtra grupos
df.groupby(...).first()	DataFrame	Primeiro registro
df.groupby(...).last()	DataFrame	Último registro
df.groupby(...).nth(0)	DataFrame	Registro por posição
df.groupby(...).rank()	DataFrame	Ranking dentro dos grupos
df.groupby(...).cumcount()	DataFrame	Número sequencial dentro do grupo
df.groupby(...).cumsum()	DataFrame	Soma acumulada por grupo
Exemplo profissional
df.groupby("categoria").agg(
    vendas=("valor", "sum"),
    media=("valor", "mean"),
    quantidade=("valor", "count"),
)
16. Transformação de dados
Instrução	Estrutura	Descrição
df.map(...)	Series	Aplica função elemento a elemento
df.apply(...)	DataFrame / Series	Aplica função
df.apply(axis=1)	DataFrame	Aplica por linha
df.apply(axis=0)	DataFrame	Aplica por coluna
df.transform(...)	DataFrame / Series	Transformação mantendo dimensão
df.replace(...)	DataFrame / Series	Substitui valores
df.rename(...)	DataFrame / Series	Renomeia
df.astype(...)	DataFrame / Series	Converte tipos
df.clip(...)	DataFrame / Series	Limita valores
df.round(...)	DataFrame / Series	Arredonda
df.where(...)	DataFrame / Series	Mantém valores quando condição
df.mask(...)	DataFrame / Series	Substitui quando condição
df.pipe(...)	DataFrame / Series	Encadeia funções
17. Operações de texto
Instrução	Estrutura	Descrição
s.str.lower()	Series	Minúsculas
s.str.upper()	Series	Maiúsculas
s.str.title()	Series	Capitalização
s.str.strip()	Series	Remove espaços
s.str.lstrip()	Series	Remove espaços à esquerda
s.str.rstrip()	Series	Remove espaços à direita
s.str.replace()	Series	Substitui texto
s.str.contains()	Series	Verifica ocorrência
s.str.startswith()	Series	Verifica início
s.str.endswith()	Series	Verifica final
s.str.len()	Series	Tamanho
s.str.split()	Series	Divide texto
s.str.extract()	Series	Extrai usando regex
s.str.findall()	Series	Localiza padrões
s.str.slice()	Series	Fatiamento
s.str.zfill()	Series	Preenche com zeros
s.str.cat()	Series	Concatena strings
18. Conversão de tipos
Instrução	Estrutura	Descrição
df.astype('int')	DataFrame / Series	Inteiro
df.astype('float')	DataFrame / Series	Decimal
df.astype('string')	DataFrame / Series	String
df.astype('category')	DataFrame / Series	Categórico
pd.to_numeric(s)	Series	Converte para numérico
pd.to_numeric(s, errors='coerce')	Series	Inválidos viram NaN
pd.to_datetime(s)	Series	Converte para data
pd.to_timedelta(s)	Series	Converte para duração
pd.api.types.is_numeric_dtype()	Series	Verifica tipo numérico
pd.api.types.is_datetime64_any_dtype()	Series	Verifica datetime
19. Datas e séries temporais
Instrução	Estrutura	Descrição
pd.to_datetime()	Series	Converte para datetime
df['data'].dt.year	Series	Ano
df['data'].dt.month	Series	Mês
df['data'].dt.day	Series	Dia
df['data'].dt.hour	Series	Hora
df['data'].dt.minute	Series	Minuto
df['data'].dt.second	Series	Segundo
df['data'].dt.dayofweek	Series	Dia da semana
df['data'].dt.day_name()	Series	Nome do dia
df['data'].dt.month_name()	Series	Nome do mês
df['data'].dt.quarter	Series	Trimestre
df['data'].dt.is_month_end	Series	Final do mês
df['data'].dt.is_month_start	Series	Início do mês
df.set_index('data')	DataFrame	Define data como índice
df.loc['2026-01']	DataFrame	Seleciona período
df.loc['2026-01-01':'2026-01-31']	DataFrame	Intervalo temporal
df.resample('D')	DataFrame / Series	Reamostragem diária
df.resample('M')	DataFrame / Series	Reamostragem mensal
df.resample('Y')	DataFrame / Series	Reamostragem anual
df.shift(1)	DataFrame / Series	Desloca valores
df.diff()	DataFrame / Series	Diferença entre períodos
df.pct_change()	DataFrame / Series	Variação percentual
df.asfreq('D')	DataFrame / Series	Define frequência
20. Janelamento de dados — Windowing
Instrução	Estrutura	Descrição
s.rolling(3)	Series	Janela móvel de 3 períodos
s.rolling(3).mean()	Series	Média móvel
s.rolling(3).sum()	Series	Soma móvel
s.rolling(3).min()	Series	Mínimo móvel
s.rolling(3).max()	Series	Máximo móvel
s.rolling(3).std()	Series	Desvio padrão móvel
s.rolling('7D')	Series	Janela móvel baseada em tempo
s.expanding()	Series	Janela expansiva
s.expanding().mean()	Series	Média acumulada expansiva
s.ewm(span=7).mean()	Series	Média móvel exponencial
s.rolling(7).apply(...)	Series	Função personalizada na janela
Exemplo
df["media_7_dias"] = (
    df["vendas"]
    .rolling(7)
    .mean()
)
21. Concatenação
Instrução	Estrutura	Descrição
pd.concat([df1, df2])	DataFrame	Empilha linhas
pd.concat([df1, df2], axis=1)	DataFrame	Junta colunas
pd.concat([...], ignore_index=True)	DataFrame	Reinicia índice
pd.concat([...], keys=[...])	DataFrame	Cria índice hierárquico
22. Junções — Merge / Join
Instrução	Estrutura	Descrição
pd.merge(df1, df2)	DataFrame	Junção
pd.merge(df1, df2, on='id')	DataFrame	Join por coluna
pd.merge(..., how='inner')	DataFrame	INNER JOIN
pd.merge(..., how='left')	DataFrame	LEFT JOIN
pd.merge(..., how='right')	DataFrame	RIGHT JOIN
pd.merge(..., how='outer')	DataFrame	FULL OUTER JOIN
pd.merge(..., left_on='id1', right_on='id2')	DataFrame	Chaves diferentes
df.join(df2)	DataFrame	Join baseado no índice
df.join(df2, how='left')	DataFrame	LEFT JOIN
df.join(df2, how='outer')	DataFrame	FULL JOIN
pd.merge(..., indicator=True)	DataFrame	Identifica origem do registro
pd.merge(..., validate='1:1')	DataFrame	Valida cardinalidade
Cardinalidades importantes
1:1  → uma linha ↔ uma linha
1:N  → uma linha ↔ várias linhas
N:1  → várias linhas ↔ uma linha
N:N  → várias linhas ↔ várias linhas
23. Pivot Tables
Instrução	Estrutura	Descrição
pd.pivot_table(df)	DataFrame	Cria tabela dinâmica
pd.pivot_table(df, values='valor')	DataFrame	Define métrica
pd.pivot_table(df, index='categoria')	DataFrame	Define linhas
pd.pivot_table(df, columns='estado')	DataFrame	Define colunas
pd.pivot_table(df, index='categoria', values='valor', aggfunc='sum')	DataFrame	Soma por categoria
pd.pivot_table(..., aggfunc=['sum','mean'])	DataFrame	Várias agregações
pd.pivot_table(..., fill_value=0)	DataFrame	Preenche ausentes
pd.pivot_table(..., margins=True)	DataFrame	Adiciona totais
pd.pivot_table(..., margins_name='Total')	DataFrame	Nomeia total
24. Crosstab / tabulação cruzada
Instrução	Estrutura	Descrição
pd.crosstab(df['sexo'], df['estado'])	DataFrame	Frequência cruzada
pd.crosstab(..., normalize=True)	DataFrame	Percentual geral
pd.crosstab(..., normalize='index')	DataFrame	Percentual por linha
pd.crosstab(..., normalize='columns')	DataFrame	Percentual por coluna
pd.crosstab(..., margins=True)	DataFrame	Totais
pd.crosstab(..., values=df['valor'], aggfunc='sum')	DataFrame	Agrega valores
25. Pivot e reshape
Instrução	Estrutura	Descrição
df.pivot()	DataFrame	Transforma dados
df.pivot_table()	DataFrame	Pivot com agregação
df.melt()	DataFrame	Wide → Long
df.stack()	DataFrame	Colunas → índice
df.unstack()	DataFrame	Índice → colunas
df.explode()	DataFrame / Series	Expande listas
pd.wide_to_long()	DataFrame	Wide → Long complexo
26. Duplicidades
Instrução	Estrutura	Descrição
df.duplicated()	DataFrame	Detecta duplicados
df.duplicated(subset=['id'])	DataFrame	Detecta por coluna
df.duplicated(keep='first')	DataFrame	Mantém primeiro
df.duplicated(keep='last')	DataFrame	Mantém último
df.drop_duplicates()	DataFrame	Remove duplicados
df.drop_duplicates(subset=['id'])	DataFrame	Remove por chave
df.drop_duplicates(keep='last')	DataFrame	Mantém último
27. Limpeza de dados
Instrução	Estrutura	Descrição
df.dropna()	DataFrame	Remove valores ausentes
df.fillna()	DataFrame	Preenche ausentes
df.replace()	DataFrame	Substitui valores
df.drop_duplicates()	DataFrame	Remove duplicidades
df.rename()	DataFrame	Padroniza nomes
df.columns.str.strip()	Index	Remove espaços dos nomes
df.columns.str.lower()	Index	Padroniza para minúsculo
df.columns.str.replace(' ', '_')	Index	Padroniza separadores
pd.to_numeric()	Series	Corrige números
pd.to_datetime()	Series	Corrige datas
df.astype()	DataFrame / Series	Corrige tipos
df.clip()	DataFrame / Series	Limita valores extremos
df.query()	DataFrame	Remove/seleciona registros inválidos
df.loc[...]	DataFrame	Corrige valores condicionais
df.mask()	DataFrame	Substitui valores inválidos
df.where()	DataFrame	Mantém somente valores válidos
df.drop(columns=...)	DataFrame	Remove colunas desnecessárias
df.select_dtypes()	DataFrame	Seleciona tipos
df.convert_dtypes()	DataFrame	Converte para tipos modernos
df.infer_objects()	DataFrame	Inferência de tipos
df.clip(lower=0)	DataFrame	Elimina valores abaixo do limite
df.loc[df['idade'] < 0, 'idade'] = np.nan	DataFrame	Trata valor inválido
28. Limpeza de strings
Instrução	Estrutura	Descrição
s.str.strip()	Series	Remove espaços
s.str.lower()	Series	Normaliza caixa
s.str.upper()	Series	Caixa alta
s.str.title()	Series	Formatação de nomes
s.str.replace()	Series	Substitui caracteres
s.str.normalize()	Series	Normalização Unicode
s.str.contains()	Series	Localiza padrões
s.str.extract()	Series	Extrai padrões
s.str.split()	Series	Divide strings
s.str.cat()	Series	Concatena strings
s.str.len()	Series	Comprimento
s.str.isnumeric()	Series	Verifica numérico
s.str.isalpha()	Series	Verifica letras
s.str.isalnum()	Series	Verifica alfanumérico
29. Limpeza e padronização de nomes de colunas

Uma operação bastante comum em pipelines ETL:

Instrução	Estrutura	Descrição
df.columns = df.columns.str.lower()	Index	Minúsculas
df.columns = df.columns.str.strip()	Index	Remove espaços
df.columns = df.columns.str.replace(' ', '_')	Index	Espaços → _
df.columns = df.columns.str.replace(r'[^\w]+', '_', regex=True)	Index	Remove caracteres especiais
df.columns = df.columns.str.normalize('NFKD')	Index	Normaliza Unicode
df.columns = df.columns.str.replace(...)	Index	Padroniza nomes

Exemplo:

df.columns = (
    df.columns
    .str.strip()
    .str.lower()
    .str.replace(" ", "_")
)
29. Leitura de dados
Instrução	Estrutura	Descrição
pd.read_csv()	DataFrame	Lê CSV
pd.read_excel()	DataFrame	Lê Excel
pd.read_json()	DataFrame	Lê JSON
pd.read_sql()	DataFrame	Lê SQL
pd.read_parquet()	DataFrame	Lê Parquet
pd.read_feather()	DataFrame	Lê Feather
pd.read_pickle()	DataFrame	Lê Pickle
pd.read_html()	DataFrame	Lê tabelas HTML
30. Exportação
Instrução	Estrutura	Descrição
df.to_csv()	DataFrame	Exporta CSV
df.to_excel()	DataFrame	Exporta Excel
df.to_json()	DataFrame	Exporta JSON
df.to_sql()	DataFrame	Exporta para SQL
df.to_parquet()	DataFrame	Exporta Parquet
df.to_feather()	DataFrame	Exporta Feather
df.to_pickle()	DataFrame	Exporta Pickle
df.to_html()	DataFrame	Exporta HTML
df.to_dict()	DataFrame	Converte para dicionário
df.to_records()	DataFrame	Converte para registros
31. Comparação entre DataFrames
Instrução	Estrutura	Descrição
df1.equals(df2)	DataFrame	Verifica igualdade
df1.compare(df2)	DataFrame	Mostra diferenças
df1.align(df2)	DataFrame	Alinha índices/colunas
df1.combine(df2, func)	DataFrame	Combina DataFrames
df1.update(df2)	DataFrame	Atualiza valores
32. Operações booleanas e lógicas
Instrução	Estrutura	Descrição
s > 10	Series	Maior
s < 10	Series	Menor
s == 10	Series	Igual
s != 10	Series	Diferente
(s > 10) & (s < 20)	Series	AND
`(s < 10)	(s > 20)`	Series
~(s > 10)	Series	NOT
s.isin([...])	Series	Pertencimento
s.between(a,b)	Series	Intervalo
s.any()	Series	Pelo menos um verdadeiro
s.all()	Series	Todos verdadeiros
33. Operações entre Series e DataFrames
Instrução	Estrutura	Descrição
df.add(s)	DataFrame	Soma alinhada
df.sub(s)	DataFrame	Subtração alinhada
df.mul(s)	DataFrame	Multiplicação
df.div(s)	DataFrame	Divisão
df.dot(s)	DataFrame	Produto matricial
df.combine_first(df2)	DataFrame	Combina preenchendo ausentes
df.align(df2)	DataFrame	Alinha índices/colunas

O ponto importante aqui é que Pandas trabalha com alinhamento automático por índice.

34. Estatísticas por categoria
Instrução	Estrutura	Descrição
df.groupby('categoria')['valor'].sum()	DataFrame	Soma por categoria
df.groupby('categoria')['valor'].mean()	DataFrame	Média
df.groupby('categoria')['valor'].median()	DataFrame	Mediana
df.groupby('categoria')['valor'].std()	DataFrame	Desvio padrão
df.groupby('categoria')['valor'].min()	DataFrame	Mínimo
df.groupby('categoria')['valor'].max()	DataFrame	Máximo
df.groupby('categoria')['valor'].count()	DataFrame	Quantidade
df.groupby('categoria')['valor'].nunique()	DataFrame	Distintos
35. Ranking
Instrução	Estrutura	Descrição
s.rank()	Series	Ranking
s.rank(ascending=False)	Series	Ranking decrescente
df['valor'].rank()	Series	Ranking de coluna
df.groupby('categoria')['valor'].rank()	Series	Ranking dentro do grupo
df.nlargest(10, 'valor')	DataFrame	Top 10
df.nsmallest(10, 'valor')	DataFrame	Bottom 10
36. Amostragem
Instrução	Estrutura	Descrição
df.sample()	DataFrame	Uma amostra
df.sample(n=100)	DataFrame	100 registros
df.sample(frac=0.1)	DataFrame	10% dos dados
df.sample(frac=1)	DataFrame	Embaralha dataset
df.sample(..., random_state=42)	DataFrame	Resultado reproduzível
37. Contagem e frequência
Instrução	Estrutura	Descrição
s.value_counts()	Series	Frequência
s.value_counts(normalize=True)	Series	Frequência relativa
s.value_counts(dropna=False)	Series	Inclui NA
df.nunique()	DataFrame	Distintos por coluna
df['col'].nunique()	Series	Distintos
df.count()	DataFrame	Valores não nulos
df.size	DataFrame	Total de elementos
38. Manipulação de categorias
Instrução	Estrutura	Descrição
s.astype('category')	Series	Converte para categoria
s.cat.categories	Series	Categorias existentes
s.cat.codes	Series	Código numérico
s.cat.add_categories()	Series	Adiciona categoria
s.cat.remove_categories()	Series	Remove categoria
s.cat.rename_categories()	Series	Renomeia categorias
s.cat.reorder_categories()	Series	Reordena categorias
s.cat.set_categories()	Series	Define categorias
39. Operações com Index
Instrução	Estrutura	Descrição
index.tolist()	Index	Lista
index.to_numpy()	Index	NumPy
index.unique()	Index	Valores únicos
index.value_counts()	Index	Frequências
index.isin()	Index	Pertencimento
index.duplicated()	Index	Duplicados
index.drop_duplicates()	Index	Remove duplicados
index.union()	Index	União
index.intersection()	Index	Interseção
index.difference()	Index	Diferença
index.symmetric_difference()	Index	Diferença simétrica
index.sort_values()	Index	Ordena
index.rename()	Index	Renomeia
index.astype()	Index	Converte tipo
index.insert()	Index	Insere elemento
index.delete()	Index	Remove elemento
index.append()	Index	Concatena índices
40. Operações com MultiIndex
Instrução	Estrutura	Descrição
mi.levels	MultiIndex	Valores dos níveis
mi.codes	MultiIndex	Códigos dos níveis
mi.names	MultiIndex	Nomes
mi.get_level_values(0)	MultiIndex	Obtém nível
mi.get_level_values('estado')	MultiIndex	Obtém nível por nome
mi.droplevel()	MultiIndex	Remove nível
mi.swaplevel()	MultiIndex	Troca níveis
df.xs()	DataFrame	Cross-section
df.sort_index(level=...)	DataFrame	Ordena determinado nível
df.reorder_levels()	DataFrame	Reorganiza níveis
41. Operações de janela temporal
Instrução	Estrutura	Descrição
rolling(7)	Series	Janela de 7 observações
rolling('7D')	Series	Janela de 7 dias
rolling(...).mean()	Series	Média móvel
rolling(...).sum()	Series	Soma móvel
rolling(...).median()	Series	Mediana móvel
rolling(...).std()	Series	Desvio padrão móvel
rolling(...).min()	Series	Mínimo
rolling(...).max()	Series	Máximo
expanding()	Series	Janela acumulativa
ewm()	Series	Média exponencial
shift()	Series	Lag/lead
diff()	Series	Diferença
pct_change()	Series	Crescimento percentual
42. shift, diff e análises temporais

Essas operações são especialmente importantes em Analytics e Data Science:

Instrução	Estrutura	Descrição
s.shift(1)	Series	Valor anterior
s.shift(-1)	Series	Próximo valor
s.diff()	Series	Diferença atual − anterior
s.diff(2)	Series	Diferença com dois períodos
s.pct_change()	Series	Crescimento percentual
s.pct_change(12)	Series	Crescimento contra 12 períodos atrás
s.cumsum()	Series	Acumulado
s.cummax()	Series	Máximo acumulado
43. Reamostragem temporal
Instrução	Estrutura	Descrição
df.resample('D').sum()	DataFrame	Diário
df.resample('W').sum()	DataFrame	Semanal
df.resample('ME').sum()	DataFrame	Mensal
df.resample('QE').sum()	DataFrame	Trimestral
df.resample('YE').sum()	DataFrame	Anual
df.resample('ME').mean()	DataFrame	Média mensal
df.resample('ME').agg(...)	DataFrame	Agregações mensais

Em versões recentes do Pandas, prefira as frequências explícitas como ME (month-end) e YE (year-end), em vez de depender de aliases antigos.

44. Limpeza de outliers

Pandas não é uma biblioteca específica de detecção de outliers, mas oferece ferramentas para tratá-los.

Instrução	Estrutura	Descrição
s.quantile(0.25)	Series	Q1
s.quantile(0.75)	Series	Q3
s.clip()	Series	Limita valores
s.between()	Series	Verifica intervalo
df.loc[condicao]	DataFrame	Filtra outliers
df.quantile()	DataFrame	Calcula quantis

Exemplo pelo IQR:

q1 = df["valor"].quantile(0.25)
q3 = df["valor"].quantile(0.75)

iqr = q3 - q1

limite_inferior = q1 - 1.5 * iqr
limite_superior = q3 + 1.5 * iqr

df_sem_outliers = df[
    df["valor"].between(
        limite_inferior,
        limite_superior,
    )
]
45. Operações de limpeza mais importantes em um ETL

Para o tipo de pipeline ETL que você vem desenvolvendo, eu organizaria a limpeza nessa sequência:

Etapa	Instrução	Estrutura	Objetivo
1	df.copy()	DataFrame	Evitar alterar fonte
2	df.columns.str.strip()	Index	Limpar nomes
3	df.columns.str.lower()	Index	Padronizar nomes
4	df.rename()	DataFrame	Padronizar nomenclatura
5	df.drop_duplicates()	DataFrame	Remover duplicidades
6	df.isna().sum()	DataFrame	Diagnosticar ausentes
7	df.dropna()	DataFrame	Remover ausentes quando necessário
8	df.fillna()	DataFrame	Preencher ausentes
9	pd.to_numeric()	Series	Corrigir números
10	pd.to_datetime()	Series	Corrigir datas
11	df.astype()	DataFrame	Padronizar tipos
12	df.replace()	DataFrame	Corrigir valores
13	df.str.strip()	Series	Limpar strings
14	df.str.lower()	Series	Padronizar texto
15	df.isin()	Series	Validar categorias
16	df.between()	Series	Validar intervalos
17	df.clip()	Series	Tratar limites
18	df.duplicated()	DataFrame	Validar duplicidades
19	df.isna().sum()	DataFrame	Validar novamente
20	df.info()	DataFrame	Inspeção final
46. Validação de qualidade dos dados

Para um projeto profissional, vale acrescentar estas verificações:

Instrução	Estrutura	Descrição
df.empty	DataFrame	Dataset vazio
df.shape	DataFrame	Quantidade de registros
df.columns	DataFrame	Verifica colunas
set(expected) - set(df.columns)	DataFrame	Colunas ausentes
set(df.columns) - set(expected)	DataFrame	Colunas inesperadas
df.dtypes	DataFrame	Verifica tipos
df.isna().sum()	DataFrame	Valores ausentes
df.duplicated().sum()	DataFrame	Duplicidades
df[column].isin(valid_values)	Series	Valores permitidos
df[column].between(a,b)	Series	Faixa válida
df[column].ge(0)	Series	Valores ≥ 0
df.index.is_unique	Index	Chave/index único
df[column].is_unique	Series	Coluna única
df[column].notna().all()	Series	Campo obrigatório
df[column].dtype	Series	Tipo da coluna
47. Uma visão geral por objeto

Essa é uma boa forma de memorizar onde cada operação pertence:

Objeto	Principais operações
Series	map, apply, unique, value_counts, isin, between, str, dt, rolling, expanding, ewm, shift, diff, pct_change, rank
DataFrame	loc, iloc, query, filter, groupby, merge, join, concat, pivot, pivot_table, melt, drop, rename, assign, sort_values, sort_index
Index	set_index, reset_index, reindex, union, intersection, difference, isin, unique, duplicated, sort_values
MultiIndex	set_index, xs, swaplevel, reorder_levels, droplevel, stack, unstack
48. Mapa mental das operações Pandas
PANDAS
│
├── Series
│   ├── criação
│   ├── seleção
│   ├── filtragem
│   ├── transformação
│   ├── strings
│   ├── datas
│   ├── estatística
│   ├── ranking
│   └── windowing
│
├── DataFrame
│   ├── criação
│   ├── inspeção
│   ├── seleção
│   ├── filtragem
│   ├── ordenação
│   ├── limpeza
│   ├── transformação
│   ├── agregação
│   ├── groupby
│   ├── merge
│   ├── join
│   ├── concat
│   ├── pivot
│   ├── melt
│   ├── crosstab
│   └── séries temporais
│
└── Index
    ├── Index simples
    │   ├── set_index
    │   ├── reset_index
    │   ├── reindex
    │   ├── sort_index
    │   └── operações de conjunto
    │
    └── MultiIndex
        ├── níveis
        ├── xs
        ├── stack
        ├── unstack
        ├── swaplevel
        ├── reorder_levels
        └── droplevel
As operações que eu consideraria essenciais

Se o objetivo é dominar Pandas para Análise de Dados, Data Science e Engenharia de Dados, eu priorizaria nesta ordem:

Nível 1 — fundamentos

DataFrame
Series
Index
head
tail
info
describe
shape
dtypes
loc
iloc

Nível 2 — manipulação

filter
query
sort_values
sort_index
rename
drop
assign
astype
replace

Nível 3 — limpeza

isna
notna
fillna
dropna
duplicated
drop_duplicates
to_numeric
to_datetime
str.*

Nível 4 — Analytics

groupby
agg
transform
value_counts
rank
pivot_table
crosstab

Nível 5 — integração

merge
join
concat
align

Nível 6 — índices

set_index
reset_index
reindex
MultiIndex
xs
stack
unstack

Nível 7 — séries temporais

to_datetime
dt.*
resample
shift
diff
pct_change
rolling
expanding
ewm

Nível 8 — ETL

read_csv
read_excel
read_json
read_sql
read_parquet

↓
validação

↓
limpeza

↓
padronização

↓
transformação

↓
agregação

↓
merge/join

↓
exportação

to_csv
to_excel
to_json
to_sql
to_parquet

Para o seu contexto de Engenharia de Dados + Analytics, essa última sequência é particularmente importante porque praticamente forma o núcleo das operações de um DataFrame dentro de um pipeline:

INGESTÃO
    ↓
pd.read_csv()
pd.read_excel()
    ↓
INSPEÇÃO
    ↓
info()
describe()
dtypes
shape
    ↓
VALIDAÇÃO
    ↓
isna()
duplicated()
isin()
between()
    ↓
LIMPEZA
    ↓
dropna()
fillna()
drop_duplicates()
replace()
astype()
    ↓
PADRONIZAÇÃO
    ↓
rename()
str.*
to_numeric()
to_datetime()
    ↓
TRANSFORMAÇÃO
    ↓
assign()
map()
apply()
transform()
    ↓
AGREGAÇÃO
    ↓
groupby()
agg()
pivot_table()
    ↓
INTEGRAÇÃO
    ↓
merge()
join()
concat()
    ↓
SÉRIES TEMPORAIS
    ↓
resample()
rolling()
shift()
diff()
pct_change()
    ↓
VALIDAÇÃO FINAL
    ↓
EXPORTAÇÃO
    ↓
to_csv()
to_parquet()
to_sql()
to_json()

Essa estrutura já é uma base de referência bastante completa para Pandas, indo além de um simples “cheat sheet” e cobrindo justamente as operações que você tende a encontrar em projetos reais de ETL, análise exploratória, tratamento de dados, Data Warehouse e APIs de dados.
