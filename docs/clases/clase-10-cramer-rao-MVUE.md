# Clase 10: Cota Inferior de Cramér-Rao y MVUE

**Capítulo II.7 – II.8 (50 páginas)**

---

## Parte I: La Cota Inferior de Cramér-Rao (CICR)

### Motivación

Para un estimador insesgado θ̂ de θ, su ECM coincide con su varianza. ¿Existe un **límite inferior** para esta varianza? Sí: la **Cota Inferior de Cramér-Rao**.

### Teorema de Cramér-Rao

Sea X⁽ⁿ⁾ una m.a. de X con f.d.p.g. f(x; θ), y suponga que se cumplen las condiciones de regularidad (intercambio de esperanza y diferenciación). Entonces, para todo estimador insesgado θ̂ de θ:

$$\boxed{\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot E\left[\left(\frac{\partial}{\partial\theta} \ln f(X;\theta)\right)^2\right]} = \text{CICR}(\theta)}$$

### Cuatro expresiones equivalentes de la CICR

$$\text{CICR}(\theta) = \frac{1}{n \cdot I(\theta)}$$

donde la **Información de Fisher** I(θ) puede calcularse de cuatro formas equivalentes:

1. $$I(\theta) = E\left[\left(\frac{\partial}{\partial\theta} \ln f(X;\theta)\right)^2\right]$$

2. $$I(\theta) = -E\left[\frac{\partial^2}{\partial\theta^2} \ln f(X;\theta)\right]$$

3. $$I(\theta) = \frac{1}{n}E\left[\left(\frac{\partial}{\partial\theta} \ln L(\theta; X^{(n)})\right)^2\right]$$

4. $$I(\theta) = -\frac{1}{n}E\left[\frac{\partial^2}{\partial\theta^2} \ln L(\theta; X^{(n)})\right]$$

donde L(θ; X⁽ⁿ⁾) = Πᵢ f(Xᵢ; θ) es la **función de verosimilitud**.

### Demostración (esquema)

Usa la **desigualdad de Cauchy-Schwarz** en la forma:

$$[E(UV)]^2 \leq E(U^2) \cdot E(V^2)$$

con U = θ̂ - θ y V = ∂/∂θ ln L(θ; X⁽ⁿ⁾).

---

## Versión para φ = φ(θ)

Si φ̂ es un estimador insesgado de φ = φ(θ), entonces:

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)} = \text{CICR}(\varphi)$$

---

## Parte II: MVUE — Estimador Insesgado de Varianza Mínima

### Definición

Un estimador θ̂ es **MVUE** (Minimum Variance Unbiased Estimator) si:
1. Es insesgado para θ
2. Su varianza **alcanza** la CICR(θ), es decir: Var(θ̂) = CICR(θ)

### ¿Cuándo se alcanza la CICR?

La igualdad en Cauchy-Schwarz se cumple cuando U y V son proporcionales:

$$\hat{\theta} - \theta = c(\theta) \cdot \frac{\partial}{\partial\theta} \ln L(\theta; X^{(n)})$$

para alguna función c(θ). Esto ocurre en familias exponenciales con parametrización natural.

---

## Cálculo del MVUE en Ejemplos

### Bernoulli(θ)

- f(x; θ) = θˣ(1-θ)¹⁻ˣ
- I(θ) = 1/[θ(1-θ)]
- CICR(θ) = θ(1-θ)/n
- **θ̂ = X̄ tiene Var = θ(1-θ)/n = CICR(θ)** → X̄ es **MVUE** para θ

### Normal(μ, σ²) con σ² conocida

- I(μ) = 1/σ²
- CICR(μ) = σ²/n
- **μ̂ = X̄ tiene Var = σ²/n = CICR(μ)** → X̄ es **MVUE** para μ

### Exponencial(θ) con f(x;θ) = (1/θ)e⁻ˣ/θ

- I(θ) = 1/θ²
- CICR(θ) = θ²/n
- **θ̂ = X̄ tiene Var = θ²/n = CICR(θ)** → X̄ es **MVUE** para θ

---

## Resumen de Criterios de Calidad

| Criterio | ¿Qué mide? |
|---|---|
| Insesgamiento | ¿El estimador está centrado en θ? |
| ECM | ¿Qué tan lejos está del parámetro? (Var + Sesgo²) |
| Consistencia en ECM | ¿Mejora al aumentar n? |
| Suficiencia | ¿Captura toda la información de la muestra? |
| MVUE | ¿Tiene la menor varianza posible entre insesgados? |
