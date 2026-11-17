# Sesión 1 — Momento 1: Predecir

**Laboratorio L1 — Primer contacto · Mensaje de Arecibo**

## P1. Interpretación inicial de una cadena binaria

> Les llega una cadena de 1 679 ceros y unos, sin nada más. ¿Qué es lo primero que intentarían para encontrarle sentido? Escriban tres ideas, en orden.

**1. Codificación de letras.** Interpretaría la secuencia como un mensaje alfabético. Propondría usar cada `1` como inicio de un bloque, convertir cada bloque binario en un número y aplicar módulo 26 para asociarlo con una letra.

_Limitación:_ no conocemos la separación original de los datos ni sabemos si se emplea esa convención; podrían aparecer letras sin sentido.

**2. Cambio de base.** Convertiría la secuencia binaria a otras bases, como la decimal o la base 6, para buscar posibles relaciones con letras mediante distintas reglas de separación.

_Limitación:_ cambiar de base no cambia el valor representado y encontrar una palabra reconocible podría ser una coincidencia.

**3. Interpretación mediante grafos.** Construiría puntos sucesivos: `1` indicaría una conexión con el punto anterior y `0` indicaría que no existe conexión. Después observaría si surge alguna figura reconocible.

_Limitación:_ la cadena no determina la posición espacial de los puntos, por lo que distintas distribuciones producirían grafos diferentes.

## P2. Representación de un dibujo mediante bits

> Si alguien quisiera mandar un dibujo con bits, ¿cómo lo haría? ¿Qué tendría que adivinar quien lo recibe?

**Propuesta.** Representaría el dibujo mediante una matriz binaria, como en el _pixel art_: `0` para el fondo y `1` para los detalles del dibujo. Después transmitiría sus valores como una cadena de bits.

**Qué tendría que deducir el receptor:**

- Que la secuencia representa una imagen formada por píxeles.
    
- Cuántas filas y columnas tiene el dibujo.
    
- En qué orden se colocan y leen los bits.
    
- Qué significa cada valor (`0` y `1`).
    
- Si se añadieron bits de relleno, cuál era la longitud original.
    

La longitud no determina las dimensiones: por ejemplo, 15 bits pueden distribuirse en una matriz de `3 × 5` o de `5 × 3`, con resultados visuales diferentes. También consideramos matrices cuadradas o bits de relleno, aunque estas opciones necesitan convenciones adicionales.

> [!TIP]  
> **Idea propuesta:** mostrar primero ejemplos pequeños de cadenas y sus dibujos podría facilitar que el receptor deduzca las reglas de representación, aunque no garantizaría que comprenda el mensaje.

## P3. Organización de 1 679 cuadritos

> ¿De cuántas maneras se pueden acomodar 1 679 cuadritos en un rectángulo completo, sin que sobre ni falte ninguno? Respondan sin computador, con lo que saben de divisores.

Para encontrar las dimensiones posibles busqué los divisores de 1679. Al probar divisibilidad entre números primos, encontré:

$$  
1679=23\cdot73,\qquad D(1679)=\{1,23,73,1679\}.  
$$

Como 23 y 73 son primos, las parejas de dimensiones son:

|Filas|Columnas|
|---|---|
|1|1679|
|23|73|
|73|23|
|1679|1|

**Resultado:** existen **cuatro parejas ordenadas** de filas y columnas. Si se consideran equivalentes los rectángulos que solo cambian de orientación, quedan **dos formas distintas**: `1 × 1679` y `23 × 73`.

---

## 4. Registro del uso de inteligencia artificial

> [!IMPORTANT]  
> El uso de inteligencia artificial debe respetar el protocolo establecido en la guía del laboratorio. La herramienta se utiliza como apoyo para analizar razonamientos, aclarar dificultades y mejorar la presentación de los resultados, pero no sustituye el trabajo autónomo ni la verificación del estudiante.

### 4.1. Registro de consultas

|Actividad|Consulta realizada|Aporte recibido|Evaluación|
|---|---|---|---|
|P1|Revisión de tres propuestas para interpretar una secuencia binaria desconocida.|Observaciones sobre las limitaciones de cada interpretación y la necesidad de establecer convenciones.|Aceptado y complementado mediante razonamiento propio.|
|P2|Evaluación de la propuesta de representar dibujos mediante matrices binarias.|Aclaraciones sobre dimensiones, orden de lectura, bits de relleno y convenciones de representación.|Aceptado y complementado durante el análisis.|
|P3|Revisión del procedimiento para encontrar los divisores de 1 679 y construir rectángulos.|Aclaración sobre la factorización prima, las parejas de factores y la diferencia entre contar orientaciones y rectángulos distintos.|Aceptado después de revisar el razonamiento matemático.|
|Documentación|Consulta sobre la representación de expresiones matemáticas y la organización visual del archivo Markdown.|Recomendaciones para utilizar LaTeX, tablas, encabezados y callouts compatibles con Obsidian y GitHub.|Aceptado como criterio de presentación del documento.|

### 4.2. Verificación de los aportes

Los aportes recibidos se revisaron considerando los siguientes criterios:

1. **Coherencia matemática:** comprobar que los razonamientos y resultados sean consistentes.
    
2. **Comprensión:** verificar que las explicaciones correspondan con las ideas desarrolladas durante el laboratorio.
    
3. **Autonomía:** conservar las propuestas propias y utilizar la herramienta únicamente como apoyo.
    
4. **Trazabilidad:** identificar qué aportes fueron aceptados, modificados o descartados.
    

En particular, para P3 se verificó la descomposición:

$$  
1679=23\cdot73  
$$

También se distinguieron las cuatro parejas ordenadas de dimensiones de las dos configuraciones rectangulares diferentes cuando no se consideran las rotaciones.

### 4.3. Reflexión sobre el uso de IA

La inteligencia artificial fue utilizada como una herramienta de apoyo para revisar nuestras ideas, identificar limitaciones y aclarar conceptos matemáticos.

El proceso permitió contrastar las propuestas iniciales con explicaciones adicionales, sin reemplazar el razonamiento desarrollado durante la actividad.

Consideramos importante evaluar cada respuesta recibida, puesto que una explicación proporcionada por una herramienta no constituye por sí misma una demostración ni garantiza que sea correcta.

Por tanto, el uso de IA debe estar acompañado de pensamiento crítico, verificación y comprensión de los resultados.

### 4.4. Evidencias y trazabilidad

Para mantener un registro verificable del proceso, se conservarán las consultas realizadas y las respuestas relevantes de la herramienta, indicando qué elementos fueron:

- **Aceptados:** aportes que se consideraron correctos y pertinentes.
    
- **Modificados:** aportes que necesitaron ajustes o complementos.
    
- **Rechazados:** aportes que no se utilizaron, junto con la justificación correspondiente.
    

---

## 5. Referencias y materiales consultados

- Guía del laboratorio L1 — Primer contacto.
    
- Conversaciones de apoyo con inteligencia artificial, registradas en la sección 4.
    

---

_Laboratorio L1 — Primer contacto · Introducción a las Ciencias de la Computación_