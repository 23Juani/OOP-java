# LISTAS ENLAZADAS

## Introducción

Las listas enlazadas son estructuras de datos dinámicas utilizadas para almacenar y organizar información mediante nodos conectados entre sí. A diferencia de los arreglos (arrays), las listas enlazadas no requieren posiciones de memoria contiguas, lo que permite una mayor flexibilidad en la inserción y eliminación de elementos.

Cada nodo de una lista enlazada contiene dos partes fundamentales:

- **Dato:** información almacenada.
- **Enlace o referencia:** dirección del siguiente nodo.

Las listas enlazadas son ampliamente utilizadas en sistemas operativos, compiladores, bases de datos y aplicaciones que requieren manipulación dinámica de datos.

---

# 3.1. Fundamentos teóricos de listas enlazadas

## Definición

Una lista enlazada es una colección lineal de elementos llamados nodos, donde cada nodo contiene información y una referencia al siguiente nodo de la secuencia.

### Representación conceptual

```none
[10|•] → [20|•] → [30|•] → NULL
```

Donde:

- 10, 20 y 30 son los datos almacenados.
- La flecha representa el enlace al siguiente nodo.
- NULL indica el final de la lista.

## Características

- Tamaño dinámico.
- Inserción eficiente.
- Eliminación sencilla.
- No requiere memoria contigua.
- Acceso secuencial a los elementos.

## Nodo de una lista enlazada

### Implementación en Java

```java
class Nodo {
    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
        this.siguiente = null;
    }
}
```

---

# 3.2. Clasificación de listas enlazadas

Las listas enlazadas pueden clasificarse según la forma en que sus nodos se conectan.

## Lista simplemente enlazada

Cada nodo apunta únicamente al siguiente nodo.

```none
[A] → [B] → [C] → NULL
```

## Lista doblemente enlazada

Cada nodo posee dos referencias:

- Nodo anterior.
- Nodo siguiente.

```none
NULL ← [A] ⇄ [B] ⇄ [C] → NULL
```

## Lista circular simple

El último nodo apunta nuevamente al primero.

```none
[A] → [B] → [C]
 ↑           ↓
 └───────────┘
```

## Lista circular doble

Posee enlaces hacia adelante y hacia atrás formando un ciclo.

```none
[A] ⇄ [B] ⇄ [C]
 ↑           ↓
 └───────────┘
```

---
# 3.3. Operaciones de listas enlazadas

## Introducción

Las listas enlazadas permiten realizar diversas operaciones para gestionar dinámicamente los datos almacenados en sus nodos. Estas operaciones son fundamentales para manipular la estructura y garantizar un acceso eficiente a la información.

Las operaciones más importantes son:

- Inserción
- Eliminación
- Búsqueda
- Recorrido
- Actualización

Cada una de estas operaciones tiene aplicaciones específicas y constituye la base para el desarrollo de estructuras de datos más complejas.

---

## 3.3.1. Inserción

### Definición

La inserción consiste en agregar un nuevo nodo dentro de la lista enlazada.

A diferencia de los arreglos, donde puede ser necesario desplazar elementos para insertar un nuevo dato, en las listas enlazadas únicamente se modifican las referencias entre nodos.

### Tipos de inserción

La inserción puede realizarse en:

- El inicio de la lista.
- El final de la lista.
- Una posición específica.
- Manteniendo un orden determinado.

### Ejemplo conceptual

Lista original:

```
10 → 20 → 30 → NULL
```

Insertar 5 al inicio:

```
5 → 10 → 20 → 30 → NULL
```

Insertar 40 al final:

```
10 → 20 → 30 → 40 → NULL
```

Insertar 25 entre 20 y 30:

```
10 → 20 → 25 → 30 → NULL
```

### Ventajas de la inserción

- No requiere redimensionar la estructura.
- No es necesario desplazar elementos.
- Permite crecimiento dinámico.
- Operación eficiente en comparación con arreglos.

### Ejemplo completo en Java
**Clase nodo**
```java
class Nodo {
    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
        siguiente = null;
    }
}
```
**Clase lista**
```java
class Lista {
	// atributo
    Nodo cabeza;

    void insertarInicio(int dato) {

        Nodo nuevo = new Nodo(dato);

        nuevo.siguiente = cabeza;
        cabeza = nuevo;
    }

    void mostrar() {

        Nodo actual = cabeza;

        while(actual != null) {
            System.out.print(actual.dato + " ");
            actual = actual.siguiente;
        }
    }
}
```

### Uso

```java
public class Main {

    public static void main(String[] args) {

        Lista lista = new Lista();

        lista.insertarInicio(30);
        lista.insertarInicio(20);
        lista.insertarInicio(10);

        lista.mostrar();
    }
}
```

### Salida

```
10 20 30
```

---

## 3.3.2. Eliminación

### Definición

La eliminación consiste en retirar un nodo existente de la lista enlazada.

Para ello se deben modificar las referencias de los nodos vecinos para mantener la continuidad de la estructura.

### Tipos de eliminación

Puede realizarse:

- Eliminando el primer nodo.
- Eliminando el último nodo.
- Eliminando un nodo específico.
- Eliminando todos los nodos.

### Ejemplo conceptual

Lista original:

```
10 → 20 → 30 → 40 → NULL
```

Eliminar 20:

```
10 → 30 → 40 → NULL
```

### Proceso de eliminación

1. Buscar el nodo.
2. Localizar el nodo anterior.
3. Modificar el enlace.
4. Liberar el nodo.

### Ventajas

- No requiere desplazar elementos.
- Operación rápida.
- Menor costo computacional que en arreglos.

### Ejemplo en Java

```java
void eliminar(int dato) {

    if(this.cabeza == null)
        return;

    if(cabeza.dato == dato) {
        cabeza = cabeza.siguiente;
        return;
    }

    Nodo actual = cabeza;

    while(actual.siguiente != null &&
          actual.siguiente.dato != dato) {

        actual = actual.siguiente;
    }

    if(actual.siguiente != null) {
        actual.siguiente =
        actual.siguiente.siguiente;
    }
}
```

### Uso

```java 
lista.eliminar(20);
lista.mostrar();
```

### Resultado

```none
10 30 40
```

---

## 3.3.3. Búsqueda

### Definición

La búsqueda consiste en localizar un elemento dentro de la lista.

Debido a que los nodos no están almacenados en posiciones consecutivas de memoria, la búsqueda debe realizarse recorriendo secuencialmente cada nodo.

### Tipos de búsqueda

#### Búsqueda secuencial

Se examina cada nodo hasta encontrar el dato.

#### Búsqueda por posición

Se busca un nodo según su índice dentro de la lista.

### Ejemplo conceptual

Buscar el valor 30:

```none
10 → 20 → 30 → 40 → NULL
          ↑
      Encontrado
```

### Algoritmo

```none
Inicio
↓
Leer primer nodo
↓
Comparar dato
↓
¿Coincide?
↓
Sí → Encontrado
No → Siguiente nodo
↓
NULL → No encontrado
```

### Implementación

```java
boolean buscar(int valor) {

    Nodo actual = cabeza;

    while(actual != null) {

        if(actual.dato == valor) {
            return true;
        }

        actual = actual.siguiente;
    }

    return false;
}
```

### Uso

```java
if(buscar(30))
    System.out.println("Dato encontrado");
else
    System.out.println("Dato no encontrado");
```

### Salida

```none
Dato encontrado
```

---

## 3.3.4. Recorrido

### Definición

El recorrido consiste en visitar cada nodo de la lista desde el primero hasta el último.

Es una de las operaciones más utilizadas, ya que sirve como base para búsquedas, actualizaciones y visualización de datos.

### Ejemplo conceptual

```none
10 → 20 → 30 → 40 → NULL 
↑
Inicio
```

Recorrido:

```none
10
20
30
40
```

### Implementación

```java
void mostrarLista() {

    Nodo actual = cabeza;

    while(actual != null) {

        System.out.print(actual.dato + " ");

        actual = actual.siguiente;
    }
}
```

### Uso

```java
lista.mostrarLista();
```

### Resultado

```
10 20 30 40
```

### Aplicaciones del recorrido

- Mostrar elementos.
- Calcular sumas.
- Contar nodos.
- Buscar datos.
- Actualizar información.

### Ejemplo para contar nodos

```java
int contarNodos() {

    int contador = 0;

    Nodo actual = cabeza;

    while(actual != null) {

        contador++;

        actual = actual.siguiente;
    }

    return contador;
}
```

### Resultado

```none
Cantidad de nodos: 4
```

---

## 3.3.5. Actualización

### Definición

La actualización consiste en modificar la información almacenada en uno o varios nodos existentes.

Esta operación no altera la estructura de enlaces de la lista, únicamente cambia el contenido del nodo.

### Ejemplo conceptual

Lista original:

```none
10 → 20 → 30 → NULL
```

Actualizar 20 por 25:

```none
10 → 25 → 30 → NULL
```

### Proceso

1. Buscar el nodo.
2. Verificar que exista.
3. Modificar el dato.
4. Guardar el nuevo valor.

### Implementación en Java

```java
boolean actualizar(int datoBuscar,int nuevoDato) {

    Nodo actual = cabeza;

    while(actual != null) {

        if(actual.dato == datoBuscar) {

            actual.dato = nuevoDato;
            return true;
        }

        actual = actual.siguiente;
    }

    return false;
}
```

### Uso

```java
actualizar(20, 25);

mostrarLista();
```

### Resultado

```none
10 25 30
```

### Ventajas de la actualización

- No modifica la estructura de la lista.
- Mantiene los enlaces intactos.
- Permite corregir información rápidamente.
- Reduce operaciones de eliminación e inserción.

---

# 3.4. Lista ordenada

## Definición

Una lista ordenada mantiene automáticamente sus elementos en un orden específico.

Puede ser:

- Ascendente.
- Descendente.

### Ejemplo

```none
5 → 10 → 15 → 20 → 25
```

## Inserción ordenada

```java
void insertarOrdenado(int dato) {

    Nodo nuevo = new Nodo(dato);

    if(cabeza == null ||
       dato < cabeza.dato) {

        nuevo.siguiente = cabeza;
        cabeza = nuevo;
        return;
    }

    Nodo actual = cabeza;

    while(actual.siguiente != null &&
          actual.siguiente.dato < dato) {

        actual = actual.siguiente;
    }

    nuevo.siguiente = actual.siguiente;
    actual.siguiente = nuevo;
}
```

## Ventajas

- Facilita búsquedas.
- Mantiene los datos organizados.
- Útil en aplicaciones de clasificación.

---

# 3.5. Lista doblemente enlazada

## Definición

Una lista doblemente enlazada es una estructura de datos dinámica formada por nodos, donde cada nodo contiene tres partes:

- Un dato o información.
- Un enlace al nodo anterior.
- Un enlace al nodo siguiente.

A diferencia de una lista simplemente enlazada, los nodos pueden recorrerse en ambas direcciones, permitiendo desplazarse tanto hacia adelante como hacia atrás dentro de la estructura.

## Características

- Cada nodo conoce a su predecesor y sucesor.
- Permite recorrido bidireccional.
- Facilita las operaciones de inserción y eliminación.
- No requiere posiciones consecutivas de memoria.
- Tiene un mayor consumo de memoria que una lista simple.

## Estructura de una lista doblemente enlazada

```none
NULL ← [10] ⇄ [20] ⇄ [30] → NULL
```

En la figura anterior:

- El nodo 10 es el primer nodo.
- El nodo 30 es el último nodo.
- Cada nodo apunta al nodo anterior y al siguiente.
- Los extremos contienen referencias NULL.

## Implementación de una lista doblemente enlazada en Java

Para implementar una lista doblemente enlazada es necesario definir dos clases:

- La clase `Nodo`, que representa cada elemento de la lista.
- La clase `ListaDoble`, que administra todos los nodos.

### Clase Nodo

```java
class Nodo {
// Atributos
    int dato;
    Nodo anterior;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
        this.anterior = null;
        this.siguiente = null;
    }
}
```

### Clase ListaDoble

```java
class ListaDoble {

    Nodo cabeza;

    ListaDoble() {
        cabeza = null;
    }
}
```

### Explicación

#### dato

Almacena la información del nodo.

#### anterior

Contiene la referencia al nodo anterior.

#### siguiente

Contiene la referencia al siguiente nodo.

#### cabeza

Es una referencia especial que siempre apunta al primer nodo de la lista.

Cuando la lista está vacía:

```none
cabeza
  ↓
NULL
```

Cuando existen elementos:

```none
cabeza
  ↓
[10] ⇄ [20] ⇄ [30]
```

A partir de la referencia `cabeza` es posible acceder a todos los nodos de la lista.

## Operaciones en listas doblemente enlazadas

Las operaciones fundamentales son:

- Inserción
- Eliminación
- Búsqueda
- Recorrido
- Actualización

## Inserción al inicio

### Definición

Consiste en agregar un nuevo nodo antes del primer elemento de la lista.

### Antes

```none
cabeza
  ↓
[20] ⇄ [30]
```

### Después de insertar 10

```none
cabeza
  ↓
[10] ⇄ [20] ⇄ [30]
```

### Implementación

```java
void insertarInicio(int dato) {

    Nodo nuevo = new Nodo(dato);

    if(cabeza != null) {
        cabeza.anterior = nuevo;
        nuevo.siguiente = cabeza;
    }

    cabeza = nuevo;
}
```

## Inserción al final

### Definición

Permite agregar un nuevo nodo al final de la lista.

### Antes

```none
[10] ⇄ [20]
```

### Después

```none
[10] ⇄ [20] ⇄ [30]
```

### Implementación

```java
void insertarFinal(int dato) {

    Nodo nuevo = new Nodo(dato);

    if(cabeza == null) {
        cabeza = nuevo;
        return;
    }

    Nodo actual = cabeza;

    while(actual.siguiente != null) {
        actual = actual.siguiente;
    }

    actual.siguiente = nuevo;
    nuevo.anterior = actual;
}
```


## Búsqueda de un elemento

### Definición

Consiste en localizar un dato dentro de la lista.

### Ejemplo conceptual

```none
[10] ⇄ [20] ⇄ [30]
               ↑
          Elemento encontrado
```

### Implementación

```java
boolean buscar(int valor) {

    Nodo actual = cabeza;

    while(actual != null) {

        if(actual.dato == valor)
            return true;

        actual = actual.siguiente;
    }

    return false;
}
```

### Uso

```java
if(buscar(30))
    System.out.println("Dato encontrado");
else
    System.out.println("Dato no encontrado");
```

## Recorrido hacia adelante

### Definición

Permite visitar los nodos desde el primero hasta el último.

### Implementación

```java
void mostrarAdelante() {

    Nodo actual = cabeza;

    while(actual != null) {

        System.out.print(actual.dato + " ");

        actual = actual.siguiente;
    }
}
```

### Resultado

```none
10 20 30
```
## Recorrido hacia atrás

### Definición

Permite visitar los nodos desde el último hasta el primero.

### Implementación

```java
void mostrarAtras() {

    Nodo actual = cabeza;

    while(actual.siguiente != null) {
        actual = actual.siguiente;
    }

    while(actual != null) {

        System.out.print(actual.dato + " ");

        actual = actual.anterior;
    }
}
```

### Resultado

```none
30 20 10
```

## Actualización de un nodo

### Definición

Consiste en modificar el dato almacenado en un nodo.

### Ejemplo

Lista original:

```none
[10] ⇄ [20] ⇄ [30]
```

Actualizar 20 por 25:

```none
[10] ⇄ [25] ⇄ [30]
```

### Implementación

```java
boolean actualizar(int viejo,int nuevo) {

    Nodo actual = cabeza;

    while(actual != null) {

        if(actual.dato == viejo) {

            actual.dato = nuevo;
            return true;
        }

        actual = actual.siguiente;
    }

    return false;
}
```

## Eliminación de un nodo

### Definición

Consiste en retirar un nodo de la lista y reorganizar las referencias.

### Lista original

```none
[10] ⇄ [20] ⇄ [30]
```

### Después de eliminar 20

```none
[10] ⇄ [30]
```

### Implementación

```java
void eliminar(int dato) {

    Nodo actual = cabeza;

    while(actual != null &&
          actual.dato != dato) {

        actual = actual.siguiente;
    }

    if(actual == null)
        return;

    if(actual.anterior != null)
        actual.anterior.siguiente =
            actual.siguiente;
    else
        cabeza = actual.siguiente;

    if(actual.siguiente != null)
        actual.siguiente.anterior =
            actual.anterior;
}
```

### Ventaja respecto a una lista simple

En una lista doblemente enlazada no es necesario buscar nuevamente el nodo anterior, ya que cada nodo posee una referencia directa hacia él.

## Ejemplo completo de uso

```java
public class Main {

    public static void main(String[] args) {

        ListaDoble lista = new ListaDoble();

        lista.insertarInicio(30);
        lista.insertarInicio(20);
        lista.insertarInicio(10);

        lista.mostrarAdelante();

        System.out.println();

        lista.mostrarAtras();
    }
}
```

### Salida

```none
10 20 30
30 20 10
```

---

# 3.6. Listas circulares

## Definición

Una lista circular es una estructura de datos dinámica derivada de las listas enlazadas, en la cual el último nodo no apunta a `NULL`, sino que apunta nuevamente al primer nodo de la lista, formando un ciclo cerrado.

Gracias a esta característica, es posible recorrer la lista indefinidamente sin encontrar un final explícito.

Las listas circulares son ampliamente utilizadas en aplicaciones donde los elementos deben procesarse de manera repetitiva o cíclica.

## Características

Las principales características de una lista circular son:

- El último nodo apunta al primer nodo.
- No existe una referencia `NULL` al final de la lista.
- Permite recorridos continuos.
- Facilita la implementación de algoritmos repetitivos.
- Puede ser simple o doblemente enlazada.
- Utiliza memoria dinámica.

## Estructura de una lista circular

### Representación conceptual

```none
10 → 20 → 30
↑         ↓
└─────────┘
```

### Representación con referencias

```none
┌─────┐     ┌─────┐     ┌─────┐
│ 10  │ ──► │ 20  │ ──► │ 30  │
└─────┘     └─────┘     └─────┘
   ▲                       │
   └───────────────────────┘
```

En esta estructura:

- El nodo 10 apunta al nodo 20.
- El nodo 20 apunta al nodo 30.
- El nodo 30 apunta nuevamente al nodo 10.

## Diferencia entre lista simple y lista circular

|Característica|Lista Simple|Lista Circular|
|---|---|---|
|Último nodo apunta a|NULL|Primer nodo|
|Existe fin de recorrido|Sí|No|
|Recorrido continuo|No|Sí|
|Adecuada para procesos cíclicos|No|Sí|


## Nodo de una lista circular

Cada nodo contiene un dato y una referencia al siguiente nodo.

### Implementación en Java

```java
class Nodo {

    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
        this.siguiente = null;
    }
}
```

### Explicación

- `dato`: almacena la información del nodo.
- `siguiente`: referencia al siguiente nodo de la lista.


## Implementación de una lista circular

Para administrar la lista se utiliza una clase adicional.

```java
class ListaCircular {

    Nodo primero;

    ListaCircular() {
        primero = null;
    }
}
```

### Variable primero

La variable `primero` apunta al primer nodo de la lista.

Lista vacía:

```none
primero
   ↓
 NULL
```

Lista con elementos:

```none
primero
↓
10 → 20 → 30
↑         ↓
└─────────┘
```

## Inserción de elementos

### Inserción del primer nodo

Cuando la lista está vacía, el nodo debe apuntarse a sí mismo.

```java
void insertarPrimero(int dato) {

    Nodo nuevo = new Nodo(dato);

    primero = nuevo;
    nuevo.siguiente = nuevo;
}
```

### Resultado

```none
10
↑ ↓
└─┘
```


## Inserción al final

### Implementación

```java
void insertarFinal(int dato) {

    Nodo nuevo = new Nodo(dato);

    if(primero == null) {

        primero = nuevo;
        nuevo.siguiente = nuevo;
        return;
    }

    Nodo actual = primero;

    while(actual.siguiente != primero) {
        actual = actual.siguiente;
    }

    actual.siguiente = nuevo;
    nuevo.siguiente = primero;
}
```

### Ejemplo

Antes:

```none
10 → 20
↑     ↓
└─────┘
```

Después de insertar 30:

```none
10 → 20 → 30
↑         ↓
└─────────┘
```

## Recorrido de una lista circular

### Definición

Debido a que la lista no posee un valor `NULL`, el recorrido debe detenerse cuando se vuelva al nodo inicial.

### Implementación

```java
void mostrar() {

    if(primero == null)
        return;

    Nodo actual = primero;

    do {

        System.out.print(actual.dato + " ");

        actual = actual.siguiente;

    } while(actual != primero);
}
```

### Resultado

```none
10 20 30
```

## Búsqueda de un elemento

### Definición

Consiste en localizar un dato específico recorriendo la lista.

### Implementación

```java
boolean buscar(int valor) {

    if(primero == null)
        return false;

    Nodo actual = primero;

    do {

        if(actual.dato == valor)
            return true;

        actual = actual.siguiente;

    } while(actual != primero);

    return false;
}
```

### Uso

```java
if(buscar(20))
    System.out.println("Elemento encontrado");
else
    System.out.println("Elemento no encontrado");
```

### Salida

```none
Elemento encontrado
```

## Eliminación de un nodo

### Definición

La eliminación consiste en retirar un nodo de la estructura y restablecer correctamente las referencias circulares.

### Ejemplo conceptual

Lista original:

```none
10 → 20 → 30
↑         ↓
└─────────┘
```

Eliminar 20:

```none
10 → 30
↑     ↓
└─────┘
```



## Aplicaciones de las listas circulares

Las listas circulares son ampliamente utilizadas en sistemas informáticos modernos.

### Planificación de procesos (Round Robin)

Los sistemas operativos utilizan listas circulares para asignar tiempo de CPU a múltiples procesos.

```none
Proceso A → Proceso B → Proceso C
     ↑                    ↓
     └────────────────────┘
```

### Juegos por turnos

Permiten gestionar jugadores que participan repetidamente.

```none
Jugador 1 → Jugador 2 → Jugador 3
     ↑                        ↓
     └────────────────────────┘
```

### Reproductores multimedia

Facilitan la reproducción continua de canciones o videos.

```none
Canción 1 → Canción 2 → Canción 3
     ↑                        ↓
     └────────────────────────┘
```

