## Parte B — Dos maneras de cambiar de base

### B.1. Objetivo

El objetivo de esta actividad es implementar diferentes procedimientos para convertir números entre sistemas de numeración, utilizando tanto estructuras iterativas como funciones recursivas.

Para ello, desarrollamos tres funciones:

- `a_base_ciclo(n, b)`: convierte un número decimal a una base `b` mediante un ciclo `while`.
    
- `a_base_rec(n, b)`: realiza la misma conversión utilizando recursión.
    
- `de_base(digitos, b)`: convierte una lista de dígitos en base `b` a su representación decimal.
    

Posteriormente, comparamos los resultados de las implementaciones, analizamos el funcionamiento de la pila recursiva y evaluamos las diferencias entre ambos procedimientos.

---

### B.2. Conversión iterativa: `a_base_ciclo(n, b)`

#### B.2.1. Fundamento matemático

Para convertir un número entero no negativo (n) a una base (b), podemos utilizar divisiones enteras sucesivas.

En cada división obtenemos:

$$  
n=bq+r,  
$$

donde:

- $$q=n//b$$ es el cociente entero.
    
- $$r=n\bmod b$$ es el residuo.
    
- $$0\leq r<b$$.
    

El residuo corresponde al dígito menos significativo del número en la base seleccionada.

Al repetir el procedimiento con el cociente, obtenemos los demás dígitos desde el menos significativo hasta el más significativo.

Por tanto, al finalizar debemos invertir su orden.

#### B.2.2. Implementación propia

```python
def a_base_ciclo(n, b):
    """CONTRATO
    Recibe: un entero n >= 0 y una base b >= 2.
    Devuelve: la lista de dígitos de n en base b,
              el más significativo primero.
              a_base_ciclo(0, b) devuelve [0].
    """
    if n == 0:
        return [0]

    digitos = []

    while n > 0:
        digito = n % b
        digitos.append(digito)
        n = n // b

    digitos.reverse()
    return digitos
```

#### B.2.3. Análisis de la implementación

En cada iteración calculamos el residuo de dividir `n` entre `b` y lo almacenamos en la lista `digitos`.

Después, actualizamos `n` mediante división entera para continuar con el siguiente dígito.

Como los residuos se obtienen comenzando por el dígito menos significativo, utilizamos `digitos.reverse()` para invertir la lista y cumplir el contrato de la función.

También consideramos el caso `n == 0`, para el cual devolvemos directamente `[0]`.

---

### B.3. Conversión recursiva: `a_base_rec(n, b)`

#### B.3.1. Fundamento matemático

La conversión recursiva utiliza las mismas operaciones de división entera y módulo, pero organiza el procedimiento mediante llamadas a la propia función.

Podemos expresar su funcionamiento como:

$$  
A(n,b)= 
[n], \hspace{0.5cm} 0\leq n<b
$$  $$
A(n//b,b)+[n\bmod b], \hspace{0.5cm} n\geq b
$$

El caso base ocurre cuando (n<b), pues el número puede representarse mediante un único dígito en esa base.

En los demás casos, la función realiza una llamada recursiva utilizando `n // b` y conserva el residuo para concatenarlo al resultado durante el retorno.

#### B.3.2. Implementación propia

```python
def a_base_rec(n, b):
    """Mismo contrato, escrita de forma recursiva."""
    if n < b:
        return [n]

    return a_base_rec(n // b, b) + [n % b]
```

#### B.3.3. Análisis de la implementación

A diferencia de la versión iterativa, la función recursiva no necesita utilizar `reverse()`.

Esto sucede porque primero se alcanza el caso base, correspondiente al dígito más significativo, y posteriormente se agregan los residuos al final de la lista durante el retorno de las llamadas.

Sin embargo, cada llamada debe conservar su estado mientras espera el resultado de la siguiente.

Por tanto, la implementación utiliza memoria adicional debido a la pila de llamadas recursivas.

---

### B.4. Conversión inversa: `de_base(digitos, b)`

#### B.4.1. Fundamento matemático

Para recuperar el valor decimal de un número representado en base (b), utilizamos su expansión posicional.

Si sus dígitos son:

$$  
(d_kd_{k-1}\cdots d_1d_0)_b,  
$$

entonces su valor es:

$$  
n=\sum_{i=0}^{k}d_i b^i.  
$$

También podemos calcularlo de manera acumulativa, procesando los dígitos desde el más significativo hasta el menos significativo.

Si `numero` contiene el valor acumulado, al leer un nuevo dígito `d` actualizamos:

$$  
\text{numero}\leftarrow \text{numero}\cdot b+d.  
$$

Este procedimiento generaliza la función `leer_numero()` que desarrollamos durante la sesión 1, sustituyendo la base binaria por una base cualquiera.

#### B.4.2. Implementación propia

```python
def de_base(digitos, b):
    """CONTRATO
    Recibe: una lista de dígitos en base b,
            el más significativo primero.
    Devuelve: el entero que representan.
    """
    numero = 0

    for d in digitos:
        numero = numero * b + d

    return numero
```

#### B.4.3. Análisis

La variable `numero` comienza en cero y se actualiza cada vez que recorremos un dígito.

Multiplicar el valor acumulado por `b` permite desplazar su representación una posición hacia la izquierda en esa base.

Posteriormente, sumamos el nuevo dígito.

De esta manera, la función reconstruye el valor decimal sin necesidad de calcular explícitamente cada potencia de la base.

---

### B.5. Pruebas y verificación de las funciones

Después de implementar las tres funciones, ejecutamos las pruebas proporcionadas en el cuaderno.

```python
# Pruebas
for f in (a_base_ciclo, a_base_rec):
    assert f(1974, 6) == [1, 3, 0, 5, 0], f.__name__
    assert f(13, 2) == [1, 1, 0, 1], f.__name__
    assert f(255, 16) == [15, 15], f.__name__
    assert f(0, 7) == [0], f.__name__
    assert f(5, 6) == [5], f.__name__

assert de_base([1, 3, 0, 5, 0], 6) == 1974

import random

for _ in range(1000):
    n, b = random.randint(0, 10**6), random.randint(2, 16)
    assert a_base_ciclo(n, b) == a_base_rec(n, b)
    assert de_base(a_base_rec(n, b), b) == n

print("✔ Las dos maneras coinciden en 1000 casos al azar, y de_base las deshace.")
```

#### Resultados obtenidos

|Número decimal|Base|Lista de dígitos|
|---|---|---|
|1974|6|`[1, 3, 0, 5, 0]`|
|13|2|`[1, 1, 0, 1]`|
|255|16|`[15, 15]`|
|0|7|`[0]`|
|5|6|`[5]`|

La ejecución de las pruebas fue satisfactoria:

```
✔ Las dos maneras coinciden en 1000 casos al azar, y de_base las deshace.
```

> [!SUCCESS] Pruebas superadas  
> Las implementaciones iterativa y recursiva produjeron los mismos resultados en los casos establecidos por el cuaderno y en 1000 pruebas aleatorias. Además, la función `de_base()` permitió recuperar los números originales.

Estas pruebas proporcionan evidencia de que nuestras implementaciones son consistentes, aunque no constituyen una demostración matemática de corrección para todos los valores posibles.

---

### B.6. Seguimiento de la función recursiva

El cuaderno solicita realizar un seguimiento de la ejecución:

```python
a_base_rec(1974, 6)
```

Debemos identificar cada llamada recursiva, los resultados de la división y el módulo, y los valores que quedan pendientes durante la ejecución.

#### B.6.1. Tabla de seguimiento

|Llamada|`n`|`n // 6`|`n % 6`|Devuelve|
|---|---|---|---|---|
|1|1974|329|0|`[1, 3, 0, 5, 0]`|
|2|329|54|5|`[1, 3, 0, 5]`|
|3|54|9|0|`[1, 3, 0]`|
|4|9|1|3|`[1, 3]`|
|5|1|—|—|`[1]`|

En la última llamada alcanzamos el caso base:

$$  
1<6.  
$$

Por tanto, la función devuelve `[1]` sin realizar nuevas llamadas recursivas.

Los guiones de la última fila indican que ya no es necesario ejecutar las operaciones de división y módulo.


La última llamada devuelve `[1]`, lo que permite comenzar el retorno de las llamadas pendientes.

#### B.6.2. Retorno de las llamadas

Durante el retorno se realizan las concatenaciones en el orden establecido por la función.

|Valor de `n`|Operación|Resultado|
|---|---|---|
|1|Caso base|`[1]`|
|9|`[1] + [3]`|`[1, 3]`|
|54|`[1, 3] + [0]`|`[1, 3, 0]`|
|329|`[1, 3, 0] + [5]`|`[1, 3, 0, 5]`|
|1974|`[1, 3, 0, 5] + [0]`|`[1, 3, 0, 5, 0]`|

Al principio cometí un error al interpretar las concatenaciones, porque estaba agregando los residuos al inicio de la lista.

Después de revisar la expresión:

```python
return a_base_rec(n // b, b) + [n % b]
```

comprendí que cada residuo debe concatenarse al final de la lista devuelta por la llamada anterior.

De esta manera, obtuvimos correctamente:

$$  
\boxed{1974_{10}=(13050)_6}.  
$$

Podemos comprobar el resultado utilizando la expansión posicional:

$$  
(13050)_6  
=1\cdot6^4+3\cdot6^3+0\cdot6^2+5\cdot6+0.  
$$

$$  
=1296+648+30=1974.  
$$

Por tanto, el resultado de la función recursiva coincide con el valor decimal inicial.

---

### B.7. Comparación entre las implementaciones

Después de desarrollar y probar ambas funciones, analizamos sus diferencias.

|Característica|Versión iterativa|Versión recursiva|
|---|---|---|
|Estructura utilizada|`while`|Llamadas recursivas|
|Obtención de los dígitos|Desde el menos significativo|Desde el más significativo durante el retorno|
|Necesita `reverse()`|Sí|No|
|Utiliza pila adicional de llamadas recursivas|No|Sí|
|Construcción de la lista|Modifica una misma lista|Concatena listas en cada retorno|
|Consumo adicional de memoria|Menor en esta implementación|Mayor por las llamadas recursivas|

#### ¿Cuál de las dos maneras prefiero y por qué?

Prefiero la versión iterativa porque, aunque debo invertir la lista de dígitos al final mediante `reverse()`, consume menos memoria que mi implementación recursiva, ya que no necesita mantener una pila de llamadas recursivas.

Además, en la versión recursiva se realizan concatenaciones que crean nuevas listas durante el retorno, lo que introduce un costo adicional.

Por estas razones, considero que la versión iterativa es más eficiente para este problema.

---

### B.8. Conclusión

En esta actividad desarrollamos tres funciones para trabajar con sistemas de numeración de diferentes bases.

La implementación iterativa permitió comprender cómo las divisiones sucesivas generan los dígitos de un número comenzando por el menos significativo.

Por su parte, la implementación recursiva permitió estudiar el funcionamiento del caso base, las llamadas pendientes y el retorno de resultados mediante la pila de ejecución.

También generalizamos el procedimiento de lectura de números binarios de la sesión 1 para recuperar valores decimales desde cualquier base válida.

Finalmente, las pruebas confirmaron que ambas conversiones producen los mismos resultados en los casos examinados y que la conversión inversa recupera el valor original.

Aunque ambos procedimientos cumplen con el objetivo de la actividad, preferimos la versión iterativa por su menor consumo de memoria y su eficiencia en Python.

---

### B.9. Referencias

- Cuaderno `L1_tarea_puente.ipynb`.
    
- Implementaciones propias de `a_base_ciclo()`, `a_base_rec()` y `de_base()`.
    
- Pruebas proporcionadas por el laboratorio.
    
- Análisis del seguimiento recursivo desarrollado durante la actividad.