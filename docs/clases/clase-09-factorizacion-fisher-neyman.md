# Clase 9: Teorema de Factorización de Fisher-Neyman

**Capítulo II.5 (continuación)**

---

## Motivación

Verificar suficiencia calculando la distribución condicional es laborioso. El **Teorema de Factorización** proporciona un método mucho más sencillo.

---

## Teorema de Factorización de Fisher-Neyman

Sea X⁽ⁿ⁾ una m.a. de X con f.d.p.g. f(x; θ). Una estadística T(X⁽ⁿ⁾) es **suficiente para θ** si y solo si la densidad conjunta de la muestra se puede escribir como:

$$f_{X^{(n)}}(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

donde:
- **g** depende de la muestra **solo a través de T** y puede depender de θ
- **h** depende de la muestra pero **no depende de θ**

---

## Aplicaciones a los Ejemplos Previos

### Bernoulli(θ)

$$f_{X^{(n)}}(x^{(n)}; \theta) = \theta^{\sum x_i}(1-\theta)^{n-\sum x_i}$$

- g(t; θ) = θᵗ(1-θ)ⁿ⁻ᵗ donde t = Σxᵢ
- h(x⁽ⁿ⁾) = 1

→ T = Σ Xᵢ es suficiente para θ ✓

### Normal(μ, σ²) con σ² conocida

$$f_{X^{(n)}} = (2\pi\sigma^2)^{-n/2} \exp\left(-\frac{1}{2\sigma^2}\sum(x_i - \mu)^2\right)$$

Usando la identidad Σ(xᵢ - μ)² = Σ(xᵢ - x̄)² + n(x̄ - μ)²:

- g(x̄; μ) = exp(-n(x̄ - μ)²/(2σ²))
- h(x⁽ⁿ⁾) = (2πσ²)⁻ⁿ/² exp(-Σ(xᵢ - x̄)²/(2σ²))

→ T = X̄ es suficiente para μ ✓

### Normal(μ, σ²) con μ conocida

- g(σ̂²; σ²) = (σ²)⁻ⁿ/² exp(-nσ̂²/(2σ²))
- h(x⁽ⁿ⁾) = (2π)⁻ⁿ/²

→ T = Σ(Xᵢ - μ)² es suficiente para σ² ✓

### Uniforme(0, θ)

$$f_{X^{(n)}} = \frac{1}{\theta^n} \cdot \prod_{i=1}^{n} \mathbf{1}_{(0,\theta)}(x_i) = \frac{1}{\theta^n} \cdot \mathbf{1}_{(0,\theta)}(x_{(n)})$$

- g(x₍ₙ₎; θ) = (1/θⁿ) · 𝟙(x₍ₙ₎ < θ)
- h(x⁽ⁿ⁾) = 𝟙(x₍₁₎ > 0)

→ T = X₍ₙ₎ es suficiente para θ ✓

---

## Suficiencia Conjunta en Normal(μ, σ²)

Cuando **ambos** parámetros μ y σ² son desconocidos, la estadística suficiente es **bidimensional**:

$$T(X^{(n)}) = \left(\sum_{i=1}^{n} X_i, \; \sum_{i=1}^{n} X_i^2\right)$$

o equivalentemente (X̄, S²).

---

## Resumen

El Teorema de Factorización es la herramienta principal para verificar suficiencia:
- Es más simple que calcular distribuciones condicionales
- Se aplica tanto a casos discretos como continuos
- Proporciona la estadística suficiente directamente por inspección de la densidad conjunta
