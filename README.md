# Atividade — Bagging e Boosting

Integrantes:
  - Caroline Guimarães Campos
  - Isabela Groke Gomes
    
## Descrição

Esta atividade tem como objetivo implementar e comparar dois métodos de aprendizado de máquina: **Bagging** e **Boosting**, utilizando a biblioteca Scikit-Learn.

O conjunto de dados utilizado é o `seattle_weather`, disponível no pacote `vega_datasets`. O objetivo é prever a temperatura máxima diária (`temp_max`) com base em informações meteorológicas.

## Tecnologias utilizadas

- Python
- Pandas
- Scikit-Learn
- Vega Datasets
- Jupyter Notebook

## Dataset

O dataset `seattle_weather` contém **1.461 registros e 6 colunas**, com informações meteorológicas da cidade de Seattle.

As variáveis originais são:

| Variável | Descrição |
|---|---|
| date | Data do registro |
| precipitation | Precipitação |
| temp_max | Temperatura máxima |
| temp_min | Temperatura mínima |
| wind | Velocidade do vento |
| weather | Condição climática |

A variável alvo é `temp_max`.

## Etapas da atividade

### 1. Preparação dos dados

- Carregamento e exploração inicial do dataset.
- Verificação dos tipos de dados e valores ausentes.
- Extração de ano, mês e dia da coluna `date`.
- Transformação da variável categórica `weather` utilizando `OneHotEncoder`.
- Separação dos dados em 80% para treinamento e 20% para teste.

### 2. Modelo Bagging

Foi utilizado o `BaggingRegressor`, tendo árvores de decisão (`DecisionTreeRegressor`) como estimadores-base.

O Bagging treina diversos modelos a partir de diferentes amostras dos dados e combina suas previsões, buscando reduzir a variância e melhorar a estabilidade dos resultados.

**Configurações:**
- 100 estimadores
- Árvore de decisão como modelo-base
- `random_state=42`

### 3. Modelo Boosting

Foi utilizado o `GradientBoostingRegressor`, que constrói modelos sequencialmente, buscando corrigir os erros das etapas anteriores.

**Configurações:**
- 100 estimadores
- Taxa de aprendizado (`learning_rate`) de 0.1
- Profundidade máxima (`max_depth`) de 3
- `random_state=42`

## Resultados

Os modelos foram avaliados utilizando três métricas:

- **MAE:** erro absoluto médio.
- **RMSE:** raiz do erro quadrático médio.
- **R²:** coeficiente de determinação.

| Modelo | MAE | RMSE | R² |
|---|---:|---:|---:|
| Bagging | 2.030 | 2.615 | 0.88 |
| Boosting | 2.026 | 2.608 | 0.88 |

## Conclusão

Os dois modelos apresentaram resultados bastante semelhantes na previsão da temperatura máxima.

O **Boosting obteve um desempenho ligeiramente superior**, apresentando menores valores de MAE e RMSE. Entretanto, a diferença foi pequena, e ambos alcançaram um R² de aproximadamente 0.88.

Dessa forma, a atividade permitiu observar o funcionamento das duas técnicas de aprendizado em conjunto (*ensemble learning*) e comparar seus desempenhos em um problema de regressão.

## Como executar

1. Instale as dependências necessárias:

```bash
pip install pandas scikit-learn vega_datasets jupyter
```

2. Abra o arquivo `Atividade_Bagging_e_Boosting.ipynb` no Jupyter Notebook ou Google Colab.

3. Execute as células na ordem apresentada para realizar o treinamento, a avaliação e a comparação dos modelos.
