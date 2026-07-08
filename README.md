# Estructuras Lineales

---

Antes de abordar las estructuras lineales debemos entender primero que son las estructuras de datos, las estructuras de datos son una forma de organizar y almacenar datos, los cuales pueden ser utilizados de manera eficiente. Gracias a estas, podemos realizar distintas operaciones como buscar, insertar o eliminar elementos, que nos ayudan a manejar los datos que tenemos de manera más sencilla.

Existen dos tipos de estructuras de datos, que son lineales y NO lineales. Las estructuras lineales organizan sus datos de manera secuencial, donde cada elemento tiene un unico predecesor y un unico sucesor. Mientras que las estructuras no lineales organizan la información de forma jerárquica o interconectada, permitiendo que un elemento tenga uno o varios predecesores, y uno o varios sucesores.

---

Los únicos tipos de estructuras no lineales son Árboles y grafos, los cuales se les abordara en su propio repositorio, por ende, ahora solo nos vamos a enfocar en los distintos tipos de estructuras lineales.

Como ya se dijo antes, estas organizan sus elementos de manera secuencial, como puede ser una fila de personas o los vagones de un tren, por lo que son las más sencillas de entender. Se caracterizan por ser faciles de implementar y son las mejores para ordenar elementos.

Entre los distintos tipos de estructuras lineales, los principales tipos son: 

- Arreglos
- Listas enlazadas
- Pilas
- Colas

A continuación, vamos a abordar cada tipo de manera más detallada con ejemplos prácticos.

---

## Arreglos

Es la estructura más conocida y básica de todas, consiste en almacenar elementos del mismo tipo de manera secuencial, asi mismo, a cada elemento se le asigna una posición fija que es su índice, este índice puede variar de $0$ a $n - 1 $ (siendo $n$ la longitud del arreglo), gracias a esto, se puede acceder a cualquier elemento con facilidad si se conoce su índice.

De igual manera esta se crea con un tamaño fijo, por lo que al momento de crearse se debe definir el tamaño, ya que este no cambia dinámicamente, en caso de llenarse y se necesita más espacio, debemos crear un nuevo arreglo más grande y copiar los datos.

Esta estructura es sencilla para buscar elementos, ya que todos al tener un índice predeterminado, es fácil de encontrar dichos elementos.

```
list = [1,2,3,4,5]
print(list[2])       # devuelve el elemento en el indice 2 osea 3 
```

Sin embargo, a la hora de ingresar o eliminar elementos es bastante lenta, ya que al hacerlos tengo que mover los elementos posteriores al elemento hacia atras o adelante, dependiendo el caso.

```
list = [1,2,3,4,5]
list.append(0)  # al hacer esto todos los elementos se mueven
```

Sus ejemplos más conocidos de uso no los vamos a abordar aca, ya que estos se realizaron con anterioridad que son [Búsqueda Binaria](https://github.com/JDavid-Moreno/Dividir-y-conquistar/blob/main/Algoritmos/BinarySearch.py) o los [Algoritmos de ordenamiento de arreglos](https://github.com/JDavid-Moreno/Algoritmos-de-ordenamiento), los cuales rápidamente tratan sobre encontrar el índice de un elemento conociendo el valor de dicho elemento y los algoritmos de ordenamiento, como dice su nombre, consisten en distintas maneras de ordenar un arreglo de elementos enteros.

---

## Pilas

Es una estructura lineal que utiliza el principio LIFO (Last In, First Out), el cual consiste en que el último elemento que ingreso es el primer elemento es sacar o eliminar, por eso su nombre, ya que es como una pila de cosas donde el elemento de más arriba que fue el último en ponerse, es el primero que se quita. Un ejemplo sencillo para imaginar una pila será una lata de pringles, ya que la última papa que se ingresó a la lata, posteriormente será la primera papa que se saque.

A diferencia de una arreglo en donde se puede ingresar un elemento en cualquier posición, en una pila para ingresar elementos, únicamente se puede hacer en un unico punto que es el tope, por lo que todas sus operaciones sé hacer en el tope que son:

- Apilar: Al agregar un nuevo elemento ese elemento se apila y se pone en el tope.
- Desa pilar: Al eliminar el elemento, este se quita de la pila y el elemento anterior se vuelve el nuevo tope.
- Mirar: se puede mirar únicamente el elemento tope de la pila-

```
stack = []
stack.append(10)    # unico elemento, sera el tope
stack.append(20)    # ultimo elemento en entrar, ese es el nuevo tope
stack.pop()         # sale el tope osea el 20, por lo que el 10 es el nuevo tope
stack[-1]           # se ve que elemento es el tope
```

### Cuando se usa

Generalmente, se usa cuando se necesita volver atrás, por ejemplos el atajo de teclado Ctrl + z es en realidad una pila por ejemplo, asi mismo, se utilizan pilas cuando hay estructuras anidadas o si algo que se abre se tiene que cerrar después como pueden ser las claves de HTML.

### Ejemplos 

### Paréntesis balanceados

Este problema es de los más conocidos sobre pilas, consiste en que dado una serie de paréntesis, ya sea (), { } o [ ], verificar que todos los paréntesis que se abran se cierren, si no que también, estén bien cerrados o balanceados, es decir, que no se puede cerrar un paréntesis en medio de otro.

Ejemplos:

`({[]})` Bien balanceado

`([)]` Mal balanceado

Implementación:

```
def balanced_brackets(sequence):
    stack = []
    brackets = {")": "(", "}": "{", "]": "["}
    for bracket in sequence:
        if bracket in brackets.values():
            stack.append(bracket)
        elif bracket in brackets:
            if len(stack) == 0:
                return False
            if stack[-1] != brackets[bracket]:
                return False
            stack.pop()
    return len(stack) == 0
```
 
Para abordar este problema, lo más recomendable es usar un diccionario, el cual asociamos a los paréntesis con sus compañeras. Una vez hecho esto, recorremos la secuencia, si encontramos un paréntesis que abre (o sea un "(", "{" o "[") lo guardamos en la pila

Por otro lado, en caso de encontrar uno paréntesis que cierra (o sea un ")", "}"), primero verificamos que la pila no este vacía, ya que si lo está automáticamente está desbalanceado. Posteriormente, verificamos si el tope es igual al compañero del elemento del tope, es decir, si tengo el ")", tengo que revisar que el tope de la pila este su compañero "(".

Si la comparación es verdadera entonces podemos desa pilar ese elemento, y asi sucesivamente hasta finalizar, en donde la pila debe quedar vacía para ser balanceada, de otro modo, esta desbalanceada.

https://github.com/user-attachments/assets/0faa28e1-1ce4-4a25-9bbd-3b9a53566cd8

### Validación HTML / XML

Este ejemplo es un poco más "real" en el sentido que sería más util en la vida real, usa el mismo principio de los paréntesis balanceados, en XML o HTML todas las etiquetas que se abren se deben cerrar, o sea tipo:

```
<html>
    <body>
        <h1>Título</h1> 
    </body>
</html>
```

Sin embargo, en HTML existen etiquetas que nunca se cierran, y para evitar complicaciones el código está enfocado únicamente en archivos XML.

```
import re

def validate_xml(filename):
    stack = []
    with open(filename, "r", encoding="utf-8") as file:
        content = file.read()
    tags = re.findall(r"</?[a-zA-Z0-9]+>", content)
    for tag in tags:
        if tag.startswith("</"):
            name = tag[2:-1]
            if not stack:
                return False
            if stack.pop() != name:
                return False
        else:
            name = tag[1:-1]
            stack.append(name)
    return len(stack) == 0
```

Para este ejemplo se importó `re` (Regular Expressions) para simplificar las búsquedas, sin embargo, se puede hacer de igual manera sin este, el caso es que este busca cadenas dada cierto parámetro, para este caso primero creamos la pila y posteriormente abrimos el archivo en modo lectura ("r"), asi mismo, se lee todo el archivo y se guarda en una variable, es decir:

```
content =
<book>
    <title>Python</title>
    <author>Juan</author>
</book>
```
Posteriormente, se extrae o filtramos las cadenas que empiezan en < y terminen en >, sin importar que haya adentro (es por eso que se ponen que se pone `</?[a-zA-Z0-9]+>`, que significa toda letra del abecedario mayúscula o minúscula y todo número es válido siempre u cuando empiece y termine en <>).

Una vez se realizan las verificaciones, para saber si está bien balanceado, donde se mira si las etiquetas de cierre tienen su compañero en el tope de la pila, para saber si avanza o ya está mal.

---

## Colas

Las colas a diferencia de las pilas usan el principio FIFO (First In, First Out), es decir el primer elemento que entra es el primero que sale, el ejemplo más sencillo es una fila de cualquier tipo, la primera persona que llego es la primera que atienden. 

Es muy parecido a un arreglo, sin embargo, este cuenta con diferencias clave en sus operaciones, ya que solo se puede eliminar el primer elemento que entro y cada que ingresa un elemento este solo se puede añadir al final de la lista.

### Cuando se usa

Las colas se usan habitualmente en varios sistemas como impresoras, donde las hojas se van imprimiendo en orden, atención al cliente, que va desde el primero que llego al último e incluso para eventos en videojuegos.

### Subtipo: Colas de prioridad 

Para este caso, lo más importante no es quien llego primero, sino que elemento tiene una prioridad mayor, el elemento con mayor prioridad será el primero en salir y en caso de que todos los elementos tengan la misma prioridad, entonces se trabajará como si fuera una cola normal.

### Ejemplos

### Cola de prioridad para hospital 

Este es un ejemplo clásico, consite en decir cuál paciente debe ser atendido primero dependiendo su prioridad que en este caso sería que tan grave esta o que tan urgente es que lo atiendan.

Para este caso baso a manejar la prioridad de la siguiente manera:

```
1 -> Emergencia crítica
2 -> Grave
3 -> Normal
4 -> Leve
```

Por lo que mientras más pequeño el número, más rapido se debe atender, por otro lado, en caso de que 2 pacientes tengan la misma prioridad se atenderá al que llego primero, asi mismo, suponemos que la estructura será `(int(Prioridad), String(Nombre))`.

```
def attend_patient(hospital):
    if len(hospital) == 0:
        return None
    priority = 0
    for i in range(1, len(hospital)):
        if hospital[i][0] < hospital[priority][0]:
            priority = i
    return hospital.pop(priority)
```

Aquí lo que hacemos es primero verificar que hay pacientes, en ese caso revisamos la lista de pacientes de modo que comparamos si la prioridad un paciente es mayor a la de los demás, y se retorna el paciente de mayor prioridad (que a la vez se elimina de la lista, ya que es el que se va a atender), en caso se quiera ver el orden de atencion de los clientes se puede realizar de varias maneras, en este caso, se crea otra función:

```
def service_order(hospital):
    order = []
    while hospital:
        order.append(attend_patient(hospital))
    return order
```

**NOTA:** Hay más ejemplos tanto para pilas como colas relacionadas con algoritmos de búsqueda (A*, DFS, BFS, etc), el caso es que varios de estos se desarrollan sobre estructuras no lineales como Árboles binarios o grafos, por lo que dichos ejemplos se abordaran en los respectivos repos de esos temas.

---

## Listas Enlazadas