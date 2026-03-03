# 3.4 Estimadores insesgados de mínima varianza (MVUE), Cramér–Rao y Rao–Blackwell–Lehmann–Scheffé

## 1) Marco: ¿qué problema resuelven estos teoremas?

Dado un modelo estadístico de la forma `f(x; θ)` y una cantidad objetivo `τ(θ)`, buscamos un estimador `δ(X)` que sea:

1. **Insesgado**: `Eθ[δ(X)] = τ(θ)` para todo `θ` en `Θ`.
2. De **varianza mínima** dentro de la clase de estimadores insesgados.

Ese estimador se llama **MVUE** (*Minimum Variance Unbiased Estimator*).

---

## 2) Teorema de Cramér–Rao (uniparametral)

Sea `X1, ..., Xn` una muestra aleatoria i.i.d. de una familia uniparametral regular `f(x; θ)`, con `θ ∈ Θ ⊂ R`.
Si `δ(X)` es insesgado para `τ(θ)` y se cumplen condiciones de regularidad (derivar bajo el signo integral, soporte no dependiente de `θ`, etc.), entonces:

`Varθ(δ) ≥ [τ'(θ)]² / (n I(θ))`

Donde la **información de Fisher por observación** es:

- `I(θ) = Eθ[(∂/∂θ log f(X; θ))²]`
- `I(θ) = -Eθ[∂²/∂θ² log f(X; θ)]`

Caso particular `τ(θ) = θ`:

`Varθ(θ̂) ≥ 1 / (n I(θ))`

### Cuándo se alcanza la igualdad

La igualdad (eficiencia) ocurre si existe una función `a(θ)` tal que, casi seguramente:

`δ(X) - τ(θ) = a(θ) * ∂/∂θ log L(θ; X)`

con `L(θ; X)` la verosimilitud muestral.

### Cómo se usa en ejercicios

1. Identificar `τ(θ)`.
2. Calcular `I(θ)`.
3. Construir la cota de Cramér–Rao.
4. Comparar `Var(δ)` contra la cota para concluir eficiencia/no eficiencia.

---

## 3) Información de Fisher en el caso normal biparametral

Si `Xi ~ N(μ, σ²)` i.i.d. y ambos parámetros son desconocidos, con `η = (μ, σ²)`, la información de Fisher muestral es:

`I_n(η) = n * [[1/σ², 0], [0, 1/(2σ⁴)]]`

La versión multivariada de Cramér–Rao establece, para estimadores insesgados vectoriales:

`Covη(η̂) - I_n(η)^(-1) ⪰ 0`

(es decir, la diferencia es semidefinida positiva).

### Lectura práctica

- Cota para `Var(μ̂)`: al menos `σ² / n`.
- Cota para `Var(σ̂²)`: al menos `2σ⁴ / n`.
- Útil para comparar precisión teórica de procedimientos de estimación.

---

## 4) Teorema de Rao–Blackwell

Sea `δ0(X)` un estimador insesgado de `τ(θ)` con varianza finita y sea `T(X)` suficiente para `θ`.
Defina:

`δ1(X) = E[δ0(X) | T(X)]`

Entonces:

1. `δ1` es función de `T` (por tanto, estadística).
2. `δ1` es insesgado para `τ(θ)`.
3. `Var(δ1) ≤ Var(δ0)`.

### Uso operativo

- Arrancas con un insesgado sencillo `δ0`.
- Condicionas sobre una suficiente `T`.
- Obtienes automáticamente un insesgado con varianza no mayor.

---

## 5) Teorema de Lehmann–Scheffé

Si `T(X)` es **completa y suficiente** para `θ`, y `g(T)` es insesgado para `τ(θ)`, entonces `g(T)` es el **único MVUE** de `τ(θ)`.

### Definiciones formales relevantes

- **Suficiencia**: la distribución condicional de la muestra dado `T = t` no depende de `θ`.
- **Completitud**: si para toda función medible `h`, se cumple `Eθ[h(T)] = 0` para todo `θ`, entonces `h(T) = 0` casi seguramente.
- **Suficiencia minimal**: `T` es suficiente y cualquier otra suficiente `S` determina a `T` (existe `u` tal que `T = u(S)`, casi seguramente).

### Uso operativo

1. Hallar una suficiente (típicamente por factorización de Fisher–Neyman).
2. Establecer minimalidad/completitud cuando aplique.
3. Construir un insesgado de la forma `g(T)`.
4. Invocar Lehmann–Scheffé para concluir MVUE y unicidad.

---

## 6) Flujo rápido para problemas tipo examen

1. **“Piden cota o eficiencia”** → Cramér–Rao.
2. **“Tengo un insesgado + suficiente”** → Rao–Blackwell.
3. **“Además la suficiente es completa”** → Lehmann–Scheffé (MVUE único).
4. **“Modelo con dos parámetros (ej. Normal μ, σ²)”** → usar Fisher matricial y Cramér–Rao multivariado.
