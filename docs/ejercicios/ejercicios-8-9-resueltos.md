# Ejercicios 8–9 Resueltos — Densidad Potencia y Transformación Y = -ln(X)

*Estos dos ejercicios están conectados. El 9 retoma el 8 desde otro ángulo.*

---

## Conceptos previos

### La distribución del ejercicio

X es una variable continua en (0, 1) con densidad:

$$f(x; \theta) = \theta x^{\theta - 1}, \quad 0 < x < 1, \quad \theta > 0$$

¿Cómo se ve? Si θ = 1, es Uniforme(0,1). Si θ > 1, la densidad crece (más probable estar cerca de 1). Si θ < 1, la densidad decrece (más probable estar cerca de 0).

### ¿Qué es una estadística suficiente?

Es una función de la muestra que **captura toda la información** sobre θ. Después de observarla, los datos ya no te dicen nada nuevo sobre θ. Se verifica con el **Teorema de Factorización** (Fisher-Neyman):

$$f(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

Si puedes factorizar la densidad conjunta en un pedazo que depende de θ solo a través de T, y otro que no depende de θ, entonces T es suficiente.

### ¿Qué es la CICR?

La **Cota Inferior de Cramér-Rao** es la menor varianza posible para un estimador insesgado:

$$\text{CICR}(\theta) = \frac{1}{n \cdot I(\theta)}$$

donde $I(\theta) = E\left[\left(\frac{\partial}{\partial\theta}\ln f(X;\theta)\right)^2\right]$

---

# Ejercicio 8

## Parte a) ¿Σ Xᵢ es suficiente para θ?

### Paso 1: Escribir la densidad conjunta

$$f(x^{(n)}; \theta) = \prod_{i=1}^{n} \theta x_i^{\theta-1} = \theta^n \prod_{i=1}^{n} x_i^{\theta-1}$$

### Paso 2: Intentar factorizar con T = Σ Xᵢ

$$f(x^{(n)}; \theta) = \theta^n \cdot \exp\left[(\theta-1) \sum_{i=1}^{n} \ln x_i\right]$$

Observa: la parte que depende de θ involucra **Σ ln Xᵢ**, no Σ Xᵢ.

### Paso 3: Conclusión

Podemos factorizar como:

$$f(x^{(n)}; \theta) = \underbrace{\theta^n \exp\left[(\theta-1)\sum \ln x_i\right]}_{g(\sum \ln x_i;\; \theta)} \cdot \underbrace{1}_{h(x^{(n)})}$$

La estadística suficiente es **T = Σ ln Xᵢ** (o equivalentemente, Π Xᵢ), **no** Σ Xᵢ.

$$\boxed{\text{No. } \sum X_i \text{ NO es suficiente para } \theta. \text{ La suficiente es } \sum \ln X_i.}$$

**¿Por qué no?** Σ Xᵢ pierde información. Dos muestras distintas pueden tener la misma suma pero diferente producto, y la densidad de una sería diferente de la otra para un mismo θ. En cambio, Σ ln Xᵢ captura todo.

---

## Parte b) Encontrar la CICR(θ)

### Paso 1: Calcular ln f(X; θ)

$$\ln f(X; \theta) = \ln \theta + (\theta - 1) \ln X$$

### Paso 2: Derivar respecto a θ

$$\frac{\partial}{\partial \theta} \ln f(X; \theta) = \frac{1}{\theta} + \ln X$$

### Paso 3: Calcular I(θ)

$$I(\theta) = E\left[\left(\frac{1}{\theta} + \ln X\right)^2\right]$$

Necesitamos E[ln X] y E[(ln X)²]. Primero calculemos E[ln X]:

$$E[\ln X] = \int_0^1 \ln x \cdot \theta x^{\theta-1} dx$$

Sustitución: sea $u = -\ln x$, entonces $x = e^{-u}$, $dx = -e^{-u}du$. Cuando x=0, u→∞; cuando x=1, u=0:

$$E[\ln X] = \int_{\infty}^{0} (-u) \cdot \theta e^{-u(\theta-1)} \cdot (-e^{-u}) du = -\theta \int_0^{\infty} u \cdot e^{-\theta u} du$$

$$= -\theta \cdot \frac{1}{\theta^2} = -\frac{1}{\theta}$$

Ahora E[(ln X)²]:

$$E[(\ln X)^2] = \theta \int_0^{\infty} u^2 e^{-\theta u} du = \theta \cdot \frac{2}{\theta^3} = \frac{2}{\theta^2}$$

### Paso 4: Juntar todo

$$I(\theta) = E\left[\frac{1}{\theta^2} + \frac{2}{\theta}\ln X + (\ln X)^2\right]$$

$$= \frac{1}{\theta^2} + \frac{2}{\theta} \cdot \left(-\frac{1}{\theta}\right) + \frac{2}{\theta^2} = \frac{1}{\theta^2} - \frac{2}{\theta^2} + \frac{2}{\theta^2} = \frac{1}{\theta^2}$$

$$\boxed{I(\theta) = \frac{1}{\theta^2} \qquad \Longrightarrow \qquad \text{CICR}(\theta) = \frac{1}{n/\theta^2} = \frac{\theta^2}{n}}$$

---

## Parte c) ¿Existe un estimador insesgado que alcance la CICR(θ)?

Un estimador alcanza la CICR si y solo si se puede escribir como función lineal del Score:

$$\hat{\theta} = a(\theta) \cdot S(\theta) + b(\theta)$$

El Score total de la muestra es:

$$S(\theta) = \sum_{i=1}^{n}\left(\frac{1}{\theta} + \ln X_i\right) = \frac{n}{\theta} + \sum_{i=1}^{n} \ln X_i$$

Para que un estimador **insesgado** de θ alcance la cota, necesitaríamos que S(θ) sea función lineal de θ̂. Pero S(θ) contiene el término n/θ que depende de θ, y θ̂ no puede depender de θ (es una estadística). Verifiquemos más formalmente.

La condición de igualdad es: $\frac{\partial}{\partial\theta}\ln L = k(\theta)[\hat{\theta} - \theta]$ para alguna función k(θ).

$$\frac{n}{\theta} + \sum \ln X_i = k(\theta)\left[\hat{\theta} - \theta\right]$$

Si θ̂ no depende de θ, el lado derecho es lineal en θ̂. El lado izquierdo tiene n/θ que no es lineal en ninguna estadística. No se puede acomodar.

$$\boxed{\text{No existe un estimador insesgado de } \theta \text{ que alcance la CICR}(\theta)}$$

---

## Parte d) ¿Existe φ(θ) para la que sí se alcance?

Buscamos φ(θ) tal que:

$$\frac{\partial}{\partial\theta}\ln L = k(\theta)[\hat{\varphi} - \varphi(\theta)]$$

Es decir:

$$\frac{n}{\theta} + \sum \ln X_i = k(\theta)\left[\hat{\varphi} - \varphi(\theta)\right]$$

Reorganizamos. Si elegimos $\hat{\varphi} = -\frac{1}{n}\sum \ln X_i$ (una estadística que no depende de θ), necesitamos:

$$\frac{n}{\theta} + \sum \ln X_i = k(\theta)\left[-\frac{1}{n}\sum \ln X_i - \varphi(\theta)\right]$$

Probemos con k(θ) = -n y veamos qué pasa:

$$\frac{n}{\theta} + \sum \ln X_i = -n\left[-\frac{1}{n}\sum \ln X_i - \varphi(\theta)\right] = \sum \ln X_i + n\varphi(\theta)$$

Simplificando: $n/\theta = n\varphi(\theta)$, así que $\varphi(\theta) = 1/\theta$.

**Verificación:** con φ(θ) = 1/θ y φ̂ = -Σ ln Xᵢ/n:

$$E[\hat{\varphi}] = -\frac{1}{n}\sum E[\ln X_i] = -\frac{1}{n} \cdot n \cdot \left(-\frac{1}{\theta}\right) = \frac{1}{\theta} = \varphi(\theta) \quad \checkmark$$

Y la CICR para φ(θ) = 1/θ:

$$\text{CICR}(\varphi) = \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)} = \frac{(-1/\theta^2)^2}{n/\theta^2} = \frac{1/\theta^4}{n/\theta^2} = \frac{1}{n\theta^2}$$

$$\text{Var}(\hat{\varphi}) = \text{Var}\left(-\frac{1}{n}\sum \ln X_i\right) = \frac{1}{n^2}\sum\text{Var}(\ln X_i) = \frac{1}{n^2} \cdot n \cdot \frac{1}{\theta^2} = \frac{1}{n\theta^2} \quad \checkmark$$

$$\boxed{\varphi(\theta) = \frac{1}{\theta}, \quad \hat{\varphi} = -\frac{1}{n}\sum_{i=1}^{n}\ln X_i \quad \text{alcanza la CICR (es MVUE)}}$$

---

# Ejercicio 9 — Transformación Y = -ln(X)

## Parte a) Distribución de Y

Si X tiene densidad f(x; θ) = θx^(θ-1) en (0,1), y definimos Y = -ln(X):

### Método del Jacobiano

Como y = -ln(x), entonces x = e⁻ʸ y |dx/dy| = e⁻ʸ.

Además, cuando x ∈ (0,1), y ∈ (0, ∞).

$$f_Y(y) = f_X(e^{-y}) \cdot |dx/dy| = \theta(e^{-y})^{\theta-1} \cdot e^{-y} = \theta e^{-\theta y}$$

$$\boxed{f_Y(y) = \theta e^{-\theta y}, \quad y > 0}$$

**¡Y tiene distribución Exponencial con parámetro 1/θ!** (O sea, E[Y] = 1/θ y Var(Y) = 1/θ².)

---

## Parte b) Estadística suficiente para θ en el modelo de Y

La densidad conjunta de Y₁, ..., Yₙ (donde Yᵢ = -ln Xᵢ) es:

$$f_{Y^{(n)}}(y^{(n)}; \theta) = \prod_{i=1}^n \theta e^{-\theta y_i} = \theta^n \exp\left(-\theta \sum_{i=1}^n y_i\right)$$

Por el Teorema de Factorización:

$$= \underbrace{\theta^n \exp\left(-\theta \sum y_i\right)}_{g(\sum y_i;\; \theta)} \cdot \underbrace{1}_{h(y^{(n)})}$$

$$\boxed{T = \sum_{i=1}^{n} Y_i = -\sum_{i=1}^{n} \ln X_i \text{ es suficiente para } \theta}$$

Esto es consistente con el Ejercicio 8: Σ ln Xᵢ era suficiente allá, y aquí Σ Yᵢ = -Σ ln Xᵢ es suficiente.

---

## Parte c) Estimador insesgado para E(Y)

Sabemos que $E[Y] = 1/\theta$. Si reparametrizamos con $h(\theta) = E[Y] = 1/\theta$, un estimador insesgado natural es:

$$\hat{h} = \bar{Y} = \frac{1}{n}\sum_{i=1}^{n} Y_i = -\frac{1}{n}\sum_{i=1}^{n}\ln X_i$$

Verificación:

$$E[\bar{Y}] = E[Y] = \frac{1}{\theta} = h(\theta) \quad \checkmark$$

$$\boxed{\hat{h} = \bar{Y} = -\frac{1}{n}\sum \ln X_i \text{ es insesgado para } E[Y] = 1/\theta}$$

---

## Parte d) CICR para E(Y)

### Opción 1: Calcular directamente en el modelo de Y

Y ∼ Exponencial(1/θ), así que su densidad es f(y;θ) = θe^(-θy).

$$\ln f(Y;\theta) = \ln\theta - \theta Y$$

$$\frac{\partial}{\partial\theta}\ln f = \frac{1}{\theta} - Y$$

$$I_Y(\theta) = E\left[\left(\frac{1}{\theta} - Y\right)^2\right] = \text{Var}(Y) = \frac{1}{\theta^2}$$

Con h(θ) = 1/θ, h'(θ) = -1/θ²:

$$\text{CICR}(h) = \frac{[h'(\theta)]^2}{n \cdot I_Y(\theta)} = \frac{1/\theta^4}{n/\theta^2} = \frac{1}{n\theta^2}$$

### Opción 2: Verificar que Ȳ alcanza la CICR

$$\text{Var}(\bar{Y}) = \frac{\text{Var}(Y)}{n} = \frac{1}{n\theta^2}$$

$$\boxed{\text{Var}(\bar{Y}) = \frac{1}{n\theta^2} = \text{CICR}(h) \quad \Longrightarrow \quad \bar{Y} \text{ es MVUE para } 1/\theta}$$

---

## Parte e) Relación con el Ejercicio 8

| Aspecto | Ejercicio 8 (modelo X) | Ejercicio 9 (modelo Y) |
|---|---|---|
| Variable | X ∈ (0,1) | Y = -ln(X) ∈ (0,∞) |
| Densidad | θx^(θ-1) | θe^(-θy) (Exponencial) |
| Suficiente | Σ ln Xᵢ | Σ Yᵢ = -Σ ln Xᵢ |
| CICR(θ) | θ²/n | θ²/n |
| ¿MVUE para θ? | No existe | No existe |
| ¿MVUE para 1/θ? | Sí: -Σ ln Xᵢ/n | Sí: Ȳ = Σ Yᵢ/n |

**Son el mismo problema visto desde dos ángulos.** La transformación Y = -ln(X) convierte la densidad potencia en una Exponencial, que es más fácil de trabajar. Pero la información estadística es la misma:

- La estadística suficiente es la misma (solo cambia de signo)
- La CICR es la misma
- El MVUE es el mismo estimador escrito en diferentes variables
- En ambos modelos, θ no tiene MVUE, pero 1/θ sí

**Lección importante:** A veces una transformación inteligente convierte un problema difícil en uno fácil (la Exponencial es mucho más manejable que la densidad potencia).
