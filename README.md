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

