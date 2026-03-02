# Clase 2: Dos Vertientes de la Estadística y el Muestreo Probabilístico

**Capítulo I.3 – I.4**

---

## Dos Vertientes de la Estadística

### 1. Análisis Exploratorio de Datos (Censo/Población completa)
- Se accede a **todos** los datos que el fenómeno puede producir.
- La descripción que se produce es **exacta**.
- Referencia: Tukey (1977).

### 2. Inferencia Estadística (Muestra)
- No es posible recolectar todos los datos (costo, inaccesibilidad, observación destructiva).
- Se usa una fracción de la población (muestra) para describir el fenómeno completo.
- La descripción es **aproximada**.
- Es fundamental medir/cuantificar el grado de aproximación.

---

## El Muestreo Probabilístico

### Definición 1.5 — Muestra
Cuando solo se tiene acceso a una fracción de los datos, a la fracción observada se le denomina **Muestra**.

### Tipos de muestreo
- **Muestra representativa:** Ideal pero inalcanzable en la práctica.
- **Muestreo por expertos:** Problemas de reproducibilidad.
- **Muestreo probabilístico (sorteo):** La solución definitiva. Hito: artículo de Jerzy Neyman (1934).

### Procedimiento de Muestreo Aleatorio Simple (sin reemplazo)

De una población finita de N elementos:
1. Etiquetar cada elemento con una etiqueta única en {1, 2, ..., N}.
2. Depositar las N etiquetas en una urna.
3. Mezclar bien y extraer una etiqueta (primer elemento de la muestra).
4. Repetir con las N-1 restantes.
5. Continuar hasta completar la muestra de tamaño n.

### Resultado Fundamental

Cuando n ≪ N, las variables X₁, X₂, ..., Xₙ son **independientes e idénticamente distribuidas (i.i.d.)**. Los datos x⁽ⁿ⁾ = (x₁, x₂, ..., xₙ) son el resultado de observar n realizaciones independientes de una misma variable aleatoria X.

---

## Ejemplos
- **Preferencias electorales:** 7.5 millones de electores; se entrevistan unos pocos centenares.
- **Ensayos farmacéuticos:** Probar un tratamiento en un grupo reducido.
- **Control de calidad:** Prueba destructiva de tabletas electrónicas.
- **Exámenes de sangre:** Se extrae una muestra de pocos mililitros, no los 4-5 litros totales.
