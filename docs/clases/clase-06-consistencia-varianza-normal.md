# Clase 6: Consistencia en ECM y Estimadores de la Varianza Normal

**Capítulo II.3 – II.4**

---

## Definición 2.9 — Consistencia en ECM

Sea X⁽ⁿ⁾ una m.a. de una v.a. X con f.d.p.g. f(x; θ). Si θ̂ es un estimador de θ, se dice que θ̂ es un **estimador consistente en error cuadrático medio**, si:

$$\text{ECM}(\hat{\theta}) \longrightarrow 0 \quad \text{cuando} \quad n \longrightarrow \infty$$

---

## Ejemplo 2: Estimación de σ² en el Modelo Normal

Sea X⁽ⁿ⁾ una m.a. de X ∼ Normal(μ, σ²), con μ **conocido** y σ² **desconocido**.

### Dos estimadores por analogía

**Estimador 1 (varianza muestral con x̄):**

$$\hat{\sigma}_1^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})^2$$

**Estimador 2 (varianza muestral con μ conocido):**

$$\hat{\sigma}_2^2 = \frac{1}{n} \sum_{i=1}^{n} (X_i - \mu)^2$$

### Distribución muestral de σ̂₂²

Definiendo Zᵢ = (Xᵢ - μ)/σ ∼ N(0,1) y Uᵢ = Zᵢ² ∼ χ²(1):

$$U = \sum_{i=1}^{n} U_i \sim \chi^2_{(n)}, \qquad \hat{\sigma}_2^2 = \frac{\sigma^2}{n} U$$

**Propiedades de σ̂₂²:**
- E[σ̂₂²] = σ² → **Insesgado**
- Var(σ̂₂²) = 2σ⁴/n
- ECM(σ̂₂²) = 2σ⁴/n → **Consistente en ECM**

### Distribución muestral de σ̂₁²

Identidad fundamental:

$$\sum_{i=1}^{n} (X_i - \mu)^2 = \sum_{i=1}^{n} (X_i - \bar{X})^2 + n(\bar{X} - \mu)^2$$

Resultado: nσ̂₁²/σ² ∼ χ²(n-1) → Se **pierde un grado de libertad** al estimar μ con X̄.

**Propiedades de σ̂₁²:**
- E[σ̂₁²] = (n-1)/n · σ² → **Sesgado** (subestima)
- Sesgo = -σ²/n → **Asintóticamente insesgado**
- Var(σ̂₁²) = 2σ⁴(n-1)/n²
- ECM(σ̂₁²) = σ⁴(2n-1)/n²  → **Consistente en ECM**

### Definición — Asintóticamente Insesgado

Si θ̂ es un estimador sesgado de θ, se dice que θ̂ es **asintóticamente insesgado** si:

$$\text{Sesgo}(\hat{\theta}) \longrightarrow 0 \quad \text{cuando} \quad n \longrightarrow \infty$$

---

## Comparación Clave: σ̂₁² vs σ̂₂²

| Propiedad | σ̂₁² (con X̄) | σ̂₂² (con μ) |
|---|---|---|
| Insesgado | No | Sí |
| Distribución | σ²/n · χ²(n-1) | σ²/n · χ²(n) |
| ECM | σ⁴(2n-1)/n² | 2σ⁴/n |

**Resultado sorprendente:** ECM(σ̂₁²) < ECM(σ̂₂²) para todo n ≥ 1.

El estimador **sesgado** σ̂₁² tiene menor ECM que el **insesgado** σ̂₂².

### Independencia de X̄ y σ̂₁²

Se demostró que Cov(Xᵢ - X̄, X̄) = 0, por lo que en el modelo Normal:
- El estimador de la media μ̂ = X̄ es **independiente** del estimador de la varianza σ̂₁²
