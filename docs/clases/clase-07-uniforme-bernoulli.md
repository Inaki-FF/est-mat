# Clase 7: Estimación en Uniforme(0,θ) y Bernoulli(θ)

**Capítulo II.4 (continuación)**

---

## Ejemplo 3: Distribución Uniforme(0, θ)

Sea X⁽ⁿ⁾ una m.a. de X ∼ Unif(0, θ), con θ > 0 desconocido.

$$f(x; \theta) = \begin{cases} 1/\theta & 0 < x < \theta \\ 0 & \text{otro caso} \end{cases}$$

### Estimador 1: θ̂₁ = 2X̄ (por analogía, usando E[X] = θ/2)

| Propiedad | Resultado |
|---|---|
| Insesgado | Sí: E[θ̂₁] = θ |
| Varianza | θ²/(3n) |
| ECM | θ²/(3n) |
| Consistente | Sí |

### Estimador 2: θ̂₂ = X₍ₙ₎ (máximo de la muestra)

Densidad del máximo muestral:

$$f_T(t) = \frac{n \cdot t^{n-1}}{\theta^n}, \quad 0 < t < \theta$$

| Propiedad | Resultado |
|---|---|
| E[θ̂₂] | nθ/(n+1) |
| Sesgo | -θ/(n+1) → Asintóticamente insesgado |
| Varianza | nθ²/[(n+1)²(n+2)] |
| ECM | 2θ²/[(n+1)(n+2)] |
| Consistente | Sí (orden n⁻²) |

### Comparación

- ECM(θ̂₁) = θ²/(3n) → converge a orden **n⁻¹**
- ECM(θ̂₂) = 2θ²/[(n+1)(n+2)] → converge a orden **n⁻²**

**Resultado:** ECM(θ̂₂) < ECM(θ̂₁) para todo n > 1. El máximo muestral es **mejor** pese a ser sesgado.

### Estimador 3: θ̂₃ = (n+1)/n · X₍ₙ₎ (corrección de sesgo)

$$E[\hat{\theta}_3] = \theta, \qquad \text{Var}(\hat{\theta}_3) = \frac{\theta^2}{n(n+2)}$$

---

## Ejemplo 4: Distribución Bernoulli(θ)

Sea X⁽ⁿ⁾ una m.a. de X ∼ Bernoulli(θ), θ ∈ (0,1) desconocido.

### Estimador: θ̂ = X̄ = Y/n, donde Y = Σ Xᵢ ∼ Binomial(n, θ)

| Propiedad | Resultado |
|---|---|
| Insesgado | Sí: E[θ̂] = θ |
| Varianza = ECM | θ(1-θ)/n |
| Consistente | Sí |

### Problema especial del caso discreto

El soporte de θ̂ es {0, 1/n, 2/n, ..., 1}. El error de estimación ε = θ̂ - θ es también discreto y su distribución **depende de θ** independientemente de la transformación usada. No es posible calcular P(|ε| > c) sin conocer θ.

→ Se resuelve con **aproximaciones asintóticas** (ver clases posteriores).
