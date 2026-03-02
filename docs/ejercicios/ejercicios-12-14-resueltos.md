# Ejercicios 12–14 Resueltos — Rao-Blackwell, Laplace y Familia Exponencial

*Los tres ejercicios finales. Desde cero.*

---

# Ejercicio 12 — Rao-Blackwellización

## ¿De qué va este ejercicio?

Imagina que ya tienes un estimador insesgado θ̂₁, pero sospechas que no es el mejor posible. La **Rao-Blackwellización** es un mecanismo para **mejorarlo** (reducir su varianza) usando una estadística suficiente.

## Enunciado

Sea θ̂₁ un estimador insesgado de θ con varianza finita, y T una estadística suficiente para θ. Definimos:

$$\hat{\theta}_2 = E[\hat{\theta}_1 \mid T]$$

(Es decir, θ̂₂ es el valor esperado de θ̂₁ dado que ya conoces T.)

Demuestra que:
- a) θ̂₂ es un estimador (estadística)
- b) θ̂₂ es insesgado
- c) Var(θ̂₂) ≤ Var(θ̂₁)

## Concepto previo: ¿Qué es E[X | T]?

Si conoces el valor de T, ya tienes información parcial sobre X. La esperanza condicional E[X | T] es el "mejor pronóstico" de X dado que observaste T.

- Es una **función de T** (no depende de los datos originales por separado)
- Cumple la propiedad: E[E[X | T]] = E[X] (la "ley de la torre" o "ley de esperanzas iteradas")

### Propiedades que usaremos

1. **Ley de esperanzas iteradas:** $E[E[X|T]] = E[X]$
2. **Ley de varianza total:** $\text{Var}(X) = E[\text{Var}(X|T)] + \text{Var}(E[X|T])$

---

## Parte a) θ̂₂ es un estimador

Un **estimador** debe ser una **estadística**: función de la muestra que no involucra cantidades desconocidas.

$\hat{\theta}_2 = E[\hat{\theta}_1 | T]$ es una función de T. Pero ¿podría depender de θ?

Aquí es donde entra la **suficiencia**. La definición de suficiencia dice que la distribución condicional de la muestra dado T **no depende de θ**. Por lo tanto:

- La distribución condicional de θ̂₁ dado T tampoco depende de θ (porque θ̂₁ es función de la muestra)
- Entonces E[θ̂₁ | T] se calcula usando una distribución que no depende de θ
- Por lo tanto θ̂₂ es función solo de T y **no involucra θ**

$$\boxed{\hat{\theta}_2 = E[\hat{\theta}_1 | T] \text{ es una función de T sin cantidades desconocidas} \Rightarrow \text{es una estadística (estimador)} \checkmark}$$

**Nota:** Sin la suficiencia de T, la esperanza condicional podría depender de θ y entonces no sería un estimador válido.

---

## Parte b) θ̂₂ es insesgado

Aplicamos la ley de esperanzas iteradas:

$$E[\hat{\theta}_2] = E[E[\hat{\theta}_1 | T]] = E[\hat{\theta}_1] = \theta$$

La última igualdad es porque θ̂₁ es insesgado por hipótesis.

$$\boxed{E[\hat{\theta}_2] = \theta \quad \checkmark}$$

---

## Parte c) Var(θ̂₂) ≤ Var(θ̂₁)

Aplicamos la **ley de varianza total** a θ̂₁:

$$\text{Var}(\hat{\theta}_1) = E[\text{Var}(\hat{\theta}_1 | T)] + \text{Var}(E[\hat{\theta}_1 | T])$$

El segundo término es exactamente Var(θ̂₂):

$$\text{Var}(\hat{\theta}_1) = \underbrace{E[\text{Var}(\hat{\theta}_1 | T)]}_{\geq 0} + \text{Var}(\hat{\theta}_2)$$

Como las varianzas (condicionales) son siempre ≥ 0, la esperanza de una varianza también es ≥ 0. Entonces:

$$\text{Var}(\hat{\theta}_1) \geq \text{Var}(\hat{\theta}_2)$$

$$\boxed{\text{Var}(\hat{\theta}_2) \leq \text{Var}(\hat{\theta}_1) \quad \checkmark}$$

La igualdad se da solo cuando Var(θ̂₁ | T) = 0 casi seguramente, es decir, cuando θ̂₁ ya es función de T (ya no se puede mejorar).

## Resumen de Rao-Blackwell

```
Empiezas con:  θ̂₁ (insesgado pero quizá no óptimo)
Ingrediente:   T  (estadística suficiente)
Produces:      θ̂₂ = E[θ̂₁ | T]
Resultado:     θ̂₂ es insesgado Y tiene varianza ≤ que θ̂₁
```

**Ejemplo concreto:** Si X₁, ..., Xₙ ∼ Bernoulli(θ) y tu estimador original es θ̂₁ = X₁ (solo la primera observación, que es insesgado pero ignora los demás datos), la estadística suficiente es T = Σ Xᵢ. Entonces:

$$\hat{\theta}_2 = E[X_1 | \Sigma X_i = t] = t/n = \bar{X}$$

¡Rao-Blackwell te lleva de usar solo X₁ a usar la media X̄!

---

# Ejercicio 13 — Doble Exponencial (Laplace)

## Enunciado

X tiene distribución de Laplace (doble exponencial):

$$f(x; \theta) = \frac{1}{2}\exp(-|x - \theta|), \quad x \in \mathbb{R}, \quad \theta \in \mathbb{R}$$

Encuentre una estadística suficiente para θ.

## ¿Qué es la distribución de Laplace?

Es como una Normal pero con "colas más pesadas" y forma de V invertida (en escala logarítmica). Está centrada en θ y es simétrica.

## Paso 1: Escribir la densidad conjunta

$$f(x^{(n)}; \theta) = \prod_{i=1}^n \frac{1}{2}\exp(-|x_i - \theta|) = \frac{1}{2^n}\exp\left(-\sum_{i=1}^n |x_i - \theta|\right)$$

## Paso 2: Intentar factorizar

$$f(x^{(n)}; \theta) = \frac{1}{2^n}\exp\left(-\sum_{i=1}^n |x_i - \theta|\right)$$

La parte que depende de θ es $\sum |x_i - \theta|$. Esta expresión **no** se puede simplificar a una función de una sola estadística sencilla como Σxᵢ o Σxᵢ².

¿Por qué no? Porque el valor absoluto |xᵢ - θ| no se puede separar como "algo de xᵢ" por "algo de θ". La expresión depende de cómo cada xᵢ se compara con θ individualmente.

## Paso 3: ¿Cuál es la estadística suficiente?

La densidad conjunta depende de θ a través de los n valores |x₁ - θ|, |x₂ - θ|, ..., |xₙ - θ|. Pero conocer todos estos valores equivale a conocer los n datos originales (con la información de su posición relativa a θ).

No hay reducción posible. La factorización más fina que podemos lograr es:

$$f(x^{(n)}; \theta) = \underbrace{\frac{1}{2^n}\exp\left(-\sum |x_i - \theta|\right)}_{g(x^{(n)};\; \theta)} \cdot \underbrace{1}_{h(x^{(n)})}$$

Aquí g depende de **toda** la muestra, no de un resumen más simple.

Sin embargo, podemos usar las **estadísticas de orden**. Si ordenamos la muestra: X₍₁₎ ≤ X₍₂₎ ≤ ... ≤ X₍ₙ₎, la densidad conjunta en función de las estadísticas de orden es:

$$f = \frac{n!}{2^n}\exp\left(-\sum_{i=1}^n |x_{(i)} - \theta|\right)$$

Y la suma Σ|x₍ᵢ₎ - θ| depende de θ y de las estadísticas de orden. Entonces:

$$\boxed{T = (X_{(1)}, X_{(2)}, \ldots, X_{(n)}) \text{ — el vector de estadísticas de orden es suficiente para } \theta}$$

## ¿Qué significa esto?

Que para la distribución de Laplace, **no hay un resumen escalar** que capture toda la información. Necesitas toda la muestra ordenada. Esto contrasta con:
- Normal: basta con (X̄, Σ(Xᵢ-X̄)²)  —  2 números
- Bernoulli: basta con Σ Xᵢ  —  1 número
- Laplace: necesitas **n** números (toda la muestra ordenada)

**¿Por qué?** El valor absoluto crea una no-linealidad que impide comprimir la información. La posición de **cada** dato respecto a θ importa individualmente.

---

# Ejercicio 14 — Familia Exponencial

## Enunciado

X tiene densidad de la **familia exponencial**:

$$f(x; \theta) = a(\theta) \cdot b(x) \cdot \exp\left(\sum_{j=1}^{k} c_j(\theta) \cdot d_j(x)\right)$$

Encuentre una estadística suficiente para θ.

## ¿Qué es la familia exponencial?

Es una **familia gigante** de distribuciones que incluye como casos particulares a: Normal, Exponencial, Poisson, Bernoulli, Binomial, Gamma, Beta, y muchas más. La gracia es que se pueden escribir todas con la misma estructura.

Los ingredientes son:
- **a(θ):** solo depende del parámetro
- **b(x):** solo depende de los datos
- **c_j(θ):** funciones del parámetro (j = 1, ..., k)
- **d_j(x):** funciones de los datos (j = 1, ..., k)

## Paso 1: Densidad conjunta de la muestra

$$f(x^{(n)}; \theta) = \prod_{i=1}^n \left[a(\theta) \cdot b(x_i) \cdot \exp\left(\sum_{j=1}^k c_j(\theta) d_j(x_i)\right)\right]$$

$$= [a(\theta)]^n \cdot \prod_{i=1}^n b(x_i) \cdot \exp\left(\sum_{j=1}^k c_j(\theta) \sum_{i=1}^n d_j(x_i)\right)$$

(En el último paso, intercambiamos el orden de las sumas: la suma sobre j sale del exponente del producto.)

## Paso 2: Factorización

$$f(x^{(n)}; \theta) = \underbrace{[a(\theta)]^n \cdot \exp\left(\sum_{j=1}^k c_j(\theta) \cdot T_j\right)}_{g(T_1, \ldots, T_k;\; \theta)} \cdot \underbrace{\prod_{i=1}^n b(x_i)}_{h(x^{(n)})}$$

donde definimos:

$$T_j = \sum_{i=1}^{n} d_j(X_i), \quad j = 1, \ldots, k$$

## Paso 3: Conclusión

Por el Teorema de Factorización, la estadística suficiente es:

$$\boxed{T = \left(\sum_{i=1}^n d_1(X_i), \; \sum_{i=1}^n d_2(X_i), \; \ldots, \; \sum_{i=1}^n d_k(X_i)\right)}$$

Es un **vector de k dimensiones**. Si θ es unidimensional (k=1), la suficiente es un solo número.

## Casos particulares: verificación

| Distribución | f(x;θ) | d(x) | Suficiente |
|---|---|---|---|
| Bernoulli(θ) | $\theta^x(1-\theta)^{1-x}$ | d₁(x) = x | $\sum X_i$ |
| Poisson(λ) | $\frac{\lambda^x e^{-\lambda}}{x!}$ | d₁(x) = x | $\sum X_i$ |
| Exponencial(θ) | $\frac{1}{\theta}e^{-x/\theta}$ | d₁(x) = x | $\sum X_i$ |
| Normal(μ, σ²) ambos desconocidos | ... | d₁(x)=x, d₂(x)=x² | $(\sum X_i, \sum X_i^2)$ |
| Potencia θx^(θ-1) | θx^(θ-1) | d₁(x) = ln x | $\sum \ln X_i$ |

**Este resultado es poderosísimo:** para CUALQUIER distribución de la familia exponencial, puedes encontrar la estadística suficiente sin hacer cuentas largas. Solo identifica las funciones d_j(x) y suma.

## ¿Por qué la Laplace (Ejercicio 13) no entra aquí?

Porque la Laplace tiene |x - θ| en el exponente, y eso **no** se puede separar como c(θ)·d(x). El valor absoluto mezcla x y θ de forma no separable. Por eso la Laplace no pertenece a la familia exponencial y necesita toda la muestra como suficiente.

---

# Resumen Final: Los 14 Ejercicios

| # | Tema | Resultado principal |
|---|---|---|
| 1 | MELI | X̄ (pesos iguales 1/n) |
| 2 | Exponencial insesgado | E[X̄]=θ, Var(X̄)=θ²/n |
| 3 | Combinación | Pesos 1/(C+1) y C/(C+1), siempre conviene combinar |
| 4 | Unif: máximo y mínimo | (n+1)/n · X₍ₙ₎ mucho mejor que (n+1)·X₍₁₎ |
| 5 | Rango y suma | X₍ₙ₎+X₍₁₎ es 2do mejor, el máximo corregido gana |
| 6 | Área con error | π(X̄² - σ²/n) — restar el sesgo |
| 7 | CICR para φ(θ) | [φ'(θ)]²/[n·I(θ)] vía Cauchy-Schwarz |
| 8 | Densidad potencia | Suficiente: Σ ln Xᵢ. MVUE solo para 1/θ |
| 9 | Y = -ln(X) | Exponencial, Ȳ es MVUE para 1/θ |
| 10 | \|X\| suficiente | Sí, para σ y para σ² |
| 11 | No i.i.d. | min{Xₖ/k} es suficiente |
| 12 | Rao-Blackwell | E[θ̂₁\|T] mejora varianza, por ley de varianza total |
| 13 | Laplace | Muestra ordenada completa es suficiente (no hay reducción) |
| 14 | Familia exponencial | (Σd₁(Xᵢ), ..., Σdₖ(Xᵢ)) — resultado universal |
