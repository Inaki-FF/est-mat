# Examen Parcial 1 — Estadística Matemática (Octubre 2016)

**Calificación:** 82/100
**Puntajes:** I: 1.000 | III: 0.607 | IV: 0.700 | V: 0.900

---

## Problema 1

Conteste *brevemente* cada una de las siguientes preguntas (no más de cuatro líneas cada una).

a) ¿Qué es la Estadística?

b) ¿Qué es la Inferencia Estadística Paramétrica?

c) ¿Qué es una muestra aleatoria?

## Problema 2

Un Ingeniero presenta datos del tiempo (en segundos) que le tomó a cada una de diez tabletas electrónicas, seleccionadas al azar, terminar la fase de inicialización:

x₁ = 3.9, x₂ = 0.2, x₃ = 17.7, x₄ = 33.2, x₅ = 3.5,
x₆ = 10.6, x₇ = 6.0, x₈ = 26.1, x₉ = 1.5, x₁₀ = 8.1

El Ingeniero considera que estos tiempos podrían modelarse con una distribución **Exponencial**.

a) ¿Cuál es el modelo Exponencial específico que usted recomendaría? ¿Por qué?

b) ¿Qué estimación le daría de la probabilidad de que una tableta tarde más de 30 segundos en alcanzar la capacidad operativa plena?

c) Utilizando la relación entre la esperanza y la varianza del modelo Exponencial, sugiera un procedimiento para argumentar a favor (o en contra) de que la distribución Exponencial es adecuada.

## Problema 3

Para la misma situación del problema 2:

a) Estime θ por máxima verosimilitud.

b) ¿Alguno de los estimadores de θ (momentos o MV) es insesgado y su varianza alcanza la CICR(θ)?

c) Encuentre una transformación φ = φ(θ) para la que exista un estimador insesgado cuya varianza alcance la CICR(φ). ¿Cuál es la interpretación de φ en el contexto del problema?

## Problema 4

Sea X₍ₙ₎ una muestra aleatoria de X ∼ Poisson(λ). Considere:

$$T_1(X_{(n)}) = \sum_{i=1}^{n} X_i \qquad T_2(X_{(n)}) = \begin{cases} 1 & \text{si } X_1 = 0 \\ 0 & \text{en otro caso} \end{cases}$$

Interesa estimar φ = P(X = 0; λ):

i) Pruebe que T₁ es suficiente para λ.

ii) Verifique que T₂ es un estimador *insesgado* de φ.

iii) Construya T₃ = E(T₂ | T₁ = t) y pruebe que es insesgado para φ.

iv) Calcule la varianza de T₃.

v) Compare las varianzas de T₂ y T₃ y comente.
