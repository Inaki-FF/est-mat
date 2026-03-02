# Ejercicios 10–11 Resueltos — Suficiencia de |X| y Variables No Idénticamente Distribuidas

*Desde cero.*

---

## Recordatorio: Teorema de Factorización

T es suficiente para θ si puedes escribir:

$$f(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

- g: depende de los datos **solo** a través de T, y puede depender de θ
- h: depende de los datos pero **no** de θ

---

# Ejercicio 10 — ¿|X| es suficiente para σ? ¿Para σ²?

## Enunciado

X es **una sola observación** de N(0, σ²). ¿Es |X| suficiente para σ? ¿Para σ²?

## Aclaración importante

Aquí n = 1 (una sola observación). La "muestra" es solo X. La densidad es:

$$f(x; \sigma) = \frac{1}{\sqrt{2\pi}\sigma}\exp\left(-\frac{x^2}{2\sigma^2}\right), \quad x \in \mathbb{R}$$

## Solución: Factorización

Reescribimos la densidad:

$$f(x; \sigma) = \underbrace{\frac{1}{\sqrt{2\pi}\sigma}\exp\left(-\frac{x^2}{2\sigma^2}\right)}_{g(x^2;\; \sigma)} \cdot \underbrace{1}_{h(x)}$$

La densidad depende de x **solamente** a través de x². Y como |x| y x² están en correspondencia uno a uno para x real (si conoces |x|, conoces x² = |x|², y viceversa), tenemos que:

- T₁ = X² es suficiente para σ
- T₂ = |X| es suficiente para σ (porque |X| = √(X²) es función uno a uno de X²)

**¿Suficiente para σ o para σ²?** La suficiencia es una propiedad de la estadística respecto al **modelo**, no respecto a una reparametrización específica. Si T es suficiente para σ, automáticamente es suficiente para cualquier función de σ, incluyendo σ².

$$\boxed{|X| \text{ es suficiente tanto para } \sigma \text{ como para } \sigma^2}$$

## ¿Por qué tiene sentido?

Si X ∼ N(0, σ²), el signo de X no tiene información sobre σ. X es positivo o negativo con probabilidad 1/2 sin importar el valor de σ. Toda la información sobre σ está en **qué tan lejos de cero** cae X, es decir, en |X|.

Formalmente: la distribución condicional de X dado |X| = t es:

$$P(X = t \mid |X| = t) = P(X = -t \mid |X| = t) = 1/2$$

No depende de σ. Eso es exactamente la definición de suficiencia.

---

# Ejercicio 11 — Variables no idénticamente distribuidas

## Enunciado

X₁, ..., Xₙ son **independientes** (pero **no** idénticamente distribuidas) con:

$$f_k(x; \theta) = \exp(k\theta - x), \quad x > k\theta, \quad k = 1, 2, \ldots, n$$

Encuentre una estadística suficiente para θ.

## ¿Por qué "no forman una muestra aleatoria"?

En una muestra aleatoria, todas las observaciones tienen la **misma** distribución. Aquí la densidad de Xₖ depende de k:
- X₁ tiene soporte x > θ
- X₂ tiene soporte x > 2θ
- X₃ tiene soporte x > 3θ
- etc.

Cada observación tiene un soporte diferente. Es como si cada medición se hiciera con un instrumento diferente.

## Paso 1: Identificar la distribución

Reescribamos la densidad de Xₖ:

$$f_k(x; \theta) = e^{k\theta} \cdot e^{-x} \cdot \mathbf{1}(x > k\theta)$$

donde **1**(x > kθ) es la función indicadora (vale 1 si x > kθ, y 0 si no).

**Esto es una distribución Exponencial desplazada:** Xₖ - kθ ∼ Exponencial(1).

## Paso 2: Densidad conjunta

$$f(x_1, \ldots, x_n; \theta) = \prod_{k=1}^{n} f_k(x_k; \theta)$$

$$= \prod_{k=1}^{n} \left[e^{k\theta - x_k} \cdot \mathbf{1}(x_k > k\theta)\right]$$

$$= \exp\left(\theta\sum_{k=1}^n k - \sum_{k=1}^n x_k\right) \cdot \prod_{k=1}^n \mathbf{1}(x_k > k\theta)$$

## Paso 3: Analizar la función indicadora

El producto de indicadoras vale 1 si y solo si **todas** se cumplen:

$$x_k > k\theta \quad \text{para todo } k = 1, \ldots, n$$

Esto equivale a:

$$\frac{x_k}{k} > \theta \quad \text{para todo } k$$

Lo cual equivale a:

$$\min_{k=1,\ldots,n}\left\{\frac{x_k}{k}\right\} > \theta$$

Así que el producto de indicadoras se puede escribir como:

$$\prod_{k=1}^n \mathbf{1}(x_k > k\theta) = \mathbf{1}\left(\min_k\left\{\frac{X_k}{k}\right\} > \theta\right)$$

## Paso 4: Factorización

$$f(x^{(n)}; \theta) = \underbrace{\exp\left(\frac{n(n+1)}{2}\theta\right) \cdot \mathbf{1}\left(\min_k\left\{\frac{x_k}{k}\right\} > \theta\right)}_{g\left(\min_k\{x_k/k\};\; \theta\right)} \cdot \underbrace{\exp\left(-\sum_{k=1}^n x_k\right)}_{h(x^{(n)})}$$

La parte que depende de θ involucra los datos **solo** a través de $\min_k\{X_k/k\}$.

$$\boxed{T = \min_{k=1,\ldots,n}\left\{\frac{X_k}{k}\right\} \text{ es suficiente para } \theta}$$

## ¿Por qué tiene sentido?

El parámetro θ determina dónde "empiezan" los datos (los soportes). La información sobre θ está concentrada en cuál observación (ajustada por su índice k) cae más cerca del borde izquierdo de su soporte. Eso es precisamente el mínimo de Xₖ/k.

**Nota:** Este es un caso donde el soporte depende del parámetro, similar a la Uniforme(0, θ). En estos casos, la estadística suficiente suele involucrar un extremo muestral (máximo o mínimo).
