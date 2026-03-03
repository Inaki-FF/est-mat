# Glosario de Conceptos — Estadística Matemática

Referencia rápida de todos los conceptos relevantes de las notas del curso, organizados en el orden en que aparecen.

---

## I. Fundamentos (Clases 1–3)

### Causalidad determinística
A una causa corresponde siempre un mismo efecto. Es la base del conocimiento común, pero **no** describe los fenómenos que estudia la Estadística.

### Fenómeno incierto
Fenómeno que, aun observado en las mismas condiciones, puede producir resultados distintos. La Estadística existe para aprender de estos fenómenos.

### Estadística (la disciplina) — Def. 1.1
Disciplina científica cuyo propósito es **describir fenómenos que se manifiestan a través de datos con variabilidad**. Toda la Estadística es, en esencia, descriptiva.

### Atributo de interés — Def. 1.2
Rasgo a través del cual se busca describir el fenómeno bajo estudio (ej: "estado de salud").

### Variable — Def. 1.3
Codificación numérica específica de un atributo que puede registrarse cada vez que se observa el fenómeno (ej: "presión arterial en mmHg"). Siempre es numérica por definición.

### Dato — Def. 1.4
Resultado específico de la observación de una variable concreta en un caso particular (ej: 120).

### Cadena fundamental
$$\text{Atributos} \;\Rightarrow\; \text{Variables} \;\Rightarrow\; \text{Datos}$$

### Análisis exploratorio de datos
Vertiente de la Estadística que opera cuando se tiene acceso a **todos** los datos (censo). La descripción es exacta.

### Inferencia estadística
Vertiente que opera cuando solo se tiene una **muestra**. La descripción es aproximada y es fundamental cuantificar el grado de aproximación. Es el foco del curso.

### Muestra — Def. 1.5
Fracción observada de los datos de una población.

### Muestreo probabilístico
Método de selección de muestra basado en sorteo aleatorio. Garantiza reproducibilidad y fundamenta la teoría de inferencia. Hito: artículo de Neyman (1934).

### Muestra aleatoria (m.a.) — Def. 1.6
Colección $X^{(n)} = (X_1, X_2, \ldots, X_n)$ de variables aleatorias **independientes e idénticamente distribuidas (i.i.d.)** según la distribución de X. Surge de muestreo aleatorio simple cuando $n \ll N$.

### Función de distribución F(x)
Descripción completa del comportamiento probabilístico de X. Es monótona no decreciente, tiende a 0 en $-\infty$ y a 1 en $+\infty$, y es continua por la derecha.

### Familia paramétrica $\mathcal{F}_\Theta$
Subconjunto de funciones de distribución indexado por un parámetro $\theta \in \Theta \subset \mathbb{R}^k$. Para cada valor fijo de θ, la distribución es totalmente conocida. Reduce un problema de dimensión infinita a optimización en $\mathbb{R}^k$.

### Parámetro θ
Índice que identifica de manera inequívoca a cada elemento de la familia paramétrica. Es la cantidad desconocida que se desea estimar.

### Espacio paramétrico Θ
Conjunto de todos los valores posibles de θ.

### Inferencia paramétrica
Producir inferencias sobre el valor del parámetro desconocido θ a partir de una m.a. Involucra tres preguntas fundamentales:

| Pregunta | Tipo |
|---|---|
| ¿Cuál es el valor de θ? | Estimación puntual |
| ¿Por dónde se localiza θ? | Estimación por intervalos (IC) |
| ¿Son los datos compatibles con una hipótesis sobre θ? | Prueba de hipótesis |

---

## II. Estimación Puntual (Clases 4–7)

### Estadística (función) — Def. 2.1
Función de la muestra aleatoria $X^{(n)}$ que toma valores en $\mathbb{R}^k$ y cuya regla de correspondencia **no involucra cantidades desconocidas**.

### Estimador / función estimadora — Def. 2.2
Estadística que toma valores en el espacio paramétrico de θ. Es decir, una fórmula $\hat{\theta} = T(X_1, \ldots, X_n)$ que produce una aproximación de θ.

### Distribución muestral — Def. 2.3
Función de distribución de una variable aleatoria obtenida como función de la m.a. $X^{(n)}$.

### Valor estimado — Def. 2.4
Valor observado de un estimador: $\hat{\theta} = T(x_1, \ldots, x_n)$.

### Principio de analogía
Método para construir estimadores: identificar el análogo muestral de una cantidad poblacional. Ejemplo: la media muestral $\bar{X}$ como análogo de la media poblacional μ.

### f.d.p.g. (función de densidad de probabilidad generalizada)
Término unificador: se refiere a la función de probabilidad en el caso discreto y a la función de densidad en el caso continuo.

### Error de estimación — Def. 2.5
Variable aleatoria $\varepsilon = \hat{\theta}(X^{(n)}) - \theta$. Es **no observable** (depende del parámetro desconocido), pero su distribución sí se puede describir completamente.

---

## III. Criterios de Calidad (Clases 5–7)

### Insesgamiento — Def. 2.6
$\hat{\theta}$ es **insesgado** para θ si $E[\hat{\theta}] = \theta$ para todo $\theta \in \Theta$.

Analogía: las flechas caen, en promedio, en el centro del blanco. Pero no dice nada sobre la dispersión.

### Sesgo — Def. 2.7
$$\text{Sesgo}(\hat{\theta}) = E[\hat{\theta}] - \theta$$

- Positivo → sobreestima en promedio
- Negativo → subestima en promedio
- Cero → insesgado

### Asintóticamente insesgado
Un estimador sesgado es **asintóticamente insesgado** si $\text{Sesgo}(\hat{\theta}) \to 0$ cuando $n \to \infty$.

### Error Cuadrático Medio (ECM) — Def. 2.8
$$\text{ECM}(\hat{\theta}) = E[(\hat{\theta} - \theta)^2]$$

Mide la distancia cuadrática promedio entre el estimador y el parámetro.

### Relación fundamental del ECM
$$\boxed{\text{ECM}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Sesgo}(\hat{\theta})]^2}$$

Consecuencia clave: un estimador sesgado con varianza pequeña puede tener menor ECM que uno insesgado con varianza grande. Si $\hat{\theta}$ es insesgado, $\text{ECM} = \text{Var}$.

### Consistencia en ECM — Def. 2.9
$\hat{\theta}$ es **consistente en ECM** si $\text{ECM}(\hat{\theta}) \to 0$ cuando $n \to \infty$. Significa que al obtener más datos, el estimador se acerca al valor real.

---

## IV. Suficiencia (Clases 8–9)

### Estadística suficiente (Fisher)
$T(X^{(n)})$ es **suficiente para θ** si la distribución condicional de la muestra dado T no depende de θ:

$$f_{X^{(n)} | T=t}(x^{(n)}) \quad \text{no depende de } \theta$$

**Intuición:** T captura *toda* la información que la muestra contiene sobre θ. Una vez que conoces T, la muestra ya no te dice nada nuevo sobre θ.

### Teorema de equivalencia de suficiencia
Si $T_2 = h(T_1)$ para alguna función h y $T_2$ es suficiente, entonces $T_1$ también es suficiente. Por ejemplo: $\bar{X}$ es suficiente $\iff$ $\sum X_i$ es suficiente.

### Teorema de Factorización de Fisher-Neyman
$T(X^{(n)})$ es suficiente para θ **si y solo si** la densidad conjunta se factoriza como:

$$f_{X^{(n)}}(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

donde **g** depende de la muestra solo a través de T y puede depender de θ, y **h** depende de la muestra pero no de θ. Es la herramienta principal para verificar suficiencia sin calcular distribuciones condicionales.

### Suficiencia conjunta
Cuando hay más de un parámetro desconocido, la estadística suficiente puede ser multidimensional. Ejemplo: en Normal(μ, σ²) con ambos desconocidos, $T = (\sum X_i, \sum X_i^2)$ es suficiente conjunta.

---

## V. Optimalidad: Cramér-Rao y MVUE (Clase 10)

### Score (función score)
$$S(\theta) = \frac{\partial}{\partial\theta}\ln f(X;\theta)$$

Mide qué tan sensible es la densidad a cambios en θ. Si un pequeño cambio en θ altera mucho la forma de f, los datos son muy informativos.

### Información de Fisher $I(\theta)$
$$I(\theta) = E\left[\left(\frac{\partial}{\partial\theta}\ln f(X;\theta)\right)^2\right] = -E\left[\frac{\partial^2}{\partial\theta^2}\ln f(X;\theta)\right]$$

Cuantifica cuánta información aporta **una sola observación** sobre θ. Más información → se puede estimar con más precisión.

### Función de verosimilitud $L(\theta; X^{(n)})$
$$L(\theta; X^{(n)}) = \prod_{i=1}^{n} f(X_i; \theta)$$

Producto de las densidades evaluadas en los datos observados. Puede verse como "qué tan plausible es cada valor de θ dados los datos".

### Cota Inferior de Cramér-Rao (CICR)
Para todo estimador insesgado $\hat{\theta}$ de θ, bajo condiciones de regularidad:

$$\boxed{\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot I(\theta)} = \text{CICR}(\theta)}$$

Es un **piso**: ningún estimador insesgado puede tener varianza menor. Si un estimador lo alcanza, es el mejor posible.

### CICR para $\varphi(\theta)$
Si en lugar de θ se estima $\varphi = \varphi(\theta)$:

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$$

El factor $[\varphi'(\theta)]^2$ refleja que estimar una función de θ puede ser más fácil o más difícil según qué tan rápido cambia φ.

### Condiciones de regularidad
Para que la CICR sea válida se requiere:
1. Poder intercambiar derivada con integral (la densidad es "suave").
2. El **soporte no depende de θ**.

**No aplica** para Uniforme(0, θ) ni distribuciones truncadas cuyo soporte cambia con θ.

### Desigualdad de Cauchy-Schwarz
$$[E(UV)]^2 \leq E(U^2) \cdot E(V^2)$$

Es la herramienta matemática con la que se demuestra la CICR (tomando $U = \hat{\theta} - \theta$ y $V = \frac{\partial}{\partial\theta}\ln L$). La igualdad se cumple cuando U y V son proporcionales.

### MVUE (Minimum Variance Unbiased Estimator)
Estimador insesgado cuya varianza **alcanza** la CICR. Es el mejor estimador insesgado posible.

Condición: la igualdad en Cauchy-Schwarz se cumple cuando:

$$\hat{\theta} - \theta = c(\theta) \cdot \frac{\partial}{\partial\theta} \ln L(\theta; X^{(n)})$$

Esto ocurre típicamente en familias exponenciales.

---

## VI. Rao-Blackwell y Lehmann-Scheffé

### Teorema de Rao-Blackwell
Sea δ(X) un estimador insesgado de θ con varianza finita, y T un estadístico suficiente. Entonces:

$$\delta^{*}(T) = E[\delta(X) \mid T]$$

cumple:
1. $\delta^{*}$ es insesgado (por ley de esperanza total).
2. $\text{Var}(\delta^{*}) \leq \text{Var}(\delta)$ (por descomposición de la varianza total).

**Intuición:** al condicionar sobre T, eliminas la variabilidad que no aporta información sobre θ.

### Ley de varianza total
$$\text{Var}(\delta) = \text{Var}(E[\delta \mid T]) + E[\text{Var}(\delta \mid T)]$$

El primer término es $\text{Var}(\delta^{*})$; el segundo es $\geq 0$. Por eso $\text{Var}(\delta^{*}) \leq \text{Var}(\delta)$.

### Completitud
T es **completo** si:

$$E[g(T)] = 0 \;\;\forall\theta \;\;\Longrightarrow\;\; g(T) = 0 \text{ c.s.}$$

Significa que no hay funciones "invisibles" de T (funciones con esperanza cero para todo θ). En familias exponenciales (Normal, Poisson, Bernoulli, Gamma, etc.), el estadístico suficiente natural es completo.

### Teorema de Lehmann-Scheffé
Si T es **suficiente y completo**, entonces $\delta^{*} = E[\delta \mid T]$ es el **único** estimador insesgado basado en T, y por lo tanto es **MVUE**.

Rao-Blackwell + completitud = MVUE automático.

---

## VII. Distribuciones del Curso

| Distribución | f.d.p.g. | E[X] | Var(X) | Suf. T | MVUE de θ |
|---|---|---|---|---|---|
| Bernoulli(θ) | $\theta^x(1-\theta)^{1-x}$ | θ | θ(1-θ) | $\sum X_i$ | $\bar{X}$ |
| Normal(μ, σ²) | $\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-\mu)^2/2\sigma^2}$ | μ | σ² | $\bar{X}$ (σ² conoc.) | $\bar{X}$ |
| Poisson(λ) | $\frac{\lambda^x}{x!}e^{-\lambda}$ | λ | λ | $\sum X_i$ | $\bar{X}$ |
| Exponencial(θ) | $\frac{1}{\theta}e^{-x/\theta}$ | θ | θ² | $\sum X_i$ | $\bar{X}$ |
| Uniforme(0, θ) | $1/\theta$ en $(0,\theta)$ | θ/2 | θ²/12 | $X_{(n)}$ | $(n+1)/n \cdot X_{(n)}$ |

### Chi-cuadrada $\chi^2_{(k)}$
Distribución de la suma de k variables $N(0,1)$ al cuadrado. Aparece en la distribución muestral de los estimadores de varianza:
- $n\hat{\sigma}_2^2/\sigma^2 \sim \chi^2_{(n)}$ (con μ conocido)
- $n\hat{\sigma}_1^2/\sigma^2 \sim \chi^2_{(n-1)}$ (con $\bar{X}$ en lugar de μ — se pierde un grado de libertad)

### Beta-potencia
$f(x;\theta) = \theta x^{\theta-1}$ en $(0,1)$. Aparece frecuentemente en exámenes.

### Geométrica, Rayleigh, Trinomial
Distribuciones que aparecen en ejercicios y exámenes como casos de aplicación de los conceptos del curso.

---

## VIII. Resultados Clave que Conectan Todo

### Un estimador sesgado puede ser mejor
$\hat{\sigma}_1^2$ (sesgado) tiene menor ECM que $\hat{\sigma}_2^2$ (insesgado) en el modelo Normal. El máximo muestral $X_{(n)}$ (sesgado) es mejor que $2\bar{X}$ (insesgado) en Uniforme(0,θ). La lección: **insesgamiento no es sinónimo de optimalidad**.

### La CICR no siempre aplica
Cuando el soporte depende de θ (Uniforme(0,θ)), la CICR no es válida. De hecho, el máximo muestral corregido tiene varianza de orden $n^{-2}$, inferior a cualquier cota de orden $n^{-1}$.

### Resumen de criterios para evaluar un estimador

| Criterio | Pregunta que responde | Fórmula |
|---|---|---|
| Insesgamiento | ¿Está centrado en θ? | $E[\hat{\theta}] = \theta$ |
| ECM | ¿Qué tan lejos cae de θ? | $\text{Var} + \text{Sesgo}^2$ |
| Consistencia | ¿Mejora con más datos? | $\text{ECM} \to 0$ |
| Suficiencia | ¿Usa toda la información? | Factorización de Fisher-Neyman |
| MVUE | ¿Es el mejor insesgado? | Alcanza la CICR |
