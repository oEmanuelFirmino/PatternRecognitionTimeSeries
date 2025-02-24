# Implementação de Regressão Linear

Este documento descreve a implementação de um modelo de **regressão linear** para prever variáveis como temperatura e umidade com base em outros fatores, utilizando **gradiente descendente** para ajustar os parâmetros do modelo. A implementação é feita a partir dos conceitos matemáticos fundamentais de álgebra linear e cálculo.

## 1. Conceitos Fundamentais

A **regressão linear** é um método utilizado para modelar a relação entre uma variável dependente $( y )$ e uma ou mais variáveis independentes $( x_1, x_2, \dots, x_n )$. O modelo tenta ajustar uma linha reta que minimize o erro entre as previsões feitas pelo modelo e os dados reais.

A fórmula para regressão linear simples é:

$$[
y = \beta_0 + \beta_1 x
]$$

Onde:
- $( y ) é a variável dependente (ex: temperatura ou umidade),
- $( x )$ é a variável independente (ex: hora ou outro fator),
- $( \beta_0 )$ é o **intercepto** da linha,
- $( \beta_1 )$ é o **coeficiente angular** (ou inclinação).

Em casos de **regressão múltipla**, onde temos várias variáveis independentes, a equação generalizada é:

$$[
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n
]$$

## 2. Função de Custo

Para encontrar os coeficientes $( \beta_0, \beta_1, \dots, \beta_n )$, o modelo é ajustado minimizando a **função de custo**. A função de custo utilizada é o **Erro Quadrático Médio (MSE)**, dada por:

$$[
MSE = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2
]$$

Onde:
- $( N )$ é o número total de pontos de dados,
- $( y_i )$ são os valores reais (observados),
- $( \hat{y}_i )$ são os valores previstos pelo modelo.

O objetivo é **minimizar** o valor do MSE ajustando os coeficientes.

## 3. Gradiente Descendente

Para minimizar a função de custo, utilizamos o algoritmo de **gradiente descendente**, que ajusta os coeficientes de forma iterativa. O gradiente descendente é baseado no cálculo das **derivadas parciais** da função de custo em relação a cada parâmetro $( \beta_j )$, e então atualiza os parâmetros na direção oposta ao gradiente.

As atualizações para os coeficientes são feitas da seguinte forma:

$$[
\beta_j = \beta_j - \alpha \cdot \frac{\partial MSE}{\partial \beta_j}
]$$

Onde:
- $( \alpha )$ é a **taxa de aprendizado** (quanto ajustamos a cada iteração),
- $( \frac{\partial MSE}{\partial \beta_j} )$ é a derivada do MSE com relação ao coeficiente $( \beta_j )$.

## 4. Derivadas Parciais do MSE

As derivadas parciais do **Erro Quadrático Médio** (MSE) em relação aos coeficientes $( \beta_0, \beta_1, \dots, \beta_n )$ são calculadas da seguinte forma:

Para o intercepto $( \beta_0 )$:

$$[
\frac{\partial MSE}{\partial \beta_0} = - \frac{2}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)
]$$

Para os outros coeficientes \( \beta_j \) (onde \( j \geq 1 \)):

$$[
\frac{\partial MSE}{\partial \beta_j} = - \frac{2}{N} \sum_{i=1}^{N} x_{ij} (y_i - \hat{y}_i)
]$$

Onde $( x_{ij} )$ representa os valores das variáveis independentes $( x_1, x_2, \dots, x_n )$.

## 5. Implementação do Algoritmo de Gradiente Descendente

### Passo 1: Inicialização dos Parâmetros

Os coeficientes $( \beta_0, \beta_1, \dots, \beta_n )$ são inicialmente configurados para zero, e a taxa de aprendizado $( \alpha )$ é definida.

```python
# Inicialização dos parâmetros
beta = np.zeros(X.shape[1])  # Inicializa os coeficientes como 0
alpha = 0.01  # Taxa de aprendizado
iterations = 1000  # Número de iterações
```

### Passo 2: Função de Custo (MSE)

A função de custo calcula o erro entre as previsões $( \hat{y})$ e os valores reais $( y )$.

```python
def compute_cost(X, y, beta):
    m = len(y)
    predictions = X.dot(beta)
    cost = (1 / (2 * m)) * np.sum(np.square(predictions - y))
    return cost
```

### Passo 3: Gradiente Descendente

O algoritmo de gradiente descendente ajusta os coeficientes iterativamente:

```python
def gradient_descent(X, y, beta, alpha, iterations):
    m = len(y)
    cost_history = []

    for i in range(iterations):
        predictions = X.dot(beta)
        error = predictions - y

        # Atualiza os coeficientes beta
        beta -= (alpha / m) * X.T.dot(error)

        # Calcula o custo a cada iteração
        cost_history.append(compute_cost(X, y, beta))

    return beta, cost_history
```

### Passo 4: Treinamento do Modelo

A função `gradient_descent` é chamada para treinar o modelo e encontrar os coeficientes ótimos.

```python
beta_optimal, cost_history = gradient_descent(X, y_temp, beta, alpha, iterations)
```

### Passo 5: Avaliação do Modelo (R²)

O **coeficiente de determinação** $R^2$ mede o quanto a variação da variável dependente é explicada pelo modelo:


$$R^2 = 1 - \frac{\sum (y - \hat{y})^2}{\sum (y - \bar{y})^2}$$


Onde:
- ( y ) são os valores reais,
- $\hat{y}$ são as previsões feitas pelo modelo,
- $\bar{y}$ é a média dos valores reais.

```python
def r2_score(y, y_pred):
    ss_total = np.sum((y - np.mean(y))**2)
    ss_residual = np.sum((y - y_pred)**2)
    return 1 - (ss_residual / ss_total)
```

### Passo 6: Visualização dos Resultados

Os resultados do modelo podem ser visualizados para comparar as previsões com os valores reais:

```python
import matplotlib.pyplot as plt

# Visualizar os resultados
plt.scatter(df['Time'], y_temp, color='blue', label='Real')
plt.plot(df['Time'], y_pred, color='red', label='Predição')
plt.xlabel('Tempo')
plt.ylabel('Temperatura')
plt.title('Temperatura Real vs Predição com Regressão Linear')
plt.legend()
plt.show()
```