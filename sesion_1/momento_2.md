# Sesión 1 — Momento 2: Ejecutar

### L1 — Primer contacto · Introducción a las Ciencias de la Computación

---

## 1. Información de la actividad

|Campo|Descripción|
|---|---|
|Laboratorio|L1 — Primer contacto|
|Sesión|1 — Recibir|
|Momento|2 — Ejecutar|
|Cuaderno de trabajo|`L1_sesion1.ipynb`|
|Entorno de ejecución|Google Colab / Python|
|Objetivo|Construir y utilizar herramientas computacionales para analizar el mensaje de Arecibo.|

### 1.1. Propósito

En este momento pasamos de las predicciones y propuestas realizadas durante el Momento 1 a la experimentación computacional.

El objetivo es construir y utilizar diferentes funciones en Python que permitan examinar la secuencia binaria, identificar sus propiedades, determinar sus posibles dimensiones rectangulares, visualizar su estructura y comenzar a interpretar la información que contiene.

Cada función debe desarrollarse a partir de su contrato, implementarse en el cuaderno y verificarse mediante pruebas con `assert`, según las indicaciones de la guía.

> [!IMPORTANT]  
> **Criterio de trabajo**
> 
> El código se desarrolla primero en el cuaderno `L1_sesion1.ipynb`. En este documento se conservarán las implementaciones propias, las pruebas, los resultados obtenidos y las observaciones realizadas durante la ejecución.
> 
> Las celdas identificadas como **CAJA** ya están implementadas en el cuaderno. No es necesario reproducir su código interno; basta con documentar su utilización y los resultados relevantes.

---

## 2. Desarrollo de la ejecución

### 2.1. Actividad 1 — Traer y conocer el dato

#### 2.1.1. Descripción

El primer paso consiste en obtener el mensaje de Arecibo mediante la función `cargar_mensaje()`, proporcionada como una caja en el cuaderno.

También se utiliza `huella(bits)`, que permite obtener información sobre la secuencia, como la cantidad de unos y su huella digital SHA-256.

Antes de aplicar cualquier algoritmo, es necesario examinar los datos y conocer sus características básicas.

#### 2.1.2. Exploración de la secuencia

Se deben determinar las siguientes propiedades:

- Longitud total de la cadena.
    
- Caracteres distintos que aparecen.
    
- Cantidad de unos.
    
- Cantidad de ceros.
    
- Primeros 60 caracteres de la secuencia.
    

#### 2.1.3. Implementación propia

**Código desarrollado en Python:**

```python
n_caracteres = len(bits)
distintos = set(bits)
n_unos = bits.count("1")
n_ceros = bits.count("0")

print("caracteres:", n_caracteres)
print("distintos:", distintos)
print("unos/ceros:", n_unos, n_ceros)
print(bits[:60])
```
#### 2.1.4. Resultados de ejecución

|Propiedad|Resultado obtenido|
|---|---|
|Número de caracteres|1679|
|Caracteres distintos|`{'1', '0'}`|
|Cantidad de unos|397|
|Cantidad de ceros|1282|
|Primeros 60 caracteres|`000000101010100000000000010100000101000000010010001000100010`|

#### 2.1.5. Análisis

**Preguntas orientadoras:**

- ¿Qué características podemos identificar al observar la secuencia?
    
- ¿Qué información podemos obtener directamente de los datos sin aplicar todavía un proceso de decodificación?
    

**Observaciones:**

> [!TIP]  
> **Hipótesis sobre la representación gráfica**
> 
> Si interpretamos la secuencia como la representación binaria de un dibujo, podemos proponer que los ceros correspondan al fondo y los unos a los detalles de la imagen.
> 
> Esta interpretación permitiría explicar por qué hay una cantidad considerablemente mayor de ceros que de unos: el fondo podría ocupar una superficie mayor que los elementos dibujados.
> 
> Sin embargo, todavía necesitamos conocer la distribución y organización de los bits para determinar si esta hipótesis tiene sentido.

> [!IMPORTANT]  
> **Posibles dimensiones de la imagen**
> 
> Como:
> 
> $$1679=23\times73$$
> 
> existen cuatro parejas ordenadas de dimensiones:
> 
> $$1\times1679,\quad 23\times73,\quad 73\times23,\quad 1679\times1$$
> 
> Si suponemos que el mensaje representa una imagen bidimensional, podemos considerar menos probables las dimensiones lineales:
> 
> $$1\times1679 \qquad \text{y} \qquad 1679\times1$$
> 
> Por tanto, las dos posibilidades bidimensionales que resulta interesante examinar son:
> 
> $$23\times73 \qquad \text{y} \qquad 73\times23$$
> 
> Estas dimensiones son posibilidades matemáticas que debemos contrastar con la representación visual.

> [!NOTE]  
> **Influencia de las dimensiones en la representación**
> 
> Aunque las matrices de dimensiones (23\times73) y (73\times23) contienen la misma cantidad de elementos, pueden generar dibujos muy diferentes debido a la distribución de los bits.
> 
> Esto muestra que conocer únicamente la cantidad de bits no es suficiente para reconstruir una imagen. También es necesario conocer sus dimensiones y el orden de lectura.

> [!NOTE]  
> **Influencia del marco cognitivo del receptor**
> 
> La selección de una posible representación también depende de la forma en que la especie receptora percibe e interpreta el mundo. Sus capacidades cognitivas, conocimientos, experiencias y convenciones culturales pueden influir en la manera en que reconoce y comprende los patrones presentes en el mensaje.
> 
> Por esta razón, una representación que para nosotros resulte reconocible podría no tener el mismo significado para otra especie. La interpretación debe considerar no solamente la estructura de la información, sino también las características del receptor que intenta descifrarla.

> [!NOTE]  
> **Dificultad de establecer una comunicación**
> 
> Una posible estrategia sería transmitir primero información sencilla que permita explicar cómo percibimos e interpretamos nuestro entorno. Para ello, sería necesario establecer convenciones, representar elementos conocidos para nosotros y mostrar las relaciones que existen entre ellos.
> 
> Sin embargo, surge una dificultad: desconocemos cómo percibe y procesa la información la especie receptora. Por tanto, no podemos garantizar que nuestras representaciones tengan para ella el mismo significado que tienen para nosotros.

> [!NOTE]  
> **Construcción progresiva de un lenguaje común**
> 
> Dado que desconocemos el sistema matemático y lógico de la especie receptora, considero más conveniente comenzar representando elementos de nuestro mundo. A partir de ellos, podríamos mostrar características, semejanzas, diferencias y relaciones.
> 
> Posteriormente, podríamos introducir la manera en que los seres humanos utilizamos esas relaciones para construir conceptos matemáticos y establecer razonamientos lógicos. De esta forma, intentaríamos construir progresivamente una base de comunicación compartida, sin asumir que la especie receptora utiliza nuestras mismas convenciones.

#### 2.1.6. Representación y almacenamiento

El mensaje contiene una secuencia de 1.679 dígitos binarios. Sin embargo, cuando se almacena como una cadena de texto, cada dígito se representa mediante un carácter.

Por tanto, es importante distinguir entre la longitud de la secuencia binaria y el espacio que ocupa su representación textual en un archivo.


```python

bits_en_disco = len(bits.encode("ascii")) * 8

print("El mensaje tiene", len(bits), "bits de información y ocupa", bits_en_disco, "bits en el disco.")

```

**Resultado obtenido al ejecutar el cálculo:**

```
El mensaje tiene 1679 bits de información y ocupa 13432 bits en el disco.

```

**Pregunta de análisis:**

>¿Cuál es la diferencia entre el carácter `'1'` y el bit `1`?

El `bit` 1 representa una unidad lógica que puede tomar el valor de `1` o  `0
mientras que el carácter `'1'` es un símbolo que ocupa 8 bits.

>[!NOTE]
>
>#### **¿Por qué no podemos considerar que ambos son exactamente el mismo dato?** 
>
>Interpretando que ambos tienen el mismo significado perderemos información relevante, por ejemplo el carácter `'00011'`  nos podría determinar una sección de un dibujo en pixeles, al convertirlo en un entero, obtenemos `11` que representa el numero `11` en decimal o el numero `6`en base 5, por lo tanto no podemos interpretarlos como si fueran el mismo dato.

---

### 2.2. Actividad 2 — La llave: función `es_primo(n)`

#### 2.2.1. Descripción

En esta actividad se retoma el algoritmo de primalidad trabajado en la clase 5 y se traduce a Python.

El propósito es construir una función que permita determinar si un número entero es primo, devolviendo un valor booleano:

- `True`: el número es primo.
    
- `False`: el número no es primo.
    

Función en PSeInt:

```
esPrimo <- (n >= 2);d <- 2;
Mientras d * d <= n y esPrimo Hacer    
	Si n mod d = 0 Entonces        
		esPrimo <- Falso;    
	FinSi    d <- d + 1;
FinMientras
```

#### 2.2.2. Implementación propia

**Código desarrollado en Python:**

```python
def es_primo(n):
	esPrimo=(n>=2)
	d=2  
	
	while d*d <=n and esPrimo:
	
		if n%d==0:	
			esPrimo=False
	
		d+=1
	return esPrimo
```

#### 2.2.3. Pruebas y verificación

La función se debe probar con diferentes números para comprobar su comportamiento.

| Número | Resultado esperado | Resultado obtenido |
| ------ | ------------------ | ------------------ |
| 91     | No primo           | False              |
| 97     | Primo              | True               |
| 1679   | No primo           | False              |

**Resultado de las pruebas con** `**assert**`**:**

```
✔ es_primo pasa las pruebas. 
¿1679 es primo? False
```


> [!TIP]  
> **Relación con los conocimientos previos**
> 
> Esta actividad permite reutilizar el algoritmo de primalidad desarrollado anteriormente y adaptarlo a un lenguaje de programación mediante funciones, condiciones y ciclos.

---

### 2.3. Actividad 3 — Las formas posibles: función `rectangulos(n)`

#### 2.3.1. Descripción

En esta actividad se construye una función que permite encontrar todas las parejas de dimensiones enteras positivas cuyo producto sea igual a un número determinado.

La función `rectangulos(n)` debe devolver una lista de parejas ordenadas:

$$  
(\text{filas},\text{columnas})  
$$

que satisfagan:

$$  
\text{filas}\cdot\text{columnas}=n  
$$

El resultado debe estar ordenado de menor a mayor número de filas.

#### 2.3.2. Implementación propia

**Código desarrollado en Python:**
```python
def rectangulos(n):

    parejas = []

    for i in range(1,n+1):
        for j in range(1,n+1):
            if i*j == n:
                parejas.append((i,j))

    return parejas
```

#### 2.3.4. Pruebas y resultados

La función se prueba inicialmente con números pequeños para verificar que encuentre correctamente las parejas de factores.

Posteriormente, se ejecuta con 1.679 y 1.680 para comparar las configuraciones posibles.

| Número | Resultado obtenido                                                                                                                                                                                                                                                                                                                                                                                 | Número de parejas |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------------: |
| 12     | [(1, 12), (2, 6), (3, 4), (4, 3), (6, 2), (12, 1)]                                                                                                                                                                                                                                                                                                                                                 |         6         |
| 7      | [(1, 7), (7, 1)]                                                                                                                                                                                                                                                                                                                                                                                   |         2         |
| 1679   | [(1, 1679), (23, 73), (73, 23), (1679, 1)]                                                                                                                                                                                                                                                                                                                                                         |         4         |
| 1680   | [(1, 1680),(2, 840),(3, 560),(4, 420),(5, 336),(6, 280),(7, 240),(8, 210), (10, 168),(12, 140),(14, 120),(15, 112),(16, 105),(20, 84),(21, 80),<br>(24, 70),(28, 60),(30, 56),(35, 48),(40, 42),(42, 40),(48, 35),(56, 30),<br>(60, 28),(70, 24),(80, 21),(84, 20),(105, 16),(112, 15),(120, 14),<br>(140, 12),(168, 10),(210, 8),(240, 7),(280, 6),(336, 5),(420, 4),(560, 3),(840, 2),(1680, 1)] |        40         |



**Resultado de las pruebas con** `**assert**`**:**

```
✔ rectangulos pasa las pruebas. 
Formas de acomodar 1679: [(1, 1679), (23, 73), (73, 23), (1679, 1)] 
Formas de acomodar 1680: 40
```

#### 2.3.5. Comparación y análisis

Durante el Momento 1 identificamos que la factorización de 1.679 permite obtener las dimensiones de sus rectángulos.

Ahora debemos confrontar ese razonamiento con los resultados del programa.

**Preguntas de análisis:**
   
>¿Por qué quien diseñó el mensaje pudo elegir una cantidad de bits que es producto de dos números primos?

Una posible ventaja de elegir una cantidad de bits que sea producto de dos números primos es que se obtiene un número reducido de posibles configuraciones rectangulares. Como observamos, 1.679 tiene únicamente cuatro divisores positivos, lo que limita las dimensiones posibles de la matriz.

Esto podría facilitar la identificación de la organización original del mensaje, ya que reduce la cantidad de configuraciones que deben considerarse. Sin embargo, no podemos asegurar que esta haya sido la intención del diseñador.

>¿Qué diferencia encontramos al comparar 1.679 con 1.680?
    
El número `1.679` tiene únicamente cuatro divisores positivos y, por tanto, permite construir cuatro parejas ordenadas de dimensiones rectangulares. En cambio, `1.680` tiene cuarenta divisores positivos y permite construir cuarenta parejas ordenadas.

Esto significa que `1.680` admite una mayor cantidad de configuraciones rectangulares que `1.679`, lo que aumenta las posibilidades de organizar sus elementos en filas y columnas.

#### 2.3.6. Optimización del algoritmo (opcional)

La guía propone una mejora: en lugar de probar todos los números hasta (n), se puede utilizar la cota:

$$  
d\leq\sqrt{n}  
$$

La idea es aprovechar que cada divisor pequeño permite obtener su pareja mediante la división entera.

**Implemetación original con contador de vueltas**

```python
def rectangulos(n):

    parejas = []
	vueltas=0
	
    for i in range(1,n+1):
        for j in range(1,n+1):
            if i*j == n:
                parejas.append((i,j))
                
			vueltas+=1
    return parejas
```

**Implementación de la versión optimizada:**

```python
def rectangulos_2(n):

	parejas=[]
	
	d=1
	vueltas=0
	
	while d*d<=n:	
		if n % d==0:
		
			parejas.append((d,n//d))
			
			#La condicion evita repetir pareja cuando es un cuadrado perfecto
			if(d != n//d):			
				parejas.append((n//d,d))
		
		vueltas+=1		
		d+=1
	
	print(f"el Algoritmo hizo: {vueltas} vueltas")
	return parejas
```

**Comparación de las dos versiones:**

| Número  | Algoritmo          |      Número de iteraciones      |
| ------- | ------------------ | :-----------------------------: |
| 1679    | Versión original   |             2819041             |
| 1679    | Versión optimizada |               40                |
| 1000000 | Versión original   | 2 min y aun seguia en ejecucion |
| 1000000 | Versión optimizada |              1000               |


---

### 2.4. Actividad 4 — Ver: funciones `filas_de()` y `dibujar()`

#### 2.4.1. Descripción

Una vez conocidas las posibles dimensiones del mensaje, el siguiente paso consiste en organizar la secuencia binaria en una representación bidimensional.

Para ello, se construyen dos funciones:

- `filas_de(bits, columnas)`: devuelve una lista de renglones con la cantidad de columnas especificada.
    
- `dibujar(bits, columnas)`: utiliza la función anterior para imprimir la representación visual del mensaje.
    

En la representación se utiliza:

- `1`: bloque lleno.
    
- `0`: espacio vacío.
    

#### 2.4.2. Contratos de las funciones

**Función:** `filas_de(bits, columnas)`

[Registrar aquí el contrato indicado en el cuaderno.]

**Función:** `dibujar(bits, columnas)`

[Registrar aquí el contrato indicado en el cuaderno.]

#### 2.4.3. Implementación propia

**Código desarrollado en Python:**

```
# Pegar aquí las implementaciones propias de filas_de()
# y dibujar().
```

#### 2.4.4. Pruebas y verificación

Se realizan pruebas con secuencias pequeñas para verificar que la distribución de los bits corresponda con el número de columnas indicado.

**Resultados de las pruebas con** `**assert**`**:**

```
Pegar aquí el resultado de la ejecución.
```

#### 2.4.5. Visualización del mensaje

La guía propone probar dos distribuciones del mensaje:

**Primera representación: 73 columnas**

```
# Registrar aquí la instrucción utilizada para dibujar el mensaje.
```

**Resultado visual:**

[Insertar aquí una captura de la salida obtenida.]

**Segunda representación: 23 columnas**

```
# Registrar aquí la instrucción utilizada para dibujar el mensaje.
```

**Resultado visual:**

[Insertar aquí una captura de la salida obtenida.]

#### 2.4.6. Visualización mediante imagen

El cuaderno también proporciona la función `dibujar_imagen(bits, columnas)`, que permite representar la secuencia como una imagen con una cuadrícula numerada.

**Instrucción ejecutada:**

```
# Registrar aquí la instrucción utilizada.
```

**Resultado:**

[Insertar aquí la imagen obtenida.]

#### 2.4.7. Análisis

Después de observar las dos representaciones, debemos determinar cuál permite identificar una estructura reconocible y cuál parece corresponder a ruido.

**Observaciones:**

[Describir las diferencias entre las dos representaciones.]

**Relación con el Momento 1:**

[Explicar cómo las dimensiones encontradas anteriormente permiten organizar el mensaje y contrastar las hipótesis iniciales.]

> [!IMPORTANT]  
> **Deducción**
> 
> Una secuencia binaria puede adquirir una estructura visual cuando se establece una distribución determinada de filas y columnas. La elección de las dimensiones es fundamental para interpretar correctamente la información.

---

### 2.5. Actividad 5 — Leer: funciones `leer_numero()` y `columna()`

#### 2.5.1. Descripción

En esta actividad se comienza a interpretar la información contenida en la representación visual.

En la parte superior del dibujo aparecen números escritos en binario y organizados verticalmente.

Para interpretarlos se necesita construir una función que convierta una lista de bits en un número entero y otra que permita extraer una sección específica de una columna de la cuadrícula.

#### 2.5.2. Lectura de números binarios

La función `leer_numero(lista_bits)` recibe una lista de valores binarios y devuelve el entero que representan en base 2.

El procedimiento se relaciona con la conversión binaria mediante un acumulador: se duplica el valor acumulado y se suma el siguiente bit.

**Ejemplo de referencia:**

$$  
1011_2=1\cdot8+0\cdot4+1\cdot2+1\cdot1=11  
$$

#### 2.5.3. Contrato de la función

**Nombre:** `leer_numero(lista_bits)`

[Registrar aquí el contrato indicado en el cuaderno.]

#### 2.5.4. Implementación propia

**Código desarrollado en Python:**

```
# Pegar aquí la implementación propia de leer_numero().
```

#### 2.5.5. Pruebas y verificación

**Resultados de las pruebas con** `**assert**`**:**

```
Pegar aquí el resultado de la ejecución.
```

#### 2.5.6. Extracción de columnas

La función `columna(bits, columnas, j, fila_desde, fila_hasta)` permite obtener una sección de una columna específica de la representación.

**Nombre:** `columna()`

**Contrato indicado en el cuaderno:**

[Registrar aquí el contrato de la función.]

**Código desarrollado en Python:**

```
# Pegar aquí la implementación propia de columna().
```

#### 2.5.7. Interpretación del mensaje

La guía indica que existe una dirección de lectura que permite reconocer la primera sección del mensaje.

Para identificarla, se deben probar las dos direcciones posibles y justificar cuál produce una interpretación coherente.

**Direcciones evaluadas:**

[Registrar las dos alternativas que se probaron.]

**Resultado de la primera sección:**

[Documentar lo que se logró interpretar mediante el código.]

Posteriormente, se debe analizar la segunda sección, que contiene cinco números que pueden relacionarse con elementos de la tabla periódica.

**Resultados obtenidos:**

|Número leído|Interpretación|Evidencia|
|---|---|---|
|1|||
|2|||
|3|||
|4|||
|5|||

#### 2.5.8. Análisis

**Preguntas orientadoras:**

- ¿Qué diferencia existe entre convertir correctamente una secuencia de bits en un número y comprender el significado que representa ese número?
    
- ¿Qué importancia tiene la dirección de lectura para interpretar la información?
    

**Observaciones:**

[Escribir aquí el análisis propio.]

---

### 2.6. Actividad 6 — Inventario del mensaje

#### 2.6.1. Descripción

Una vez desarrolladas las herramientas anteriores, debemos utilizar los resultados obtenidos para elaborar un inventario de las diferentes partes del mensaje.

Es importante distinguir entre la información que se logró descifrar mediante el código y aquella cuya interpretación todavía depende de observaciones visuales o hipótesis.

#### 2.6.2. Inventario de las secciones

|Sección del mensaje|Resultado obtenido|Método utilizado|Nivel de certeza|
|---|---|---|---|
|Primera sección||||
|Segunda sección||||
|Tercera sección||||
|Cuarta sección||||
|Otras partes identificadas||||

#### 2.6.3. Diferencia entre descifrar e interpretar

Para cada sección debemos identificar si el resultado proviene de una operación computacional verificable o de una interpretación basada en la observación del dibujo.

- **Descifrado mediante código:** información obtenida mediante las funciones y operaciones implementadas.
    
- **Interpretación visual:** hipótesis formuladas al observar las representaciones obtenidas.
    
- **Información pendiente:** elementos que todavía no se pueden interpretar con suficiente evidencia.
    

**Análisis propio:**

[Explicar qué partes se lograron descifrar y cuáles siguen siendo hipótesis.]

> [!IMPORTANT]  
> **Conclusión de la actividad**
> 
> El hecho de obtener una representación visual o un número a partir de una secuencia binaria no implica automáticamente que se haya comprendido su significado. Es necesario diferenciar los resultados verificables de las interpretaciones que todavía requieren evidencia.

---

## 3. Síntesis de la ejecución

### 3.1. Inventario de herramientas utilizadas y construidas

|Función|Propósito|Estado de implementación|Pruebas|
|---|---|---|---|
|`cargar_mensaje()`|Obtener la secuencia binaria.|Caja proporcionada||
|`huella(bits)`|Obtener información de la secuencia y su SHA-256.|Caja proporcionada||
|`es_primo(n)`|Determinar si un número es primo.|||
|`rectangulos(n)`|Obtener las parejas de dimensiones posibles.|||
|`rectangulos_rapido(n)`|Optimizar la búsqueda de divisores.|Opcional||
|`filas_de(bits, columnas)`|Organizar la secuencia en renglones.|||
|`dibujar(bits, columnas)`|Imprimir la representación visual.|||
|`dibujar_imagen(bits, columnas)`|Mostrar la representación como imagen.|Caja proporcionada||
|`leer_numero(lista_bits)`|Convertir una lista de bits a un entero.|||
|`columna(...)`|Extraer una sección de una columna.|||

### 3.2. Resultados principales

**Resultado 1 — Exploración de los datos**

[Registrar el resultado más importante de la exploración.]

**Resultado 2 — Propiedades matemáticas**

[Registrar los resultados obtenidos con las funciones de primalidad y rectángulos.]

**Resultado 3 — Representación visual**

[Registrar qué se observó al distribuir los bits en filas y columnas.]

**Resultado 4 — Interpretación**

[Registrar qué información se logró descifrar.]

### 3.3. Dificultades encontradas

|Dificultad|Causa identificada|Cómo se verificó o resolvió|
|---|---|---|
||||
||||
||||

### 3.4. Conclusión del Momento 2

En este momento se pasó de las hipótesis iniciales a la experimentación mediante herramientas computacionales.

La implementación de funciones permitió examinar la secuencia binaria, estudiar sus propiedades matemáticas, construir posibles distribuciones rectangulares, visualizar el mensaje y comenzar a interpretar su contenido.

El proceso también permitió comprobar que una herramienta computacional debe tener un propósito definido, un contrato claro y pruebas que permitan verificar su comportamiento.

**Conclusión propia:**

[Escribir aquí qué aprendiste durante la ejecución y cómo cambiaron o se confirmaron las ideas del Momento 1.]

---

## 4. Registro del uso de inteligencia artificial

> [!IMPORTANT]  
> El uso de inteligencia artificial debe respetar el protocolo establecido en la guía del laboratorio. No se deben solicitar a la herramienta las funciones del cuaderno, los contratos de lectura, las soluciones de los ejercicios ni las respuestas del Momento 3.

### 4.1. Consultas realizadas

|Actividad|Consulta realizada|Aporte recibido|Evaluación|
|---|---|---|---|
|Actividad 1||||
|Actividad 2||||
|Actividad 3||||
|Actividad 4||||
|Actividad 5||||
|Actividad 6||||

### 4.2. Evaluación de los aportes

Los aportes recibidos deben clasificarse según su utilidad y su correspondencia con el trabajo realizado.

- **Aceptados:** explicaciones que se comprobaron y resultaron correctas.
    
- **Modificados:** explicaciones que necesitaron ajustes.
    
- **Rechazados:** respuestas que no se utilizaron por falta de coherencia o evidencia.
    

### 4.3. Verificación

[Describir cómo se comprobaron los aportes recibidos mediante el cuaderno, las pruebas `assert` o el razonamiento propio.]

### 4.4. Reflexión sobre el uso de IA

[Escribir una reflexión sobre el papel de la IA durante la ejecución, sus limitaciones y la importancia de verificar sus respuestas.]

---

## 5. Referencias y materiales utilizados

- Guía L1 — Primer contacto.
    
- Cuaderno `L1_sesion1.ipynb`.
    
- Repositorio del curso: [Laboratorios de Cálculo 2026-2](https://github.com/cmorregof/labs-calculo-2026-2).
    
- Documentación de Python consultada, si corresponde.
    
- Evidencias y resultados obtenidos durante la ejecución.
    

---

_Laboratorio L1 — Primer contacto · Sesión 1 · Momento 2 — Ejecutar_