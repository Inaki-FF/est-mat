# Examen Parcial 1 — Estadística Matemática (Enero 2025)

**Calificación:** 62/100
**Puntajes:** I: 0.933 | II: 0.833 | III: 0.733 | IV: 0.000

---

## Problema 1

Conteste *brevemente* cada una de las siguientes preguntas (no más de cinco líneas cada una).

a) ¿Qué es la Estadística?

b) ¿Qué es la Inferencia Estadística Paramétrica?

c) ¿Qué relación guarda el muestreo probabilístico con las muestras llamadas *representativas*?

## Problema 2

Sea X₍ₙ₎ una muestra aleatoria de una variable aleatoria X con función de densidad:

$$f(x; \theta) = \begin{cases} 1 & \text{si } \theta - \frac{1}{2} \leq x \leq \theta + \frac{1}{2} \\ 0 & \text{en otro caso} \end{cases}$$

a) ¿En qué sentido se puede afirmar que θ̂ = X̄ es un estimador por analogía para θ?

b) Verifique si θ̂ es un estimador consistente en Error Cuadrático Medio.

c) Establezca si θ̂ es suficiente para θ.

## Problema 3

Sea X₍ₙ₎ una muestra aleatoria de una variable aleatoria X con distribución **Bernoulli** y probabilidad de éxito θ. Suponga que es de interés estimar (insesgadamente) el parámetro φ = θ².

a) Compruebe que el estimador por analogía más inmediato, φ̂₁ = X̄², es sesgado.

Considere el siguiente estimador de φ:

$$\hat{\varphi}_2 = \begin{cases} 1 & \text{si } X_1 = 1 \text{ y } X_2 = 1 \\ 0 & \text{en otro caso} \end{cases}$$

donde X₁ y X₂ son las dos primeras observaciones en la muestra.

b) Pruebe que φ̂₂ es insesgado pero no es consistente en ECM.

c) Obtenga la expresión explícita de E{φ̂₂ | T(X₍ₙ₎) = t} y comente sus propiedades si esta esperanza se utiliza como otro estimador φ̂₃ de φ (es el de **Rao-Blackwell**).

## Problema 4

Sea X₁, X₂, ..., Xₙ una colección de variables aleatorias independientes tales que E(Xᵢ) = μ y Var(Xᵢ) = σᵢ² para i = 1, ..., n.

a) Encuentre el **MELI** (Mejor Estimador Lineal Insesgado) para μ, si todas las varianzas son conocidas.

b) Verifique si, cuando se tiene normalidad, este MELI es además **MVUE**.
