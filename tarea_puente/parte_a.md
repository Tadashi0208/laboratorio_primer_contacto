# Tarea puente — L1 Primer contacto

**Laboratorio:** Introducción a las Ciencias de la Computación

## Parte A — No me creas: reproducirlo

### A.1. Objetivo

El objetivo de esta actividad es reproducir la obtención del mensaje de Arecibo y comprobar su integridad mediante una función hash criptográfica.

Considero que no debemos confiar únicamente en el archivo proporcionado por el profesor, ya que existe la posibilidad de que haya sido modificado, accidental o intencionalmente.

Por ello, es importante obtener nuevamente la información desde su fuente original y comparar los resultados. Esto permite verificar los datos mediante un procedimiento reproducible, en lugar de depender exclusivamente de una fuente.

### A.2. Reproducción del mensaje

Para reproducir la obtención de los datos, utilizamos el programa `congelar_arecibo.py`, proporcionado en el repositorio oficial del laboratorio.

El programa descarga el mensaje desde su fuente y genera un archivo denominado `mi_arecibo.txt`.

Después de ejecutar el programa en Google Colab, obtuvimos los siguientes resultados:

|Propiedad|Resultado obtenido|
|---|---|
|Nombre del archivo|`mi_arecibo.txt`|
|Longitud del mensaje|1679 caracteres|
|Cantidad de unos|397|
|Cantidad de ceros|1282|
|Algoritmo de verificación|SHA-256|

La huella calculada fue:

`24babf56f872fc2c38c940b4a438811be454f04a041fe56b3c239662f261dd66`

### A.3. Comparación con las cifras de control

El README oficial del laboratorio proporciona las cifras de control que debemos utilizar para verificar el mensaje reproducido.

Para ello, completamos las variables del cuaderno:

```python
UNOS_README = 397
SHA_README = "24babf56f872fc2c38c940b4a438811be454f04a041fe56b3c239662f261dd66"
```

Posteriormente, ejecutamos nuevamente la celda de comparación.

**Resultados obtenidos:**

```
Mis unos: 397   README: 397
Mi SHA  : 24babf56f872fc2c38c940b4a438811be454f04a041fe56b3c239662f261dd66
README  : 24babf56f872fc2c38c940b4a438811be454f04a041fe56b3c239662f261dd66
¿Idénticos? True
```

|Propiedad|Resultado obtenido|README|Coincidencia|
|---|---|---|---|
|Cantidad de unos|397|397|Sí|
|SHA-256|`24babf56...261dd66`|`24babf56...261dd66`|Sí|
|Comparación automática|`True`|—|Verificación satisfactoria|

> [!SUCCESS] Verificación completada  
> La huella SHA-256 del mensaje reproducido coincide exactamente con la publicada en el README oficial del laboratorio. La comparación automática devolvió `True`.

**Análisis**

Inicialmente, la comparación devolvió `False`, debido a que las variables `UNOS_README` y `SHA_README` todavía no contenían los valores de referencia.

Después de completar ambas variables y ejecutar nuevamente la celda, obtuvimos `True`.

Esto proporciona evidencia extremadamente confiable de que el mensaje obtenido mediante el procedimiento de reproducción coincide con el archivo de referencia del curso.

Sin embargo, debemos recordar que la coincidencia entre huellas permite comprobar la integridad respecto a una referencia, pero no garantiza por sí sola la autenticidad de dicha referencia.

### A.4. Pregunta de análisis

> ¿Por qué comparar dos huellas de 64 caracteres es una manera confiable de saber que dos archivos de 1679 caracteres son idénticos? ¿Qué tendría que pasar para que dos mensajes distintos tuvieran la misma huella?

**Respuesta**

Comparar las huellas SHA-256 de dos archivos es un procedimiento confiable para verificar su integridad, porque el algoritmo es determinista y produce una huella de 256 bits, representada mediante 64 caracteres hexadecimales.

Aunque matemáticamente pueden existir colisiones, encontrarlas es computacionalmente muy difícil. Para una función hash ideal, encontrar una colisión cualquiera requiere aproximadamente $$2^{128}$$ intentos, mientras que encontrar otro mensaje que produzca la misma huella que uno previamente fijado, conocido como segunda preimagen, requiere aproximadamente $$2^{256}$$intentos mediante una búsqueda genérica.

Por tanto, si dos archivos producen la misma huella SHA-256, existe evidencia extremadamente confiable de que contienen la misma información, aunque no una garantía matemática absoluta de identidad.

Además, para verificar la autenticidad del mensaje, es importante que los datos utilizados como referencia provengan de una fuente independiente y confiable.

### A.5. Conclusión

La actividad permitió comprender la importancia de reproducir y verificar resultados científicos, en lugar de aceptar automáticamente la información proporcionada.

Mediante la ejecución de `congelar_arecibo.py`, recuperamos el mensaje de 1679 caracteres y comprobamos que su cantidad de unos y su huella SHA-256 coinciden con las cifras de control publicadas en el README del curso.

También distinguimos entre integridad y autenticidad, y comprendimos por qué las funciones hash criptográficas son útiles para detectar modificaciones en archivos.

Finalmente, concluimos que, aunque las colisiones son matemáticamente inevitables debido al principio del palomar, la dificultad computacional de encontrarlas hace que SHA-256 sea una herramienta confiable para verificar la integridad de los datos.

---
### A.6. Referencias

- [Repositorio oficial del laboratorio L1 — Primer contacto](https://github.com/cmorregof/labs-calculo-2026-2/tree/main/introduccion_cc)
    
- Cuaderno `L1_tarea_puente.ipynb`.
    
- Programa `congelar_arecibo.py`.
    
- README del curso, sección «Cifras de control».