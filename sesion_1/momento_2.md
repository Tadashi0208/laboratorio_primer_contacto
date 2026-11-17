# Sesión 1 — Momento 2: Ejecutar

**Laboratorio L1 — Primer contacto · Cuaderno:** `**L1_sesion1.ipynb**`

## Actividad 1. Traer y conocer el dato

La función proporcionada `cargar_mensaje()` permite obtener la secuencia. Para examinarla utilicé:

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

**Resultados de ejecución**

|Propiedad|Resultado|
|---|---|
|Número de caracteres|1679|
|Caracteres distintos|`{'1', '0'}`|
|Unos|397|
|Ceros|1282|
|Primeros 60 caracteres|`000000101010100000000000010100000101000000010010001000100010`|

> [!TIP]  
> **Hipótesis propia:** si los bits representan un dibujo, los ceros podrían corresponder al fondo y los unos a sus detalles. Falta contrastarlo con una distribución visual.

**Representación y almacenamiento**

```python
bits_en_disco = len(bits.encode("ascii")) * 8
print("El mensaje tiene", len(bits), "bits de información y ocupa", bits_en_disco, "bits en el disco.")
```

```
El mensaje tiene 1679 bits de información y ocupa 13432 bits en el disco.
```

**¿Qué diferencia existe entre el carácter** `**'1'**` **y el bit** `**1**`**?** El bit representa un valor binario; el carácter `'1'` es un símbolo de texto que, en la codificación ASCII utilizada, ocupa 8 bits al almacenarse. Por ello, el valor binario y su representación textual no son el mismo dato.

## Actividad 2. La llave: `es_primo(n)`

**Implementación propia**

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

**Pruebas registradas**

|Entrada|Resultado|
|---|---|
|91|`False`|
|97|`True`|
|1679|`False`|

```
✔ es_primo pasa las pruebas.
¿1679 es primo? False
```

## Actividad 3. Las formas posibles: `rectangulos(n)`

La función obtiene las parejas ordenadas `(filas, columnas)` cuyo producto es `n`.

**Implementación propia**

```python
def rectangulos(n):

    parejas = []

    for i in range(1,n+1):
        for j in range(1,n+1):
            if i*j == n:
                parejas.append((i,j))

    return parejas
```

**Pruebas registradas**

|Entrada|Número de parejas|
|---|---|
|12|6|
|7|2|
|1679|4|
|1680|40|

```
✔ rectangulos pasa las pruebas.
Formas de acomodar 1679: [(1, 1679), (23, 73), (73, 23), (1679, 1)]
Formas de acomodar 1680: 40
```

>**¿Por qué pudo elegirse una longitud que es producto de dos primos?** 

La factorización `1679 = 23 × 73` deja pocas distribuciones rectangulares posibles y podría facilitar la búsqueda de la forma original. No es posible asegurar solo con este resultado que esa fuera la intención del diseñador.

>**¿Qué cambia si hay 1680 bits?** 

En las pruebas, 1680 admite 40 parejas de dimensiones, frente a las cuatro de 1679. Por ello, hay más configuraciones que examinar.

### Optimización opcional realizada

Para reducir las divisiones probadas, desarrollé otra versión que busca divisores mientras `d*d <= n` y obtiene la pareja mediante división entera, evita duplicados y ademas ordena la lista. Esta es la implementación registrada en mis apuntes:

```python
def rectangulos_rapido(n):

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
		
	#Ordemanos las parejas
	parejas.sort()
	
	print(f"el Algoritmo hizo: {vueltas} vueltas")
	return parejas
```

```python
#Comprobando que las dos versiones devuelven las misma parejas

assert rectangulos(12)==rectangulos_rapido(12)

assert rectangulos(100)==rectangulos_rapido(100)
```

**Comparación registrada**

|Entrada|Versión original|Versión optimizada|
|---|---|---|
|1679|2 819 041 iteraciones|40 iteraciones|
|1 000 000|Más de 2 minutos sin finalizar|1000 iteraciones|

> [!NOTE]  
> La fila de 1 000 000 compara una ejecución no finalizada con un conteo de iteraciones; no son mediciones equivalentes.


---
## Actividad 4. Ver: `filas_de` y `dibujar`

### Implementación propia

La función `filas_de(bits, columnas)` organiza una cadena binaria en renglones del tamaño indicado.

```python
def filas_de(bits, columnas):
    """CONTRATO
    Recibe: una cadena de bits y un número de columnas que divide su longitud.
    Devuelve: la lista de renglones, cada uno de longitud 'columnas'.
    """
    if len(bits) % columnas == 0:
        b = columnas
        i = 0
        renglones = []

        while b <= len(bits):
            renglones.append(bits[i:b])
            i = b
            b = i + columnas

        return renglones
    else:
        print("El # de columnas debe dividir la longitud de la cadena de bits")
```

La función `dibujar(bits, columnas)` utiliza `filas_de` para imprimir los renglones, representando los unos mediante `█` y los ceros mediante espacios.

```python
def dibujar(bits, columnas):
    """CONTRATO
    Recibe: una cadena de bits y un número de columnas.
    Devuelve: nada. Imprime los renglones con '█' para 1 y ' ' para 0.
    """
    renglones = filas_de(bits, columnas)
    for i in renglones:
        aux = ''
        for j in i:
            if j == '1':
                aux += '█'
            elif j == '0':
                aux += ' '
        print(aux)
```

### Pruebas y verificación

Se ejecutaron las pruebas del cuaderno utilizando la cadena original `bits` de 1679 caracteres.

```python
assert filas_de("101100", 3) == ["101", "100"]
assert filas_de("101100", 2) == ["10", "11", "00"]
assert len(filas_de(bits, 23)) == 73
print("✔ filas_de pasa las pruebas.")
```

**Resultado:**

```
✔ filas_de pasa las pruebas.
```

### Visualización del mensaje

Se probaron las dos distribuciones indicadas en la guía:

```python
dibujar(bits, 73)
dibujar(bits, 23)
```

|Distribución|Observación|
|---|---|
|23 filas × 73 columnas|Los bloques aparecen dispersos y no logré identificar figuras reconocibles.|
|73 filas × 23 columnas|Se distinguen patrones organizados y algunas figuras conocidas.|

**Visualización mediante la función proporcionada** `**dibujar_imagen**`**:**

```python
dibujar_imagen(bits, 23)
```

**Imagen obtenida**

![Mensaje de Arecibo: 73 filas y 23 columnas](./imagenes/arecibo_23_columnas.png)


> [!NOTE]  
> **Observación:** La distribución de 23 columnas presenta una estructura visual más reconocible. Identifiqué una figura que podría representar a una persona y otra semejante a la letra M. Sin embargo, todavía no es posible asegurar que estas figuras tengan el significado que les estoy atribuyendo.

La comparación muestra que una misma secuencia binaria puede producir representaciones visuales diferentes dependiendo de cómo se organice en filas y columnas.

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