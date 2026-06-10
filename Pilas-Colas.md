# PILAS Y COLAS

## 2.1. Introducción

Las **pilas** y **colas** son estructuras de datos lineales ampliamente utilizadas en la programación y en el diseño de algoritmos. Ambas permiten almacenar y organizar elementos, pero difieren en la forma en que se realizan las operaciones de inserción y eliminación.

Estas estructuras son fundamentales para resolver problemas relacionados con la gestión de procesos, navegación entre páginas web, llamadas a funciones, planificación de tareas y simulación de sistemas reales.

---

# 2.2. Pilas

## 2.2.1. Concepto de pila

Una **pila** (_Stack_) es una estructura de datos lineal que sigue el principio:

**LIFO (Last In, First Out)**

Lo último que entra es lo primero que sale.

### Ejemplo cotidiano

Una pila de platos:

- El último plato colocado encima será el primero en retirarse.
    
- Solo se puede acceder al elemento que se encuentra en la parte superior.
    

### Operaciones básicas

|Operación|Descripción|
|---|---|
|Push|Inserta un elemento en la cima|
|Pop|Elimina el elemento de la cima|
|Peek o Top|Consulta el elemento superior|
|IsEmpty|Verifica si la pila está vacía|
|IsFull|Verifica si la pila está llena (en implementación estática)|

### Representación

```none
      TOP
       ↓
    +-----+
    | 40 |
    +-----+
    | 30 |
    +-----+
    | 20 |
    +-----+
    | 10 |
    +-----+
```

### Aplicaciones

- Historial de navegación web.
    
- Deshacer/Rehacer en editores.
    
- Llamadas recursivas.
    
- Evaluación de expresiones matemáticas.
    
- Conversión entre notaciones.
    

---

## 2.2.2. Pila implementada con arrays

### Definición

Una forma sencilla de implementar una pila es mediante un arreglo.

Se utiliza una variable denominada **top** que indica la posición del último elemento insertado.

### Implementación en Java

```java
class Pila {
    private int[] elementos;
    private int top;

    public Pila(int tamaño) {
        elementos = new int[tamaño];
        top = -1;
    }

    public void push(int dato) {
        if (top < elementos.length - 1) {
            elementos[++top] = dato;
        }
    }

    public int pop() {
        if (top >= 0) {
            return elementos[top--];
        }
        return -1;
    }

    public int peek() {
        if (top >= 0) {
            return elementos[top];
        }
        return -1;
    }
}
```

### Uso

```java
public class Main {
    public static void main(String[] args) {

        Pila pila = new Pila(5);

        pila.push(10);
        pila.push(20);
        pila.push(30);

        System.out.println(pila.pop());
        System.out.println(pila.peek());
    }
}
```

### Salida

```none
30
20
```

### Ventajas

- Fácil implementación.
    
- Acceso rápido.
    
- Bajo consumo de memoria.
    

### Desventajas

- Tamaño fijo.
    
- Posibles desperdicios de memoria.
    

---

## 2.2.3. Pila implementada como una lista enlazada

### Definición

En esta implementación cada elemento se almacena en un nodo.

La pila puede crecer dinámicamente sin necesidad de definir un tamaño máximo.

### Nodo

```java
class Nodo {
    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
    }
}
```

### Implementación

```java
class Pila {
    private Nodo cima;

    public void push(int dato) {
        Nodo nuevo = new Nodo(dato);

        nuevo.siguiente = cima;
        cima = nuevo;
    }

    public int pop() {
        if (cima == null)
            return -1;

        int dato = cima.dato;
        cima = cima.siguiente;

        return dato;
    }
}
```

### Ventajas

- Tamaño dinámico.
    
- Mejor aprovechamiento de memoria.
    

### Desventajas

- Mayor complejidad.
    
- Uso adicional de referencias.
    

---

# 2.3. Colas

## 2.3.1. Concepto de Cola

Una **cola** (_Queue_) es una estructura de datos lineal que sigue el principio:

**FIFO (First In, First Out)**

El primero que entra es el primero que sale.

### Ejemplo cotidiano

La fila de un banco:

- La primera persona en llegar será la primera en ser atendida.
    
- Los nuevos elementos se agregan al final.
    

### Operaciones básicas

|Operación|Descripción|
|---|---|
|Enqueue|Insertar elemento|
|Dequeue|Eliminar elemento|
|Front|Consultar el primer elemento|
|IsEmpty|Verificar si está vacía|
|IsFull|Verificar si está llena|

### Representación

```none
FRONT                     REAR
 ↓                          ↓
+----+----+----+----+
| 10 | 20 | 30 | 40 |
+----+----+----+----+
```

### Aplicaciones

- Gestión de impresoras.
    
- Sistemas operativos.
    
- Planificación de procesos.
    
- Simulación de atención al cliente.
    
- Redes de computadoras.
    

---

## 2.3.2. Colas implementadas con arrays

### Definición

Las colas pueden implementarse mediante arreglos utilizando dos índices:

- **front** (inicio)
    
- **rear** (final)
    

### Implementación en Java

```java
class Cola {

    private int[] datos;
    private int front;
    private int rear;

    public Cola(int tamaño) {
        datos = new int[tamaño];
        front = 0;
        rear = -1;
    }

    public void enqueue(int dato) {
        datos[++rear] = dato;
    }

    public int dequeue() {
        return datos[front++];
    }
}
```

### Uso

```java
public class Main {
    public static void main(String[] args) {

        Cola cola = new Cola(5);

        cola.enqueue(10);
        cola.enqueue(20);
        cola.enqueue(30);

        System.out.println(cola.dequeue());
    }
}
```

### Salida

```none
10
```

### Ventajas

- Fácil implementación.
    
- Acceso rápido.
    

### Desventajas

- Tamaño limitado.
    
- Puede generar espacios desperdiciados.
    

---

## 2.3.3. Cola con una lista enlazada

### Definición

Utiliza nodos enlazados para almacenar los elementos.

Se mantienen referencias al primer y último nodo de la cola.

### Nodo

```java
class Nodo {
    int dato;
    Nodo siguiente;

    Nodo(int dato) {
        this.dato = dato;
    }
}
```

### Implementación

```java
class Cola {

    private Nodo frente;
    private Nodo fin;

    public void enqueue(int dato) {

        Nodo nuevo = new Nodo(dato);

        if (fin != null) {
            fin.siguiente = nuevo;
        }

        fin = nuevo;

        if (frente == null) {
            frente = nuevo;
        }
    }

    public int dequeue() {

        if (frente == null)
            return -1;

        int dato = frente.dato;

        frente = frente.siguiente;

        if (frente == null) {
            fin = null;
        }

        return dato;
    }
}
```

### Uso

```java
public class Main {
    public static void main(String[] args) {

        Cola cola = new Cola();

        cola.enqueue(100);
        cola.enqueue(200);
        cola.enqueue(300);

        System.out.println(cola.dequeue());
        System.out.println(cola.dequeue());
    }
}
```

### Salida

```none
100
200
```

### Ventajas

- Tamaño dinámico.
    
- Inserciones y eliminaciones eficientes.
    

### Desventajas

- Mayor uso de memoria.
    
- Implementación más compleja.
    

---

## Diferencias entre Pilas y Colas

|Característica|Pila|Cola|
|---|---|---|
|Principio|LIFO|FIFO|
|Inserción|En la cima|Al final|
|Eliminación|Desde la cima|Desde el frente|
|Aplicación típica|Recursión, historial|Planificación, atención|
|Operaciones|Push / Pop|Enqueue / Dequeue|
