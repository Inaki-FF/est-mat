# Guía de Estudio — Estadística Matemática

**Curso:** Estadística Matemática — Prof. Manuel Mendoza Ramírez, ITAM
**Material:** 10 clases, 1 lista de ejercicios, 7 exámenes pasados

---

## Índice

1. [Estructura del Curso](#estructura-del-curso)
2. [Temas por Clase](#temas-por-clase)
3. [Fórmulas y Teoremas Esenciales](#fórmulas-y-teoremas-esenciales)
4. [Definiciones Clave](#definiciones-clave)
5. [Distribuciones Modelo](#distribuciones-modelo)
6. [Patrones de Exámenes](#patrones-de-exámenes)
7. [Guía de Archivos](#guía-de-archivos)

---

## Estructura del Curso

El curso sigue una progresión lógica:

```
Cap. I: Elementos del Análisis Estadístico
  ├── I.1  Introducción (¿Qué es la Estadística?)
  ├── I.2  Atributos, Variables, Datos
  ├── I.3  Dos vertientes: Exploratoria vs. Inferencial
  ├── I.4  Muestreo probabilístico
  └── I.5  Inferencia paramétrica (familias, espacio Θ)

Cap. II: Estimación Puntual
  ├── II.1  Función estimadora y valor estimado
  ├── II.2  Error de estimación
  ├── II.3  Insesgamiento, Sesgo, ECM, Consistencia
  ├── II.4  Ejemplos (Normal, Uniforme, Bernoulli)
  ├── II.5  Estadísticas suficientes
  ├── II.6  Factorización de Fisher-Neyman
  ├── II.7  Cota Inferior de Cramér-Rao
  └── II.8  MVUE (Estimador Insesgado de Varianza Mínima)

Cap. III: Estimación por Intervalos (Parcial 2)
  ├── Intervalos de confianza
  ├── Variables pivotales
  └── Función de verosimilitud
```

---

## Temas por Clase

| Clase | Tema | Archivo |
|---|---|---|
| 1 | Introducción: fenómenos inciertos, Estadística, Atributos→Variables→Datos | [clase-01](clases/clase-01-introduccion.md) |
| 2 | Exploratoria vs. Inferencia, Muestreo probabilístico | [clase-02](clases/clase-02-muestreo.md) |
| 3 | Inferencia paramétrica, familias paramétricas, 3 preguntas | [clase-03](clases/clase-03-inferencia-parametrica.md) |
| 4 | Estimación puntual, función estimadora, principio de analogía | [clase-04](clases/clase-04-estimacion-puntual.md) |
| 5 | Error de estimación, Insesgamiento, Sesgo, ECM, Consistencia | [clase-05](clases/clase-05-error-ECM-consistencia.md) |
| 6 | Consistencia ECM, estimadores σ² en Normal, σ̂₁² vs σ̂₂² | [clase-06](clases/clase-06-consistencia-varianza-normal.md) |
| 7 | Estimación en Uniforme(0,θ) y Bernoulli(θ) | [clase-07](clases/clase-07-uniforme-bernoulli.md) |
| 8 | Estadísticas suficientes (definición, verificación por condicional) | [clase-08](clases/clase-08-estadisticas-suficientes.md) |
| 9 | Teorema de Factorización de Fisher-Neyman | [clase-09](clases/clase-09-factorizacion-fisher-neyman.md) |
| 10 | Cota Inferior de Cramér-Rao, MVUE | [clase-10](clases/clase-10-cramer-rao-MVUE.md) |

---

## Fórmulas y Teoremas Esenciales

### 1. Relación Fundamental del ECM

$$\boxed{\text{ECM}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Sesgo}(\hat{\theta})]^2}$$

Si θ̂ es insesgado: ECM = Var.

### 2. Cota Inferior de Cramér-Rao

$$\boxed{\text{Var}(\hat{\theta}) \geq \frac{1}{n \cdot I(\theta)} = \text{CICR}(\theta)}$$

donde I(θ) = E[(∂/∂θ ln f(X;θ))²] = -E[∂²/∂θ² ln f(X;θ)]

### 3. CICR para φ(θ)

$$\text{Var}(\hat{\varphi}) \geq \frac{[\varphi'(\theta)]^2}{n \cdot I(\theta)}$$

### 4. Factorización de Fisher-Neyman

T(X⁽ⁿ⁾) es **suficiente** para θ si y solo si:

$$f_{X^{(n)}}(x^{(n)}; \theta) = g(T(x^{(n)}); \theta) \cdot h(x^{(n)})$$

### 5. Rao-Blackwellización

Si θ̂₁ es insesgado y T es suficiente, entonces θ̂₂ = E[θ̂₁ | T] es:
- Insesgado
- Var(θ̂₂) ≤ Var(θ̂₁)

---

## Definiciones Clave

| # | Concepto | Definición |
|---|---|---|
| 1.1 | Estadística (disciplina) | Describe fenómenos a través de datos con variabilidad |
| 1.6 | Muestra Aleatoria | Colección de v.a. i.i.d. según F(x) |
| 2.1 | Estadística (función) | Función de X⁽ⁿ⁾ sin cantidades desconocidas |
| 2.2 | Estimador | Estadística que toma valores en el espacio paramétrico |
| 2.6 | Insesgado | E[θ̂] = θ para todo θ |
| 2.7 | Sesgo | E[θ̂] - θ |
| 2.8 | ECM | E[(θ̂ - θ)²] |
| 2.9 | Consistente en ECM | ECM → 0 cuando n → ∞ |
| — | Asintóticamente insesgado | Sesgo → 0 cuando n → ∞ |
| — | Suficiente | f(X⁽ⁿ⁾ \| T=t) no depende de θ |
| — | MVUE | Insesgado + alcanza la CICR |

---

## Distribuciones Modelo

### Bernoulli(θ)

| Estimador | θ̂ = X̄ |
|---|---|
| Insesgado | ✅ |
| Varianza | θ(1-θ)/n |
| Consistente | ✅ |
| Suficiente | ✅ (T = Σ Xᵢ) |
| MVUE | ✅ |

### Normal(μ, σ²) — estimación de μ (σ² conocida)

| Estimador | μ̂ = X̄ |
|---|---|
| Insesgado | ✅ |
| Varianza | σ²/n |
| Consistente | ✅ |
| Suficiente | ✅ |
| MVUE | ✅ |

### Normal(μ, σ²) — estimación de σ² (μ conocida)

| | σ̂₁² = Σ(Xᵢ-X̄)²/n | σ̂₂² = Σ(Xᵢ-μ)²/n |
|---|---|---|
| Insesgado | ❌ (sesgo = -σ²/n) | ✅ |
| Distribución | σ²/n · χ²(n-1) | σ²/n · χ²(n) |
| ECM | σ⁴(2n-1)/n² | 2σ⁴/n |
| Mejor ECM | ✅ | ❌ |

### Uniforme(0, θ)

| | θ̂₁ = 2X̄ | θ̂₂ = X₍ₙ₎ |
|---|---|---|
| Insesgado | ✅ | ❌ |
| ECM | θ²/(3n) | 2θ²/[(n+1)(n+2)] |
| Orden ECM | n⁻¹ | n⁻² |
| Suficiente | ❌ | ✅ |
| Mejor | ❌ | ✅ |

### Exponencial(θ)

| Estimador | θ̂ = X̄ |
|---|---|
| Insesgado | ✅ |
| Varianza | θ²/n |
| MVUE | ✅ |

---

## Patrones de Exámenes

### Parcial 1 — Temas principales
1. **Preguntas conceptuales** (siempre): ¿Qué es la Estadística?, ¿Qué es la Inferencia Paramétrica?, ¿Qué es una muestra aleatoria?
2. **Problema aplicado** con datos: estimar parámetro de Poisson/Exponencial, interpretar modelo, evaluar adecuación
3. **Estimación**: momentos, MV, insesgamiento, suficiencia, CICR
4. **Rao-Blackwell / MELI / MVUE**: construir estimadores mejorados

### Parcial 2 — Temas principales
1. **Preguntas conceptuales**: Variables pivotales, función de verosimilitud, intervalos de confianza
2. **Intervalos de confianza**: construir IC al nivel (1-α)×100%
3. **Comparación de poblaciones**: distribuciones exponenciales
4. **Aplicación práctica**: paneles solares, encuestas electorales

### Distribuciones frecuentes en exámenes
- Bernoulli / Binomial
- Poisson
- Exponencial
- Normal
- Uniforme (continua)
- Geométrica
- Beta-potencia: f(x;θ) = θx^(θ-1) en (0,1)

### Cuantiles de la Normal Estándar (memorizarlos)
| Cuantil | Valor |
|---|---|
| Z₀.₉₀ | 1.282 |
| Z₀.₉₅ | 1.645 |
| Z₀.₉₇₅ | 1.960 |
| Z₀.₉₈ | 2.05 |

---

## Guía de Archivos

### Clases
```
docs/clases/
├── clase-01-introduccion.md
├── clase-02-muestreo.md
├── clase-03-inferencia-parametrica.md
├── clase-04-estimacion-puntual.md
├── clase-05-error-ECM-consistencia.md
├── clase-06-consistencia-varianza-normal.md
├── clase-07-uniforme-bernoulli.md
├── clase-08-estadisticas-suficientes.md
├── clase-09-factorizacion-fisher-neyman.md
└── clase-10-cramer-rao-MVUE.md
```

### Ejercicios
```
docs/ejercicios/
├── lista-ejercicios-1-ene2026.md    (14 ejercicios del semestre actual)
└── ejercicios-teoremas-CICR.md       (de imágenes: CICR, Uniforme, Rayleigh)
```

### Exámenes Pasados
```
docs/examenes/
├── examen-parcial1-oct2015.md       (Geométrica, Poisson, Rao-Blackwell)
├── examen-parcial1-oct2016.md       (Exponencial, Poisson, Rao-Blackwell)
├── examen-parcial1-oct2024.md       (Poisson, Bernoulli θ², trinomial)
├── examen-parcial1-ene2025.md       (Uniforme, Bernoulli θ², MELI)
├── examen-parcial2-abril2024.md     (Beta-potencia, IC electoral)
├── examen-parcial2-abril2025.md     (IC exponenciales, comparación)
└── examen-parcial2-paneles-solares.md (IC proporción, Uniforme asimétrica)
```

---

## Modo Interactivo Profesor-Alumno

Esta guía está diseñada para que **Claude actúe como profesor** y tú como estudiante. Aquí hay formas de usarla:

### Sesiones de repaso
- "Explícame el Teorema de Factorización como si fuera mi primera vez"
- "Dame un ejemplo paso a paso de cómo verificar suficiencia en Exponencial"
- "¿Por qué el estimador sesgado puede ser mejor que el insesgado?"

### Simulación de examen
- "Hazme un examen parcial 1 tipo ITAM con 4 problemas"
- "Dame un problema de Rao-Blackwellización y ayúdame a resolverlo"
- "Quiero practicar problemas de CICR, dame 3 ejercicios de dificultad creciente"

### Verificación de comprensión
- "Hazme 5 preguntas conceptuales del Parcial 1 y evalúa mis respuestas"
- "Te voy a explicar qué es una estadística suficiente, corrígeme si me equivoco"
- "¿Mi demostración de la CICR para φ(θ) está correcta?" (pega tu trabajo)

### Resolución guiada
- "Ayúdame a resolver el Ejercicio 12 (Rao-Blackwellización) paso a paso"
- "Empecé el problema 4 del examen Oct 2024 pero me atoré en el inciso d)"
- "¿Cómo identifico la estadística suficiente en la familia exponencial?"

---

## Estrategia de Estudio Recomendada

### Fase 1: Fundamentos (Clases 1-3)
- Dominar las definiciones formales
- Entender la diferencia entre exploratoria e inferencia
- Saber qué es una familia paramétrica y las 3 preguntas

### Fase 2: Estimación Puntual (Clases 4-7)
- Practicar el cálculo de E[θ̂], Var(θ̂), ECM(θ̂)
- Hacer los ejercicios de comparación entre estimadores
- Entender por qué un estimador sesgado puede ser mejor

### Fase 3: Suficiencia y Optimalidad (Clases 8-10)
- Dominar el Teorema de Factorización
- Practicar el cálculo de la CICR en todas las distribuciones
- Saber identificar cuándo un estimador es MVUE

### Fase 4: Práctica con Exámenes
- Resolver los 7 exámenes pasados sin ver las soluciones
- Los problemas conceptuales (pregunta 1) se repiten — memorizar respuestas modelo
- Practicar la interpretación de parámetros en contexto aplicado
