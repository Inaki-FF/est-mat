# Cota Inferior de Cramér-Rao — Desde Cero

---

## ¿Qué problema resuelve?

Ya sabes que un estimador insesgado "apunta" al valor correcto en promedio. Pero hay infinitos estimadores insesgados. ¿Cómo sabes si el tuyo es bueno? ¿Existe alguno con varianza más chiquita?

La CICR responde: **hay un piso. Ningún estimador insesgado puede tener varianza menor que este número.**

$$\boxed{\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot I(\theta)}}$$

Si tu estimador alcanza ese piso, es el **mejor posible** (MVUE). Si no lo alcanza, puede que exista uno mejor.

---

## ¿Qué es I(θ)? La Información de Fisher

Imagina que observas un dato X. ¿Cuánto te "dice" ese dato sobre θ? Eso es la Información de Fisher:

$$I(\theta) = E\left[\left(\frac{\partial}{\partial\theta}\ln f(X;\theta)\right)^2\right]$$

Desmenucemos esto:

1. **f(X; θ)** — la densidad de X, que depende de θ
2. **ln f(X; θ)** — le sacas logaritmo (más fácil de trabajar)
3. **∂/∂θ ln f** — derivas respecto a θ. Esto se llama **Score**. Mide qué tan sensible es la densidad a cambios en θ
4. **Elevas al cuadrado** — para que no se cancelen los positivos y negativos
5. **Tomas esperanza** — promedias sobre todas las posibles X

**Intuición:** Si cambiar un poquito θ cambia mucho la forma de f, entonces los datos son muy informativos sobre θ → I(θ) grande → CICR chica → puedes estimar con precisión.

### Expresión alternativa (más fácil de calcular)

$$I(\theta) = -E\left[\frac{\partial^2}{\partial\theta^2}\ln f(X;\theta)\right]$$

La segunda derivada mide la "curvatura" del logaritmo de la densidad. Más curvatura = más información.

---

## Ejemplo completo: Bernoulli(θ)

X vale 1 con probabilidad θ, y 0 con probabilidad 1-θ.

### Paso 1: ln f

$$f(x;\theta) = \theta^x(1-\theta)^{1-x} \implies \ln f = x\ln\theta + (1-x)\ln(1-\theta)$$

### Paso 2: Score (primera derivada)

$$\frac{\partial}{\partial\theta}\ln f = \frac{x}{\theta} - \frac{1-x}{1-\theta}$$

### Paso 3: Información de Fisher (segunda derivada, más fácil)

$$\frac{\partial^2}{\partial\theta^2}\ln f = -\frac{x}{\theta^2} - \frac{1-x}{(1-\theta)^2}$$

$$I(\theta) = -E\left[-\frac{X}{\theta^2} - \frac{1-X}{(1-\theta)^2}\right] = \frac{E[X]}{\theta^2} + \frac{1-E[X]}{(1-\theta)^2} = \frac{1}{\theta} + \frac{1}{1-\theta} = \frac{1}{\theta(1-\theta)}$$

### Paso 4: La CICR

$$\text{CICR}(\theta) = \frac{1}{n \cdot I(\theta)} = \frac{\theta(1-\theta)}{n}$$

### Paso 5: ¿X̄ la alcanza?

$$\text{Var}(\bar{X}) = \frac{\theta(1-\theta)}{n} = \text{CICR}$$

**Sí. X̄ es MVUE para θ en el modelo Bernoulli.**

---

## ¿Cuándo NO aplica?

La CICR necesita **condiciones de regularidad**:
- Puedes intercambiar derivada con integral (la densidad es "suave")
- El **soporte no depende de θ**

Por eso **no aplica para Uniforme(0, θ)** — ahí el soporte (0, θ) cambia con θ. Y de hecho, para la Uniforme existen estimadores con varianza de orden n⁻² (como el máximo corregido), que sería menor que cualquier CICR de orden n⁻¹. La cota simplemente no es válida ahí.

---

## Versión para φ(θ) (Ejercicio 7)

Si en lugar de θ quieres estimar φ = φ(θ):

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$$

El factor φ'(θ)² aparece porque estimar una función de θ puede ser más fácil o más difícil que estimar θ directamente. Si φ cambia lento (φ' chico), la cota baja. Si cambia rápido (φ' grande), la cota sube.

---

## Resumen

| Concepto | Fórmula | Intuición |
|---|---|---|
| Score | $\frac{\partial}{\partial\theta}\ln f(X;\theta)$ | "¿Cuánto cambia la densidad si muevo θ?" |
| Info de Fisher | $I(\theta) = E[\text{Score}^2]$ | "¿Qué tan informativo es un dato?" |
| CICR | $\frac{1}{n \cdot I(\theta)}$ | "El piso de varianza para cualquier estimador insesgado" |
| MVUE | Alcanza la CICR | "El mejor estimador insesgado posible" |
| CICR para φ(θ) | $\frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$ | "El piso ajustado por la velocidad de cambio de φ" |
| No aplica cuando... | Soporte depende de θ | Uniforme(0,θ), distribuciones truncadas, etc. |
