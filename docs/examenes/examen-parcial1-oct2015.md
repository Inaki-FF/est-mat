# Examen Parcial 1 — Estadística Matemática (Octubre 2015)

**Calificaciones obtenidas:** 64 (Elisa Casares) y 86 (Marian Tlatelpa)
**Puntajes ejemplo (86):** I: 1.000 | II: 0.900 | III: 0.933 | IV: 0.600

---

## Problema 1

Conteste *brevemente* cada una de las siguientes preguntas (no más de cinco líneas cada una).

a) ¿Qué es la Estadística?

b) ¿Qué es la Inferencia Estadística Paramétrica?

c) ¿Qué es una Muestra Aleatoria?

## Problema 2

La empresa *Fitness Max*, que distribuye aplicaciones para monitorear la actividad física a través de los teléfonos celulares, se ha enterado de problemas para instalar su aplicación *Jogging Universe*. Para cuantificar el tamaño del problema, selecciona una muestra aleatoria X₍ₙ₎ de usuarios de la aplicación y les pregunta: ¿La última vez que descargó una actualización de *Jogging Universe*, cuántas veces lo intentó sin éxito, antes de lograrlo?

La empresa supone que los datos X₍ₙ₎ constituyen una muestra aleatoria de una variable X, con distribución geométrica:

$$P(X = x; \theta) = \theta(1 - \theta)^x, \quad x = 0, 1, 2, \ldots$$

a) ¿Cuál es la interpretación del parámetro θ en este contexto?

b) Encuentre una estadística suficiente para θ.

c) Estime θ por momentos.

## Problema 3

Para la misma situación del problema 2:

a) Estime θ por máxima verosimilitud.

b) ¿Alguno de los estimadores de θ (momentos o MV) es insesgado y su varianza alcanza la CICR(θ)?

c) Encuentre una transformación φ = φ(θ) para la que exista un estimador insesgado cuya varianza alcance la CICR(φ). ¿Cuál es la interpretación de φ en el contexto del problema?

## Problema 4

Sea X₍ₙ₎ una muestra aleatoria de una variable aleatoria X con distribución **Poisson** con parámetro λ. Considere las estadísticas:

$$T_1(X_{(n)}) = \sum_{i=1}^{n} X_i$$

$$T_2(X_{(n)}) = \begin{cases} 1 & \text{si } X_1 = 0 \\ 0 & \text{en otro caso} \end{cases}$$

Suponga que interesa estimar el parámetro φ = P(X = 0; λ). Observe que φ = φ(λ) es una función uno a uno de λ.

i) Pruebe que T₁(X₍ₙ₎) es suficiente para λ.

ii) Verifique que T₂(X₍ₙ₎) es un estimador *insesgado* de φ.

iii) Construya T₃(X₍ₙ₎) = E(T₂(X₍ₙ₎) | T₁(X₍ₙ₎) = t) y pruebe que es un estimador *insesgado* de φ.

iv) Calcule la varianza de T₃(X₍ₙ₎).

v) Compare las varianzas de T₂(X₍ₙ₎) y T₃(X₍ₙ₎) y comente.
