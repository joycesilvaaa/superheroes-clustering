# superheroes-clustering

Análise e clustering (KMeans) das habilidades de super-heróis usando um dataset público.

Este repositório contém um notebook Jupyter (`superheros.ipynb`) que carrega um dataset de habilidades de super-heróis, realiza análise exploratória, pré-processamento, escolhe um número ótimo de clusters (Elbow + Silhouette) e aplica KMeans, com visualizações em 2D/3D usando PCA.

## Estrutura

- `superheros.ipynb` - Notebook principal que contém todo o fluxo de trabalho: carregamento dos dados, EDA, pré-processamento, seleção de k, execução do KMeans e visualizações (PCA 2D/3D).

## Descrição do fluxo principal

1. Baixa/abre o dataset (o notebook usa `kagglehub.dataset_download("hemajitpatel/superheros-abilities-dataset")`). O arquivo utilizado é `superhero_abilities_dataset.csv`.
2. Carrega os dados com pandas e realiza análise exploratória: visualizações, boxplots e matriz de correlação.
3. Tratamento de valores ausentes (o notebook preenche usando médias das colunas numéricas).
4. Seleção de features para clustering (padrão no notebook):
	- `Strength`, `Speed`, `Intelligence`, `Combat Skill`
5. Padronização com `StandardScaler`.
6. Seleção do número de clusters k usando Elbow (inertia) e Silhouette score (range padrão no notebook: 2 a 10).
7. Ajuste final do `KMeans` com o k escolhido; anexa coluna `Cluster` ao DataFrame.
8. Cálculo e exibição dos centroides na escala original (inverte a padronização para interpretação).
9. Redução de dimensionalidade com PCA (2D e 3D) e plotagem dos clusters (matplotlib e plotly para 3D).

## Requisitos

- Python 3.8+
- Bibliotecas usadas (exemplo de instalação):

```bash
pip install pandas numpy matplotlib seaborn scikit-learn plotly kagglehub
```

Observação: dependendo do seu ambiente, você pode preferir criar um virtualenv ou usar conda.

## Como executar

1. Certifique-se de ter as dependências instaladas.
2. Abra o notebook `superheros.ipynb` com Jupyter Notebook / JupyterLab:

```bash
jupyter lab
# ou
jupyter notebook
```

3. Execute as células do notebook na ordem. A célula que baixa o dataset usa `kagglehub`; pode ser necessário configurar credenciais do Kaggle localmente, caso não esteja autenticado (consulte a documentação do `kagglehub`/Kaggle para detalhes).

4. Ajustes rápidos que você pode fazer no notebook:
	- `features`: alterar a lista de atributos usados para o clustering.
	- `K_range`: alterar o intervalo de k a ser testado.
	- Parâmetros do KMeans (`n_init`, `max_iter`, `random_state`).

## Resultados esperados

- Gráficos de EDA (boxplots, matriz de correlação).
- Gráficos Elbow e Silhouette para escolha de k.
- DataFrame com coluna `Cluster` e tabela com centroides (valores em escala original) para interpretação dos grupos.
- Visualização dos clusters em 2D (PCA) e 3D (plotly).

## Sugestões de extensões / próximos passos

- Experimentar com mais atributos do dataset.
- Testar outros algoritmos de clustering (DBSCAN, Agglomerative).
- Normalizar/transformar variáveis de forma diferente (RobustScaler, MinMaxScaler).
- Fazer análise qualitativa dos clusters (listar nomes/identidades dos super-heróis por cluster).
- Salvar resultados em CSV para análises futuras.

## Observações

- O notebook foi criado para ser exploratório e educativo — ajuste hiperparâmetros conforme o objetivo (análise versus produção).

