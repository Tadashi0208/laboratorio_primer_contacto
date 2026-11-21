# Momento 3 — Explicar

## 1. Convenciones utilizadas en el mensaje

Durante el laboratorio identifiqué diferentes convenciones que podrían dificultar la interpretación del mensaje por parte de una civilización extraterrestre.

|Convención identificada|¿Deducir o adivinar?|Justificación|
|---|---|---|
|**Uso del sistema binario**|Podría deducirse, pero no está garantizado.|Los patrones podrían proporcionar pistas, aunque otra civilización podría utilizar sistemas de representación diferentes y no reconocer nuestra numeración.|
|**Organización de los bits en un rectángulo**|Podría inferirse parcialmente.|La factorización de 1679 permite obtener distintas configuraciones. Los patrones visuales podrían favorecer una de ellas, pero no aseguran una interpretación correcta.|
|**Reconocimiento de la figura humana**|Podría requerir adivinar su significado.|Una civilización con una anatomía diferente podría interpretar la figura como otro organismo, un objeto o simplemente ruido.|
|**Relación entre números y elementos químicos**|Considero que faltan pistas para deducirla con seguridad.|Aunque el receptor comprenda los números y conozca la estructura atómica, no necesariamente sabrá que las cantidades representan números atómicos.|

### Reflexión sobre las convenciones

Considero que una civilización extraterrestre podría identificar patrones dentro del mensaje sin comprender necesariamente su significado.

Nuestra interpretación depende de los conocimientos científicos, matemáticos y culturales que hemos desarrollado. Una civilización con experiencias y tecnologías diferentes podría atribuir otros significados a las mismas figuras.

Por ejemplo, conocer que el carbono tiene seis protones es diferente de comprender que una secuencia binaria del mensaje se refiere precisamente a ese elemento.

Por tanto, aunque las regularidades matemáticas pueden proporcionar pistas, no garantizan que el receptor reconstruya las convenciones utilizadas por el emisor.

## 2. Confrontación de P1, P2 y P3

### P1 — Interpretaciones iniciales

Inicialmente propuse interpretar la cadena de 1679 bits mediante codificación de letras, conversiones numéricas o una representación mediante grafos.

La hipótesis del grafo no encontró respaldo durante el análisis. En cambio, la interpretación binaria resultó útil para descifrar las primeras secciones del mensaje.

También consideré la posibilidad de que los bits representaran una imagen y que fuera necesario establecer una convención de filas y columnas.

Las diferencias entre mis primeras hipótesis y los resultados se debieron principalmente a la poca información disponible. Al principio interpreté los bits utilizando únicamente mis conocimientos y las convenciones con las que estoy familiarizado.

### P2 — Organización matricial

En P2 propuse organizar los bits en filas y columnas para intentar reconocer patrones conocidos.

Esta expectativa se cumplió, pues la representación matricial permitió identificar figuras y secuencias que posteriormente analizamos.

Sin embargo, también descubrí que reconocer patrones visuales no significa necesariamente comprender su significado.

### P3 — Divisores de 1679

La factorización:

$$  
1679=23\times73  
$$

permitió identificar las posibles configuraciones rectangulares del mensaje.

Esto reforzó mi propuesta de P2, porque proporcionó una justificación matemática para organizar los bits en una matriz.

La factorización no determinó por sí sola la orientación adecuada, pero permitió reducir las posibilidades y comparar las representaciones.

### Conclusión de la confrontación

Las actividades P1, P2 y P3 permitieron pasar de interpretaciones iniciales basadas en suposiciones a una representación que podía analizarse mediante procedimientos matemáticos y computacionales.

Este proceso mostró la importancia de las convenciones para representar información y las dificultades que aparecen cuando desconocemos cómo debe interpretarse.

## 3. La frase obligatoria: «Representar es...»

> **Representar es llegar a una convención sobre cómo vamos a interpretar determinado fenómeno, actividad o propiedad, y qué símbolos, figuras o estructuras usaremos para expresar información sobre ellos.**


---
# 7. La revelación del mensaje de Arecibo

## 7.1. Objetivo de la actividad

Después de completar el Momento 3, procedimos a ejecutar la función `revelar(bits)` del cuaderno, cuyo propósito era mostrar la interpretación del mensaje de Arecibo.

Esta actividad nos permitió comparar nuestras hipótesis iniciales con el significado de las diferentes secciones del mensaje, identificar cuáles de nuestras interpretaciones eran correctas y reconocer la importancia de las convenciones empleadas para representar y transmitir información.

Posteriormente, utilizamos la función `zoom(bits, seccion)` para examinar cada región con mayor detalle.

> [!IMPORTANT] Distinción metodológica  
> Debemos diferenciar entre las interpretaciones que realizamos **antes de la revelación** y los significados que identificamos **después de conocer el contenido del mensaje**. Asimismo, comprobar una cantidad con Python no implica necesariamente haber descubierto por nuestra cuenta qué representaba.

---

## 7.2. Comparación entre nuestras hipótesis y la revelación

Durante los momentos anteriores analizamos las diferentes regiones del mensaje organizado en una matriz de 73 filas y 23 columnas.

La revelación permitió establecer la siguiente comparación:

|Sección|Nuestra interpretación inicial|Interpretación después de la revelación|
|---|---|---|
|Números|Identificamos los números del 1 al 10 mediante su representación binaria.|Confirmamos que corresponden a los números del 1 al 10.|
|Elementos|Identificamos los números 1, 6, 7, 8 y 15 y los relacionamos con elementos químicos.|Confirmamos que corresponden a H, C, N, O y P, elementos importantes para la composición de las moléculas biológicas representadas.|
|Nucleótidos|Observamos figuras repetidas con diferencias en su estructura interna, sin determinar qué representaban.|Identificamos representaciones relacionadas con los componentes de los nucleótidos del ADN.|
|Doble hélice|Reconocimos una estructura aproximadamente simétrica, pero no identificamos su significado.|Comprendimos que representa la doble hélice del ADN y una cantidad relacionada con el material genético.|
|Figura humana|Identificamos visualmente la silueta de una persona.|Reconocimos también las referencias numéricas a la estatura humana y a la población terrestre.|
|Sistema solar|Inicialmente interpretamos la figura como una posible bandera o estructura horizontal.|Identificamos la representación del sistema solar y la posición destacada de la Tierra.|
|Radiotelescopio|Consideramos que la figura podía representar una construcción semejante a una casa o un templo.|Identificamos el radiotelescopio de Arecibo y una cantidad asociada al diámetro de su reflector.|

### 7.2.1. Reflexión sobre nuestras interpretaciones

La comparación muestra que algunas secciones resultaron más fáciles de interpretar que otras.

En particular, logramos identificar representaciones numéricas y algunas figuras conocidas, como la silueta humana. Sin embargo, otras regiones requerían información adicional para comprender su significado.

Por ejemplo, reconocer una figura simétrica no era suficiente para concluir que representaba el ADN. Del mismo modo, observar una estructura horizontal no nos permitió identificar inicialmente el sistema solar.

Esto evidencia que una misma secuencia de bits puede adquirir diferentes significados dependiendo de las convenciones y los conocimientos del receptor.

---

## 7.3. Verificación de la información numérica

Una vez conocida la interpretación de las distintas secciones, utilizamos nuestras funciones para comprobar algunas de las cantidades codificadas.

Es importante destacar que estas verificaciones se realizaron **después de la revelación**, cuando ya disponíamos de información acerca de lo que representaban las regiones.

### 7.3.1. Cantidad relacionada con el ADN

En la región de la doble hélice identificamos una secuencia binaria asociada con la cantidad de nucleótidos representada en el mensaje.

Para recuperarla, examinamos las columnas 11 y 10, entre las filas 26 y 41.

Leímos primero los 16 bits de la columna 11 y después los 16 bits de la columna 10. Al concatenar las dos secuencias y aplicar nuestra función `leer_numero()`, obtuvimos:

$$ 
N=4,294,441,822.  
$$

Esta cantidad corresponde al valor codificado en el mensaje para representar información relacionada con el ADN humano.

**Análisis:** antes de la revelación habíamos observado una estructura simétrica, pero no identificamos que correspondiera al ADN. La revelación nos permitió establecer esa interpretación y posteriormente verificar la cantidad numérica.

### 7.3.2. Estatura humana

En la sección correspondiente a la figura humana observamos una barra vertical situada a su izquierda.

Para interpretar la referencia numérica, recuperamos los bits de la fila 50, entre las columnas 1 y 4, utilizando el orden correspondiente a la codificación.

Obtuvimos:

$$  
(1110)_2=14.  
$$

El mensaje utiliza como unidad de referencia la longitud de onda de transmisión, aproximadamente (12.6) cm.

Por tanto:

$$  
h=14(12.6\text{ cm})  
$$

$$  
h=176.4\text{ cm}=1.764\text{ m}.  
$$

Este resultado representa la estatura humana aproximada codificada en el mensaje.

**Análisis:** reconocimos la figura humana antes de ejecutar la revelación, pero inicialmente no identificamos que la barra situada a su izquierda codificaba una referencia de estatura.

### 7.3.3. Población humana

En el lado derecho de la figura humana encontramos otra representación numérica.

Para interpretarla, examinamos las columnas 22 a 17, entre las filas 48 y 53, leyendo cada columna de abajo hacia arriba y comenzando por la columna situada más a la derecha.

La secuencia recuperada fue:

```
000011111111110111111011111111110110
```

Al convertirla a decimal mediante nuestra función `leer_numero()`, obtuvimos:

$$  
N=4,292,853,750.  
$$

Esta cantidad corresponde al valor codificado para representar la población humana de la época.

**Análisis:** el valor debe interpretarse dentro del contexto histórico del mensaje, transmitido en 1974. No representa necesariamente una cifra censal exacta, ni corresponde a la población terrestre actual.

### 7.3.4. Dimensiones del radiotelescopio

En la última sección del mensaje identificamos una figura correspondiente al radiotelescopio de Arecibo.

Después de conocer su significado, examinamos una secuencia de 12 bits obtenida de las filas 71 y 72, entre las columnas 7 y 12.

La secuencia recuperada fue:

$$  
(100101111110)_2=2430.  
$$

Utilizando nuevamente la longitud de onda como referencia:

$$  
D=2430(12.6\text{ cm})  
$$

$$  
D=30,618\text{ cm}  
$$

$$  
\boxed{D=306.18\text{ m}}.  
$$

Este resultado proporciona una aproximación al diámetro del reflector representado.

**Análisis:** inicialmente interpretamos esta figura como una posible construcción arquitectónica. La revelación permitió identificar su significado y reconocer que también contenía información numérica.

### 7.3.5. Conclusión de las verificaciones

Las comprobaciones muestran que los valores numéricos pueden recuperarse mediante procedimientos matemáticos y computacionales, siempre que conozcamos la disposición y el orden de lectura de los bits.

Sin embargo, recuperar un número no equivale necesariamente a comprender su significado.

Para interpretar las cantidades obtenidas necesitamos reconocer las convenciones empleadas, las unidades de medida y el contexto científico de cada sección.

---

## 7.4. Preguntas posteriores a la revelación

### Pregunta 1

> ¿Qué parte del mensaje habrían podido descifrar sin saber química? ¿Y sin saber que en 1974 Plutón contaba como planeta? Agreguen esas convenciones a su lista.

**Respuesta**

Sin conocimientos de química, habríamos podido descifrar algunas representaciones numéricas del mensaje, como los números del 1 al 10 y los valores 1, 6, 7, 8 y 15, utilizando nuestros procedimientos de lectura y conversión binaria.

Sin embargo, no habríamos podido identificar que estos últimos números corresponden a elementos de la tabla periódica ni establecer su relación con la composición del ADN.

Esto demuestra que debemos distinguir entre recuperar información numérica e interpretar su significado científico.

Por otra parte, si hubiéramos reconocido la representación del sistema solar, pero desconociéramos que Plutón era considerado un planeta en 1974, la presencia de un noveno cuerpo podría generar confusión.

Inicialmente podríamos interpretarlo como una marca adicional, un elemento de control o una estructura con otra función dentro del mensaje.

La clasificación de Plutón cambió en 2006, cuando pasó a considerarse un planeta enano. Por ello, la interpretación del mensaje también requiere conocer el contexto histórico en el que fue construido.

Esta necesidad de contexto aparece en otras secciones. Por ejemplo, la población terrestre representada corresponde aproximadamente a la época de transmisión y no a la población actual. Asimismo, las dimensiones del radiotelescopio describen el instrumento original y no necesariamente otros instrumentos que puedan construirse posteriormente.

**Conclusión**

Las matemáticas permiten recuperar cantidades y reconocer patrones, pero para interpretar correctamente el mensaje también necesitamos conocimientos científicos y del contexto histórico del emisor.

Por tanto, agregamos a nuestra lista de convenciones la identificación de elementos químicos mediante sus números atómicos, la clasificación del sistema solar utilizada en 1974 y la interpretación temporal de los datos representados.

---

### Pregunta 2

> La cabeza del humano es un solo bit, y la barra del ADN termina justo en ella. ¿Es casualidad o es un mensaje? ¿Cómo lo sabrían?

**Respuesta**

Consideramos que la conexión visual entre la barra del ADN y la cabeza de la figura humana podría ser intencional.

Una posible interpretación es que esta disposición busca comunicar que la información genética representada pertenece a la especie humana y no a otra especie.

Sin embargo, esta interpretación no constituye por sí sola una prueba de que los diseñadores tuvieran esa intención.

Podríamos intentar comprobar si la información genética representada es coherente con lo que se conocía sobre el ADN humano, pero esa comprobación biológica tampoco demostraría necesariamente que la disposición visual fue elegida para transmitir dicha relación.

Para corroborar la intención de los emisores sería más apropiado consultar explicaciones de los científicos responsables del diseño o publicaciones originales relacionadas con el mensaje.

De esta manera podríamos distinguir entre una relación que nosotros interpretamos y una relación que efectivamente fue diseñada para comunicar información.

Además, incluso si la disposición fue intencional, esto no garantiza que otra civilización pueda interpretarla correctamente.

**Conclusión**

La relación visual entre las dos figuras podría transmitir información sobre la especie humana, pero no es posible demostrar la intención del emisor únicamente a partir de la imagen. Necesitaríamos evidencia adicional sobre el diseño del mensaje.

---

### Pregunta 3

> Si ustedes hubieran diseñado el mensaje, ¿qué habrían cambiado para que fuera más fácil de leer?

**Respuesta**

Una de las principales modificaciones que propondríamos sería establecer una convención de lectura más uniforme.

Durante el laboratorio encontramos que algunas cantidades debían interpretarse de arriba hacia abajo, otras de abajo hacia arriba, de izquierda a derecha o de derecha a izquierda. Incluso fue necesario combinar varias filas o columnas para recuperar determinados valores.

Esto dificultaba el descifrado, porque no siempre resultaba evidente qué orden debíamos utilizar.

Consideramos que establecer una dirección de lectura consistente y facilitar al receptor la identificación de esa regla podría reducir la ambigüedad del mensaje.

Otra modificación sería aprovechar fenómenos y propiedades físicas que puedan reconocerse independientemente de las convenciones culturales humanas.

Por ejemplo, podríamos emplear constantes físicas universales, como la constante de gravitación universal, o fenómenos astronómicos observables para proporcionar referencias comunes.

Entre estas posibilidades investigamos el uso de los **púlsares** como referencias temporales.

#### Los púlsares como relojes naturales

Un púlsar es una estrella de neutrones en rotación que emite radiación en haces. Cuando uno de estos haces atraviesa nuestra línea de visión, detectamos un pulso.

Como algunos púlsares presentan una rotación muy estable, sus pulsos permiten medir intervalos de tiempo con gran precisión.

Sin embargo, muchos púlsares pierden energía gradualmente, lo que hace que disminuya su frecuencia de rotación y aumente su período.

Recordemos que:

$$  
P=\frac{1}{f},  
$$

donde (P) representa el período y (f) la frecuencia.

Si una civilización conoce el período que tenía un púlsar en el momento de transmitir un mensaje y puede determinar cómo ha evolucionado, podría utilizar esa información para estimar el tiempo transcurrido.

Para ello no sería suficiente indicar únicamente el período: también sería necesario identificar el púlsar y disponer de información sobre su evolución.

Esta referencia temporal podría ayudar a interpretar datos históricos, como la población humana representada en el mensaje.

No obstante, también identificamos una limitación: aunque los fenómenos físicos obedecen leyes universales, su representación y medición siguen requiriendo convenciones que el receptor debe reconocer.

**Conclusión**

Propondríamos dos modificaciones principales:

1. Establecer una convención de lectura más uniforme y reconocible.
    
2. Incorporar referencias físicas y astronómicas que faciliten la interpretación de las medidas y del contexto temporal del mensaje.
    

Estas modificaciones no eliminarían todas las dificultades de comunicación, pero podrían reducir algunas de las ambigüedades que encontramos durante el laboratorio.

---

## 7.5. Convenciones identificadas después de la revelación

Después de analizar el significado del mensaje, reconocimos que su interpretación depende de diversas convenciones.

|Convención|Importancia para interpretar el mensaje|
|---|---|
|Disposición rectangular de los bits|Permite reconstruir la representación visual a partir de una secuencia lineal.|
|Dirección de lectura|Determina el orden en que deben interpretarse las filas, columnas y cantidades.|
|Sistema de numeración binario|Permite recuperar los valores numéricos representados.|
|Números atómicos|Permiten asociar determinadas cantidades con elementos químicos.|
|Conocimientos de biología|Permiten reconocer los nucleótidos, el ADN y su relación con el ser humano.|
|Unidades de referencia|Permiten interpretar las magnitudes físicas, como la estatura y el diámetro del radiotelescopio.|
|Clasificación histórica de los planetas|Permite comprender por qué el mensaje representa nueve planetas.|
|Contexto temporal|Permite interpretar correctamente datos que cambian con el tiempo, como la población humana.|
|Relaciones espaciales entre figuras|Pueden comunicar asociaciones entre diferentes secciones del mensaje, aunque su significado no siempre sea evidente.|


También consideramos que, para diseñar futuros mensajes, podrían utilizarse referencias físicas universales y fenómenos astronómicos, como los púlsares. Estas son **propuestas de mejora**, no convenciones que hayamos identificado como parte del mensaje original de Arecibo.

---

## 7.6. Reflexión final

La revelación del mensaje nos permitió comprender que representar información y conseguir que otra persona o civilización la interprete correctamente son problemas diferentes.

Durante el laboratorio logramos reconstruir la matriz de bits, identificar patrones, reconocer algunas figuras y recuperar cantidades mediante funciones que desarrollamos en Python.

No obstante, varias secciones solamente adquirieron un significado claro después de conocer su interpretación.

Esto demuestra que las herramientas matemáticas y computacionales son necesarias para analizar la información, pero no siempre son suficientes para comprenderla.

También reconocimos la importancia de los conocimientos científicos, las convenciones de lectura y el contexto histórico. Incluso cuando una representación es matemáticamente correcta, puede resultar ambigua para un receptor que desconoce las reglas utilizadas por el emisor.

Finalmente, la actividad nos permitió distinguir entre tres procesos:

- **Reconocer:** identificar patrones o figuras en una representación.
    
- **Descifrar:** recuperar información mediante reglas o procedimientos verificables.
    
- **Interpretar:** asignar significado a la información recuperada utilizando conocimientos y contexto.
    

En conclusión, consideramos que el principal desafío de la comunicación con otra civilización no consiste únicamente en transmitir una secuencia de bits, sino en lograr que el receptor pueda reconstruir las convenciones necesarias para interpretarla.# 7. La revelación del mensaje de Arecibo

---
## 5. Referencias y materiales utilizados

- Guía L1 — Primer contacto.
    
- Cuaderno `L1_sesion1.ipynb`.
    
- Repositorio del curso: [Laboratorios de Cálculo 2026-2](https://github.com/cmorregof/labs-calculo-2026-2).
    
- Documentación de Python consultada, si corresponde.
    
- Evidencias y resultados obtenidos durante la ejecución.
    