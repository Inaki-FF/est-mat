# Ejercicios 1–3 Resueltos — Desde Cero

*Cada paso está explicado asumiendo que no sabes nada. Si algo no queda claro, pregúntame.*

---

## Antes de empezar: lo que necesitas saber

### ¿Qué es un estimador?

Tienes una población enorme (millones de personas) y quieres conocer algún número de esa población, por ejemplo, la estatura promedio. Ese número se llama **parámetro** y lo escribimos como **θ** (theta) o **μ** (mu).

Como no puedes medir a todos, tomas una **muestra**: mides a n personas. Cada medición es X₁, X₂, ..., Xₙ.

Un **estimador** es una fórmula que metes en una calculadora con tus datos y te escupe un número que (esperamos) esté cerca del parámetro real. Por ejemplo:

$$\hat{\mu} = \bar{X} = \frac{X_1 + X_2 + \cdots + X_n}{n}$$

### ¿Qué es "insesgado"?

Si repites el experimento muchas veces (tomas muchas muestras diferentes), el **promedio de todos tus estimados** debería dar exactamente el valor real del parámetro. En fórmula:

$$E[\hat{\theta}] = \theta$$

E[·] significa "esperanza" o "promedio a largo plazo". Si se cumple, decimos que el estimador es **insesgado**.

### ¿Qué es la varianza de un estimador?

Mide **qué tan dispersos** están los resultados cada vez que estimas. Varianza chica = estimaciones consistentes. Varianza grande = un día estimas 5, otro día 50.

$$\text{Var}(\hat{\theta}) = E[(\hat{\theta} - E[\hat{\theta}])^2]$$

### Propiedades de la esperanza y varianza que usaremos

| Propiedad | Fórmula |
|---|---|
| Linealidad de E | $E[aX + b] = aE[X] + b$ |
| E de una suma | $E[X_1 + X_2 + \cdots] = E[X_1] + E[X_2] + \cdots$ |
| Var con constante | $\text{Var}(aX) = a^2 \text{Var}(X)$ |
| Var de suma (independientes) | $\text{Var}(X_1 + X_2) = \text{Var}(X_1) + \text{Var}(X_2)$ |

---

# Ejercicio 1 — MELI (Mejor Estimador Lineal Insesgado)

## Enunciado

Tenemos una muestra X₁, X₂, ..., Xₙ de una variable X con media μ y varianza σ². Consideramos **solo** estimadores de la forma:

$$T = a_1 X_1 + a_2 X_2 + \cdots + a_n X_n$$

donde a₁, a₂, ..., aₙ son constantes que nosotros elegimos. **Encuentra** las constantes que hacen que T sea insesgado y tenga la menor varianza posible.

## Solución paso a paso

### Paso 1: ¿Qué significa que T sea insesgado?

Insesgado quiere decir $E[T] = \mu$. Calculemos $E[T]$:

$$E[T] = E[a_1 X_1 + a_2 X_2 + \cdots + a_n X_n]$$

Por la linealidad de la esperanza (la E "pasa" a cada sumando):

$$E[T] = a_1 E[X_1] + a_2 E[X_2] + \cdots + a_n E[X_n]$$

Ahora, como todas las Xᵢ vienen de la misma población, todas tienen la misma media: $E[X_i] = \mu$. Entonces:

$$E[T] = a_1 \mu + a_2 \mu + \cdots + a_n \mu = \mu \cdot (a_1 + a_2 + \cdots + a_n)$$

$$\boxed{E[T] = \mu \cdot \sum_{i=1}^{n} a_i}$$

Para que $E[T] = \mu$, necesitamos:

$$\boxed{\sum_{i=1}^{n} a_i = 1} \quad \text{(Condición de insesgamiento)}$$

### Paso 2: ¿Cuál es la varianza de T?

$$\text{Var}(T) = \text{Var}(a_1 X_1 + a_2 X_2 + \cdots + a_n X_n)$$

Como las Xᵢ son **independientes**, la varianza de la suma es la suma de las varianzas. Además, $\text{Var}(aX) = a^2 \text{Var}(X)$:

$$\text{Var}(T) = a_1^2 \text{Var}(X_1) + a_2^2 \text{Var}(X_2) + \cdots + a_n^2 \text{Var}(X_n)$$

Todas las Xᵢ tienen varianza σ²:

$$\boxed{\text{Var}(T) = \sigma^2 \sum_{i=1}^{n} a_i^2}$$

### Paso 3: Minimizar Var(T) sujeto a la restricción

Queremos encontrar a₁, ..., aₙ que minimicen $\sum a_i^2$ sujeto a $\sum a_i = 1$.

**Usamos multiplicadores de Lagrange** (o sentido común, como verás):

Formamos la función:

$$L(a_1, \ldots, a_n, \lambda) = \sum_{i=1}^{n} a_i^2 - \lambda\left(\sum_{i=1}^{n} a_i - 1\right)$$

Derivamos respecto a cada aᵢ e igualamos a cero:

$$\frac{\partial L}{\partial a_i} = 2a_i - \lambda = 0 \implies a_i = \frac{\lambda}{2}$$

**Observación clave:** todos los aᵢ son iguales. Llamémoslos a.

Aplicamos la restricción: $\sum a_i = n \cdot a = 1$, así que:

$$a = \frac{1}{n}$$

### Paso 4: El MELI

Sustituyendo $a_i = 1/n$ en T:

$$\boxed{T = \frac{1}{n} X_1 + \frac{1}{n} X_2 + \cdots + \frac{1}{n} X_n = \frac{1}{n}\sum_{i=1}^{n} X_i = \bar{X}}$$

**El MELI es la media muestral X̄.**

### Paso 5: Su varianza

$$\text{Var}(\bar{X}) = \sigma^2 \sum_{i=1}^{n} \left(\frac{1}{n}\right)^2 = \sigma^2 \cdot n \cdot \frac{1}{n^2} = \frac{\sigma^2}{n}$$

### Resumen del Ejercicio 1

| Pregunta | Respuesta |
|---|---|
| ¿Cuál es el MELI? | $\bar{X} = \frac{1}{n}\sum X_i$ |
| ¿Por qué esas constantes? | Son las únicas que minimizan $\sum a_i^2$ con la restricción $\sum a_i = 1$ |
| ¿Cuál es su varianza? | $\sigma^2 / n$ |
| Intuición | Todas las observaciones contribuyen por igual — no hay razón para darle más peso a una que a otra |

---

# Ejercicio 2 — Exponencial: X̄ es insesgado con varianza θ²/n

## Enunciado

X tiene distribución Exponencial con densidad:

$$f(x; \theta) = \frac{1}{\theta} e^{-x/\theta}, \quad x > 0, \quad \theta > 0$$

Demuestra que $\bar{X}$ es insesgado para θ y tiene varianza θ²/n.

## ¿Qué es la distribución Exponencial?

Modela **tiempos de espera**. Ejemplo: "¿cuánto tiempo pasa hasta que llega el siguiente cliente?" Si el promedio es 5 minutos, entonces θ = 5.

La gracia de esta distribución es que:
- **E[X] = θ** (el promedio de espera es θ)
- **Var(X) = θ²** (la dispersión de los tiempos es θ al cuadrado)

Estos dos hechos son todo lo que necesitamos. Pero vamos a **demostrarlos** desde la integral.

## Solución paso a paso

### Paso 1: Calcular E[X] (demostrar que E[X] = θ)

Por definición de esperanza para variables continuas:

$$E[X] = \int_0^{\infty} x \cdot f(x; \theta) \, dx = \int_0^{\infty} x \cdot \frac{1}{\theta} e^{-x/\theta} \, dx$$

Hacemos la sustitución $u = x/\theta$, entonces $x = \theta u$ y $dx = \theta \, du$:

$$E[X] = \int_0^{\infty} (\theta u) \cdot \frac{1}{\theta} e^{-u} \cdot \theta \, du = \theta \int_0^{\infty} u \, e^{-u} \, du$$

La integral $\int_0^{\infty} u \, e^{-u} \, du$ es la función Gamma evaluada en 2: $\Gamma(2) = 1! = 1$.

$$\boxed{E[X] = \theta}$$

### Paso 2: Calcular E[X²] (lo necesitamos para la varianza)

$$E[X^2] = \int_0^{\infty} x^2 \cdot \frac{1}{\theta} e^{-x/\theta} \, dx$$

Con la misma sustitución $u = x/\theta$:

$$E[X^2] = \theta^2 \int_0^{\infty} u^2 \, e^{-u} \, du = \theta^2 \cdot \Gamma(3) = \theta^2 \cdot 2! = 2\theta^2$$

### Paso 3: Calcular Var(X)

$$\text{Var}(X) = E[X^2] - (E[X])^2 = 2\theta^2 - \theta^2 = \theta^2$$

$$\boxed{\text{Var}(X) = \theta^2}$$

### Paso 4: Demostrar que X̄ es insesgado para θ

$$E[\bar{X}] = E\left[\frac{1}{n}\sum_{i=1}^{n} X_i\right] = \frac{1}{n}\sum_{i=1}^{n} E[X_i] = \frac{1}{n} \cdot n \cdot \theta = \theta$$

$$\boxed{E[\bar{X}] = \theta \quad \checkmark \quad \text{(insesgado)}}$$

### Paso 5: Calcular Var(X̄)

$$\text{Var}(\bar{X}) = \text{Var}\left(\frac{1}{n}\sum_{i=1}^{n} X_i\right) = \frac{1}{n^2}\sum_{i=1}^{n} \text{Var}(X_i) = \frac{1}{n^2} \cdot n \cdot \theta^2$$

$$\boxed{\text{Var}(\bar{X}) = \frac{\theta^2}{n} \quad \checkmark}$$

### Resumen del Ejercicio 2

| Afirmación | Demostración |
|---|---|
| X̄ es insesgado | $E[\bar{X}] = \theta$ porque $E[X_i] = \theta$ para cada observación |
| Var(X̄) = θ²/n | Sale de Var(X) = θ² dividida entre n por independencia |
| Consistente | Sí, porque Var → 0 cuando n → ∞ |

---

# Ejercicio 3 — Combinación de dos estimadores

## Enunciado

Tienes dos estimadores independientes e insesgados θ̂₁ y θ̂₂. La varianza del primero es **C veces** la del segundo:

$$\text{Var}(\hat{\theta}_1) = C \cdot \text{Var}(\hat{\theta}_2), \quad C > 0 \text{ conocida}$$

## Contexto: ¿Cuándo pasa esto?

Imagina que dos laboratorios diferentes miden la misma cantidad θ. Cada uno produce su estimador. Un laboratorio es más preciso que el otro (tiene menos varianza). Ahora tú tienes ambas estimaciones y quieres combinarlas inteligentemente.

## Parte a) ¿Cuál de los dos preferiría?

**Respuesta: θ̂₂**, el que tiene menor varianza.

**¿Por qué?** Ambos son insesgados, lo que significa que ambos "apuntan" al valor correcto en promedio. La diferencia está en la **dispersión**: θ̂₂ tiene varianza Var(θ̂₂), mientras que θ̂₁ tiene varianza C·Var(θ̂₂).

- Si C > 1: θ̂₁ es **más disperso** → prefiero θ̂₂
- Si C = 1: son igualmente buenos
- Si C < 1: θ̂₁ es **menos disperso** → prefiero θ̂₁

Como el problema dice "C veces", y lo natural es que C > 1 (de lo contrario dirían que es una fracción de), **preferimos θ̂₂**.

En general: entre estimadores insesgados, **el de menor varianza es mejor** porque sus estimaciones son más consistentes.

## Parte b) ¿Cómo elegir k₁, k₂ para que θ̂₃ sea insesgado?

Definimos el estimador combinado:

$$\hat{\theta}_3 = k_1 \hat{\theta}_1 + k_2 \hat{\theta}_2$$

**Condición de insesgamiento:** $E[\hat{\theta}_3] = \theta$.

$$E[\hat{\theta}_3] = k_1 E[\hat{\theta}_1] + k_2 E[\hat{\theta}_2]$$

Como ambos son insesgados: $E[\hat{\theta}_1] = \theta$ y $E[\hat{\theta}_2] = \theta$:

$$E[\hat{\theta}_3] = k_1 \theta + k_2 \theta = (k_1 + k_2)\theta$$

Para que esto sea igual a θ:

$$\boxed{k_1 + k_2 = 1}$$

Es decir, k₂ = 1 - k₁. El estimador combinado es una **mezcla ponderada**:

$$\hat{\theta}_3 = k_1 \hat{\theta}_1 + (1 - k_1) \hat{\theta}_2$$

**Intuición:** le das peso k₁ al primero y el resto (1-k₁) al segundo. Los pesos deben sumar 1 para que el estimador siga "apuntando" al valor correcto.

## Parte c) ¿Cómo elegir k₁, k₂ para que además tenga varianza mínima?

### Paso 1: Calcular Var(θ̂₃)

Usando k₂ = 1 - k₁ y que θ̂₁ y θ̂₂ son **independientes**:

$$\text{Var}(\hat{\theta}_3) = k_1^2 \text{Var}(\hat{\theta}_1) + (1-k_1)^2 \text{Var}(\hat{\theta}_2)$$

Sustituimos Var(θ̂₁) = C · Var(θ̂₂). Para simplificar, llamemos $v = \text{Var}(\hat{\theta}_2)$:

$$\text{Var}(\hat{\theta}_3) = k_1^2 \cdot Cv + (1-k_1)^2 \cdot v = v\left[Ck_1^2 + (1-k_1)^2\right]$$

### Paso 2: Minimizar respecto a k₁

Derivamos el contenido del corchete respecto a k₁ e igualamos a cero:

$$\frac{d}{dk_1}\left[Ck_1^2 + (1-k_1)^2\right] = 2Ck_1 - 2(1-k_1) = 0$$

Resolvemos:

$$2Ck_1 - 2 + 2k_1 = 0$$

$$k_1(2C + 2) = 2$$

$$\boxed{k_1 = \frac{1}{C + 1}}$$

Y por tanto:

$$\boxed{k_2 = 1 - k_1 = \frac{C}{C + 1}}$$

### Paso 3: Verificar que es un mínimo

La segunda derivada es $2C + 2 > 0$, así que efectivamente es un mínimo.

### Paso 4: El estimador óptimo

$$\hat{\theta}_3 = \frac{1}{C+1}\hat{\theta}_1 + \frac{C}{C+1}\hat{\theta}_2$$

**Observación importante:** El estimador con **mayor** varianza (θ̂₁, que tiene varianza Cv) recibe el peso **menor** (1/(C+1)), y el estimador con **menor** varianza (θ̂₂) recibe el peso **mayor** (C/(C+1)).

**Ejemplo numérico:** Si C = 3 (θ̂₁ es 3 veces más disperso):
- k₁ = 1/4 = 25% de peso al estimador malo
- k₂ = 3/4 = 75% de peso al estimador bueno

### Paso 5: La varianza del estimador óptimo

$$\text{Var}(\hat{\theta}_3) = v\left[C \cdot \frac{1}{(C+1)^2} + \frac{C^2}{(C+1)^2}\right]$$

$$= \frac{v}{(C+1)^2}\left[C + C^2\right] = \frac{vC(1+C)}{(C+1)^2} = \frac{Cv}{C+1}$$

$$\boxed{\text{Var}(\hat{\theta}_3) = \frac{C}{C+1} \cdot \text{Var}(\hat{\theta}_2)}$$

## Parte d) ¿Vale la pena la combinación?

**Sí, siempre vale la pena.** Comparemos:

| Estimador | Varianza | Con C=3, v=1 |
|---|---|---|
| θ̂₁ (el peor solo) | $Cv$ | 3 |
| θ̂₂ (el mejor solo) | $v$ | 1 |
| θ̂₃ (combinado) | $\frac{C}{C+1} v$ | 3/4 = 0.75 |

El combinado **siempre** tiene varianza menor que el mejor de los dos originales, porque:

$$\frac{C}{C+1} < 1 \quad \text{para todo } C > 0$$

Esto significa que $\text{Var}(\hat{\theta}_3) < \text{Var}(\hat{\theta}_2)$.

**¿Por qué?** Aunque θ̂₁ es peor, todavía contiene **algo** de información sobre θ. Descartarlo completamente sería desperdiciar esa información. La combinación óptima extrae lo mejor de cada uno dándole más peso al más preciso.

**Caso extremo:** Si C → ∞ (θ̂₁ es pésimo), entonces k₁ → 0 y θ̂₃ → θ̂₂. Es decir, el estimador combinado automáticamente ignora al estimador inútil.

---

# Resumen general

| Ejercicio | Resultado clave | Lección |
|---|---|---|
| 1 (MELI) | $\bar{X}$ es el mejor estimador lineal insesgado | Todas las observaciones deben pesar igual |
| 2 (Exponencial) | $\bar{X}$ es insesgado con Var = θ²/n | Siempre verifica E[θ̂]=θ y calcula Var directamente |
| 3 (Combinación) | El combinado siempre gana | Nunca descartes información — combina dando más peso al mejor |
