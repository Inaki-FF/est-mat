# Estrategia de Estudio — Parcial 1

Análisis basado en los 4 exámenes pasados (Oct 2015, Oct 2016, Oct 2024, Ene 2025) y la lista de 14 ejercicios.

---

## 1. Estructura fija del examen

El Parcial 1 tiene **siempre 4 problemas** con una estructura predecible:

| Problema | Tema | Peso aprox. | Dificultad |
|---|---|---|---|
| 1 | Preguntas conceptuales (3 incisos) | 15–20% | Fácil (memorización) |
| 2 | Problema aplicado con datos reales o modelo nuevo | 25% | Medio |
| 3 | Estimación + Rao-Blackwell o sesgo | 30% | Medio-Alto |
| 4 | Problema teórico (CICR, MVUE, MELI o distribución rara) | 25% | Alto |

---

## 2. Lo que SIEMPRE cae (4/4 exámenes)

### Preguntas conceptuales del Problema 1

Estas preguntas se repiten textualmente. Memoriza respuestas de 3–5 líneas para:

| Pregunta | Aparece en |
|---|---|
| ¿Qué es la Estadística? | **Los 4 exámenes** |
| ¿Qué es la Inferencia Estadística Paramétrica? | **Los 4 exámenes** |
| ¿Qué es una muestra aleatoria? | Oct 2015, Oct 2016 |
| ¿Qué relación tiene el muestreo probabilístico con muestras representativas? | Oct 2024, Ene 2025 |

**Respuestas modelo:**

- **Estadística:** "Disciplina científica cuyo propósito es describir fenómenos que se manifiestan a través de datos que presentan variabilidad."
- **Inferencia Paramétrica:** "Rama de la Estadística que, a partir de una muestra aleatoria, produce inferencias sobre el valor de un parámetro desconocido θ que identifica a un elemento de una familia paramétrica."
- **Muestra Aleatoria:** "Colección de v.a. $X_1, \ldots, X_n$ independientes e idénticamente distribuidas (i.i.d.) según la distribución de X."
- **Muestreo probabilístico vs. representativas:** "La muestra representativa es un ideal inalcanzable. El muestreo probabilístico no garantiza representatividad, pero permite cuantificar el error de la inferencia."

### Suficiencia por factorización

Aparece en **todos** los exámenes. Siempre tienes que factorizar $f(x^{(n)}; \theta) = g(T; \theta) \cdot h(x^{(n)})$.

### Rao-Blackwell

Aparece en **todos** los exámenes. El patrón es siempre el mismo:
1. Te dan un estimador insesgado burdo (indicadora o producto de dos observaciones).
2. Te dan o pides la estadística suficiente T.
3. Calculas $E[\hat{\theta} \mid T = t]$ usando combinatoria condicional.
4. Comentas propiedades (insesgado, menor varianza, consistente, posible MVUE).

### Insesgamiento y ECM

Siempre tienes que calcular $E[\hat{\theta}]$, verificar si es θ, y calcular ECM = Var + Sesgo².

---

## 3. Lo que cae MUY frecuentemente (3/4 exámenes)

### CICR e identificación de MVUE

| Examen | Cómo aparece |
|---|---|
| Oct 2015 | "¿La varianza de θ̂ alcanza la CICR?" + "Encuentre φ(θ) para la que sí se alcance" |
| Oct 2016 | Idéntico al 2015 |
| Oct 2024 | "¿Es MVUE?" |
| Ene 2025 | "¿El MELI es MVUE bajo normalidad?" |

**Receta:** calcular $I(\theta) = -E\left[\frac{\partial^2}{\partial\theta^2}\ln f\right]$, luego CICR = $\frac{1}{n \cdot I(\theta)}$, y comparar con Var($\hat{\theta}$).

### Problema aplicado con datos

Siempre hay un problema donde te dan datos numéricos y un modelo. Tienes que:
1. **Identificar el modelo específico** (ej: Poisson con λ̂ = x̄ = 3.1).
2. **Estimar una probabilidad** usando el modelo (ej: $P(X = 0) = e^{-3.1}$).
3. **Argumentar si el modelo es razonable** comparando media y varianza muestrales.

---

## 4. Los dos problemas estrella (se repiten casi idénticos)

### Problema estrella 1: Poisson — estimar $P(X = 0) = e^{-\lambda}$

**Apareció en Oct 2015 Y Oct 2016 (literalmente el mismo problema).**

- $T_1 = \sum X_i$ es suficiente (factorización).
- $T_2 = \mathbb{1}(X_1 = 0)$ es insesgado para $e^{-\lambda}$.
- Rao-Blackwell: $T_3 = E[T_2 \mid T_1 = t] = (1 - 1/n)^t$.
- $\text{Var}(T_3) \leq \text{Var}(T_2)$, y $T_3$ es MVUE.

**Practica:** Ejercicios de `rao-blackwell-explicado.md` (ejemplo Poisson).

### Problema estrella 2: Bernoulli — estimar $\theta^2$

**Apareció en Oct 2024 Y Ene 2025 (casi el mismo problema).**

- $\bar{X}^2$ es sesgado: sesgo = $\theta(1-\theta)/n$.
- $\hat{\varphi}_2 = X_1 X_2$ es insesgado pero no consistente.
- Rao-Blackwell: $\hat{\varphi}_3 = E[X_1 X_2 \mid T = t] = \frac{t(t-1)}{n(n-1)}$.
- Es MVUE por Lehmann-Scheffé.

**Practica:** Problema 3 del examen Ene 2025 y Oct 2024.

---

## 5. Distribuciones que debes dominar

Ordenadas por frecuencia de aparición en exámenes:

| Prioridad | Distribución | Aparece en | Qué te piden |
|---|---|---|---|
| **ALTA** | Poisson(λ) | Oct 2015, Oct 2016, Oct 2024 | Suficiencia, Rao-Blackwell, estimar $e^{-\lambda}$ |
| **ALTA** | Bernoulli(θ) | Oct 2024, Ene 2025 | Sesgo de $\bar{X}^2$, Rao-Blackwell para θ², MVUE |
| **ALTA** | Exponencial(θ) | Oct 2016, Ejercicios 2 | CICR, MVUE, analogía |
| **MEDIA** | Uniforme | Ene 2025, Ejercicios 4–5 | Suficiencia (extremos), analogía, consistencia |
| **MEDIA** | Geométrica | Oct 2015 | Suficiencia, momentos, MV, CICR |
| **MEDIA** | Normal(μ,σ²) | Ejercicio 6, Prob 4 Ene 2025 | MELI, varianza, χ² |
| **BAJA** | Trinomial/rara | Oct 2024 (Prob 4) | Suficiencia, analogía, ECM |
| **BAJA** | Beta-potencia $\theta x^{\theta-1}$ | Ejercicios 8–9 | Suficiencia, CICR, transformación |

---

## 6. Habilidades técnicas que debes practicar

### Tier 1 — Sin esto no pasas

| Habilidad | Dónde practicar |
|---|---|
| Calcular $E[\hat{\theta}]$ y verificar insesgamiento | Todas las clases, todos los ejercicios |
| Calcular $\text{Var}(\hat{\theta})$ y ECM | Clase 5, Clase 6, Ejercicios 1–6 |
| Factorización de Fisher-Neyman | Clase 9, Ejercicios 10, 11, 13, 14 |
| Rao-Blackwell: calcular $E[\hat{\theta} \mid T = t]$ | Clase Rao-Blackwell, Ejercicio 12 |

### Tier 2 — Lo que separa el 80 del 100

| Habilidad | Dónde practicar |
|---|---|
| Calcular $I(\theta)$ y la CICR | Clase 10, Ejercicios 7, 8, 9 |
| Encontrar φ(θ) cuyo estimador alcance la CICR | Ejercicios 8d, 9c–d, Exámenes 2015/2016 Prob 3c |
| Multiplicadores de Lagrange para MELI | Ejercicio 1, Examen Ene 2025 Prob 4 |
| Verificar si MELI es MVUE (comparar con CICR) | Examen Ene 2025 Prob 4b |

### Tier 3 — Para el 100

| Habilidad | Dónde practicar |
|---|---|
| Distribuciones "raras" (trinomial, Laplace) | Ejercicios 13, Examen Oct 2024 Prob 4 |
| Variables no i.i.d. | Ejercicio 11 |
| Familia exponencial general | Ejercicio 14 |

---

## 7. Plan de estudio día por día

### Día 1 — Fundamentos y definiciones
- [ ] Memorizar las 4 respuestas conceptuales del Problema 1
- [ ] Repasar Clases 1–3 (solo definiciones formales)
- [ ] Resolver Problema 1 de cualquier examen pasado (cronometrar: máx 10 min)

### Día 2 — ECM, sesgo, consistencia
- [ ] Repasar Clases 5–6 (relación fundamental ECM = Var + Sesgo²)
- [ ] Resolver Ejercicios 1–3 (MELI, Exponencial, combinación de estimadores)
- [ ] Practicar: calcular E[θ̂], Var(θ̂), ECM(θ̂) para Normal, Bernoulli, Exponencial

### Día 3 — Suficiencia y factorización
- [ ] Repasar Clases 8–9 (factorización de Fisher-Neyman)
- [ ] Factorizar al menos 5 distribuciones: Bernoulli, Normal, Poisson, Exponencial, Uniforme
- [ ] Resolver Ejercicios 10, 11, 13, 14

### Día 4 — CICR y MVUE
- [ ] Repasar Clase 10 y `cramer-rao-explicado.md`
- [ ] Calcular I(θ) y CICR para: Bernoulli, Normal, Poisson, Exponencial
- [ ] Resolver Ejercicios 7, 8, 9

### Día 5 — Rao-Blackwell (el tema más importante)
- [ ] Repasar `rao-blackwell-explicado.md`
- [ ] Resolver el problema Poisson-$e^{-\lambda}$ (Oct 2015/2016 Prob 4)
- [ ] Resolver el problema Bernoulli-θ² (Oct 2024/Ene 2025 Prob 3)
- [ ] Resolver Ejercicio 12

### Día 6 — Simulacro de examen
- [ ] Elegir un examen que NO hayas resuelto todavía
- [ ] Resolverlo completo con cronómetro (2 horas)
- [ ] Comparar con soluciones
- [ ] Identificar errores y repasar esos temas

### Día 7 — Repaso final
- [ ] Segundo simulacro con otro examen
- [ ] Repasar los temas donde fallaste
- [ ] Revisar fórmulas clave una última vez

---

## 8. Fórmulas para tener en la punta de los dedos

```
ECM(θ̂) = Var(θ̂) + [Sesgo(θ̂)]²

CICR(θ) = 1 / [n · I(θ)]

CICR(φ) = [φ'(θ)]² / [n · I(θ)]

I(θ) = E[(∂/∂θ ln f)²] = -E[∂²/∂θ² ln f]

Factorización: f(x⁽ⁿ⁾; θ) = g(T; θ) · h(x⁽ⁿ⁾)

Rao-Blackwell: δ* = E[δ | T], entonces Var(δ*) ≤ Var(δ)

Var(X̄) = Var(X) / n

Ley de varianza total: Var(Y) = Var(E[Y|T]) + E[Var(Y|T)]
```

---

## 9. Errores frecuentes a evitar

1. **Olvidar que ECM ≠ Var cuando hay sesgo.** Siempre verifica primero si es insesgado.
2. **Intentar aplicar CICR a Uniforme(0,θ).** El soporte depende de θ → no aplica.
3. **En Rao-Blackwell, confundir T con t.** La esperanza condicional $E[\delta \mid T = t]$ es función de t; luego sustituyes t por T para tener el estimador.
4. **En el MELI, olvidar la restricción $\sum a_i = 1$.**
5. **Calcular Var(X̄²) directamente.** Es más fácil usar $E[\bar{X}^2] = \text{Var}(\bar{X}) + (E[\bar{X}])^2$.
6. **No comentar propiedades.** En Rao-Blackwell siempre menciona: insesgado, menor varianza, función de T, posible MVUE.
