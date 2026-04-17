# Tarefa - Fase 2: Detecção de Anomalias e Visualizações (base_census)

## Estrutura do Notebook `census0417_amt4.ipynb`

---

## Fase 1 - Análise Exploratória de Anomalias (Cells 11-26)

### Possíveis valores nulos (Cells 12-14)
- Verificação de dados nulos com `isnull().sum()`
- Listagem de registros que possuem valores nulos

### Possíveis valores "?" em colunas categóricas (Cells 15-17)
- Detecção de dados faltantes disfarçados como `"?"` nas colunas categóricas
- Colunas afetadas: `workclass`, `occupation`, `native-country`
- Exibição dos registros com `"?"` na coluna `workclass`

### Possíveis idades negativas ou fora de faixa (Cells 18-19)
- Busca por registros com `age < 0` (incongruências lógicas)

### Possíveis capital-gain com valor 99999 (Cells 20-22)
- Identificação de possíveis valores de teto/anomalia em `capital-gain`
- Contagem e percentual dos registros com valor `99999`

### Possíveis horas por semana extremas (Cells 23-24)
- Registros com `hour-per-week > 80` (outliers ou incongruências)

### Possíveis valores negativos em colunas numéricas (Cells 25-26)
- Verificação sistemática de todas as colunas numéricas:
  - `age`, `final-weight`, `education-num`, `capital-gain`, `capital-loos`, `hour-per-week`

---

## Fase 2 - Visualização de Dados e Anomalias (Cells 27-44)

### Eixos de Alvos de Aprendizagem (Cells 28-30)
- `np.unique()` para contagem de valores da variável alvo `income`
- `sns.countplot()` com paleta de cores (`skyblue`, `salmon`) para visualizar distribuição de `<=50K` vs `>50K`

### Distribuições das Variáveis Numéricas (Cells 31-34)
- Histograma de `age`
- Histograma de `education-num`
- Histograma de `hour-per-week`

### Detecção de Outliers em capital-gain (Cells 35-37)
- Histograma de `capital-gain` — detecta área de outliers (valor `99999`)
- Histograma de `capital-loos`

### Boxplots para Detecção Visual de Outliers (Cells 38-39)
- Grid 2x3 de boxplots para todas as variáveis numéricas:
  - `age`, `final-weight`, `education-num`
  - `capital-gain`, `capital-loos`, `hour-per-week`
- Permite identificar visualmente pontos fora da distribuição esperada

### Matriz de Dispersão (Cells 40-41)
- `px.scatter_matrix()` interativa (Plotly) com:
  - Dimensões: `age`, `education-num`, `hour-per-week`, `capital-gain`
  - Cor: `income` (variável alvo)
- Permite visualizar correlações e padrões entre variáveis numéricas

### Visualização de Dados Faltantes "?" (Cells 42-43)
- Gráfico de barras mostrando quantidade de registros com `"?"` por coluna categórica

### Treemap Hierárquico (Cell 44)
- Visualização hierárquica com Plotly: `occupation` > `relationship` > `age`
