# Estadística Matemática — Conceptos Base y Panorama del Curso

*Documento introductorio para empezar a estudiar desde cero*

---

## Parte 1: ¿De qué va este curso?

### La gran pregunta

Imagina que quieres saber la estatura promedio de todos los estudiantes universitarios de México. Son millones. No puedes medirlos a todos. Entonces mides a 100 y con eso intentas **adivinar** el promedio real.

Eso es la Estadística Matemática: **la ciencia de adivinar cosas sobre el todo, observando solo una parte**, y además poder decir **qué tan buena es tu adivinanza**.

### Dos mundos

| | Análisis Exploratorio | Inferencia Estadística |
|---|---|---|
| ¿Qué tienes? | TODOS los datos | Solo una MUESTRA |
| ¿Tu descripción es...? | Exacta | Aproximada |
| Ejemplo | Un censo de población | Una encuesta electoral |

El curso se centra en **Inferencia Estadística**: cómo pasar de una muestra a conclusiones sobre la población completa.

---

## Parte 2: El lenguaje que necesitas

### La cadena fundamental

```
Fenómeno → Atributo → Variable → Datos
```

- **Atributo**: lo que te interesa observar (ej: "estado de salud")
- **Variable**: cómo lo codificas numéricamente (ej: "presión arterial en mmHg")
- **Dato**: el número concreto que mides (ej: 120)

### Notación que verás todo el semestre

| Símbolo | Significado |
|---|---|
| X | Variable aleatoria (lo que mides, antes de medir) |
| x | Dato concreto (lo que obtuviste al medir) |
| X₁, X₂, ..., Xₙ | **Muestra aleatoria** (n copias independientes de X) |
| x₁, x₂, ..., xₙ | Los datos observados |
| θ (theta) | El **parámetro** desconocido (lo que quieres encontrar) |
| θ̂ (theta-hat) | Tu **estimador** del parámetro (tu adivinanza) |
| f(x; θ) | Función de densidad/probabilidad (el modelo) |
| n | Tamaño de muestra |

### ¿Qué es una muestra aleatoria?

Es una colección X₁, X₂, ..., Xₙ de variables aleatorias que son:
- **Independientes**: medir una no afecta a las otras
- **Idénticamente distribuidas (i.i.d.)**: todas siguen la misma distribución

Esto ocurre cuando seleccionas tu muestra **al azar** de una población grande.

---

## Parte 3: El problema central — Estimación Puntual

### Setup

1. Tienes una muestra aleatoria X₁, ..., Xₙ de una distribución conocida (ej: Normal) pero con parámetro θ desconocido
2. Quieres **estimar θ** usando los datos

### Tu herramienta: la función estimadora

Un **estimador** es una fórmula que toma los datos y produce un número:

$$\hat{\theta} = T(X_1, X_2, \ldots, X_n)$$

El ejemplo más básico: para estimar la media poblacional μ, usas la **media muestral**:

$$\hat{\mu} = \bar{X} = \frac{1}{n}\sum_{i=1}^{n} X_i$$

### ¿Cómo sabes si tu estimador es bueno?

Aquí está el corazón del curso. Hay **5 criterios** que vas a aprender, uno por uno:

---

## Parte 4: Los 5 criterios de calidad (el corazón del curso)

### Criterio 1: Insesgamiento (Clase 5)

*"¿Tu estimador está centrado en el blanco?"*

Un estimador es **insesgado** si en promedio da el valor correcto:

$$E[\hat{\theta}] = \theta$$

Analogía: si tiras flechas al blanco, el insesgamiento dice que **en promedio** le das al centro. Pero no dice nada de qué tan dispersas están.

### Criterio 2: Error Cuadrático Medio — ECM (Clase 5)

*"¿Qué tan lejos caen tus flechas del centro?"*

$$\text{ECM}(\hat{\theta}) = E[(\hat{\theta} - \theta)^2] = \text{Varianza} + \text{Sesgo}^2$$

**La fórmula más importante del curso.** Un estimador sesgado pero con poca varianza puede ser mejor que uno insesgado pero muy disperso.

### Criterio 3: Consistencia en ECM (Clase 6)

*"¿Mejora tu estimador al tener más datos?"*

$$\text{ECM}(\hat{\theta}) \to 0 \quad \text{cuando} \quad n \to \infty$$

Si obtienes más datos, tu estimador debería acercarse más al valor real.

### Criterio 4: Suficiencia (Clases 8-9)

*"¿Tu estimador captura TODA la información de la muestra sobre θ?"*

Una estadística T es **suficiente** para θ si, una vez que conoces T, la muestra ya no te dice nada nuevo sobre θ. Se verifica con el **Teorema de Factorización**:

$$f(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

### Criterio 5: MVUE — Optimalidad (Clase 10)

*"¿Es tu estimador el MEJOR posible entre todos los insesgados?"*

La **Cota Inferior de Cramér-Rao** te dice cuál es la varianza mínima que cualquier estimador insesgado puede tener:

$$\text{Var}(\hat{\theta}) \geq \text{CICR}(\theta) = \frac{1}{n \cdot I(\theta)}$$

Si tu estimador alcanza esta cota, es el **MVUE** (Minimum Variance Unbiased Estimator) — el mejor posible.

---

## Parte 5: Las distribuciones que usarás constantemente

### 1. Bernoulli(θ) — la más simple

X solo vale 0 o 1. θ = P(X=1). Piensa en lanzar una moneda.

$$P(X = x) = \theta^x (1-\theta)^{1-x}, \quad x \in \{0, 1\}$$

- E[X] = θ
- Var(X) = θ(1-θ)
- Estimador natural: θ̂ = X̄ (proporción de éxitos)

### 2. Normal(μ, σ²) — la más usada

La campana de Gauss. Dos parámetros: media μ y varianza σ².

$$f(x; \mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$

- E[X] = μ
- Var(X) = σ²
- Propiedad clave: X̄ ∼ Normal(μ, σ²/n)

### 3. Poisson(λ) — conteo de eventos

Cuenta eventos raros (número de llamadas por hora, casos de influenza por semana).

$$P(X = x) = \frac{\lambda^x}{x!} e^{-\lambda}, \quad x \in \{0, 1, 2, \ldots\}$$

- E[X] = Var(X) = λ (¡son iguales!)
- Estimador: λ̂ = X̄

### 4. Exponencial(θ) — tiempos de espera

Tiempo hasta que ocurre un evento (tiempo de fallo de un componente).

$$f(x; \theta) = \frac{1}{\theta} e^{-x/\theta}, \quad x > 0$$

- E[X] = θ
- Var(X) = θ²

### 5. Uniforme(0, θ) — soporte depende del parámetro

Todos los valores entre 0 y θ son igualmente probables.

$$f(x; \theta) = \frac{1}{\theta}, \quad 0 < x < \theta$$

- E[X] = θ/2
- Var(X) = θ²/12
- Ojo: la CICR **no aplica** aquí (el soporte depende de θ)

---

## Parte 6: Mapa visual del curso (las 10 clases)

```
CLASE 1-2: ¿Qué es la Estadística?
    │       Atributos → Variables → Datos
    │       Exploratoria vs. Inferencia
    │       Muestreo probabilístico → i.i.d.
    │
CLASE 3: Inferencia Paramétrica
    │       Familias paramétricas F_θ
    │       3 preguntas: Estimación puntual / IC / Prueba de hipótesis
    │
CLASE 4: Estimación Puntual
    │       Función estimadora T, valor estimado, analogía
    │       Error de estimación ε = θ̂ - θ
    │
CLASE 5: Criterios de Calidad ← FUNDAMENTAL
    │       Insesgamiento, Sesgo, ECM = Var + Sesgo²
    │       Consistencia en ECM
    │
CLASE 6: Ejemplo Normal (estimar σ²)
    │       σ̂₁² vs σ̂₂²: el sesgado puede ganar en ECM
    │       χ² con n y n-1 grados de libertad
    │
CLASE 7: Ejemplos Uniforme y Bernoulli
    │       2X̄ vs X₍ₙ₎: el máximo muestral es mejor
    │       Problemas con estimadores discretos
    │
CLASE 8: Suficiencia ← CONCEPTO CLAVE
    │       Definición por distribución condicional
    │       Verificación en Bernoulli, Normal, Uniforme
    │
CLASE 9: Factorización de Fisher-Neyman ← HERRAMIENTA CLAVE
    │       f(x;θ) = g(T;θ) · h(x)
    │       Suficiencia conjunta en Normal bivariada
    │
CLASE 10: Cramér-Rao y MVUE ← EL GRAN FINAL
            CICR(θ) = 1/[n·I(θ)]
            Información de Fisher
            4 expresiones equivalentes
            Identificación del MVUE
```

---

## Parte 7: Prerrequisitos — Lo que deberías saber

### Probabilidad
- Variables aleatorias discretas y continuas
- Función de probabilidad y función de densidad
- Esperanza E[X], varianza Var(X)
- Distribuciones: Bernoulli, Binomial, Poisson, Normal, Exponencial, Uniforme, χ²
- Independencia de variables aleatorias
- Función generadora de momentos

### Cálculo
- Derivadas e integrales
- Sumas y series
- Optimización (encontrar máximos/mínimos con derivadas)

### Álgebra
- Sumatorias y productorias
- Logaritmos y exponenciales

---

## Parte 8: ¿Cómo usar este material?

1. **Lee este documento completo** para tener el panorama general
2. **Ve clase por clase** en orden (docs/clases/clase-01 hasta clase-10)
3. **Después de cada bloque**, intenta resolver ejercicios relacionados
4. **Practica con exámenes pasados** (docs/examenes/) — los patrones se repiten
5. **Usa la guía de estudio** (docs/GUIA-DE-ESTUDIO.md) como referencia rápida

### Orden sugerido de estudio

| Día | Contenido | Ejercicios |
|---|---|---|
| 1 | Clases 1-3 (conceptos fundacionales) | Definiciones del Parcial 1 |
| 2 | Clases 4-5 (estimación, ECM) | Ejercicios 1-3 de la lista |
| 3 | Clase 6 (Normal, varianza) | Ejercicio 6 (área del círculo) |
| 4 | Clase 7 (Uniforme, Bernoulli) | Ejercicios 4-5 |
| 5 | Clases 8-9 (suficiencia, factorización) | Ejercicios 10-11, 13-14 |
| 6 | Clase 10 (CICR, MVUE) | Ejercicios 7-9, 12 |
| 7 | Repaso con exámenes pasados | Parciales 1 completos |
