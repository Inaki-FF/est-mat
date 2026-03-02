# Ejercicios 4–5 Resueltos — Uniforme(0, θ): Máximo, Mínimo y Rango

*Cada paso explicado desde cero.*

---

## Conceptos previos que necesitas

### ¿Qué es la distribución Uniforme(0, θ)?

Imagina que un número se elige **completamente al azar** entre 0 y θ. No hay preferencia por ningún valor — todos son igual de probables. Su densidad es:

$$f(x; \theta) = \frac{1}{\theta}, \quad 0 < x < \theta$$

Es un rectángulo de altura 1/θ y base θ (así el área total es 1, como debe ser).

Propiedades:
- $E[X] = \theta/2$ (el promedio está en la mitad)
- $\text{Var}(X) = \theta^2/12$

### ¿Qué son las estadísticas de orden?

Si tienes datos x₁, x₂, ..., xₙ y los **ordenas de menor a mayor**, obtienes:

$$X_{(1)} \leq X_{(2)} \leq \cdots \leq X_{(n)}$$

- $X_{(1)}$ = el **mínimo** de la muestra
- $X_{(n)}$ = el **máximo** de la muestra

### ¿Cómo se obtiene la densidad del máximo X₍ₙ₎?

El máximo es menor que t si y solo si **todas** las observaciones son menores que t:

$$F_{X_{(n)}}(t) = P(X_{(n)} \leq t) = P(X_1 \leq t, X_2 \leq t, \ldots, X_n \leq t)$$

Como son independientes:

$$F_{X_{(n)}}(t) = [F_X(t)]^n$$

Derivando para obtener la densidad:

$$f_{X_{(n)}}(t) = n \cdot [F_X(t)]^{n-1} \cdot f_X(t)$$

### ¿Cómo se obtiene la densidad del mínimo X₍₁₎?

El mínimo es mayor que t si y solo si **todas** las observaciones son mayores que t:

$$P(X_{(1)} > t) = [1 - F_X(t)]^n$$

Entonces:

$$F_{X_{(1)}}(t) = 1 - [1 - F_X(t)]^n$$

Derivando:

$$f_{X_{(1)}}(t) = n \cdot [1 - F_X(t)]^{n-1} \cdot f_X(t)$$

---

# Ejercicio 4 — Estimadores insesgados a partir de X₍ₙ₎ y X₍₁₎

## Parte a) Estimador insesgado a partir del máximo X₍ₙ₎

### Paso 1: Encontrar la densidad de X₍ₙ₎

Para X ∼ Unif(0, θ):

$$F_X(t) = \frac{t}{\theta} \quad \text{para } 0 < t < \theta$$

Sustituyendo en la fórmula del máximo:

$$f_{X_{(n)}}(t) = n \cdot \left(\frac{t}{\theta}\right)^{n-1} \cdot \frac{1}{\theta} = \frac{n \cdot t^{n-1}}{\theta^n}, \quad 0 < t < \theta$$

### Paso 2: Calcular E[X₍ₙ₎]

$$E[X_{(n)}] = \int_0^{\theta} t \cdot \frac{n \cdot t^{n-1}}{\theta^n} \, dt = \frac{n}{\theta^n} \int_0^{\theta} t^n \, dt$$

$$= \frac{n}{\theta^n} \cdot \frac{t^{n+1}}{n+1}\Bigg|_0^{\theta} = \frac{n}{\theta^n} \cdot \frac{\theta^{n+1}}{n+1} = \frac{n}{n+1} \cdot \theta$$

**El máximo subestima a θ** (da en promedio n/(n+1) de θ, que es menos que θ).

### Paso 3: Corregir para hacer insesgado

Si $E[X_{(n)}] = \frac{n}{n+1}\theta$, entonces multiplicamos por el recíproco:

$$\hat{\theta}_a = \frac{n+1}{n} X_{(n)}$$

Verificación: $E[\hat{\theta}_a] = \frac{n+1}{n} \cdot \frac{n}{n+1}\theta = \theta$ ✓

$$\boxed{\hat{\theta}_a = \frac{n+1}{n} X_{(n)} \quad \text{es insesgado para } \theta}$$

### Paso 4: Calcular la varianza (la necesitaremos en el inciso c)

Primero necesitamos $E[X_{(n)}^2]$:

$$E[X_{(n)}^2] = \int_0^{\theta} t^2 \cdot \frac{n \cdot t^{n-1}}{\theta^n} \, dt = \frac{n}{\theta^n} \cdot \frac{\theta^{n+2}}{n+2} = \frac{n}{n+2} \theta^2$$

$$\text{Var}(X_{(n)}) = \frac{n}{n+2}\theta^2 - \left(\frac{n}{n+1}\right)^2 \theta^2 = \theta^2 \cdot n \cdot \frac{1}{(n+1)^2(n+2)}$$

$$= \frac{n\theta^2}{(n+1)^2(n+2)}$$

Entonces:

$$\text{Var}(\hat{\theta}_a) = \left(\frac{n+1}{n}\right)^2 \text{Var}(X_{(n)}) = \frac{(n+1)^2}{n^2} \cdot \frac{n\theta^2}{(n+1)^2(n+2)}$$

$$\boxed{\text{Var}(\hat{\theta}_a) = \frac{\theta^2}{n(n+2)}}$$

---

## Parte b) Estimador insesgado a partir del mínimo X₍₁₎

### Paso 1: Encontrar la densidad de X₍₁₎

$$f_{X_{(1)}}(t) = n \cdot \left(1 - \frac{t}{\theta}\right)^{n-1} \cdot \frac{1}{\theta}, \quad 0 < t < \theta$$

### Paso 2: Calcular E[X₍₁₎]

$$E[X_{(1)}] = \int_0^{\theta} t \cdot \frac{n}{\theta}\left(1 - \frac{t}{\theta}\right)^{n-1} dt$$

Hacemos la sustitución $u = 1 - t/\theta$, entonces $t = \theta(1-u)$ y $dt = -\theta \, du$. Cuando t=0, u=1; cuando t=θ, u=0:

$$E[X_{(1)}] = \int_1^{0} \theta(1-u) \cdot \frac{n}{\theta} \cdot u^{n-1} \cdot (-\theta) \, du = n\theta \int_0^{1} (1-u) \cdot u^{n-1} \, du$$

$$= n\theta \left[\int_0^1 u^{n-1} du - \int_0^1 u^n du\right] = n\theta \left[\frac{1}{n} - \frac{1}{n+1}\right]$$

$$= n\theta \cdot \frac{1}{n(n+1)} = \frac{\theta}{n+1}$$

### Paso 3: Corregir para hacer insesgado

Si $E[X_{(1)}] = \frac{\theta}{n+1}$, entonces:

$$\hat{\theta}_b = (n+1) \cdot X_{(1)}$$

Verificación: $E[\hat{\theta}_b] = (n+1) \cdot \frac{\theta}{n+1} = \theta$ ✓

$$\boxed{\hat{\theta}_b = (n+1) \cdot X_{(1)} \quad \text{es insesgado para } \theta}$$

### Paso 4: Calcular la varianza

Necesitamos $E[X_{(1)}^2]$:

$$E[X_{(1)}^2] = n\theta^2 \int_0^1 (1-u)^2 u^{n-1} du = n\theta^2\left[\frac{1}{n} - \frac{2}{n+1} + \frac{1}{n+2}\right]$$

$$= n\theta^2 \cdot \frac{2}{n(n+1)(n+2)} = \frac{2\theta^2}{(n+1)(n+2)}$$

$$\text{Var}(X_{(1)}) = \frac{2\theta^2}{(n+1)(n+2)} - \frac{\theta^2}{(n+1)^2} = \frac{\theta^2 \cdot n}{(n+1)^2(n+2)}$$

$$\text{Var}(\hat{\theta}_b) = (n+1)^2 \cdot \frac{\theta^2 n}{(n+1)^2(n+2)}$$

$$\boxed{\text{Var}(\hat{\theta}_b) = \frac{n\theta^2}{n+2}}$$

---

## Parte c) ¿Cuál preferiría?

Comparemos las varianzas:

| Estimador | Varianza |
|---|---|
| $\hat{\theta}_a = \frac{n+1}{n}X_{(n)}$ | $\dfrac{\theta^2}{n(n+2)}$ |
| $\hat{\theta}_b = (n+1)X_{(1)}$ | $\dfrac{n\theta^2}{n+2}$ |

El cociente es:

$$\frac{\text{Var}(\hat{\theta}_b)}{\text{Var}(\hat{\theta}_a)} = \frac{n\theta^2/(n+2)}{\theta^2/[n(n+2)]} = n^2$$

**θ̂_b tiene varianza n² veces mayor que θ̂_a.**

Por ejemplo, con n = 10:
- Var(θ̂_a) = θ²/120 ≈ 0.0083 θ²
- Var(θ̂_b) = 10θ²/12 ≈ 0.833 θ²

$$\boxed{\text{Preferimos } \hat{\theta}_a = \frac{n+1}{n}X_{(n)} \text{ porque su varianza es muchísimo menor}}$$

**¿Por qué?** El máximo X₍ₙ₎ está siempre **cerca** de θ (justo debajo), así que con una pequeña corrección da un buen estimador. El mínimo X₍₁₎ está **lejos** de θ (cerca de 0), así que multiplicarlo por (n+1) amplifica enormemente su variabilidad.

---

# Ejercicio 5 — Rango y suma de extremos

## Enunciado

Considere los estimadores:
- **Rango:** $R = X_{(n)} - X_{(1)}$
- **Suma de extremos:** $S = X_{(n)} + X_{(1)}$

¿Cómo se comparan con θ̂_a y θ̂_b del ejercicio 4?

## Paso 1: Calcular E[R] y E[S]

Ya sabemos:
- $E[X_{(n)}] = \frac{n}{n+1}\theta$
- $E[X_{(1)}] = \frac{\theta}{n+1}$

Entonces:

$$E[R] = E[X_{(n)}] - E[X_{(1)}] = \frac{n}{n+1}\theta - \frac{\theta}{n+1} = \frac{n-1}{n+1}\theta$$

$$E[S] = E[X_{(n)}] + E[X_{(1)}] = \frac{n}{n+1}\theta + \frac{\theta}{n+1} = \theta$$

**S ya es insesgado sin corrección.** Para R necesitamos corregir:

$$\hat{\theta}_R = \frac{n+1}{n-1} R$$

## Paso 2: Calcular las varianzas

Para la varianza de S, necesitamos Cov(X₍ₙ₎, X₍₁₎). La densidad conjunta de X₍₁₎ y X₍ₙ₎ para Unif(0,θ) es:

$$f_{X_{(1)},X_{(n)}}(s, t) = \frac{n(n-1)}{\theta^n}(t-s)^{n-2}, \quad 0 < s < t < \theta$$

Tras calcular (la cuenta es larga pero directa):

$$E[X_{(1)} X_{(n)}] = \frac{n}{(n+1)(n+2)}\theta^2$$

$$\text{Cov}(X_{(1)}, X_{(n)}) = \frac{n\theta^2}{(n+1)(n+2)} - \frac{n\theta^2}{(n+1)^2} \cdot \frac{1}{1} = \frac{\theta^2}{(n+1)^2(n+2)}$$

### Varianza de S = X₍ₙ₎ + X₍₁₎

$$\text{Var}(S) = \text{Var}(X_{(n)}) + \text{Var}(X_{(1)}) + 2\text{Cov}(X_{(n)}, X_{(1)})$$

$$= \frac{n\theta^2}{(n+1)^2(n+2)} + \frac{n\theta^2}{(n+1)^2(n+2)} + \frac{2\theta^2}{(n+1)^2(n+2)}$$

$$\boxed{\text{Var}(S) = \frac{2\theta^2(n+1)}{(n+1)^2(n+2)} = \frac{2\theta^2}{(n+1)(n+2)}}$$

### Varianza de θ̂_R

De forma análoga:

$$\text{Var}(R) = \text{Var}(X_{(n)}) + \text{Var}(X_{(1)}) - 2\text{Cov}(X_{(n)}, X_{(1)})$$

$$= \frac{2n\theta^2 - 2\theta^2}{(n+1)^2(n+2)} = \frac{2(n-1)\theta^2}{(n+1)^2(n+2)}$$

$$\text{Var}(\hat{\theta}_R) = \left(\frac{n+1}{n-1}\right)^2 \cdot \frac{2(n-1)\theta^2}{(n+1)^2(n+2)} = \frac{2\theta^2}{(n-1)(n+2)}$$

## Paso 3: Comparación final

| Estimador | Varianza | Con n=10 |
|---|---|---|
| $\hat{\theta}_a = \frac{n+1}{n}X_{(n)}$ | $\dfrac{\theta^2}{n(n+2)}$ | $\theta^2/120$ |
| $\hat{\theta}_b = (n+1)X_{(1)}$ | $\dfrac{n\theta^2}{n+2}$ | $10\theta^2/12$ |
| $S = X_{(n)} + X_{(1)}$ | $\dfrac{2\theta^2}{(n+1)(n+2)}$ | $2\theta^2/132$ |
| $\hat{\theta}_R = \frac{n+1}{n-1}R$ | $\dfrac{2\theta^2}{(n-1)(n+2)}$ | $2\theta^2/108$ |

**Ranking de mejor a peor:**

$$\text{Var}(\hat{\theta}_a) < \text{Var}(S) < \text{Var}(\hat{\theta}_R) \ll \text{Var}(\hat{\theta}_b)$$

**Conclusiones:**

1. El **máximo corregido** (θ̂_a) sigue siendo el mejor — usa la observación más informativa
2. La **suma S** es segundo lugar y tiene la ventaja de ser insesgado sin corrección
3. El **rango corregido** es aceptable pero peor que S y θ̂_a
4. El **mínimo corregido** (θ̂_b) es pésimo — no usar
