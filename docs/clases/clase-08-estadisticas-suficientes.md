# Clase 8: Estadísticas Suficientes

**Capítulo II.5 – II.6**

---

## Motivación

Además del insesgamiento, ECM y consistencia, existe otro criterio fundamental: ¿El estimador captura **toda la información** que la muestra contiene sobre el parámetro?

### Idea Central

Si T(X⁽ⁿ⁾) es una estadística y su distribución muestral depende de θ, entonces T guarda relación con θ. La pregunta es: ¿captura **toda** la información?

Para responder, se analiza la **distribución condicional** de la muestra dado T:

$$f_{X^{(n)} | T=t}(x^{(n)})$$

- Si **depende de θ**: la muestra aún tiene información sobre θ que T no capturó.
- Si **no depende de θ**: T extrajo **toda** la información → T es **suficiente**.

---

## Definición — Estadística Suficiente (Fisher)

Sea X⁽ⁿ⁾ una m.a. de X con f.d.p.g. f(x; θ). Sea T(X⁽ⁿ⁾) una estadística. Se dice que **T es suficiente para θ** si:

$$f_{X^{(n)} | T=t}(x^{(n)}) \quad \text{no depende de } \theta$$

---

## Teorema de Equivalencia

Si T₂(X⁽ⁿ⁾) = h(T₁(X⁽ⁿ⁾)) para alguna función h, y T₂ es suficiente para θ, entonces **T₁ también es suficiente para θ**.

Consecuencia: X̄ es suficiente ⟺ Σ Xᵢ es suficiente (son funciones uno a uno).

---

## Ejemplo 4: Bernoulli(θ)

Verificar si T = Σ Xᵢ es suficiente para θ:

$$P(X^{(n)} = x^{(n)} | \sum X_i = t) = \frac{\theta^{\sum x_i}(1-\theta)^{n-\sum x_i}}{\binom{n}{t}\theta^t(1-\theta)^{n-t}} = \frac{1}{\binom{n}{t}}$$

**No depende de θ** → Σ Xᵢ (y por tanto X̄) es **suficiente** para θ.

**Propiedades completas de θ̂ = X̄ en Bernoulli:**
1. Insesgado
2. Var = θ(1-θ)/n
3. Consistente en ECM
4. **Suficiente** para θ

---

## Ejemplo 5: Normal(μ, σ²) — estimación de μ (σ² conocida)

Calcular f(X⁽ⁿ⁾ | X̄ = t):

$$\frac{f_{X^{(n)}}(x^{(n)})}{f_{\bar{X}}(t)} = (2\pi\sigma^2)^{-(n-1)/2} n^{-1/2} \exp\left(-\frac{1}{2\sigma^2}\sum(x_i - \bar{x})^2\right)$$

**No depende de μ** → X̄ es **suficiente** para μ.

**Propiedades completas de μ̂ = X̄:**
1. Insesgado
2. Var = ECM = σ²/n
3. Consistente en ECM
4. **Suficiente** para μ

---

## Ejemplo 6: Normal(μ, σ²) — estimación de σ² (μ conocida)

Se verifica que σ̂² = (1/n)Σ(Xᵢ - μ)² es suficiente para σ².

---

## Ejemplo 7: Uniforme(0, θ) — suficiencia

Se verifica que el **máximo muestral** X₍ₙ₎ es suficiente para θ, mientras que X̄ **no** es suficiente.

**Conclusión importante:** En Uniforme(0,θ), el máximo muestral es mejor que X̄ tanto en ECM como en suficiencia.
