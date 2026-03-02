# Clase 5: Error de Estimación, ECM y Consistencia

**Capítulo II.2 – II.3**

---

## Cuantificación Probabilística del Error

Aunque el error e = θ̂ - θ no se puede calcular, la variable aleatoria ε tiene distribución **totalmente conocida**.

$$P(|\varepsilon| > c) = 1 - P(-c \leq \varepsilon \leq c)$$

Para el modelo Normal: estandarizando,

$$q = 2 \cdot \Phi\left(-\frac{\sqrt{n}}{\sigma} \cdot c\right)$$

La relación entre c (margen de error) y q (probabilidad de excederlo) es **inversa**: a mayor margen c, menor probabilidad q.

### Ejemplo: Relación c-q (n=10, σ=0.1)

| Margen de error c | Probabilidad q de excederlo |
|---|---|
| 8 cm | 1.1% |
| 5 cm | 11.4% |
| 3 cm | 34.3% |
| 1 cm | 75.2% |

---

## Definiciones Formales

### Definición 2.1 — Estadística
Una **estadística** es una función de la muestra aleatoria X⁽ⁿ⁾ que toma valores en ℝᵏ y cuya regla de correspondencia **no involucra cantidades desconocidas**.

### Definición 2.2 — Estimador
Un **estimador o función estimadora** es una estadística que toma valores en el espacio paramétrico de θ.

### Definición 2.3 — Distribución Muestral
La función de distribución de una variable aleatoria que se obtiene como función de la m.a. X⁽ⁿ⁾.

### Definición 2.4 — Valor Estimado
El valor observado de un estimador.

### Definición 2.5 — Error de Estimación
Variable aleatoria que se calcula como la diferencia entre un estimador y el parámetro: ε = θ̂(X⁽ⁿ⁾) - θ. Es una **v.a. no observable**.

### Definición 2.6 — Insesgamiento
θ̂ es **insesgado** para θ si E[θ̂] = θ, para todo valor de θ.

### Definición 2.7 — Sesgo
$$\text{Sesgo}(\hat{\theta}) = E[\hat{\theta}] - \theta$$

- Sesgo positivo ⟹ sobreestima (en promedio)
- Sesgo negativo ⟹ subestima (en promedio)
- Insesgado ⟹ Sesgo = 0

### Definición 2.8 — Error Cuadrático Medio (ECM)
$$\text{ECM}(\hat{\theta}) = E[(\hat{\theta} - \theta)^2]$$

---

## Relación Fundamental del ECM

$$\boxed{\text{ECM}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Sesgo}(\hat{\theta})]^2}$$

**Demostración:**

$$\text{ECM} = E[(\hat{\theta} - \theta)^2] = E[(\hat{\theta} - E[\hat{\theta}] + E[\hat{\theta}] - \theta)^2]$$

$$= E[(\hat{\theta} - E[\hat{\theta}])^2] + 2 \cdot \underbrace{E[\hat{\theta} - E[\hat{\theta}]]}_{= 0} \cdot (E[\hat{\theta}] - \theta) + (E[\hat{\theta}] - \theta)^2$$

$$= \text{Var}(\hat{\theta}) + [\text{Sesgo}(\hat{\theta})]^2$$

**Caso particular:** Si θ̂ es insesgado, entonces ECM(θ̂) = Var(θ̂).

---

## Para X̄ del modelo Normal

- E[X̄] = μ (insesgado)
- Var(X̄) = σ²/n
- ECM(X̄) = σ²/n
- El ECM aumenta con σ² y disminuye con n
- Si n se multiplica por k, el ECM se divide por k

---

## Ideas Importantes

- **Insesgamiento** no garantiza que los valores estén CERCA del parámetro; solo que están ALREDEDOR de él.
- Un estimador **sesgado** con varianza muy pequeña puede ser preferible a uno insesgado con varianza grande.
- **Consistencia:** Al aumentar n, el ECM disminuye y la descripción se vuelve exacta.
