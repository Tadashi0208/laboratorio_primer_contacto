# Sesión 1 — Recibir: el mensaje de Arecibo

## 1. Información de la sesión

|Campo|Descripción|
|---|---|
|Laboratorio|L1 — Primer contacto|
|Sesión|1 — Recibir|
|Actividad|El mensaje de Arecibo|
|Tema central|Representación e interpretación de información binaria|
|Modalidad|Análisis y razonamiento sin computador|

---

## 2. Desarrollo de las preguntas

### 2.1. Pregunta 1 — Interpretación inicial de un mensaje binario

#### Enunciado

> Les llega una cadena de 1 679 ceros y unos, sin nada más. ¿Qué es lo primero que intentarían para encontrarle sentido? Escriban tres ideas, en orden.

#### Ideas iniciales

**Primera idea: Codificación de letras**

Interpretar la cadena como un mensaje codificado, donde cada número representa la posición de una letra en el alfabeto.

Para ello, propondría recorrer la cadena utilizando el bit `1` como indicador del comienzo de un nuevo bloque. Cada bloque se interpretaría como un número binario y, posteriormente, aplicaría módulo 26 para obtener un valor que pueda relacionarse con una letra del alfabeto.

> [!WARNING]  
> **Limitaciones**
> 
> Este método podría dividir incorrectamente la información, producir letras repetidas o generar interpretaciones sin sentido. Además, desconozco si el mensaje utiliza realmente esta convención.

---

**Segunda idea: Cambio de base**

Interpretar la cadena como una representación binaria y convertirla a otras bases, como la decimal o la base 6.

Entiendo que cambiar de base no modifica el valor del número, sino únicamente su representación. Mi intención sería aprovechar esas representaciones para establecer posibles correspondencias con letras, utilizando diferentes reglas de separación.

> [!WARNING]  
> **Limitaciones**
> 
> Una regla que funciona para una representación podría no funcionar para otra. Además, encontrar una palabra conocida no garantizaría que el mensaje haya sido interpretado correctamente, pues podría tratarse de una coincidencia.

---

**Tercera idea: Interpretación mediante grafos**

Construir un grafo a partir de los bits recibidos. Para ello, crearía puntos sucesivos y utilizaría el valor `1` para indicar una conexión con el punto anterior y el valor `0` para indicar que no existe dicha conexión.

Después intentaría observar si el grafo resultante forma alguna figura reconocible.

> [!WARNING]  
> **Limitaciones**
> 
> La cadena no proporciona información sobre la ubicación espacial de los puntos. Dependiendo de cómo se organicen, el grafo podría producir figuras distintas o no representar ninguna estructura con significado.

#### Conclusión de P1

Las tres propuestas representan diferentes maneras de intentar encontrar una estructura en una secuencia binaria desconocida. Sin embargo, cada interpretación depende de convenciones que no están especificadas en el mensaje.

Por tanto, una misma cadena de bits podría admitir diferentes interpretaciones dependiendo de cómo decidamos organizarla y asignarle significado. Antes de concluir que encontramos un mensaje, sería necesario comprobar que la interpretación utilizada tiene coherencia y no corresponde simplemente a una coincidencia.

---

### 2.2. Pregunta 2 — Representación de un dibujo mediante bits

#### Enunciado

> Si alguien quisiera mandar un dibujo con bits, ¿cómo lo haría? ¿Qué tendría que adivinar quien lo recibe?

#### 1. Propuesta inicial

Nuestra primera propuesta consiste en representar el dibujo mediante una matriz binaria, siguiendo una estructura similar al pixel art. Cada posición de la matriz representaría un píxel del dibujo, utilizando dos valores:

- `0`: representa un píxel del fondo.
    
- `1`: representa un píxel del dibujo.
    

De esta manera, podríamos transformar una imagen en una secuencia de ceros y unos que posteriormente se organizaría en una matriz.

#### 2. Organización de la cadena binaria

Una vez obtenida la cadena de bits, es necesario establecer cómo se organizará. Consideramos que el número de bits por fila podría ser una convención previamente acordada entre el emisor y el receptor.

También observamos que un dibujo normalmente tiene unas dimensiones determinadas de ancho y alto, las cuales podrían corresponderse con el número de columnas y filas de la matriz.

Por tanto, el receptor necesitaría conocer las dimensiones para reconstruir correctamente la distribución de los píxeles.

#### 3. Problema de las dimensiones

Identificamos que conocer únicamente la longitud de la cadena no es suficiente para reconstruir el dibujo.

Por ejemplo, una cadena de 15 bits podría organizarse en una matriz de 3 × 5 o de 5 × 3. Aunque ambas matrices contienen exactamente los mismos bits, su distribución espacial es diferente y, por tanto, pueden producir dibujos distintos.

Inicialmente propusimos utilizar matrices cuadradas para simplificar la organización. Sin embargo, encontramos una dificultad: no todos los dibujos tienen dimensiones cuadradas.

Como alternativa, propusimos agregar filas o bits de relleno para completar la matriz. Para distinguir los bits originales de los agregados, sería necesario conocer la longitud original de la cadena y comparar esa longitud con la cantidad total de posiciones de la matriz.

> [!IMPORTANT]  
> **Deducción**
> 
> La cantidad de bits permite conocer la longitud de la secuencia, pero no determina por sí sola las dimensiones de la matriz ni la distribución espacial de los píxeles.

#### 4. Convenciones necesarias para reconstruir el dibujo

Durante el análisis identificamos que transmitir los bits y sus dimensiones tampoco garantiza que el receptor pueda reconstruir correctamente la imagen.

La otra especie podría desconocer qué es una matriz y cómo se organiza. Por ello, sería necesario establecer algunas convenciones:

1. Que la secuencia de bits representa una distribución de píxeles.
    
2. Cuántas filas y columnas tiene la representación.
    
3. En qué orden se deben organizar los bits, por ejemplo, de izquierda a derecha y de arriba hacia abajo.
    
4. Qué representa cada valor binario: `0` y `1`.
    
5. Cuál es la longitud original de la cadena, en caso de utilizar bits adicionales para completar la matriz.
    

#### 5. Enseñar el sistema de representación

Para abordar el problema de que el receptor desconozca nuestras convenciones, propusimos enviar primero ejemplos pequeños y progresivos.

La idea consiste en comenzar con cadenas de bits de longitudes reducidas, mostrar cómo se organizan espacialmente y presentar diferentes tamaños de matrices.

A través de estos ejemplos, el receptor podría observar la relación entre las cadenas binarias y las representaciones visuales, identificar patrones y formular hipótesis sobre las reglas utilizadas.

Sin embargo, concluimos que estos ejemplos no garantizan que la otra especie comprenda nuestra representación. Solamente aumentan la posibilidad de que encuentre los patrones y deduzca las convenciones que estamos utilizando.

> [!TIP]  
> **Deducción**
> 
> Presentar ejemplos progresivos puede facilitar que el receptor identifique patrones y formule hipótesis sobre el sistema de representación. No obstante, encontrar esos patrones no garantiza que interprete el mensaje de la misma manera que el emisor.

#### 6. Conclusión de P2

Representar un dibujo mediante bits no consiste únicamente en convertir una imagen en ceros y unos. También es necesario establecer convenciones que permitan organizar, reconstruir e interpretar la información.

El receptor debe conocer o deducir cómo se distribuyen los bits, cuáles son las dimensiones de la representación, qué significa cada valor y en qué orden debe realizar la lectura.

Por tanto, incluso si dos especies reciben exactamente la misma cadena binaria, no necesariamente interpretarán el mismo dibujo si no comparten las convenciones utilizadas para representarlo.

> [!IMPORTANT]  
> **Conclusión de P2**
> 
> Nuestra conclusión es que la representación de información requiere acuerdos que permitan asignar significado a los bits. Cuando estos acuerdos no son compartidos, es necesario proporcionar ejemplos y evidencias que faciliten su deducción, aunque esto no garantice una interpretación idéntica.

---

### 2.3. Pregunta 3 — Organización de 1 679 cuadritos en un rectángulo

#### Enunciado

> ¿De cuántas maneras se pueden acomodar 1 679 cuadritos en un rectángulo completo, sin que sobre ni falte ninguno? Respondan sin computador, con lo que saben de divisores.

#### 1. Idea inicial

Para determinar las posibles configuraciones rectangulares, considero que debemos encontrar los divisores de 1 679. Esto se debe a que las dimensiones de un rectángulo formado por cuadritos deben ser números enteros positivos cuyo producto sea exactamente la cantidad total de cuadritos.

Una estrategia para encontrar todos los divisores consiste en realizar la descomposición en factores primos.

#### 2. Análisis y procedimiento

Inicialmente, identificamos que 1 y 1 679 son divisores del número. Posteriormente, probamos la divisibilidad entre números primos, comenzando por 2, hasta encontrar que 23 divide exactamente a 1 679:

$$  
\frac{1679}{23}=73  
$$

Por lo tanto:

$$  
1679=23\cdot73  
$$

Como 23 y 73 son números primos, la descomposición obtenida permite identificar todos los divisores positivos:

$$  
D(1679)={1,23,73,1679}  
$$

#### 3. Construcción de los rectángulos

A partir de los divisores encontrados, podemos formar las siguientes parejas de factores:

|Filas|Columnas|Total de cuadritos|
|---|---|---|
|1|1679|1679|
|23|73|1679|
|73|23|1679|
|1679|1|1679|

Todas las configuraciones utilizan exactamente 1 679 cuadritos.

Sin embargo, debemos considerar que intercambiar las dimensiones de un rectángulo solamente cambia su orientación. Por ejemplo, uno de dimensiones (23\times73) representa el mismo rectángulo que uno de dimensiones (73\times23), pero girado.

Lo mismo sucede con las configuraciones (1\times1679) y (1679\times1).

#### 4. Conclusión

Encontramos cuatro divisores positivos de 1 679, que permiten formar cuatro parejas ordenadas de dimensiones. No obstante, si no distinguimos los rectángulos que se obtienen mediante una rotación, existen solamente **dos configuraciones rectangulares diferentes**:

$$  
\boxed{1\times1679 \qquad \text{y} \qquad 23\times73}  
$$

Por tanto, la respuesta es que podemos acomodar los 1 679 cuadritos de **dos maneras diferentes**, considerando equivalentes las configuraciones que únicamente cambian de orientación.

Este ejercicio muestra cómo la factorización prima permite determinar las posibles dimensiones enteras de un rectángulo a partir de una cantidad total de elementos.

---

## 3. Síntesis y conclusiones generales

### 3.1. Síntesis de resultados

|Pregunta|Problema analizado|Resultado principal|
|---|---|---|
|P1|Interpretación de una secuencia binaria|Una cadena puede admitir diferentes interpretaciones según las convenciones utilizadas.|
|P2|Representación de un dibujo mediante bits|Se necesitan dimensiones y convenciones para reconstruir una representación visual.|
|P3|Organización de 1 679 elementos|La factorización permite determinar las posibles dimensiones rectangulares.|

### 3.2. Deducciones generales

> [!TIP]  
> **Deducción 1 — La representación depende de convenciones**
> 
> Una secuencia de bits puede organizarse e interpretarse de diferentes maneras. Para reconstruir correctamente la información, el emisor y el receptor necesitan compartir determinadas reglas.

> [!TIP]  
> **Deducción 2 — La longitud no determina la estructura**
> 
> Conocer la cantidad de bits no permite establecer por sí sola cómo deben distribuirse en una representación bidimensional.

> [!TIP]  
> **Deducción 3 — Transmitir no equivale a comunicar**
> 
> Recibir correctamente una secuencia de bits no garantiza comprender el significado que el emisor pretendía transmitir.

> [!TIP]  
> **Deducción 4 — Los ejemplos facilitan la identificación de patrones**
> 
> Proporcionar ejemplos progresivos puede ayudar al receptor a formular hipótesis sobre las convenciones utilizadas, aunque no garantiza que llegue a la interpretación esperada.

### 3.3. Conclusión general

El análisis de esta sesión permite reconocer que la comunicación mediante bits requiere algo más que transmitir una secuencia de ceros y unos. Es necesario establecer una estructura y unas convenciones que permitan interpretar la información.

La representación de un mensaje depende de cómo se codifica, cómo se organiza y qué significado se asigna a cada elemento. Por ello, la comunicación requiere tanto la transmisión de datos como la posibilidad de reconstruir e interpretar correctamente su contenido.

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