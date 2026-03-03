# 3.4 Estimadores insesgados de mínima varianza (MVUE), Cramér–Rao y Rao–Blackwell–Lehmann–Scheffé

## 1) Marco: ¿qué problema resuelven estos teoremas?

Dado un modelo estadístico \(\{f(x;\theta):\theta\in\Theta\}\) y una cantidad objetivo
\(\tau(\theta)\), buscamos un estimador \(\delta(X)\) que sea:

1. **insesgado**: \(\mathbb E_\theta[\delta(X)] = \tau(\theta)\) para todo \(\theta\in\Theta\);
2. de **varianza mínima** dentro de la clase de estimadores insesgados.

Ese estimador se llama **MVUE** (Minimum Variance Unbiased Estimator).

---

## 2) Teorema de Cramér–Rao (uniparametral)

Sea \(X_1,\dots,X_n\) una muestra aleatoria i.i.d. de una familia uniparametral regular
\(f(x;\theta)\), \(\theta\in\Theta\subset\mathbb R\). Si \(\delta(X)\) es insesgado para
\(\tau(\theta)\) y se cumplen las condiciones de regularidad (derivar bajo el signo integral,
soporte no dependiente de \(\theta\), etc.), entonces:

\[
\operatorname{Var}_\theta(\delta)\;\ge\;\frac{[\tau'(\theta)]^2}{nI(\theta)},
\]

donde la **información de Fisher por observación** es

\[
I(\theta)
=\mathbb E_\theta\!\left[\left(\frac{\partial}{\partial\theta}\log f(X;\theta)\right)^2\right]
=-\mathbb E_\theta\!\left[\frac{\partial^2}{\partial\theta^2}\log f(X;\theta)\right].
\]

Caso particular \(\tau(\theta)=\theta\):
\[
\operatorname{Var}_\theta(\hat\theta)\ge\frac{1}{nI(\theta)}.
\]

### Cuándo se alcanza la igualdad

La igualdad (eficiencia) ocurre si existe una función \(a(\theta)\) tal que, c.s.,
\[
\delta(X)-\tau(\theta)
= a(\theta)\,\frac{\partial}{\partial\theta}\log L(\theta;X),
\]
con \(L\) la verosimilitud muestral.

### Cómo se usa en ejercicios

1. Identificar \(\tau(\theta)\).
2. Calcular \(I(\theta)\).
3. Armar la cota de Cramér–Rao.
4. Comparar \(\operatorname{Var}(\delta)\) contra la cota para concluir eficiencia/no eficiencia.

---

## 3) Información de Fisher en el caso normal biparametral

Si \(X_i\sim\mathcal N(\mu,\sigma^2)\) i.i.d. y ambos parámetros son desconocidos, con
\(\eta=(\mu,\sigma^2)\), la información de Fisher muestral es

\[
\mathcal I_n(\eta)
= n\begin{pmatrix}
\sigma^{-2} & 0\\
0 & (2\sigma^{4})^{-1}
\end{pmatrix}.
\]

La versión multivariada de Cramér–Rao establece, para estimadores insesgados vectoriales,
\[
\operatorname{Cov}_\eta(\hat\eta)-\mathcal I_n(\eta)^{-1}\succeq 0,
\]
(es decir, la diferencia es semidefinida positiva).

### Lectura práctica

- Cota para \(\operatorname{Var}(\hat\mu)\): al menos \(\sigma^2/n\).
- Cota para \(\operatorname{Var}(\widehat{\sigma^2})\): al menos \(2\sigma^4/n\).
- Útil para comparar precisión teórica de procedimientos de estimación.

---

## 4) Teorema de Rao–Blackwell

Sea \(\delta_0(X)\) un estimador insesgado de \(\tau(\theta)\) con varianza finita y sea
\(T(X)\) suficiente para \(\theta\). Defina

\[
\delta_1(X) = \mathbb E[\delta_0(X)\mid T(X)].
\]

Entonces:

1. \(\delta_1\) es función de \(T\) (por tanto, estadística).
2. \(\delta_1\) es insesgado para \(\tau(\theta)\).
3. \(\operatorname{Var}(\delta_1)\le \operatorname{Var}(\delta_0)\).

### Uso operativo

- Arrancas con un insesgado sencillo \(\delta_0\).
- Condicionas sobre una suficiente \(T\).
- Obtienes automáticamente un insesgado con varianza no mayor.

---

## 5) Teorema de Lehmann–Scheffé

Si \(T(X)\) es **completa y suficiente** para \(\theta\), y \(g(T)\) es insesgado para
\(\tau(\theta)\), entonces \(g(T)\) es el **único MVUE** de \(\tau(\theta)\).

### Definiciones formales relevantes

- **Suficiencia:** la distribución condicional de la muestra dado \(T=t\) no depende de \(\theta\).
- **Completitud:** si para toda función medible \(h\),
  \(\mathbb E_\theta[h(T)]=0\ \forall\theta\Rightarrow h(T)=0\) c.s.
- **Suficiencia minimal:** \(T\) es suficiente y cualquier otra suficiente \(S\) determina a \(T\)
  (existe \(u\) tal que \(T=u(S)\) c.s.).

### Uso operativo

1. Hallar una suficiente (típicamente por factorización de Fisher–Neyman).
2. Establecer minimalidad/completitud cuando aplique.
3. Construir un insesgado de la forma \(g(T)\).
4. Invocar Lehmann–Scheffé para concluir MVUE y unicidad.

---

## 6) Flujo rápido para problemas tipo examen

1. **“Piden cota o eficiencia”** \(\Rightarrow\) Cramér–Rao.
2. **“Tengo un insesgado + suficiente”** \(\Rightarrow\) Rao–Blackwell.
3. **“Además la suficiente es completa”** \(\Rightarrow\) Lehmann–Scheffé (MVUE único).
4. **“Modelo con dos parámetros (ej. Normal \(\mu,\sigma^2\))”** \(\Rightarrow\) usar Fisher matricial y Cramér–Rao multivariado.

