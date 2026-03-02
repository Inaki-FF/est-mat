# Clase 4: Estimación Puntual — Valor Estimado y Función Estimadora

**Capítulo II.1 – II.2**

---

## Estimación Puntual

**Objetivo:** Producir, a partir de una muestra aleatoria, un valor aproximado del parámetro θ.

### Elementos Fundamentales

- **Función estimadora T:** Función que mapea del espacio muestral al espacio paramétrico: T: X⁽ⁿ⁾ → ℝ
- **Valor estimado:** T(x⁽ⁿ⁾) = θ̂ (estimación del parámetro)
- **Principio de analogía:** Identificar el análogo muestral de una cantidad poblacional como estimador. Ejemplo: la media muestral como análogo de la media poblacional.

### f.d.p.g. (función de densidad de probabilidad generalizada)
Término que se refiere a la función de probabilidad en el caso discreto y a la función de densidad en el caso continuo.

---

## Planteamiento General

Sea X⁽ⁿ⁾ una m.a. de una v.a. X con f.d.p.g. f(x; θ), de forma conocida. Utilice esta información para estimar el valor del parámetro θ.

### Para el modelo Normal(μ, σ²) con σ² conocida:

**Función estimadora por analogía (media muestral):**

$$T(x^{(n)}) = \frac{1}{n} \sum_{i=1}^{n} x_i = \bar{x}$$

Es decir: μ̂ = x̄

---

## El Error de Estimación

- **Error de estimación:** e = θ̂(x⁽ⁿ⁾) - θ (número desconocido, no calculable).
- **Error de estimación como v.a.:** ε = θ̂(X⁽ⁿ⁾) - θ (variable aleatoria cuya distribución SÍ se puede describir).

### Distribución de la Función Estimadora

Para el modelo Normal:

$$\hat{\mu}(X^{(n)}) = \bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$$

**Error de estimación:**

$$\varepsilon = \hat{\mu}(X^{(n)}) - \mu \sim N\left(0, \frac{\sigma^2}{n}\right)$$

---

## Ejemplo: Estaturas

- X = estatura en metros de estudiantes universitarios
- Modelo: Normal(μ, σ²) con σ = 0.1
- Muestra de n = 10: 1.90, 1.65, 1.82, 1.68, 1.63, 1.89, 1.66, 1.69, 1.57, 1.76
- Valor estimado: x̄ = 1.73, es decir, μ̂ = 1.73
