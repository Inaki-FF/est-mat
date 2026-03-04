# Examen Parcial 1 — Enero 2025 (Resuelto paso a paso)

**Curso:** Estadística Matemática — Prof. Manuel Mendoza Ramírez, ITAM

---

## Problema 1 — Preguntas conceptuales

*Conteste brevemente cada una de las siguientes preguntas (no más de cinco líneas cada una).*

### a) ¿Qué es la Estadística?

La Estadística es una disciplina científica cuyo propósito es **describir fenómenos que se manifiestan a través de datos que presentan variabilidad**.

Tres ideas clave en una oración:

- Es una **disciplina científica** (no un conjunto de trucos).
- Su objetivo es **describir** (toda la Estadística es descriptiva).
- Se ocupa de datos con **variabilidad** (fenómenos inciertos, no determinísticos).

### b) ¿Qué es la Inferencia Estadística Paramétrica?

Es la rama de la Estadística que, a partir de una **muestra aleatoria**, produce inferencias sobre el valor de un **parámetro desconocido** θ que identifica a un elemento dentro de una **familia paramétrica** de distribuciones.

Desglose:

- No tenemos todos los datos, solo una muestra.
- Suponemos que los datos vienen de una familia conocida (Normal, Poisson, etc.) indexada por θ.
- Queremos averiguar θ: su valor (estimación puntual), su ubicación (intervalos de confianza) o si es compatible con una hipótesis (prueba de hipótesis).

### c) ¿Qué relación guarda el muestreo probabilístico con las muestras "representativas"?

Una muestra "representativa" es un ideal inalcanzable: sería una que reproduce perfectamente las características de la población. El **muestreo probabilístico** (por sorteo) es la solución práctica: no garantiza representatividad exacta, pero sí permite **cuantificar el error** cometido al usar la muestra para inferir sobre la población. Es decir, no promete que la muestra sea perfecta, sino que permite medir qué tan imperfecta es.

---

## Problema 2 — Uniforme centrada en θ

**Enunciado.** Sea $X^{(n)}$ una muestra aleatoria de una variable aleatoria X con función de densidad:

$$f(x; \theta) = \begin{cases} 1 & \text{si } \theta - \frac{1}{2} \leq x \leq \theta + \frac{1}{2} \\ 0 & \text{en otro caso} \end{cases}$$

Es decir, $X \sim \text{Uniforme}(\theta - \tfrac{1}{2},\; \theta + \tfrac{1}{2})$: un rectángulo de ancho 1 centrado en θ.

**Propiedades básicas de esta distribución:**

$$E[X] = \frac{(\theta - 1/2) + (\theta + 1/2)}{2} = \theta$$

$$\text{Var}(X) = \frac{(\theta + 1/2 - \theta + 1/2)^2}{12} = \frac{1}{12}$$

### a) ¿En qué sentido $\hat{\theta} = \bar{X}$ es estimador por analogía?

**Principio de analogía:** reemplazar una cantidad poblacional por su análogo muestral.

Sabemos que $E[X] = \theta$. Es decir, la media poblacional es exactamente θ. Entonces el análogo muestral natural es:

$$\hat{\theta} = \bar{X} = \frac{1}{n}\sum_{i=1}^n X_i$$

> $\bar{X}$ es estimador por analogía porque $E[X] = \theta$, y al reemplazar la media poblacional por la media muestral obtenemos $\hat{\theta} = \bar{X}$ como aproximación de θ.

### b) ¿Es $\hat{\theta} = \bar{X}$ consistente en ECM?

Necesitamos verificar que $\text{ECM}(\bar{X}) \to 0$ cuando $n \to \infty$.

**Paso 1 — ¿Es insesgado?**

$$E[\bar{X}] = E\left[\frac{1}{n}\sum X_i\right] = \frac{1}{n}\sum E[X_i] = \frac{1}{n} \cdot n\theta = \theta$$

Sesgo = 0, así que $\text{ECM} = \text{Var} + \text{Sesgo}^2 = \text{Var}$.

**Paso 2 — Varianza.**

Como las $X_i$ son i.i.d.:

$$\text{Var}(\bar{X}) = \frac{\text{Var}(X)}{n} = \frac{1/12}{n} = \frac{1}{12n}$$

**Paso 3 — Verificar consistencia.**

$$\text{ECM}(\bar{X}) = \frac{1}{12n} \xrightarrow{n \to \infty} 0 \quad \checkmark$$

> Sí, $\bar{X}$ es consistente en ECM porque su ECM = 1/(12n) tiende a cero.

### c) ¿Es $\hat{\theta} = \bar{X}$ suficiente para θ?

Usamos el **Teorema de Factorización de Fisher-Neyman**: T es suficiente si y solo si $f(x^{(n)}; \theta) = g(T; \theta) \cdot h(x^{(n)})$.

La densidad conjunta de la muestra es:

$$f(x^{(n)}; \theta) = \prod_{i=1}^n f(x_i; \theta) = \prod_{i=1}^n \mathbf{1}_{\left[\theta - \frac{1}{2},\; \theta + \frac{1}{2}\right]}(x_i)$$

Esa indicadora dice: "cada $x_i$ debe estar entre $\theta - 1/2$ y $\theta + 1/2$". Esto equivale a pedir:

$$\theta - \tfrac{1}{2} \leq x_{(1)} \quad \text{y} \quad x_{(n)} \leq \theta + \tfrac{1}{2}$$

donde $x_{(1)}$ es el mínimo y $x_{(n)}$ es el máximo de la muestra. Entonces:

$$f(x^{(n)}; \theta) = \underbrace{\mathbf{1}\left(x_{(1)} \geq \theta - \tfrac{1}{2}\right) \cdot \mathbf{1}\left(x_{(n)} \leq \theta + \tfrac{1}{2}\right)}_{g\left((x_{(1)}, x_{(n)}); \theta\right)} \cdot \underbrace{1}_{h(x^{(n)})}$$

La densidad depende de θ **a través de $x_{(1)}$ y $x_{(n)}$**, no a través de $\bar{x}$.

No hay manera de factorizar esto como $g(\bar{x}; \theta) \cdot h(x^{(n)})$ porque el soporte depende de θ a través de los extremos muestrales, no de la media.

> **No**, $\bar{X}$ no es suficiente para θ. La estadística suficiente es el par $(X_{(1)}, X_{(n)})$ (mínimo y máximo muestrales), ya que el soporte de la distribución depende de θ y se controla a través de los extremos.

---

## Problema 3 — Bernoulli, estimar $\varphi = \theta^2$

**Enunciado.** Sea $X^{(n)}$ una muestra aleatoria de $X \sim \text{Bernoulli}(\theta)$. Se quiere estimar insesgadamente $\varphi = \theta^2$.

**Recordatorio:**

- $E[X_i] = \theta$, $\text{Var}(X_i) = \theta(1-\theta)$
- $T = \sum X_i \sim \text{Binomial}(n, \theta)$ es suficiente para θ.
- Como $X_i$ es Bernoulli (vale 0 o 1), $X_i^2 = X_i$ y $E[X_i^2] = \theta$.

### a) Comprobar que $\hat{\varphi}_1 = \bar{X}^2$ es sesgado

Usamos la identidad $E[Y^2] = \text{Var}(Y) + (E[Y])^2$ con $Y = \bar{X}$:

$$E[\bar{X}^2] = \text{Var}(\bar{X}) + (E[\bar{X}])^2 = \frac{\theta(1-\theta)}{n} + \theta^2$$

$$E[\bar{X}^2] = \frac{\theta - \theta^2}{n} + \theta^2 = \frac{\theta}{n} + \theta^2\left(1 - \frac{1}{n}\right) = \frac{\theta}{n} + \frac{(n-1)\theta^2}{n}$$

El sesgo es:

$$\text{Sesgo} = E[\bar{X}^2] - \theta^2 = \frac{\theta}{n} + \frac{(n-1)\theta^2}{n} - \theta^2 = \frac{\theta - \theta^2}{n} = \frac{\theta(1-\theta)}{n}$$

> El sesgo es $\theta(1-\theta)/n > 0$ para $\theta \in (0,1)$, así que $\bar{X}^2$ **sobreestima** $\theta^2$. Es sesgado (aunque asintóticamente insesgado porque el sesgo $\to 0$).

### b) Probar que $\hat{\varphi}_2 = X_1 X_2$ es insesgado pero no consistente

El estimador es $\hat{\varphi}_2 = X_1 \cdot X_2$: vale 1 solo si las dos primeras observaciones son 1.

**Insesgamiento:**

$$E[\hat{\varphi}_2] = E[X_1 \cdot X_2] = E[X_1] \cdot E[X_2] = \theta \cdot \theta = \theta^2 = \varphi \quad \checkmark$$

(Usamos independencia para separar la esperanza del producto.)

**¿Es consistente en ECM?**

Como es insesgado, ECM = Var. Calculemos la varianza.

$$E[\hat{\varphi}_2^2] = E[(X_1 X_2)^2] = E[X_1^2] \cdot E[X_2^2]$$

Como $X_i^2 = X_i$ (Bernoulli), $E[X_i^2] = \theta$:

$$E[\hat{\varphi}_2^2] = \theta \cdot \theta = \theta^2$$

$$\text{Var}(\hat{\varphi}_2) = E[\hat{\varphi}_2^2] - (E[\hat{\varphi}_2])^2 = \theta^2 - \theta^4 = \theta^2(1 - \theta^2)$$

**La varianza no depende de n.** No importa si la muestra tiene 10 o 10 millones de observaciones, la varianza es siempre $\theta^2(1-\theta^2)$.

$$\text{ECM} = \theta^2(1-\theta^2) \not\to 0$$

> $\hat{\varphi}_2$ **no es consistente** porque solo usa $X_1$ y $X_2$, ignorando el resto de la muestra. Su ECM no tiende a cero.

### c) Rao-Blackwellización: $\hat{\varphi}_3 = E[\hat{\varphi}_2 \mid T = t]$

Aplicamos el Teorema de Rao-Blackwell: condicionamos el estimador insesgado (pero malo) sobre el estadístico suficiente $T = \sum X_i$ para obtener uno mejor.

Necesitamos:

$$\hat{\varphi}_3 = E[X_1 X_2 \mid T = t] = P(X_1 = 1, X_2 = 1 \mid T = t)$$

**¿Cómo se distribuye la muestra dado T = t?**

Dado que hubo t éxitos en total entre n ensayos Bernoulli, la distribución de cuáles ensayos fueron éxito es simétrica. Concretamente, $P(X_1 = 1, X_2 = 1 \mid T = t)$ es el número de formas de que $X_1 = 1$ y $X_2 = 1$ (repartiendo los $t - 2$ éxitos restantes entre las $n - 2$ posiciones restantes) dividido por el total de formas de ubicar t éxitos en n posiciones:

$$P(X_1 = 1, X_2 = 1 \mid T = t) = \frac{\binom{n-2}{t-2}}{\binom{n}{t}}$$

**Simplificación:**

$$\frac{\binom{n-2}{t-2}}{\binom{n}{t}} = \frac{\frac{(n-2)!}{(t-2)!(n-t)!}}{\frac{n!}{t!(n-t)!}} = \frac{(n-2)! \cdot t!}{n! \cdot (t-2)!} = \frac{t(t-1)}{n(n-1)}$$

Entonces:

$$\boxed{\hat{\varphi}_3 = \frac{T(T-1)}{n(n-1)}}$$

donde $T = \sum_{i=1}^n X_i$.

**Propiedades de $\hat{\varphi}_3$:**

1. **Insesgado** para $\theta^2$ — garantizado por Rao-Blackwell (heredado de $\hat{\varphi}_2$).
2. **$\text{Var}(\hat{\varphi}_3) \leq \text{Var}(\hat{\varphi}_2)$** — garantizado por Rao-Blackwell.
3. **Consistente en ECM** — ahora sí depende de n (a diferencia de $\hat{\varphi}_2$), y su varianza tiende a 0.
4. **Es función de T** (suficiente) — usa toda la información de la muestra.
5. Como T es suficiente y completo en Bernoulli, por **Lehmann-Scheffé** este es el **MVUE** de $\theta^2$.

---

## Problema 4 — MELI (Mejor Estimador Lineal Insesgado)

**Enunciado.** Sea $X_1, X_2, \ldots, X_n$ una colección de variables aleatorias independientes tales que $E(X_i) = \mu$ y $\text{Var}(X_i) = \sigma_i^2$ para $i = 1, \ldots, n$.

**Nota:** las $X_i$ son independientes pero **no** idénticamente distribuidas (tienen la misma media μ pero varianzas distintas).

Un estimador lineal tiene la forma:

$$\hat{\mu} = \sum_{i=1}^n a_i X_i$$

Queremos encontrar los pesos $a_i$ que minimicen la varianza, sujeto a que sea insesgado.

### a) Encontrar el MELI (varianzas conocidas)

**Restricción de insesgamiento:**

$$E[\hat{\mu}] = \sum a_i E[X_i] = \sum a_i \mu = \mu \sum a_i = \mu$$

Esto requiere:

$$\sum_{i=1}^n a_i = 1$$

**Función a minimizar (varianza):**

$$\text{Var}(\hat{\mu}) = \sum a_i^2 \sigma_i^2$$

(por independencia, no hay covarianzas cruzadas).

**Optimización con restricción — Multiplicadores de Lagrange:**

$$\mathcal{L}(a_1, \ldots, a_n, \lambda) = \sum_{i=1}^n a_i^2 \sigma_i^2 - \lambda\left(\sum_{i=1}^n a_i - 1\right)$$

Derivando respecto a cada $a_i$ e igualando a cero:

$$\frac{\partial \mathcal{L}}{\partial a_i} = 2a_i \sigma_i^2 - \lambda = 0 \quad \Longrightarrow \quad a_i = \frac{\lambda}{2\sigma_i^2}$$

Es decir, **el peso de cada observación es inversamente proporcional a su varianza**. Tiene sentido: le das más importancia a las observaciones más precisas.

**Determinamos λ** aplicando la restricción $\sum a_i = 1$:

$$\sum_{i=1}^n \frac{\lambda}{2\sigma_i^2} = 1 \quad \Longrightarrow \quad \frac{\lambda}{2} = \frac{1}{\sum_{i=1}^n \frac{1}{\sigma_i^2}}$$

**Sustituyendo:**

$$\boxed{a_i = \frac{1/\sigma_i^2}{\sum_{j=1}^n 1/\sigma_j^2}}$$

$$\boxed{\hat{\mu}_{\text{MELI}} = \frac{\sum_{i=1}^n X_i / \sigma_i^2}{\sum_{i=1}^n 1/\sigma_i^2}}$$

Es un **promedio ponderado por el inverso de las varianzas**.

**Su varianza es:**

$$\text{Var}(\hat{\mu}_{\text{MELI}}) = \sum a_i^2 \sigma_i^2 = \frac{\sum \frac{1}{\sigma_i^4} \cdot \sigma_i^2}{\left(\sum \frac{1}{\sigma_i^2}\right)^2} = \frac{\sum \frac{1}{\sigma_i^2}}{\left(\sum \frac{1}{\sigma_i^2}\right)^2} = \frac{1}{\sum_{i=1}^n 1/\sigma_i^2}$$

**Caso particular:** si todas las varianzas son iguales ($\sigma_i^2 = \sigma^2$), entonces $a_i = 1/n$ y el MELI se reduce a $\bar{X}$.

### b) ¿Es MVUE bajo normalidad?

Si $X_i \sim N(\mu, \sigma_i^2)$ independientes, calculamos la **Información de Fisher total** y la **CICR**.

**Log-verosimilitud para una observación $X_i$:**

$$\ln f(x_i; \mu) = -\frac{1}{2}\ln(2\pi\sigma_i^2) - \frac{(x_i - \mu)^2}{2\sigma_i^2}$$

**Score:**

$$\frac{\partial}{\partial \mu}\ln f(x_i; \mu) = \frac{x_i - \mu}{\sigma_i^2}$$

**Información de Fisher de $X_i$:**

$$I_i(\mu) = -E\left[\frac{\partial^2}{\partial \mu^2}\ln f(x_i; \mu)\right] = \frac{1}{\sigma_i^2}$$

**Información total** de la muestra (sumando todas las observaciones independientes):

$$I_{\text{total}}(\mu) = \sum_{i=1}^n I_i(\mu) = \sum_{i=1}^n \frac{1}{\sigma_i^2}$$

**CICR:**

$$\text{CICR}(\mu) = \frac{1}{I_{\text{total}}(\mu)} = \frac{1}{\sum_{i=1}^n 1/\sigma_i^2}$$

**Comparación:**

$$\text{Var}(\hat{\mu}_{\text{MELI}}) = \frac{1}{\sum_{i=1}^n 1/\sigma_i^2} = \text{CICR}(\mu) \quad \checkmark$$

> **Sí**, bajo normalidad el MELI alcanza la Cota Inferior de Cramér-Rao, por lo que es **MVUE** para μ.

---

## Resumen

| Problema | Tema central | Herramientas usadas |
|---|---|---|
| 1 | Definiciones conceptuales | Defs. 1.1, inferencia paramétrica, muestreo |
| 2 | Uniforme centrada en θ | Analogía, ECM = Var (insesgado), factorización de Fisher-Neyman |
| 3 | Bernoulli, estimar θ² | Sesgo, consistencia, Rao-Blackwell, combinatoria condicional |
| 4 | MELI con varianzas distintas | Multiplicadores de Lagrange, información de Fisher, CICR |
