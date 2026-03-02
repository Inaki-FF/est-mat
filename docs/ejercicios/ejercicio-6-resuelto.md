# Ejercicio 6 Resuelto — Área del círculo con error Normal

*Explicado desde cero.*

---

## Enunciado

Cada vez que mides el radio r de un círculo, cometes un error de medición que se distribuye N(0, σ²). Tienes n mediciones independientes del radio. Proponga un estimador **insesgado del área** del círculo.

## ¿Qué está pasando?

El círculo tiene un radio verdadero **r** (desconocido, fijo). Cada vez que lo mides, obtienes:

$$X_i = r + \varepsilon_i$$

donde εᵢ ∼ N(0, σ²) es el error. Entonces cada medición Xᵢ se distribuye:

$$X_i \sim N(r, \sigma^2)$$

El **área** del círculo es $A = \pi r^2$. Queremos estimar **A**, no r.

## El problema con el estimador "obvio"

Tu primer instinto sería: "Estimo r con X̄, y luego el área con π X̄²". Veamos si funciona:

$$E[\pi \bar{X}^2] = \pi E[\bar{X}^2]$$

Ahora, hay un truco fundamental. Recordemos que para cualquier variable aleatoria:

$$E[Z^2] = \text{Var}(Z) + (E[Z])^2$$

Aplicamos esto a X̄, que sabemos tiene $E[\bar{X}] = r$ y $\text{Var}(\bar{X}) = \sigma^2/n$:

$$E[\bar{X}^2] = \frac{\sigma^2}{n} + r^2$$

Entonces:

$$E[\pi \bar{X}^2] = \pi\left(\frac{\sigma^2}{n} + r^2\right) = \pi r^2 + \frac{\pi \sigma^2}{n}$$

**No es insesgado.** Sobreestima el área por $\pi\sigma^2/n$. El sesgo viene de que "el cuadrado del promedio no es el promedio del cuadrado".

## El estimador insesgado correcto

Para corregir, restamos el sesgo:

$$\hat{A} = \pi \bar{X}^2 - \frac{\pi \sigma^2}{n}$$

$$\boxed{\hat{A} = \pi\left(\bar{X}^2 - \frac{\sigma^2}{n}\right)}$$

Verificación:

$$E[\hat{A}] = \pi\left(E[\bar{X}^2] - \frac{\sigma^2}{n}\right) = \pi\left(\frac{\sigma^2}{n} + r^2 - \frac{\sigma^2}{n}\right) = \pi r^2 = A \quad \checkmark$$

## ¿Es válido este estimador?

Hay un detalle: $\hat{A}$ podría dar valores **negativos** si X̄² < σ²/n. Esto es conceptualmente extraño (¿un área negativa?) pero matemáticamente el estimador sigue siendo insesgado. En la práctica, si n es grande y r no es cercano a 0, la probabilidad de que esto ocurra es despreciable.

## ¿Qué podemos decir de su varianza?

$$\text{Var}(\hat{A}) = \pi^2 \text{Var}(\bar{X}^2)$$

Para calcular Var(X̄²), necesitamos E[X̄⁴]. Como X̄ ∼ N(r, σ²/n), podemos usar los momentos de la Normal. Para Z ∼ N(μ, τ²):

$$E[Z^4] = \mu^4 + 6\mu^2\tau^2 + 3\tau^4$$

Con μ = r y τ² = σ²/n:

$$E[\bar{X}^4] = r^4 + 6r^2 \frac{\sigma^2}{n} + 3\frac{\sigma^4}{n^2}$$

$$(E[\bar{X}^2])^2 = \left(r^2 + \frac{\sigma^2}{n}\right)^2 = r^4 + 2r^2\frac{\sigma^2}{n} + \frac{\sigma^4}{n^2}$$

$$\text{Var}(\bar{X}^2) = 4r^2\frac{\sigma^2}{n} + 2\frac{\sigma^4}{n^2}$$

Finalmente:

$$\boxed{\text{Var}(\hat{A}) = \pi^2\left(\frac{4r^2\sigma^2}{n} + \frac{2\sigma^4}{n^2}\right)}$$

**Observaciones:**
- La varianza depende de r (desconocido), así que no la podemos calcular exactamente
- Cuando n → ∞, Var(Â) → 0, así que el estimador es **consistente**
- El término dominante es $4\pi^2 r^2\sigma^2/n$, que decrece como 1/n
