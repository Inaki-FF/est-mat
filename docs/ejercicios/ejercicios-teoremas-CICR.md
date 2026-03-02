# Ejercicios — Teorema de Cramér-Rao y Estimación

---

## Ejercicio: Teorema de Cramér y Rao para φ(θ)

En clase se probó el **Teorema de Cramér y Rao** que establece:

Si X₍ₙ₎ es una muestra aleatoria de una v.a. X con función de densidad generalizada f(x; θ), donde θ es un parámetro real, y se cumplen las condiciones que permiten intercambiar los operadores de esperanza y diferenciación, entonces para todo estimador insesgado θ̂ de θ:

$$\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot E\left[\left(\frac{\partial}{\partial \theta} \ln f(X; \theta)\right)^2\right]}$$

A la expresión del lado derecho se le conoce como la **Cota Inferior de Cramér-Rao** para θ [CICR(θ)].

**Tarea:** Demuestre la versión de este resultado para el caso en que el parámetro que se desea estimar no es θ sino φ = φ(θ).

---

## Ejercicio: Distribución Uniforme y EMV

Sea X₍ₙ₎ una m.a. de X con distribución **Uniforme** en (θ ± 1/2), con θ un número real arbitrario.

a) ¿Existe un estimador de máxima verosimilitud para θ?

b) ¿Ese estimador es único?

c) Si no lo es, proponga uno que además de ser de MV, sea insesgado.

---

## Ejercicio: Expresión alternativa de la CICR

**Demuestre** que la CICR(θ) puede calcularse con la expresión alternativa:

$$\text{CICR}(\theta) = \frac{1}{-n \cdot E\left\{\frac{\partial^2}{\partial \theta^2} \ln f(X; \theta)\right\}}$$

donde el cuadrado de la primera derivada se reemplaza por el **negativo de la segunda derivada** y la verosimilitud de la muestra completa se sustituye por n veces la verosimilitud de una sola observación.

---

## Ejercicio: Distribución Rayleigh

Sea X₍ₙ₎ una muestra aleatoria de X continua con densidad:

$$f(x; \theta) = \frac{x}{\theta} \exp\left\{-\frac{x^2}{2\theta}\right\}, \quad x > 0, \quad \theta > 0$$

a) ¿Coinciden los estimadores de momentos y máxima verosimilitud de θ?

b) ¿El estimador de máxima verosimilitud es insesgado?

c) ¿Es suficiente?

d) ¿Alcanza la CICR(θ)?
