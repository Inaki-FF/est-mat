# Teorema de Rao-Blackwell — Desde Cero

---

## ¿Qué problema resuelve?

Tienes un estimador insesgado de θ, digamos δ(X). Funciona, pero tal vez su varianza es alta. ¿Puedes mejorarlo *sin inventar otro estimador desde cero*?

Rao-Blackwell dice: **sí, condiciona sobre un estadístico suficiente y automáticamente obtienes algo igual o mejor.**

$$\boxed{\delta^{*}(T) = E[\delta(X) \mid T] \quad \Longrightarrow \quad \text{Var}(\delta^{*}) \leq \text{Var}(\delta)}$$

Es decir, "exprimes" la información que ya tienes en T y descartas el ruido que no aporta.

---

## Los ingredientes

### 1. Estadístico suficiente T

Un estadístico T = T(X₁, …, Xₙ) es **suficiente** para θ si la distribución condicional de la muestra dado T no depende de θ.

**Intuición:** T captura *toda* la información sobre θ que hay en los datos. Todo lo demás es ruido.

**Criterio de factorización (Neyman-Fisher):**

$$f(\mathbf{x};\theta) = g(T(\mathbf{x}), \theta) \cdot h(\mathbf{x})$$

Si la densidad conjunta se puede escribir así (una parte que depende de θ solo a través de T, y otra que no depende de θ), entonces T es suficiente.

### 2. Estimador insesgado δ(X)

Cualquier estimador con $E[\delta(X)] = \theta$ (o más general, $= \varphi(\theta)$).

---

## El Teorema

**Teorema (Rao-Blackwell).** Sea δ(X) un estimador insesgado de θ con varianza finita, y sea T un estadístico suficiente para θ. Define:

$$\delta^{*}(T) = E[\delta(X) \mid T]$$

Entonces:

1. **δ\* es insesgado:** $E[\delta^{*}] = E[E[\delta \mid T]] = E[\delta] = \theta$ (por la ley de esperanza total)
2. **δ\* tiene varianza menor o igual:**

$$\text{Var}(\delta) = \text{Var}(E[\delta \mid T]) + E[\text{Var}(\delta \mid T)] = \text{Var}(\delta^{*}) + \underbrace{E[\text{Var}(\delta \mid T)]}_{\geq 0}$$

$$\Longrightarrow \text{Var}(\delta^{*}) \leq \text{Var}(\delta)$$

La igualdad vale si y solo si δ ya es función de T (es decir, no había nada que mejorar).

---

## ¿Por qué funciona? (Intuición)

Imagina que tiras 10 dados y quieres estimar la probabilidad de que salga 6.

- **Estimador bruto δ:** mirar solo el primer dado. Es insesgado pero ignora 9 datos.
- **Estadístico suficiente T:** el número total de 6's en los 10 dados. Captura toda la info.
- **δ\* = E[δ | T]:** dado que hubo T seises en total, ¿cuál es la probabilidad de que el primer dado haya sido 6? Es T/10. Mucho más estable que mirar un solo dado.

Al condicionar sobre T, eliminas la variabilidad que no aporta información sobre θ.

---

## Ejemplo completo: Poisson(λ)

Sea X₁, …, Xₙ ~ Poisson(λ). Queremos estimar $\varphi(\lambda) = e^{-\lambda} = P(X_1 = 0)$.

### Paso 1: Un estimador insesgado (burdo)

$$\delta(X) = \mathbb{1}(X_1 = 0) = \begin{cases} 1 & \text{si } X_1 = 0 \\ 0 & \text{si } X_1 \neq 0 \end{cases}$$

Es insesgado porque $E[\delta] = P(X_1 = 0) = e^{-\lambda}$, pero tiene varianza alta (es 0 o 1).

### Paso 2: Estadístico suficiente

$$T = \sum_{i=1}^n X_i \sim \text{Poisson}(n\lambda)$$

T es suficiente (por factorización de la densidad conjunta).

### Paso 3: Rao-Blackwellizar

$$\delta^{*}(T) = E[\mathbb{1}(X_1 = 0) \mid T = t] = P(X_1 = 0 \mid T = t)$$

Necesitamos calcular esto. Dado que $T = t$, usamos que $X_1 \mid T = t$ tiene distribución Binomial:

$$P(X_1 = 0 \mid T = t) = P\left(\text{Bin}\left(t, \frac{1}{n}\right) = 0\right) = \left(1 - \frac{1}{n}\right)^t$$

Entonces:

$$\boxed{\delta^{*}(T) = \left(1 - \frac{1}{n}\right)^T}$$

### Paso 4: Comparar varianzas

| Estimador | Expresión | Varianza |
|---|---|---|
| δ (indicadora) | $\mathbb{1}(X_1 = 0)$ | $e^{-\lambda}(1 - e^{-\lambda})$ |
| δ* (Rao-Blackwell) | $(1 - 1/n)^T$ | Mucho menor, decrece con n |

El estimador mejorado usa *toda* la muestra a través de T, no solo X₁.

---

## Rao-Blackwell + Completitud = MVUE (Lehmann-Scheffé)

Rao-Blackwell te da un estimador **mejor**, pero ¿es **el mejor**?

Si T es **suficiente y completo**, entonces δ\* = E[δ | T] es el **único** estimador insesgado basado en T, y por lo tanto es **MVUE**.

**Completitud** significa que no hay funciones "invisibles" de T:

$$E[g(T)] = 0 \;\forall\theta \implies g(T) = 0 \text{ c.s.}$$

En las familias exponenciales (Normal, Poisson, Bernoulli, Gamma, etc.), el estadístico suficiente natural es completo. Entonces Rao-Blackwell + completitud = MVUE automático.

---

## Receta práctica

1. **Encuentra T suficiente** — usa factorización de Neyman-Fisher
2. **Propón cualquier δ insesgado** — puede ser burdo, no importa
3. **Calcula E[δ | T]** — esta es la parte que requiere trabajo
4. **Si T es completo** → ya tienes el MVUE (Lehmann-Scheffé)
5. **Verifica con CICR** (si aplica) — si la varianza de δ\* alcanza la cota de Cramér-Rao, confirmación extra de que es MVUE

---

## Resumen

| Concepto | Fórmula | Intuición |
|---|---|---|
| Suficiencia | $f(\mathbf{x};\theta) = g(T,\theta) \cdot h(\mathbf{x})$ | "T captura toda la info sobre θ" |
| Rao-Blackwell | $\delta^{*} = E[\delta \mid T]$ | "Condicionar sobre T elimina ruido" |
| Mejora de varianza | $\text{Var}(\delta^{*}) \leq \text{Var}(\delta)$ | "Nunca empeoras, casi siempre mejoras" |
| Completitud | $E[g(T)] = 0 \;\forall\theta \Rightarrow g = 0$ | "No hay funciones ocultas de T" |
| Lehmann-Scheffé | T suf. + completo → δ\* es MVUE | "El combo definitivo para encontrar el MVUE" |
