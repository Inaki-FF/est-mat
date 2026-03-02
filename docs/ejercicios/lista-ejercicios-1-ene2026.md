# Lista de Ejercicios No. 1 — Estadística Matemática (Febrero 2026)

---

## Ejercicio 1 — MELI (Mejor Estimador Lineal Insesgado)

Sea X⁽ⁿ⁾ una m.a. de X con media μ y varianza σ². Si solo se consideran estimadores lineales de la forma:

$$T(X_1, \ldots, X_n) = a_1X_1 + a_2X_2 + \cdots + a_nX_n$$

donde los coeficientes a₁, ..., aₙ son constantes conocidas, **encuentre el estimador insesgado de varianza mínima (MELI)**.

---

## Ejercicio 2 — Exponencial: X̄ insesgado

Demuestre que X̄ de una m.a. de tamaño n de X con densidad:

$$f(x; \theta) = \frac{1}{\theta} \exp\left(-\frac{x}{\theta}\right), \quad x > 0, \quad \theta > 0$$

es un estimador **insesgado** de θ y tiene varianza θ²/n.

---

## Ejercicio 3 — Combinación de estimadores independientes

Si se tienen dos estimadores independientes e insesgados θ̂₁ y θ̂₂, con Var(θ̂₁) = C · Var(θ̂₂):

a) ¿Cuál de los dos preferiría? ¿Por qué?

b) Para θ̂₃ = k₁θ̂₁ + k₂θ̂₂, ¿cómo elegir k₁, k₂ para que sea insesgado?

c) ¿Cómo elegir k₁, k₂ para que además tenga varianza mínima?

d) ¿Vale la pena la combinación?

---

## Ejercicio 4 — Uniforme(0, θ): estimadores a partir de X₍ₙ₎ y X₍₁₎

Sea X⁽ⁿ⁾ m.a. de X ∼ Unif(0, θ).

a) Construya un estimador **insesgado** para θ a partir del máximo X₍ₙ₎.

b) Construya un estimador **insesgado** para θ a partir del mínimo X₍₁₎.

c) ¿Cuál preferiría? ¿Por qué?

---

## Ejercicio 5 — Comparación con rango y suma de extremos

Considere los estimadores X₍ₙ₎ - X₍₁₎ (rango) y X₍ₙ₎ + X₍₁₎ (suma). ¿Cómo se comparan con los anteriores?

---

## Ejercicio 6 — Área del círculo con error Normal

Si el radio se mide con error N(0, σ²), con n mediciones independientes, proponga un estimador **insesgado del área** del círculo. ¿Qué puede decir de su varianza?

---

## Ejercicio 7 — Demostración: CICR para φ(θ)

Demuestre la versión de la **Cota Inferior de Cramér-Rao** para el caso en que se estima φ = φ(θ) en lugar de θ directamente.

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$$

---

## Ejercicio 8 — Densidad f(x;θ) = θx^(θ-1) en (0,1)

a) ¿Será cierto que Σ Xᵢ es una estadística suficiente para θ?

b) Encuentre la CICR(θ).

c) ¿Existe un estimador insesgado de θ que alcance la CICR(θ)?

d) ¿Existe φ = φ(θ) para la que se pueda encontrar un estimador que alcance la CICR correspondiente?

---

## Ejercicio 9 — Transformación Y = -ln(X)

Si X tiene densidad f(x;θ) = θx^(θ-1) y Y = -ln(X):

a) Encuentre la distribución de Y.

b) Encuentre una estadística suficiente para θ.

c) Si reparametriza en términos de E(Y) = h(θ), encuentre un estimador insesgado.

d) Encuentre la CICR para E(Y).

e) ¿Cómo se relacionan con los resultados del ejercicio 8?

---

## Ejercicio 10 — |X| como estadística suficiente

Si X es una observación de N(0, σ²), ¿es |X| suficiente para σ? ¿Para σ²?

---

## Ejercicio 11 — Variables no idénticamente distribuidas

X₁, ..., Xₙ independientes con densidad fₖ(x; θ) = exp(kθ - x) para x > kθ. Encuentre una estadística suficiente para θ.

**Nota:** Las observaciones **no** forman una muestra aleatoria según la definición estándar.

---

## Ejercicio 12 — Rao-Blackwellización

Sea θ̂₁ un estimador insesgado con varianza finita, y T una estadística suficiente. Si θ̂₂ = E[θ̂₁ | T]:

a) θ̂₂ es un estimador de θ.

b) θ̂₂ es insesgado.

c) Var(θ̂₂) ≤ Var(θ̂₁).

Este mecanismo se conoce como **Rao-Blackwellización**.

---

## Ejercicio 13 — Doble exponencial (Laplace)

Sea X con densidad f(x; θ) = (1/2)exp(-|x - θ|). Encuentre una estadística suficiente para θ.

---

## Ejercicio 14 — Familia Exponencial

Si X tiene f.d.p.g. de la familia exponencial:

$$f(x; \theta) = a(\theta) \cdot b(x) \cdot \exp\left(\sum_{j=1}^{k} c_j(\theta) d_j(x)\right)$$

Encuentre una estadística suficiente para θ.
