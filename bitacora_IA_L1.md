# Bitácora de IA · L1 Primer contacto

**Nombre:** Maicol Chizabas
**Equipo / especie:** Glitx Synkai  
**Asistentes:** ChatGPT y Gemini

> Registro condensado de las intervenciones más importantes. Las consultas de la tabla son fragmentos literales representativos; no sustituyen el registro de cada consulta individual que pide la plantilla oficial. Usé la IA para revisar mis ideas, no para sustituir mis implementaciones.

| # | Qué pedí (fragmento literal) | Qué aportó la IA | Qué acepté, corregí o rechacé | Cómo lo comprobé |
|---|---|---|---|---|
| 1 | «mi idea era encontrar cual era el numero mas grande que divide a 1679» | Orientación sobre divisores y factorización. | Utilicé la factorización prima. | Verifiqué $1679=23\times73$ y sus rectángulos. |
| 2 | «noto que estas pruebas tienen un error» | Revisión de pruebas de `filas_de()` y `dibujar()`. | Corregí la prueba para usar la cadena correspondiente. | Ejecuté las pruebas y reconstruí el dibujo en Colab. |
| 3 | «procedamos a organizar la informacion que tenemos» | Revisión y organización de la tarea puente. | Conservé mi diseño del laberinto y el personaje; aclaré las convenciones. | Contrasté el boceto con los 1679 bits; verifiqué Arecibo mediante SHA-256 y las conversiones con pruebas en Python. |
| 4 | «podemos usar en cada renglo count(1) y count(0)» | Aclaración sobre cadenas, paridad y errores en mis funciones. | Corregí mis propias implementaciones. | Las cinco funciones del canal pasaron las pruebas del profesor. |
| 5 | «la de paridad me parece mejor» | Explicó la diferencia entre detectar y corregir errores. | Cambié mi elección a repetición triple. | En 1000 simulaciones hubo 459 recuperaciones exactas; el archivo final tuvo 7473 bits. |
| 6 | «de momento el tres nos puede dar una pista de que uso proteccion triple?» | Ayudó a evaluar la hipótesis sin darla por segura. | Contrasté protección, dimensiones y conteo del mensaje recibido. | Obtuve 422 grupos uniformes de 437, 19 columnas y patrones compatibles con base 6. |
| 7 | «identifico una taza, y tambien una especie de greca» | Propuso posibles lecturas de las figuras. | Conservé solo hipótesis provisionales: taza y cruz; descarté afirmar que fuera una greca. | Revisé la imagen; falta contrastarla con el contrato del emisor. |

## Experimento estrella — Sesión 1

Entregué a **Gemini** los **1679 bits de Arecibo sin contexto**. Identificó el mensaje, propuso la matriz $73\times23$ y describió figuras como la humana y el ADN. Comprobé la longitud, los factores y la visualización con mis herramientas. **No puedo asegurar que lo descifrara desde cero:** pudo reconocer un mensaje conocido. Para distinguirlo, propongo repetir el experimento con un mensaje nuevo no publicado.

## Contraprueba — Sesión 2

Analicé con ChatGPT capturas y observaciones de un mensaje desconocido de **1311 bits**, pero **no realicé aún la contraprueba formal de entregar solamente la cadena sin pistas**. Inferimos provisionalmente repetición triple, una matriz de $23\times19$, conteo en base 6 y posibles figuras de taza y cruz. **El contrato de lectura no ha sido revelado**, de modo que no puedo afirmar cuáles interpretaciones fueron correctas ni si la IA inventó significados.

## Conclusión

La IA me ayudó a detectar errores, aclarar conceptos y organizar mis notas.  
Las funciones, decisiones y pruebas fueron desarrolladas y verificadas por mí.  
Una respuesta convincente no equivale a una interpretación demostrada.  
Distinguiré siempre las observaciones, las hipótesis y las verificaciones.  
Desconfiaré especialmente cuando la IA afirme significados sin evidencia independiente.
