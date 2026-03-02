# Clase 3: Inferencia Paramétrica

**Capítulo I.4 – I.5**

---

## Conceptos Clave

- **Función de Distribución F(x):** El objetivo último del estudio es describir la función de distribución de X.
- **Espacio de funciones de distribución F:** Conjunto de dimensión infinita.
- **Familia paramétrica:** Subconjunto de funciones de distribución indexado por un parámetro θ, que simplifica el problema.
- **Inferencia Paramétrica:** Producir inferencias sobre el valor del parámetro desconocido θ.

---

## Definición Formal de Muestra Aleatoria

### Definición 1.6
Se dice que X⁽ⁿ⁾ = (X₁, X₂, ..., Xₙ) es una **muestra aleatoria (m.a.)** de la variable aleatoria X, si constituye una colección de variables aleatorias **independientes e idénticamente distribuidas (i.i.d.)** de acuerdo a la función de distribución de X.

---

## Condiciones de una Función de Distribución F(x)

- F(x) monótona no decreciente
- F(x) → 0 cuando x → -∞
- F(x) → 1 cuando x → +∞
- F(x) continua por la derecha

---

## Familia Paramétrica

$$\mathcal{F}_\Theta = \{ F(x) \mid F(x) = F(x; \theta), \; \theta \in \Theta \}$$

- Para cada valor fijo de θ, la distribución F(x; θ) es totalmente conocida.
- θ es el **parámetro** de la familia: un índice que identifica de manera inequívoca a cada elemento.
- Si el espacio paramétrico Θ ⊂ ℝᵏ, el problema se reduce a optimización en ℝᵏ.

---

## Las Tres Preguntas Fundamentales

| Pregunta | Tipo de inferencia |
|---|---|
| ¿Cuál es el valor de θ? | **Estimación Puntual** |
| ¿Por dónde se localiza θ? | **Estimación por Regiones** (Intervalos de Confianza) |
| ¿Son los datos compatibles con una idea preconcebida sobre θ? | **Contraste o Prueba de Hipótesis** |
