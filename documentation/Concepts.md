# 📘 Documentação: Reconhecimento de Padrões em Séries Temporais

## **1️⃣ Introdução**

Séries temporais são conjuntos de dados ordenados cronologicamente. Elas aparecem frequentemente em fenômenos, como oscilações em circuitos, variações de temperatura e sistemas dinâmicos caóticos.

O objetivo desta documentação é apresentar métodos de análise e previsão de séries temporais físicas, incluindo seus fundamentos matemáticos.

---

## **2️⃣ Características Fundamentais das Séries Temporais**

### **1. Tendência**

A tendência é a variação de longo prazo da série temporal, que pode ser modelada por funções polinomiais:

$$
T(t) = a_0 + a_1 t + a_2 t^2 + \dots + a_n t^n
$$

### **2. Sazonalidade**

Representa padrões repetitivos com um período fixo, podendo ser modelada por séries de Fourier:

$$
S(t) = \sum_{k=1}^{N} \left(A_k \cos\left(\frac{2\pi k t}{P}\right) + B_k \sin\left(\frac{2\pi k t}{P}\right)\right)
$$

Onde:

- \( P \) é o período da oscilação,
- \( A_k \) e \( B_k \) são coeficientes da série.

### **3. Ruído**

Ruído é a parte aleatória da série temporal e pode ser modelado por distribuições estatísticas como Gaussiana:

$$
X(t) \sim \mathcal{N}(\mu, \sigma^2)
$$

---

## **3️⃣ Métodos de Análise de Séries Temporais**

### **1. Transformada de Fourier (FFT)**

A Transformada de Fourier converte a série do domínio do tempo para o domínio da frequência:

$$
F(\omega) = \int_{-\infty}^{\infty} x(t) e^{-i\omega t} dt
$$

A versão discreta (DFT) usada em computação é:

$$
X_k = \sum_{n=0}^{N-1} x_n e^{-i 2\pi k n / N}
$$

Essa abordagem permite identificar frequências dominantes em uma série periódica.

### **2. Modelos Autoregressivos (ARIMA)**

O modelo ARIMA combina três componentes:

1. **AR (Autoregressivo):** Representa a relação entre valores passados da série:
   $$
   X_t = c + \sum_{i=1}^{p} \phi_i X_{t-i} + \varepsilon_t
   $$
2. **I (Integração):** Diferença entre valores sucessivos para tornar a série estacionária:
   $$
   Y_t = X_t - X_{t-1}
   $$
3. **MA (Média Móvel):** Modela o erro com base em erros passados:
   $$
   X_t = \mu + \sum_{j=1}^{q} \theta_j \varepsilon_{t-j} + \varepsilon_t
   $$

O modelo completo ARIMA(p,d,q) é uma combinação dessas três equações.

### **3. Redes Neurais Recorrentes (RNN) e LSTM**

As RNNs são úteis para séries temporais porque retêm informações passadas. A atualização dos estados segue a equação:

$$
 h_t = f(W_h h_{t-1} + W_x x_t + b)
$$

No caso das **LSTM**, há três portas principais:

1. **Porta de Esquecimento:** Decide quais informações descartar:
   $$
   f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)
   $$
2. **Porta de Entrada:** Atualiza o estado da célula:
   $$
   i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)
   $$
3. **Porta de Saída:** Define a próxima saída da célula:
   $$
   o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)
   $$

Isso permite que o modelo aprenda padrões longos sem o problema do **desvanecimento do gradiente**.

---

## **4️⃣ Implementação e Avaliação**

### **Métricas de Avaliação**

- **Erro Quadrático Médio (MSE):**
  $$
  MSE = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y_i})^2
  $$
- **Erro Absoluto Médio (MAE):**
  $$
  MAE = \frac{1}{N} \sum_{i=1}^{N} |y_i - \hat{y_i}|
  $$
- **Coeficiente de Correlação de Pearson:**
  $$
  r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}}
  $$

---

## **5️⃣ Conclusão**

O reconhecimento de padrões em séries temporais físicas é uma ferramenta poderosa para previsão e análise de fenômenos físicos complexos. Métodos clássicos como FFT e ARIMA são úteis para padrões simples, enquanto redes neurais recorrentes como LSTM capturam dinâmicas mais complexas.
