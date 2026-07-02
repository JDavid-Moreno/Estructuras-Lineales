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
list.append(0)  #al hacer esto todos los elementos se mueven
```

Sus ejemplos más conocidos de uso no los vamos a abordar aca, ya que estos se realizaron con anterioridad que son [Búsqueda Binaria](https://github.com/JDavid-Moreno/Dividir-y-conquistar/blob/main/Algoritmos/BinarySearch.py) o los [Algoritmos de ordenamiento de arreglos](https://github.com/JDavid-Moreno/Algoritmos-de-ordenamiento), los cuales rapidamente trantan sobre encontrar el indice de un elemento conociendo el valor de dicho elemento y los algoritmos de ordenamiento, como dice su nombre, consisten en distintas maneras de ordenar un arreglo de elementos enteros.

---

## Pilas

