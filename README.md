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

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.head() | DataFrame | Primeiras 5 linhas |
| df.head(10) | DataFrame | Primeiras 10 linhas |
| df.tail() | DataFrame | Últimas 5 linhas |
| df.tail(10) | DataFrame | Últimas 10 linhas |
| df.sample() | DataFrame | Amostra aleatória |
| df.sample(10) | DataFrame | 10 registros aleatórios |
| df.info() | DataFrame | Estrutura, tipos e valores não nulos |
| df.describe() | DataFrame | Estatísticas descritivas numéricas |
| df.describe(include='all') | DataFrame | Estatísticas de todas as colunas |
| df.describe(include='object') | DataFrame | Estatísticas de texto/categorias |
| df.dtypes | DataFrame | Tipos das colunas |
| df.astype(...) | DataFrame / Series | Converte tipos |
| df.nunique() | DataFrame / Series | Número de valores únicos |
| df.unique() | Series | Valores únicos |
| df.value_counts() | Series | Frequência dos valores |
| df.is_unique | Series / Index | Verifica unicidade |
| df.index.is_unique | Index | Verifica se índice é único |
| df.empty | DataFrame / Series | Verifica se está vazio |
| df.memory_usage() | DataFrame | Memória utilizada |
| df.memory_usage(deep=True) | DataFrame | Memória detalhada |
| df.select_dtypes(...) | DataFrame | Seleciona colunas por tipo |
| df.columns | DataFrame | Lista nomes das colunas |
| df.index | DataFrame | Visualiza índice |
| df.axes | DataFrame | Retorna eixos |
| df.keys() | DataFrame | Retorna colunas |
| df.count() | DataFrame / Series | Conta valores não nulos |
| df.isna().sum() | DataFrame | Conta valores ausentes |
| df.duplicated().sum() | DataFrame | Conta duplicidades |
| df.corr() | DataFrame | Correlação entre variáveis numéricas |
| df.cov() | DataFrame | Covariância |
| df.rank() | DataFrame / Series | Calcula ranking |

## 3. Seleção de dados
### DataFrame
| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df['coluna'] | DataFrame | Seleciona uma coluna como Series |
| df[['col1','col2']] | DataFrame | Seleciona várias colunas |
| df.loc[...] | DataFrame / Series | Seleção por rótulo |
| df.iloc[...] | DataFrame / Series | Seleção por posição |
| df.at[...] | DataFrame / Series | Acessa uma célula por rótulo |
| df.iat[...] | DataFrame / Series | Acessa uma célula por posição |
| df.loc[:, 'coluna'] | DataFrame | Seleciona coluna por nome |
| df.loc[0:10, ['a','b']] | DataFrame | Linhas e colunas por rótulo |
| df.iloc[0:10, 0:2] | DataFrame | Linhas e colunas por posição |
| df.filter(items=[...]) | DataFrame | Seleciona colunas/linhas específicas |
| df.filter(like='sales') | DataFrame | Seleciona nomes contendo texto |
| df.filter(regex='^sales') | DataFrame | Seleção usando expressão regular |

### Series

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| s[0] | Series | Acesso por índice |
| s.iloc[0] | Series | Acesso posicional |
| s.loc['A'] | Series | Acesso por rótulo |
| s.iloc[0:5] | Series | Fatiamento posicional |
| s.loc['A':'D'] | Series | Fatiamento por rótulo |

## 4. Filtragem de dados

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df[df['idade'] > 18] | DataFrame | Filtra condição |
| df[df['cidade'] == 'Recife'] | DataFrame | Igualdade |
| df[df['valor'] != 0] | DataFrame | Diferente |
| df[df['valor'] >= 100] | DataFrame | Maior ou igual |
| df[df['valor'] <= 100] | DataFrame | Menor ou igual |
| df[(df['idade'] > 18) & (df['idade'] < 60)] | DataFrame | AND |
| df[(df['cidade']=='Recife') | DataFrame | Filtro por cidade |
| df[~(df['status']=='Cancelado')] | DataFrame | NOT |
| df['cidade'].isin([...]) | Series | Verifica pertencimento |
| df['idade'].between(18, 60) | Series | Intervalo |
| df['nome'].str.contains('ana') | Series | Procura texto |
| df['nome'].str.startswith('A') | Series | Começa com |
| df['nome'].str.endswith('a') | Series | Termina com |
| df.query("idade > 18") | DataFrame | Filtragem com expressão |
| df.query("cidade == 'Recife'") | DataFrame | Query textual |
| df.nlargest(10, 'valor') | DataFrame | 10 maiores valores |
| df.nsmallest(10, 'valor') | DataFrame | 10 menores valores |

## 5. Ordenação

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.sort_values('valor') | DataFrame | Ordena coluna |
| df.sort_values('valor', ascending=False) | DataFrame | Ordem decrescente |
| df.sort_values(['cidade','valor']) | DataFrame | Ordena por várias colunas |
| df.sort_values(['cidade','valor'], ascending=[True,False]) | DataFrame | Ordem diferente por coluna |
| df.sort_index() | DataFrame / Series | Ordena pelo índice |
| df.sort_index(ascending=False) | DataFrame / Series | Índice decrescente |
| s.sort_values() | Series | Ordena valores |
| s.sort_index() | Series | Ordena índice |
| df.nlargest(5, 'valor') | DataFrame | Maiores registros |
| df.nsmallest(5, 'valor') | DataFrame | Menores registros |

## 6. Índice simples

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.index | Index | Obtém índice |
| df.index.name | Index | Obtém nome |
| df.index.names | Index | Obtém nomes dos níveis |
| df.set_index('id') | DataFrame | Define coluna como índice |
| df.reset_index() | DataFrame | Converte índice em coluna |
| df.reset_index(drop=True) | DataFrame | Remove índice |
| df.rename_axis('id') | DataFrame / Index | Renomeia eixo |
| df.reindex([...]) | DataFrame | Reindexa |
| df.reindex(columns=[...]) | DataFrame | Reordena/reindexa colunas |
| df.index.tolist() | Index | Converte índice em lista |
| df.index.unique() | Index | Índices únicos |
| df.index.duplicated() | Index | Detecta índices duplicados |
| df.index.is_monotonic_increasing | Index | Verifica ordenação crescente |
| df.index.is_monotonic_decreasing | Index | Verifica ordenação decrescente |

## 7. MultiIndex / índice hierárquico

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| pd.MultiIndex.from_tuples(...) | Index | Cria índice hierárquico |
| pd.MultiIndex.from_arrays(...) | Index | Cria níveis a partir de arrays |
| pd.MultiIndex.from_product(...) | Index | Produto cartesiano |
| df.set_index(['estado','cidade']) | DataFrame | Cria MultiIndex |
| df.reset_index() | DataFrame | Remove MultiIndex |
| df.index.levels | MultiIndex | Lista níveis |
| df.index.codes | MultiIndex | Códigos dos níveis |
| df.index.names | MultiIndex | Nomes dos níveis |
| df.xs('PE', level='estado') | DataFrame | Seleciona nível específico |
| df.loc['PE'] | DataFrame | Seleciona primeiro nível |
| df.loc[('PE','Recife')] | DataFrame | Seleciona combinação |
| df.swaplevel() | DataFrame | Troca níveis |
| df.reorder_levels(...) | DataFrame | Reorganiza níveis |
| df.sort_index() | DataFrame | Ordena MultiIndex |
| df.droplevel(...) | DataFrame / Index | Remove nível |
| df.unstack() | DataFrame | Transforma nível em coluna |
| df.stack() | DataFrame | Transforma colunas em índice |

## 8. Operações com índices

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.set_index() | DataFrame | Define índice |
| df.reset_index() | DataFrame | Redefine índice |
| df.reindex() | DataFrame / Series | Reindexação |
| df.rename_axis() | DataFrame / Series | Renomeia índice/eixo |
| df.sort_index() | DataFrame / Series | Ordena índice |
| df.index.union(other) | Index | União |
| df.index.intersection(other) | Index | Interseção |
| df.index.difference(other) | Index | Diferença |
| df.index.symmetric_difference(other) | Index | Diferença simétrica |
| df.index.isin([...]) | Index | Verifica pertencimento |
| df.index.duplicated() | Index | Detecta duplicidade |
| df.index.drop_duplicates() | Index | Remove índices duplicados |
| df.index.rename('novo') | Index | Renomeia índice |
| df.index.astype(...) | Index | Converte tipo |

## 9. Valores ausentes

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.isna() | DataFrame | Detecta ausentes |
| df.isnull() | DataFrame | Alias de isna() |
| df.notna() | DataFrame | Detecta não nulos |
| df.isna().sum() | DataFrame | Quantidade de ausentes |
| df.dropna() | DataFrame / Series | Remove registros com NA |
| df.dropna(axis=1) | DataFrame | Remove colunas com NA |
| df.dropna(subset=['coluna']) | DataFrame | Remove NA de colunas específicas |
| df.dropna(how='all') | DataFrame | Remove somente linhas totalmente vazias |
| df.fillna(0) | DataFrame / Series | Substitui NA |
| df.fillna({'idade':0}) | DataFrame | Valor específico por coluna |
| df.ffill() | DataFrame / Series | Propaga valor anterior |
| df.bfill() | DataFrame / Series | Propaga próximo valor |
| df.interpolate() | DataFrame / Series | Interpolação |
| df.replace(np.nan, 0) | DataFrame / Series | Substituição |
| df.isna().mean() | DataFrame | Percentual de NA |

## 10. Operações com colunas

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df['nova'] = ... | DataFrame | Cria coluna |
| df.assign(nova=...) | DataFrame | Cria colunas |
| df.insert(...) | DataFrame | Insere coluna em posição |
| df.drop(columns=['x']) | DataFrame | Remove coluna |
| df.rename(columns={'x':'y'}) | DataFrame | Renomeia coluna |
| df.columns = [...] | DataFrame | Redefine nomes |
| df.columns.str.lower() | Index | Coloca nomes em minúsculo |
| df.columns.str.upper() | Index | Coloca nomes em maiúsculo |
| df.columns.str.strip() | Index | Remove espaços |
| df.columns.str.replace(...) | Index | Substitui caracteres |
| df.pop('coluna') | DataFrame | Remove e retorna coluna |
| df.filter(regex=...) | DataFrame | Seleciona colunas por padrão |
| df.select_dtypes(...) | DataFrame | Seleciona por tipo |

## 11. Operadores de colunas

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df['a'] + df['b'] | DataFrame / Series | Soma |
| df['a'] - df['b'] | DataFrame / Series | Subtração |
| df['a'] * df['b'] | DataFrame / Series | Multiplicação |
| df['a'] / df['b'] | DataFrame / Series | Divisão |
| df['a'] // df['b'] | Series | Divisão inteira |
| df['a'] % df['b'] | Series | Módulo |
| df['a'] ** 2 | Series | Potência |
| df['a'].abs() | Series | Valor absoluto |
| df['a'].round(2) | Series | Arredondamento |
| df['a'].clip(0,100) | Series | Limita valores |
| df['a'].add(df['b']) | Series | Soma |
| df['a'].sub(df['b']) | Series | Subtração |
| df['a'].mul(df['b']) | Series | Multiplicação |
| df['a'].div(df['b']) | Series | Divisão |
| df.eval('total = preco * quantidade') | DataFrame | Operações com expressão |

## 12. Operações matemáticas e estatísticas

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.sum() | DataFrame / Series | Soma
| df.mean() | DataFrame / Series | Média |
| df.median() | DataFrame / Series | Mediana |
| df.mode() | DataFrame / Series | Moda |
| df.min() | DataFrame / Series | Mínimo |
| df.max() | DataFrame / Series | Máximo |
| df.std() | DataFrame / Series | Desvio padrão |
| df.var() | DataFrame / Series | Variância |
| df.sem() | DataFrame / Series | Erro padrão |
| df.skew() | DataFrame / Series | Assimetria |
| df.kurt() | DataFrame / Series | Curtose |
| df.quantile(0.25) | DataFrame / Series | Percentil |
| df.cumsum() | DataFrame / Series | Soma acumulada |
| df.cumprod() | DataFrame / Series | Produto acumulado |
| df.cummin() | DataFrame / Series | Mínimo acumulado |
| df.cummax() | DataFrame / Series | Máximo acumulado |
| df.pct_change() | Series / DataFrame | Variação percentual |

## 13. Agregação de dados

| Instrução | Estrutura | Descrição |
| --------- | --------- | --------- |
| df.sum() | DataFrame / Series | Soma |
| df.mean() | DataFrame / Series | Média |
| df.count() | DataFrame / Series | Contagem |
| df.min() | DataFrame / Series | Mínimo |
| df.max() | DataFrame / Series | Máximo |
| df.agg('sum') | DataFrame / Series | Agregação |
| df.agg(['sum','mean','max']) | DataFrame | Múltiplas agregações |
| df.agg({'vendas':'sum','preco':'mean'}) | DataFrame | Agregações diferentes |
| s.agg(...) | Series | Agregação da Series |
| df.value_counts() | DataFrame / Series | Frequência |
| df.nunique() | DataFrame / Series | Quantidade de distintos |

## 14. Agrupamento — groupby

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
```df.groupby("categoria").agg(
    vendas=("valor", "sum"),
    media=("valor", "mean"),
    quantidade=("valor", "count"),
)
```

## 15. Transformação de dados

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

## 16. Operações de texto

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

## 17. Conversão de tipos

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

## 18. Datas e séries temporais

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

## 19. Janelamento de dados — Windowing

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
```
df["media_7_dias"] = (
    df["vendas"]
    .rolling(7)
    .mean()
)
```

## 20. Concatenação

Instrução	Estrutura	Descrição
pd.concat([df1, df2])	DataFrame	Empilha linhas
pd.concat([df1, df2], axis=1)	DataFrame	Junta colunas
pd.concat([...], ignore_index=True)	DataFrame	Reinicia índice
pd.concat([...], keys=[...])	DataFrame	Cria índice hierárquico

## 21. Junções — Merge / Join

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

### Cardinalidades importantes

1:1  → uma linha ↔ uma linha
1:N  → uma linha ↔ várias linhas
N:1  → várias linhas ↔ uma linha
N:N  → várias linhas ↔ várias linhas

## 22. Pivot Tables

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

## 23. Crosstab / tabulação cruzada

Instrução	Estrutura	Descrição
pd.crosstab(df['sexo'], df['estado'])	DataFrame	Frequência cruzada
pd.crosstab(..., normalize=True)	DataFrame	Percentual geral
pd.crosstab(..., normalize='index')	DataFrame	Percentual por linha
pd.crosstab(..., normalize='columns')	DataFrame	Percentual por coluna
pd.crosstab(..., margins=True)	DataFrame	Totais
pd.crosstab(..., values=df['valor'], aggfunc='sum')	DataFrame	Agrega valores

## 24. Pivot e reshape

Instrução	Estrutura	Descrição
df.pivot()	DataFrame	Transforma dados
df.pivot_table()	DataFrame	Pivot com agregação
df.melt()	DataFrame	Wide → Long
df.stack()	DataFrame	Colunas → índice
df.unstack()	DataFrame	Índice → colunas
df.explode()	DataFrame / Series	Expande listas
pd.wide_to_long()	DataFrame	Wide → Long complexo

## 25. Duplicidades

Instrução	Estrutura	Descrição
df.duplicated()	DataFrame	Detecta duplicados
df.duplicated(subset=['id'])	DataFrame	Detecta por coluna
df.duplicated(keep='first')	DataFrame	Mantém primeiro
df.duplicated(keep='last')	DataFrame	Mantém último
df.drop_duplicates()	DataFrame	Remove duplicados
df.drop_duplicates(subset=['id'])	DataFrame	Remove por chave
df.drop_duplicates(keep='last')	DataFrame	Mantém último

## 26. Limpeza de dados

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

## 27. Limpeza de strings

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

## 28. Limpeza e padronização de nomes de colunas

Uma operação bastante comum em pipelines ETL:

Instrução	Estrutura	Descrição
df.columns = df.columns.str.lower()	Index	Minúsculas
df.columns = df.columns.str.strip()	Index	Remove espaços
df.columns = df.columns.str.replace(' ', '_')	Index	Espaços → _
df.columns = df.columns.str.replace(r'[^\w]+', '_', regex=True)	Index	Remove caracteres especiais
df.columns = df.columns.str.normalize('NFKD')	Index	Normaliza Unicode
df.columns = df.columns.str.replace(...)	Index	Padroniza nomes

Exemplo:
```
df.columns = (
    df.columns
    .str.strip()
    .str.lower()
    .str.replace(" ", "_")
)
```

## 29. Leitura de dados

Instrução	Estrutura	Descrição
pd.read_csv()	DataFrame	Lê CSV
pd.read_excel()	DataFrame	Lê Excel
pd.read_json()	DataFrame	Lê JSON
pd.read_sql()	DataFrame	Lê SQL
pd.read_parquet()	DataFrame	Lê Parquet
pd.read_feather()	DataFrame	Lê Feather
pd.read_pickle()	DataFrame	Lê Pickle
pd.read_html()	DataFrame	Lê tabelas HTML

## 30. Exportação

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

## 31. Comparação entre DataFrames

Instrução	Estrutura	Descrição
df1.equals(df2)	DataFrame	Verifica igualdade
df1.compare(df2)	DataFrame	Mostra diferenças
df1.align(df2)	DataFrame	Alinha índices/colunas
df1.combine(df2, func)	DataFrame	Combina DataFrames
df1.update(df2)	DataFrame	Atualiza valores

## 32. Operações booleanas e lógicas

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

## 33. Operações entre Series e DataFrames

Instrução	Estrutura	Descrição
df.add(s)	DataFrame	Soma alinhada
df.sub(s)	DataFrame	Subtração alinhada
df.mul(s)	DataFrame	Multiplicação
df.div(s)	DataFrame	Divisão
df.dot(s)	DataFrame	Produto matricial
df.combine_first(df2)	DataFrame	Combina preenchendo ausentes
df.align(df2)	DataFrame	Alinha índices/colunas

O ponto importante aqui é que Pandas trabalha com alinhamento automático por índice.

## 34. Estatísticas por categoria

Instrução	Estrutura	Descrição
df.groupby('categoria')['valor'].sum()	DataFrame	Soma por categoria
df.groupby('categoria')['valor'].mean()	DataFrame	Média
df.groupby('categoria')['valor'].median()	DataFrame	Mediana
df.groupby('categoria')['valor'].std()	DataFrame	Desvio padrão
df.groupby('categoria')['valor'].min()	DataFrame	Mínimo
df.groupby('categoria')['valor'].max()	DataFrame	Máximo
df.groupby('categoria')['valor'].count()	DataFrame	Quantidade
df.groupby('categoria')['valor'].nunique()	DataFrame	Distintos

## 35. Ranking

Instrução	Estrutura	Descrição
s.rank()	Series	Ranking
s.rank(ascending=False)	Series	Ranking decrescente
df['valor'].rank()	Series	Ranking de coluna
df.groupby('categoria')['valor'].rank()	Series	Ranking dentro do grupo
df.nlargest(10, 'valor')	DataFrame	Top 10
df.nsmallest(10, 'valor')	DataFrame	Bottom 10

## 36. Amostragem

Instrução	Estrutura	Descrição
df.sample()	DataFrame	Uma amostra
df.sample(n=100)	DataFrame	100 registros
df.sample(frac=0.1)	DataFrame	10% dos dados
df.sample(frac=1)	DataFrame	Embaralha dataset
df.sample(..., random_state=42)	DataFrame	Resultado reproduzível

## 37. Contagem e frequência

Instrução	Estrutura	Descrição
s.value_counts()	Series	Frequência
s.value_counts(normalize=True)	Series	Frequência relativa
s.value_counts(dropna=False)	Series	Inclui NA
df.nunique()	DataFrame	Distintos por coluna
df['col'].nunique()	Series	Distintos
df.count()	DataFrame	Valores não nulos
df.size	DataFrame	Total de elementos

## 38. Manipulação de categorias

Instrução	Estrutura	Descrição
s.astype('category')	Series	Converte para categoria
s.cat.categories	Series	Categorias existentes
s.cat.codes	Series	Código numérico
s.cat.add_categories()	Series	Adiciona categoria
s.cat.remove_categories()	Series	Remove categoria
s.cat.rename_categories()	Series	Renomeia categorias
s.cat.reorder_categories()	Series	Reordena categorias
s.cat.set_categories()	Series	Define categorias

## 39. Operações com Index

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

## 40. Operações com MultiIndex

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

## 41. Operações de janela temporal

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

## 42. shift, diff e análises temporais

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

## 43. Reamostragem temporal

Instrução	Estrutura	Descrição
df.resample('D').sum()	DataFrame	Diário
df.resample('W').sum()	DataFrame	Semanal
df.resample('ME').sum()	DataFrame	Mensal
df.resample('QE').sum()	DataFrame	Trimestral
df.resample('YE').sum()	DataFrame	Anual
df.resample('ME').mean()	DataFrame	Média mensal
df.resample('ME').agg(...)	DataFrame	Agregações mensais

Em versões recentes do Pandas, prefira as frequências explícitas como ME (month-end) e YE (year-end), em vez de depender de aliases antigos.

## 44. Limpeza de outliers

Pandas não é uma biblioteca específica de detecção de outliers, mas oferece ferramentas para tratá-los.

Instrução	Estrutura	Descrição
s.quantile(0.25)	Series	Q1
s.quantile(0.75)	Series	Q3
s.clip()	Series	Limita valores
s.between()	Series	Verifica intervalo
df.loc[condicao]	DataFrame	Filtra outliers
df.quantile()	DataFrame	Calcula quantis

Exemplo pelo IQR:
```
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
```

## 45. Operações de limpeza mais importantes em um ETL

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

## 46. Validação de qualidade dos dados

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

## 47. Uma visão geral por objeto

Essa é uma boa forma de memorizar onde cada operação pertence:

Objeto	Principais operações
Series	map, apply, unique, value_counts, isin, between, str, dt, rolling, expanding, ewm, shift, diff, pct_change, rank
DataFrame	loc, iloc, query, filter, groupby, merge, join, concat, pivot, pivot_table, melt, drop, rename, assign, sort_values, sort_index
Index	set_index, reset_index, reindex, union, intersection, difference, isin, unique, duplicated, sort_values
MultiIndex	set_index, xs, swaplevel, reorder_levels, droplevel, stack, unstack

## 48. Mapa mental das operações Pandas

## PANDAS
```
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
```
As operações que eu consideraria essenciais

Se o objetivo é dominar Pandas para Análise de Dados, Data Science e Engenharia de Dados, eu priorizaria nesta ordem:

### Nível 1 — fundamentos

* DataFrame
* Series
* Index
* head
* tail
* info
* describe
* shape
* dtypes
* loc
* iloc

N### ível 2 — manipulação

* filter
* query
* sort_values
* sort_index
* rename
* drop
* assign
* astype
* replace

### Nível 3 — limpeza

* isna
* notna
* fillna
* dropna
* duplicated
* drop_duplicates
* to_numeric
* to_datetime
* str.*

### Nível 4 — Analytics

* groupby
* agg
* transform
* value_counts
* rank
* pivot_table
* crosstab

### Nível 5 — integração

* merge
* join
* concat
* align

### Nível 6 — índices

* set_index
* reset_index
* reindex
* MultiIndex
* xs
* stack
* unstack

### Nível 7 — séries temporais

* to_datetime
* dt.*
* resample
* shift
* diff
* pct_change
* rolling
* expanding
* ewm

### Nível 8 — ETL

* read_csv
* read_excel
* read_json
* read_sql
* read_parquet

```
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
```

Para o seu contexto de Engenharia de Dados + Analytics, essa última sequência é particularmente importante porque praticamente forma o núcleo das operações de um DataFrame dentro de um pipeline:


```
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
```

Essa estrutura já é uma base de referência bastante completa para Pandas, indo além de um simples “cheat sheet” e cobrindo justamente as operações que você tende a encontrar em projetos reais de ETL, análise exploratória, tratamento de dados, Data Warehouse e APIs de dados.

# Numpy

## 1. Importação e criação de arrays

### import numpy as np — importa NumPy.

| Instrução | Descrição |
| --------- | --------- |
| np.array([1, 2, 3]) | cria um ndarray. |
| np.array([[1, 2], [3, 4]]) | cria array multidimensional. |
| np.asarray(...) | converte para array sem cópia desnecessária quando possível. |
| np.asanyarray(...) | semelhante a asarray, preservando subclasses. |
| np.fromiter(...) | cria array a partir de um iterável. |
| np.fromfunction(...) | cria array usando uma função. |
| np.frombuffer(...) | cria array a partir de buffer. |
| np.fromstring(...) | cria array a partir de string. |
| np.zeros(5) | array preenchido com zeros. |
| np.zeros((3, 4)) | matriz 3 × 4 de zeros. |
| np.ones(5) | array preenchido com 1. |
| np.ones((3, 4)) | matriz de 1. |
| np.empty(5) | array não inicializado. |
| np.empty((3, 4)) | matriz não inicializada. |
| np.full(5, 10) | array preenchido com 10. |
| np.full((3, 3), 7) | matriz preenchida com 7. |
| np.eye(3) | matriz identidade. |
| np.identity(3) | matriz identidade. |
| np.diag([1, 2, 3]) | cria matriz diagonal. |
| np.tri(3) | matriz triangular inferior. |
| np.ones_like(a) | array de 1 com formato de outro. |
| np.zeros_like(a) | array de zeros com formato de outro. |
| np.empty_like(a) | array vazio com formato de outro. |
| np.full_like(a, 10) | array preenchido mantendo formato. |

## 2. Arrays e propriedades fundamentais

a.ndim — número de dimensões.
a.shape — dimensões do array.
a.size — quantidade total de elementos.
a.dtype — tipo dos elementos.
a.itemsize — tamanho em bytes de cada elemento.
a.nbytes — memória ocupada pelo array.
a.strides — deslocamento em bytes entre elementos.
a.flags — informações sobre memória/layout.
a.T — transposição.
a.real — parte real.
a.imag — parte imaginária.
a.flat — iterador sobre todos os elementos.
a.base — verifica se o array é uma view de outro array.

Exemplo:

import numpy as np

a = np.array([
    [10, 20, 30],
    [40, 50, 60],
])

print(a.ndim)
print(a.shape)
print(a.size)
print(a.dtype)
3. Tipos de dados — dtype
np.int8
np.int16
np.int32
np.int64
np.uint8
np.uint16
np.uint32
np.uint64
np.float16
np.float32
np.float64
np.longdouble
np.complex64
np.complex128
np.bool_
np.str_
np.bytes_
np.object_

Conversão:

a.astype(np.int64) — converte para inteiro.
a.astype(np.float64) — converte para float.
a.astype(np.bool_) — converte para booleano.
a.astype(str) — converte para string.
4. Criação de sequências numéricas
np.arange(10) — sequência de 0 a 9.
np.arange(0, 10, 2) — sequência com passo 2.
np.linspace(0, 10, 5) — 5 valores igualmente espaçados.
np.logspace(1, 3, 5) — escala logarítmica.
np.geomspace(1, 1000, 5) — progressão geométrica.
np.r_ — concatenação por sintaxe de índices.
np.c_ — concatenação por colunas.
5. Números aleatórios

O módulo moderno recomendado é np.random.Generator.

rng = np.random.default_rng(42) — cria gerador reproduzível.
rng.random(10) — números aleatórios entre 0 e 1.
rng.random((3, 4)) — matriz aleatória.
rng.integers(0, 100, 10) — inteiros aleatórios.
rng.uniform(0, 10, 10) — distribuição uniforme.
rng.normal(0, 1, 10) — distribuição normal.
rng.standard_normal(10) — normal padrão.
rng.binomial(10, 0.5, 100) — distribuição binomial.
rng.poisson(3, 100) — distribuição Poisson.
rng.exponential(2, 100) — distribuição exponencial.
rng.choice([1, 2, 3], size=10) — amostragem.
rng.choice(a, size=10, replace=False) — amostragem sem reposição.
rng.shuffle(a) — embaralha.
rng.permutation(a) — retorna permutação.
rng.integers(...) — gera inteiros aleatórios.
6. Indexação
a[0] — primeiro elemento.
a[-1] — último elemento.
a[1:5] — slicing.
a[:5] — primeiros elementos.
a[5:] — a partir do índice 5.
a[::2] — elementos alternados.
a[::-1] — array invertido.
a[0, 1] — elemento de matriz.
a[:, 0] — primeira coluna.
a[0, :] — primeira linha.
a[:, 1:3] — intervalo de colunas.
a[..., 0] — seleção usando ellipsis.
7. Fancy indexing
a[[0, 2, 4]] — seleciona posições específicas.
a[[0, 2], :] — seleciona linhas específicas.
a[:, [0, 2]] — seleciona colunas específicas.
a[[0, 1], [2, 3]] — seleciona pares de posições.

Exemplo:

a = np.array([10, 20, 30, 40, 50])

resultado = a[[0, 2, 4]]

Resultado:

[10 30 50]
8. Boolean indexing
a[a > 10] — valores maiores que 10.
a[a == 10] — valores iguais a 10.
a[a != 10] — valores diferentes.
a[(a > 10) & (a < 50)] — AND.
a[(a < 10) | (a > 50)] — OR.
a[~(a > 10)] — NOT.

Funções relacionadas:

np.where(...)
np.nonzero(...)
np.flatnonzero(...)
np.argwhere(...)
9. where
np.where(a > 10) — retorna posições.
np.where(a > 10, 1, 0) — condição → 1 ou 0.
np.where(a > 10, a, 0) — mantém valores ou substitui.
np.where(a > 10, "alto", "baixo") — classificação condicional.

Exemplo:

resultado = np.where(
    vendas > 1000,
    "Alta",
    "Baixa",
)
10. nonzero, argwhere e posições
np.nonzero(a) — posições de elementos diferentes de zero.
np.flatnonzero(a) — posições em array achatado.
np.argwhere(a) — índices dos elementos que satisfazem condição.
np.argwhere(a > 10) — posições dos valores > 10.
11. Reshape
a.reshape(2, 3) — altera formato.
a.reshape((2, 3)) — mesma operação.
a.reshape(-1) — transforma em 1D.
a.reshape(2, -1) — NumPy calcula dimensão automaticamente.
a.ravel() — achata array.
a.flatten() — cria cópia achatada.
np.reshape(a, ...) — versão funcional.

Diferença importante:

ravel()
    geralmente retorna uma view quando possível

flatten()
    sempre retorna uma cópia
12. Transposição
a.T — transposta.
np.transpose(a) — transpõe.
np.transpose(a, axes=(1, 0)) — define ordem dos eixos.
np.swapaxes(a, 0, 1) — troca dois eixos.
np.moveaxis(a, 0, 2) — move eixo.
13. Alteração de dimensões
np.expand_dims(a, axis=0) — adiciona dimensão.
np.expand_dims(a, axis=1) — adiciona eixo.
np.squeeze(a) — remove dimensões de tamanho 1.
a[:, np.newaxis] — adiciona eixo.
a[None, :] — adiciona dimensão.
14. Broadcasting

Broadcasting permite realizar operações entre arrays de formatos diferentes.

a + 10
a * 2
a + b
a * b
a + np.array([1, 2, 3])

Exemplo:

a = np.array([
    [10, 20, 30],
    [40, 50, 60],
])

b = np.array([1, 2, 3])

resultado = a + b

Resultado:

[[11 22 33]
 [41 52 63]]

Conceitos relacionados:

broadcasting
alinhamento de dimensões
expansão implícita
operações vetorizadas
15. Concatenação
np.concatenate([a, b]) — concatena.
np.concatenate([a, b], axis=0) — concatena por linhas.
np.concatenate([a, b], axis=1) — concatena por colunas.
np.stack([a, b]) — cria novo eixo.
np.vstack([a, b]) — empilha verticalmente.
np.hstack([a, b]) — empilha horizontalmente.
np.dstack([a, b]) — empilha na terceira dimensão.
np.column_stack([a, b]) — empilha como colunas.
np.row_stack([a, b]) — empilha como linhas.
16. Divisão de arrays
np.split(a, 2) — divide em partes iguais.
np.array_split(a, 3) — permite partes desiguais.
np.hsplit(a, 2) — divide horizontalmente.
np.vsplit(a, 2) — divide verticalmente.
np.dsplit(a, 2) — divide no terceiro eixo.
17. Repetição
np.repeat(a, 2) — repete elementos.
np.repeat(a, [1, 2, 3]) — repetições diferentes.
np.tile(a, 3) — repete estrutura inteira.
np.tile(a, (2, 3)) — repete em várias dimensões.
18. Operações aritméticas
np.add(a, b) — soma.
np.subtract(a, b) — subtração.
np.multiply(a, b) — multiplicação.
np.divide(a, b) — divisão.
np.floor_divide(a, b) — divisão inteira.
np.mod(a, b) — módulo.
np.power(a, 2) — potência.
np.sqrt(a) — raiz quadrada.
np.square(a) — quadrado.
np.cbrt(a) — raiz cúbica.
np.reciprocal(a) — inverso.

Operadores também funcionam:

a + b
a - b
a * b
a / b
a // b
a % b
a ** 2
19. Funções matemáticas
np.abs(a) — valor absoluto.
np.absolute(a) — valor absoluto.
np.sign(a) — sinal.
np.exp(a) — exponencial.
np.exp2(a) — 2 elevado a a.
np.expm1(a) — exp(x) - 1.
np.log(a) — logaritmo natural.
np.log2(a) — logaritmo base 2.
np.log10(a) — logaritmo base 10.
np.log1p(a) — log(1+x).
np.sqrt(a) — raiz quadrada.
np.square(a) — quadrado.
np.reciprocal(a) — inverso.
20. Funções trigonométricas
np.sin(a)
np.cos(a)
np.tan(a)
np.arcsin(a)
np.arccos(a)
np.arctan(a)
np.arctan2(y, x)
np.sinh(a)
np.cosh(a)
np.tanh(a)
np.degrees(a) — radianos → graus.
np.radians(a) — graus → radianos.
21. Arredondamento
np.round(a, 2) — arredonda.
np.around(a, 2) — arredonda.
np.floor(a) — arredonda para baixo.
np.ceil(a) — arredonda para cima.
np.trunc(a) — remove parte decimal.
np.fix(a) — arredondamento em direção a zero.
22. Agregações
np.sum(a) — soma.
np.prod(a) — produto.
np.mean(a) — média.
np.median(a) — mediana.
np.std(a) — desvio padrão.
np.var(a) — variância.
np.min(a) — mínimo.
np.max(a) — máximo.
np.ptp(a) — amplitude.
np.percentile(a, 50) — percentil.
np.quantile(a, 0.5) — quantil.
np.average(a) — média ponderada.
np.sum(a, axis=0) — soma por coluna.
np.sum(a, axis=1) — soma por linha.
23. Estatística
np.mean(a)
np.median(a)
np.average(a)
np.std(a)
np.var(a)
np.percentile(a, 25)
np.percentile(a, 50)
np.percentile(a, 75)
np.quantile(a, 0.25)
np.quantile(a, 0.75)
np.ptp(a)
np.corrcoef(a, b) — correlação.
np.cov(a, b) — covariância.
24. Acumulados
np.cumsum(a) — soma acumulada.
np.cumprod(a) — produto acumulado.
np.minimum.accumulate(a) — mínimo acumulado.
np.maximum.accumulate(a) — máximo acumulado.
np.add.accumulate(a) — acumulação genérica.

Exemplo:

a = np.array([10, 20, 30, 40])

np.cumsum(a)

Resultado:

[ 10  30  60 100]
25. Mínimos e máximos
np.min(a)
np.max(a)
np.argmin(a) — posição do mínimo.
np.argmax(a) — posição do máximo.
np.minimum(a, b) — mínimo elemento a elemento.
np.maximum(a, b) — máximo elemento a elemento.
np.nanmin(a) — mínimo ignorando NaN.
np.nanmax(a) — máximo ignorando NaN.
26. Ordenação
np.sort(a) — retorna array ordenado.
a.sort() — ordena o próprio array.
np.argsort(a) — retorna índices da ordenação.
np.lexsort(...) — ordenação por múltiplas chaves.
np.partition(a, k) — particionamento.
np.argpartition(a, k) — índices do particionamento.
27. Busca e localização
np.argmax(a)
np.argmin(a)
np.where(condition)
np.nonzero(a)
np.argwhere(condition)
np.searchsorted(a, value) — posição de inserção.
np.flatnonzero(a) — posições dos elementos não zero.
28. Valores únicos
np.unique(a) — valores únicos.
np.unique(a, return_counts=True) — valores e frequências.
np.unique(a, return_index=True) — valores e índices.
np.unique(a, return_inverse=True) — mapeamento inverso.

Exemplo:

valores, contagens = np.unique(
    a,
    return_counts=True,
)
29. Valores ausentes — NaN
np.nan
np.isnan(a) — identifica NaN.
np.isfinite(a) — verifica valores finitos.
np.isinf(a) — verifica infinito.
np.nan_to_num(a) — substitui NaN/infinito.
np.nanmean(a) — média ignorando NaN.
np.nanmedian(a) — mediana ignorando NaN.
np.nanstd(a) — desvio padrão ignorando NaN.
np.nanvar(a) — variância ignorando NaN.
np.nansum(a) — soma ignorando NaN.
np.nanmin(a) — mínimo ignorando NaN.
np.nanmax(a) — máximo ignorando NaN.
np.nanpercentile(a, 50) — percentil ignorando NaN.
30. Comparações
np.equal(a, b)
np.not_equal(a, b)
np.greater(a, b)
np.greater_equal(a, b)
np.less(a, b)
np.less_equal(a, b)
np.isclose(a, b) — comparação numérica com tolerância.
np.allclose(a, b) — verifica se arrays são aproximadamente iguais.
31. Operações lógicas
np.logical_and(a, b)
np.logical_or(a, b)
np.logical_not(a)
np.logical_xor(a, b)
np.all(a) — todos verdadeiros.
np.any(a) — pelo menos um verdadeiro.
32. Operações bit a bit
np.bitwise_and(a, b)
np.bitwise_or(a, b)
np.bitwise_xor(a, b)
np.bitwise_not(a)
np.left_shift(a, 2)
np.right_shift(a, 2)
33. Álgebra linear

O módulo principal é np.linalg.

np.linalg.inv(A) — inversa.
np.linalg.det(A) — determinante.
np.linalg.matrix_rank(A) — posto.
np.linalg.solve(A, b) — resolve sistema linear.
np.linalg.lstsq(A, b) — mínimos quadrados.
np.linalg.eig(A) — autovalores/autovetores.
np.linalg.eigh(A) — matrizes simétricas/Hermitianas.
np.linalg.svd(A) — decomposição SVD.
np.linalg.norm(A) — norma.
np.linalg.qr(A) — decomposição QR.
np.linalg.cholesky(A) — decomposição de Cholesky.
np.linalg.pinv(A) — pseudoinversa.
34. Multiplicação de matrizes
np.dot(a, b) — produto.
np.matmul(a, b) — multiplicação matricial.
a @ b — operador de multiplicação matricial.
np.vdot(a, b) — produto interno.
np.inner(a, b) — produto interno.
np.outer(a, b) — produto externo.
np.kron(a, b) — produto de Kronecker.

Exemplo:

C = A @ B

Para álgebra linear moderna, @ é geralmente a forma mais clara.

35. Matrizes especiais
np.eye(n) — identidade.
np.identity(n) — identidade.
np.diag(v) — diagonal.
np.diagflat(v) — diagonal achatada.
np.tril(A) — triangular inferior.
np.triu(A) — triangular superior.
np.vander(x) — matriz de Vandermonde.
36. Geração de grades
np.meshgrid(x, y) — cria grade cartesiana.
np.mgrid[...] — cria grids densos.
np.ogrid[...] — cria grids abertos.
np.indices(...) — gera índices de uma grade.
37. Manipulação de eixos
np.expand_dims()
np.squeeze()
np.swapaxes()
np.moveaxis()
np.rollaxis() — operação mais antiga; normalmente prefira moveaxis.
np.transpose()
38. Rotação e deslocamento
np.roll(a, 1) — desloca elementos.
np.roll(a, 1, axis=0) — desloca por eixo.
np.rot90(a) — rotaciona 90°.
np.flip(a) — inverte.
np.flipud(a) — flip vertical.
np.fliplr(a) — flip horizontal.
39. Matrizes diagonais e triangulares
np.diag(A) — obtém diagonal.
np.diag(v) — cria diagonal.
np.diagonal(A) — obtém diagonal.
np.triu(A) — triangular superior.
np.tril(A) — triangular inferior.
np.trace(A) — soma diagonal.
40. Manipulação de memória e cópia
a.copy() — cópia independente.
a.view() — cria view.
a.base — verifica array base.
np.copy(a) — copia array.

Conceito fundamental:

VIEW
→ compartilha memória

COPY
→ possui memória independente
41. Views e slices
a = np.array([10, 20, 30, 40])

b = a[1:3]

b normalmente é uma view de a.

Já:

b = a[1:3].copy()

cria uma cópia independente.

Isso é particularmente importante quando você está trabalhando com grandes volumes de dados.

42. Funções universais — ufuncs

O NumPy possui operações vetorizadas chamadas Universal Functions — ufuncs.

Exemplos:

np.add
np.subtract
np.multiply
np.divide
np.power
np.sqrt
np.exp
np.log
np.sin
np.cos
np.tan
np.maximum
np.minimum
np.absolute

A grande vantagem é evitar loops Python desnecessários.

Em vez de:

resultado = []

for x in dados:
    resultado.append(x * 2)

use:

resultado = dados * 2
43. vectorize
np.vectorize(func) — transforma uma função Python em uma interface vetorizada.

Exemplo:

def classificar(x):
    return "alto" if x > 100 else "baixo"

func = np.vectorize(classificar)

resultado = func(a)

Importante: np.vectorize() melhora a conveniência da sintaxe, mas não é necessariamente uma otimização de desempenho. Para performance, prefira ufuncs e operações vetorizadas nativas.

44. Funções condicionais
np.where()
np.select()
np.choose()
np.piecewise()

Exemplo:

resultado = np.select(
    [
        vendas < 100,
        vendas < 500,
        vendas >= 500,
    ],
    [
        "Baixa",
        "Média",
        "Alta",
]
)
45. Interpolação
np.interp(x, xp, fp) — interpolação linear.
np.polynomial — ferramentas para polinômios.
46. Polinômios
np.polynomial.Polynomial
np.polynomial.Chebyshev
np.polynomial.Legendre
np.polynomial.Hermite
np.polynomial.Laguerre

Operações relacionadas:

fit()
roots()
deriv()
integ()
convert()
47. Transformada de Fourier

Módulo:

np.fft

Principais instruções:

np.fft.fft() — FFT.
np.fft.ifft() — transformada inversa.
np.fft.fft2() — FFT 2D.
np.fft.ifft2() — inversa 2D.
np.fft.fftfreq() — frequências.
np.fft.rfft() — FFT para sinais reais.
np.fft.irfft() — inversa para sinais reais.
np.fft.fftshift() — desloca componente zero.
48. Números complexos
np.real(z) — parte real.
np.imag(z) — parte imaginária.
np.conj(z) — conjugado.
np.angle(z) — argumento.
np.abs(z) — módulo.
np.real_if_close(z) — converte para real quando apropriado.
49. Datas e tempo

O NumPy possui:

np.datetime64
np.timedelta64

Exemplos:

data = np.datetime64("2026-08-20")
intervalo = np.timedelta64(7, "D")

Operações:

data + intervalo
data - intervalo
np.arange(...) com datetime64
comparação de datas.
50. Funções de calendário
np.busday_count() — quantidade de dias úteis.
np.is_busday() — verifica dia útil.
np.busday_offset() — desloca dias úteis.

Exemplo:

inicio = np.datetime64("2026-08-20")
fim = np.datetime64("2026-08-31")

np.busday_count(inicio, fim)
51. Estatística básica com pesos
np.average(a, weights=w) — média ponderada.
np.cov(a, weights=...) — dependendo do caso/versão.
np.histogram(a) — distribuição de frequência.
np.histogram2d(x, y) — histograma bidimensional.
np.histogramdd(...) — multidimensional.
52. Histogramas e distribuição
np.histogram(a)
np.histogram(a, bins=10)
np.histogram(a, bins=[0, 10, 20, 30])
np.histogram2d(x, y)
np.histogramdd(data)

Muito utilizados em EDA.

53. Correlação e covariância
np.corrcoef(x, y) — matriz de correlação.
np.cov(x, y) — matriz de covariância.

Exemplo:

correlacao = np.corrcoef(
    vendas,
    publicidade,
)[0, 1]
54. Contagem
np.count_nonzero(a) — conta valores diferentes de zero.
np.count_nonzero(a > 10) — conta valores que satisfazem condição.
np.unique(a, return_counts=True) — frequência de valores.
55. Amostragem

Com Generator:

rng.choice()
rng.integers()
rng.permutation()
rng.shuffle()

Exemplo:

rng = np.random.default_rng(42)

amostra = rng.choice(
    dados,
    size=100,
    replace=False,
)
56. Probabilidade e distribuições

O módulo:

np.random.Generator

permite gerar amostras de distribuições como:

uniforme
normal
binomial
Poisson
exponencial
beta
gamma
lognormal
multinomial
hipergeométrica
geométrica
Weibull

Exemplos:

rng.normal(
    loc=100,
    scale=15,
    size=1000,
)
rng.binomial(
    n=10,
    p=0.5,
    size=1000,
)
57. Comparação de arrays
np.array_equal(a, b) — igualdade exata.
np.array_equiv(a, b) — equivalência por broadcasting.
np.allclose(a, b) — igualdade aproximada.
np.isclose(a, b) — comparação elemento a elemento.
58. Operações de conjuntos

Para arrays:

np.unique()
np.intersect1d()
np.union1d()
np.setdiff1d()
np.setxor1d()
np.isin()

Exemplo:

np.intersect1d(
    clientes_janeiro,
    clientes_fevereiro,
)
59. Arrays estruturados
np.dtype([...])
np.zeros(..., dtype=...)
np.recarray
np.core.records.fromarrays(...)

São úteis quando se deseja representar estruturas tabulares diretamente com NumPy, embora para dados tabulares normalmente o Pandas seja mais apropriado.

60. Leitura e gravação
np.save() — salva .npy.
np.load() — carrega .npy/outros formatos suportados.
np.savez() — salva múltiplos arrays.
np.savez_compressed() — versão comprimida.
np.loadtxt() — carrega texto.
np.savetxt() — salva texto.
np.genfromtxt() — carrega texto com maior flexibilidade.

Exemplo:

np.save(
    "dados.npy",
    array,
)
dados = np.load(
    "dados.npy",
)
61. Conversão para Python
a.tolist() — converte para listas Python.
a.item() — converte elemento NumPy para tipo Python.
a.tobytes() — bytes.
a.astype(...) — conversão de dtype.
62. Verificação de tipo
np.isscalar(x) — verifica escalar.
np.issubdtype(...) — verifica relação entre tipos.
np.issubclass_() — verifica subclasses de dtype.
np.iscomplexobj()
np.isrealobj()
np.issubdtype(dtype, np.number)
np.issubdtype(dtype, np.integer)
np.issubdtype(dtype, np.floating)
63. Funções de sinal e classificação
np.sign()
np.signbit()
np.copysign()
np.heaviside()
64. Funções numéricas adicionais
np.gcd() — máximo divisor comum.
np.lcm() — mínimo múltiplo comum.
np.mod()
np.remainder()
np.divmod()
np.fmod()
np.maximum()
np.minimum()
np.fmax()
np.fmin().
65. Funções especiais
np.clip() — limita valores.
np.diff() — diferenças.
np.gradient() — gradiente.
np.ediff1d() — diferenças entre elementos.
np.cross() — produto vetorial.
np.inner() — produto interno.
np.outer() — produto externo.
66. Eixos — axis

Um dos conceitos mais importantes do NumPy.

Para:

a = np.array([
    [10, 20, 30],
    [40, 50, 60],
])

temos:

shape = (2, 3)

axis=0
↓
opera entre as linhas
resultado por coluna

axis=1
→
opera entre as colunas
resultado por linha

Exemplos:

np.sum(a, axis=0)

Resultado:

[50 70 90]

E:

np.sum(a, axis=1)

Resultado:

[ 60 150]
67. keepdims
np.sum(a, axis=1, keepdims=True)
np.mean(a, axis=0, keepdims=True)
np.max(a, axis=1, keepdims=True)

Mantém a dimensão do eixo agregado.

Isso é muito importante para operações com broadcasting.

68. einsum

Uma das operações mais poderosas do NumPy:

np.einsum(...)

Pode representar:

produto interno
multiplicação matricial
soma ponderada
operações multidimensionais
contração de tensores

Exemplo:

np.einsum(
    "ij,jk->ik",
    A,
    B,
)

equivale, conceitualmente, a:

A @ B
69. Operações de álgebra tensorial
np.tensordot()
np.einsum()
np.einsum_path()
np.inner()
np.outer()
np.dot()
np.matmul()

São particularmente relevantes em:

Machine Learning
Deep Learning
processamento de imagens
computação científica.
70. Performance

Boas práticas:

preferir operações vetorizadas;
evitar for Python quando houver operação NumPy equivalente;
evitar np.vectorize() quando performance for o objetivo;
utilizar dtype apropriado;
evitar cópias desnecessárias;
utilizar views quando apropriado;
trabalhar com operações axis;
usar broadcasting;
utilizar arrays contíguos quando necessário;
utilizar np.linalg para álgebra linear;
considerar numba para algoritmos que realmente exigem loops.
71. NumPy × Python

Em vez de:

resultado = []

for valor in valores:
    resultado.append(valor * 2)

prefira:

resultado = valores * 2

Em vez de:

resultado = []

for valor in valores:
    if valor > 100:
        resultado.append(1)
    else:
        resultado.append(0)

prefira:

resultado = np.where(
    valores > 100,
    1,
    0,
)
72. NumPy × Pandas

Uma distinção importante para seu estudo:

NumPy
│
├── ndarray
├── vetores
├── matrizes
├── álgebra linear
├── operações numéricas
├── estatística numérica
├── broadcasting
├── computação vetorizada
└── arrays multidimensionais

Enquanto:

Pandas
│
├── Series
├── DataFrame
├── Index
├── dados tabulares
├── dados categóricos
├── datas
├── valores ausentes
├── groupby
├── merge/join
├── pivot
└── ETL/EDA

Na prática:

import numpy as np
import pandas as pd

df = pd.DataFrame({
    "vendas": [100, 200, 300],
    "custos": [50, 120, 180],
})

df["lucro"] = (
    df["vendas"].to_numpy()
    - df["custos"].to_numpy()
)

Mas muitas vezes o próprio Pandas já resolve:

df["lucro"] = df["vendas"] - df["custos"]
73. Fluxo NumPy para Data Science

Uma forma útil de visualizar o NumPy:

DADOS
  ↓
np.array()
  ↓
INSPEÇÃO
  ↓
shape
ndim
size
dtype
  ↓
LIMPEZA
  ↓
isnan()
isfinite()
where()
  ↓
TRANSFORMAÇÃO
  ↓
reshape()
transpose()
astype()
  ↓
VETORIZAÇÃO
  ↓
broadcasting
ufuncs
  ↓
ESTATÍSTICA
  ↓
mean()
median()
std()
percentile()
  ↓
ÁLGEBRA LINEAR
  ↓
dot()
matmul()
solve()
svd()
  ↓
MODELAGEM / ANÁLISE
  ↓
Pandas / Scikit-learn / SciPy
74. O que realmente dominar primeiro

Para o seu objetivo de Análise de Dados + Data Science + Engenharia de Dados, eu dividiria o estudo de NumPy em níveis:

Nível 1 — Fundamental
np.array()
np.zeros()
np.ones()
np.arange()
np.linspace()

shape
ndim
size
dtype

[]
[:]
Nível 2 — Manipulação
reshape()
ravel()
flatten()
transpose()
T
concatenate()
stack()
vstack()
hstack()
split()
Nível 3 — Seleção
indexing
slicing
fancy indexing
boolean indexing

where()
nonzero()
argwhere()
Nível 4 — Computação vetorizada
+
-
*
/
**
np.add()
np.multiply()
np.sqrt()
np.exp()
np.log()

broadcasting
ufuncs
Nível 5 — Estatística
sum()
mean()
median()
std()
var()
min()
max()
percentile()
quantile()
corrcoef()
cov()
Nível 6 — Dados
unique()
isin()
sort()
argsort()
searchsorted()
histogram()
Nível 7 — Valores ausentes
isnan()
isfinite()
isinf()
nanmean()
nanmedian()
nansum()
nanmin()
nanmax()
nan_to_num()
Nível 8 — Álgebra linear
dot()
matmul()
@
inv()
det()
solve()
eig()
svd()
norm()
Nível 9 — Estatística e simulação
default_rng()
random()
integers()
choice()
normal()
uniform()
binomial()
poisson()
exponential()
Nível 10 — Avançado
einsum()
tensordot()
FFT
polynomial
structured arrays
memory views
broadcasting avançado
Resumindo a relação entre NumPy e Pandas

Uma boa sequência para seu aprendizado seria:

                    PYTHON
                       │
                       ▼
                    NUMPY
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
       arrays       vetorização   matemática
          │            │            │
          └────────────┼────────────┘
                       ▼
                    PANDAS
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      DataFrame      Series       Index
          │
          ▼
       limpeza
          │
          ▼
      transformação
          │
          ▼
       groupby
          │
          ▼
     merge / join
          │
          ▼
       análise
          │
          ▼
     VISUALIZAÇÃO
          │
     ┌────┴────┐
     ▼         ▼
 Matplotlib   Seaborn
     │
     ▼
 DATA SCIENCE
     │
     ▼
Scikit-learn

Em termos de prioridade: para trabalhar profissionalmente com dados, eu consideraria NumPy + Pandas como a dupla fundamental do ecossistema Python de dados. NumPy fornece a base numérica e vetorizada; Pandas acrescenta a camada tabular, índices, limpeza, agregação e integração de dados.
