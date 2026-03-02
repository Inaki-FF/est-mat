# Ejercicio 7 Resuelto — CICR para φ(θ)

*La demostración más importante del curso, explicada desde cero.*

---

## Contexto: ¿Qué es la CICR?

### El problema

Tienes un estimador insesgado θ̂ de θ. Ya sabes que es "bueno" porque en promedio da el valor correcto. Pero, ¿qué tan pequeña puede ser su varianza? ¿Hay un **límite inferior**?

### La respuesta: el Teorema de Cramér-Rao

Sí. Ningún estimador insesgado puede tener varianza menor que cierta cota:

$$\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot I(\theta)} = \text{CICR}(\theta)$$

donde $I(\theta)$ es la **Información de Fisher**:

$$I(\theta) = E\left[\left(\frac{\partial}{\partial \theta} \ln f(X; \theta)\right)^2\right]$$

**Esto ya se demostró en clase para estimar θ directamente.** Ahora nos piden demostrarlo para estimar una **función** de θ.

## Enunciado preciso

Si en lugar de estimar θ, quieres estimar **φ = φ(θ)** (una función de θ), demuestra que para todo estimador insesgado φ̂ de φ:

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$$

## Conceptos previos

### La desigualdad de Cauchy-Schwarz

Para dos variables aleatorias U y V:

$$[E(UV)]^2 \leq E[U^2] \cdot E[V^2]$$

O equivalentemente, en términos de covarianza:

$$[\text{Cov}(U, V)]^2 \leq \text{Var}(U) \cdot \text{Var}(V)$$

Esto es como decir que la correlación siempre está entre -1 y 1. Es la herramienta central de esta demostración.

### La función Score

Definimos la **función Score** como:

$$S(\theta) = \frac{\partial}{\partial \theta} \ln L(\theta; X^{(n)})$$

donde $L(\theta; X^{(n)}) = \prod_{i=1}^{n} f(X_i; \theta)$ es la verosimilitud. Entonces:

$$S(\theta) = \sum_{i=1}^{n} \frac{\partial}{\partial \theta} \ln f(X_i; \theta)$$

**Propiedad fundamental del Score:**

$$E[S(\theta)] = 0$$

(Esto se demuestra intercambiando derivada con integral — es parte de las "condiciones de regularidad" que se piden.)

**Varianza del Score:**

$$\text{Var}(S(\theta)) = E[S(\theta)^2] = n \cdot I(\theta)$$

## Demostración

### Paso 1: Planteamiento

Sea φ̂ un estimador insesgado de φ(θ). Eso significa:

$$E[\hat{\varphi}] = \varphi(\theta) \quad \text{para todo } \theta$$

Escrito como integral (o suma):

$$\int \hat{\varphi}(x^{(n)}) \cdot f_{X^{(n)}}(x^{(n)}; \theta) \, dx^{(n)} = \varphi(\theta)$$

### Paso 2: Derivar ambos lados respecto a θ

Lado derecho:

$$\frac{d}{d\theta} \varphi(\theta) = \varphi'(\theta)$$

Lado izquierdo (intercambiando derivada con integral — aquí entran las condiciones de regularidad):

$$\int \hat{\varphi}(x^{(n)}) \cdot \frac{\partial}{\partial \theta} f_{X^{(n)}}(x^{(n)}; \theta) \, dx^{(n)}$$

### Paso 3: El truco clave

Usamos la identidad:

$$\frac{\partial}{\partial \theta} f = f \cdot \frac{\partial}{\partial \theta} \ln f = f \cdot S(\theta)$$

Esto sale de que $\frac{d}{d\theta}\ln f = \frac{1}{f}\frac{df}{d\theta}$, así que $\frac{df}{d\theta} = f \cdot \frac{d \ln f}{d\theta}$.

Sustituyendo:

$$\int \hat{\varphi} \cdot f \cdot S(\theta) \, dx^{(n)} = \varphi'(\theta)$$

El lado izquierdo es precisamente $E[\hat{\varphi} \cdot S(\theta)]$:

$$E[\hat{\varphi} \cdot S(\theta)] = \varphi'(\theta)$$

### Paso 4: Calcular la covarianza

Como E[S(θ)] = 0:

$$\text{Cov}(\hat{\varphi}, S(\theta)) = E[\hat{\varphi} \cdot S(\theta)] - E[\hat{\varphi}] \cdot E[S(\theta)]$$

$$= \varphi'(\theta) - \varphi(\theta) \cdot 0 = \varphi'(\theta)$$

### Paso 5: Aplicar Cauchy-Schwarz

$$[\text{Cov}(\hat{\varphi}, S(\theta))]^2 \leq \text{Var}(\hat{\varphi}) \cdot \text{Var}(S(\theta))$$

Sustituyendo:

$$[\varphi'(\theta)]^2 \leq \text{Var}(\hat{\varphi}) \cdot n \cdot I(\theta)$$

Despejando:

$$\boxed{\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}}$$

**Q.E.D.** ∎

## Casos particulares

| Caso | φ(θ) | φ'(θ) | CICR |
|---|---|---|---|
| Estimar θ mismo | φ(θ) = θ | φ'(θ) = 1 | 1/[n·I(θ)] |
| Estimar θ² | φ(θ) = θ² | φ'(θ) = 2θ | 4θ²/[n·I(θ)] |
| Estimar 1/θ | φ(θ) = 1/θ | φ'(θ) = -1/θ² | 1/[θ⁴·n·I(θ)] |
| Estimar ln(θ) | φ(θ) = ln(θ) | φ'(θ) = 1/θ | 1/[θ²·n·I(θ)] |

## ¿Cuándo se alcanza la igualdad?

La igualdad en Cauchy-Schwarz se da cuando $\hat{\varphi} = a \cdot S(\theta) + b$ para constantes a, b. Esto ocurre solo en familias exponenciales y para ciertas funciones φ(θ). Cuando se alcanza, el estimador es **MVUE** (el mejor insesgado posible).
