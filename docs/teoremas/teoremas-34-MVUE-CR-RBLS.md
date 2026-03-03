# 3.4 Estimadores insesgados de mínima varianza

## 1) ¿Qué es un estimador insesgado de mínima varianza (MVUE)?

Para un parámetro (o función del parámetro) \(\tau(\theta)\), un estimador \(\hat\tau\) es **MVUE** si:

1. Es insesgado: \(\mathbb{E}_\theta[\hat\tau]=\tau(\theta)\) para todo \(\theta\).
2. Tiene varianza mínima entre todos los estimadores insesgados de \(\tau(\theta)\).

---

## 2) Teorema de Cramér–Rao (caso uniparametral)

Sea \(X_1,\dots,X_n\) una m.a. con densidad/masa \(f(x;\theta)\), \(\theta\in\Theta\subset\mathbb{R}\), y suponga condiciones de regularidad. Si \(\hat\tau\) es insesgado para \(\tau(\theta)\), entonces:

\[
\mathrm{Var}_\theta(\hat\tau)\;\ge\;\frac{[\tau'(\theta)]^2}{nI(\theta)},
\]

con información de Fisher uniparametral:

\[
I(\theta)=\mathbb{E}_\theta\!\left[\left(\frac{\partial}{\partial\theta}\log f(X;\theta)\right)^2\right]
= -\mathbb{E}_\theta\!\left[\frac{\partial^2}{\partial\theta^2}\log f(X;\theta)\right].
\]

En particular, para \(\tau(\theta)=\theta\):

\[
\mathrm{Var}_\theta(\hat\theta)\ge \frac{1}{nI(\theta)}.
\]

### ¿Cómo se usa en ejercicios?

1. Identificar qué parámetro (o función \(\tau(\theta)\)) se estima.
2. Calcular \(I(\theta)\).
3. Construir la cota \(\frac{[\tau'(\theta)]^2}{nI(\theta)}\).
4. Si un estimador insesgado alcanza la cota, es eficiente (y candidato a MVUE).

---

## 3) Información de Fisher en el caso normal biparametral

Si \(X_i\sim\mathcal N(\mu,\sigma^2)\) i.i.d. y ambos parámetros son desconocidos, el parámetro es vectorial
\(\eta=(\mu,\sigma^2)\). La información de Fisher es matricial:

\[
\mathcal I_n(\eta)=n\begin{pmatrix}
\frac{1}{\sigma^2} & 0\\
0 & \frac{1}{2\sigma^4}
\end{pmatrix}.
\]

La versión multivariada de Cramér–Rao dice que la matriz de covarianzas de cualquier estimador insesgado vectorial está acotada inferiormente por \(\mathcal I_n(\eta)^{-1}\) (en orden semidefinido positivo).

### ¿Cómo se usa en práctica?

- Para evaluar precisión mínima teórica de \(\hat\mu\), \(\widehat{\sigma^2}\), o combinaciones lineales.
- Para justificar eficiencia asintótica de estimadores y comparar métodos.

---

## 4) Teorema de Rao–Blackwell

Sea \(\hat\tau_0\) un estimador insesgado de \(\tau(\theta)\) con varianza finita y sea \(T\) suficiente para \(\theta\). Defina:

\[
\hat\tau_1=\mathbb E[\hat\tau_0\mid T].
\]

Entonces:

1. \(\hat\tau_1\) es estimador de \(\tau(\theta)\).
2. \(\hat\tau_1\) es insesgado.
3. \(\mathrm{Var}(\hat\tau_1)\le \mathrm{Var}(\hat\tau_0)\).

### ¿Cómo se usa?

- Se parte de un insesgado “fácil”.
- Se condiciona en una estadística suficiente.
- Se obtiene automáticamente un estimador no peor en varianza.

---

## 5) Teorema de Lehmann–Scheffé

Si \(T\) es **completa y suficiente** para \(\theta\), y \(g(T)\) es insesgado para \(\tau(\theta)\), entonces \(g(T)\) es el **único MVUE** de \(\tau(\theta)\).

### ¿Qué significan “completa” y “suficiencia minimal”?

- **Suficiente:** \(T\) concentra toda la información sobre \(\theta\).
- **Minimal suficiente:** es suficiente y cualquier otra suficiente lo contiene funcionalmente.
- **Completa:** si \(\mathbb E_\theta[h(T)]=0\) para todo \(\theta\), entonces \(h(T)=0\) casi seguro.

### ¿Cómo se usa en ejercicios?

Ruta estándar:

1. Encontrar una estadística suficiente (idealmente minimal) por factorización.
2. Verificar/comentar completitud (en familias exponenciales es frecuente).
3. Construir un insesgado de la forma \(g(T)\).
4. Concluir por Lehmann–Scheffé que es el MVUE único.

---

## 6) Mapa rápido de decisión en problemas de examen

1. ¿Piden “cota”, “eficiencia”, “varianza mínima teórica”?  \(\Rightarrow\) Cramér–Rao.
2. ¿Ya tienes un insesgado y una suficiente?  \(\Rightarrow\) Rao–Blackwell.
3. ¿Además la suficiente es completa?  \(\Rightarrow\) Lehmann–Scheffé (MVUE único).

