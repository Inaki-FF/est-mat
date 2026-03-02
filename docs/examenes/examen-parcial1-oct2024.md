# Examen Parcial 1 — Estadística Matemática (Octubre 2024)

**Calificación:** 99/100
**Puntajes:** 1: 1.000 | 2: 0.967 | 3: 0.975 | 4: 1.000

---

## Problema 1

Conteste *brevemente* cada una de las siguientes preguntas (no más de cinco líneas cada una).

a) ¿Qué es la Estadística?

b) ¿Qué es la Inferencia Estadística Paramétrica?

c) ¿Qué relación guarda el muestreo probabilístico con las muestras llamadas *representativas*?

## Problema 2

Un Médico presenta los siguientes datos del número de personas que recibió, durante las diez semanas más recientes, con síntomas de influenza:

x₁ = 4, x₂ = 6, x₃ = 0, x₄ = 4, x₅ = 4, x₆ = 3, x₇ = 1, x₈ = 2, x₉ = 2, x₁₀ = 5 (Σ = 31)

El Médico considera que podría modelarse con una distribución **Poisson**:

$$P(X = x; \lambda) = \frac{\lambda^x}{x!} e^{-\lambda}, \quad \lambda > 0, \quad x \in \{0, 1, 2, 3, \ldots\}$$

a) ¿Cuál sería el modelo Poisson específico que usted le recomendaría? ¿Por qué?

b) ¿Qué estimación daría de la probabilidad de que en la siguiente semana no se le presenten casos?

c) Dada la relación de la esperanza con la varianza en el modelo Poisson, ¿es razonable este modelo?

## Problema 3

Sea X₍ₙ₎ una m.a. de X con distribución **Bernoulli** y probabilidad de éxito θ. Interesa estimar insesgadamente φ = θ².

a) Demuestre que φ̂₁ = X̄² es un estimador por analogía para φ, pero es sesgado.

Considere:

$$\hat{\varphi}_2 = \begin{cases} 1 & \text{si } X_1 = 1 \text{ y } X_2 = 1 \\ 0 & \text{en otro caso} \end{cases}$$

b) Pruebe que φ̂₂ es insesgado.

c) Pruebe que T(X₍ₙ₎) = Σᵢ Xᵢ es estadística suficiente para φ.

d) Calcule φ̂₃ = E{φ̂₂ | T(X₍ₙ₎) = t} y compárelo con φ̂₁ y φ̂₂.

## Problema 4

Sea X₍ₙ₎ una m.a. de X que solo puede tomar los valores -1, 0 y 1. La función de probabilidad:

$$P(X = x; \theta) = \left(\frac{\theta}{2}\right)^{|x|} (1 - \theta)^{1 - |x|}, \quad x = -1, 0, 1, \quad \theta \in (0, 1)$$

a) Encuentre una estadística suficiente, de dimensión 1, para θ.

b) ¿En qué sentido T(X₍ₙ₎) = (1/n) Σᵢ Xᵢ² es estimador por analogía para θ?

c) ¿Es insesgado?

d) ¿Cuál es su varianza?

e) ¿Es MVUE?

f) ¿Es consistente en ECM?
