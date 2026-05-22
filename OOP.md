# PROGRAMACIÓN ORIENTADA A OBJETOS (POO) EN JAVA
**Introducción** 
La Programación Orientada a Objetos (POO) es un [Paradigma](https://github.com/23Juani/OOP-java/blob/main/Paradigma.md) de programación que organiza el software en objetos que contienen [Atributos y métodos](https://github.com/23Juani/OOP-java/blob/main/Atributos%20y%20m%C3%A9todos.md). Este enfoque permite desarrollar sistemas más reutilizables, escalables y fáciles de mantener.

Java es uno de los lenguajes más utilizados para aplicar la POO debido a que está diseñado completamente bajo este paradigma. 
## 1. PROGRAMACIÓN ORIENTADA A OBJETOS

#### Conceptos fundamentales de la POO

La POO se basa en cuatro pilares principales:
- **[Encapsulamiento](https://github.com/23Juani/OOP-java/blob/main/Encapsulamiento.md)**
- **[Herencia](https://github.com/23Juani/OOP-java/blob/main/Herencia.md)**
- **[Polimorfismo](https://github.com/23Juani/OOP-java/blob/main/Polimorfismo.md)**
- **[Abstracción](https://github.com/23Juani/OOP-java/blob/main/Abstracci%C3%B3n.md)**

#### Clase
Una clase es una plantilla o molde para crear objetos.
```java
class Persona {
	String nombre;
	int edad;
	
	void saludar() {
		System.out.println("Hola, mi nombre es " + nombre);
	}
}
```

#### Objeto
Un objeto es una **instancia** de una clase.
```java
public class Main {
	public static void main(String[] args) {
		Persona estudiante1 = new Persona();
		estudiante1.nombre = "Jose Mauricio";
		estudiante1.edad = 25;
		estudiante1.saludar();
	}
}
```

### 1.1. Sobrecarga de funciones
#### Definición

La sobrecarga de funciones (Overloading) consiste en crear varios métodos con el mismo nombre, pero con diferentes parámetros.

La diferencia puede estar en:
- Cantidad de parámetros
- Tipo de parámetros
- Orden de parámetros
#### Ventajas
- Facilita la reutilización de métodos.
- Hace el código más legible.
- Permite realizar operaciones similares con diferentes tipos de datos.
---

#### Ejemplo básico
```java
class Calculadora {
	int sumar(int a, int b) {
		return a + b;
	}
	double sumar(double a, double b) {
		return a + b;
	}
	int sumar(int b, int c, int a) {
		return a + b + c;
	}

}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	
		Calculadora calc = new Calculadora();

		System.out.println(calc.sumar(5, 3));
		System.out.println(calc.sumar(5.5, 3.2));
		System.out.println(calc.sumar(1, 2, 3));
	}
}
```
### 1.2. Definición de generalización y especialización

#### Generalización
La generalización consiste en crear una clase general a partir de varias clases específicas.

Representa una relación de herencia.
#### Ejemplo conceptual

- Animal
	- Perro
	- Gato
	- Ave

En este caso:
- Animal = clase general
- Perro, Gato y Ave = clases específicas

#### Especialización
La especialización consiste en crear clases más específicas a partir de una clase general.

#### Ejemplo en Java
#### Clase general
```java
class Vehiculo {
	String marca;
	void arrancar() {
		System.out.println("El vehículo está arrancando");
	}
}
```
#### Clase especializadas
```java
class Auto extends Vehiculo {
	int puertas;
}

class Moto extends Vehiculo {
	boolean casco;
}
```
#### Uso 
```java
public class Main {
	public static void main(String[] args) {
	
		Auto auto = new Auto();
		auto.marca = "Toyota";
		auto.puertas = 4;
		
		auto.arrancar();
		
		Moto moto = new Moto();
		moto.marca = "Honda";
		moto.casco = true; 
		
		moto.arrancar();
	}
}
```
#### Ventajas de la generalización y especialización

- Reutilización de código
- Menor duplicación
- Mejor organización
- Facilita el mantenimiento
### 1.3. Representación mediante diagramas UML
#### ¿Qué es UML?

**UML** (Unified Modeling Language) es un lenguaje gráfico utilizado para modelar sistemas orientados a objetos.

#### Objetivos de UML

- Visualizar sistemas
- Diseñar software
- Documentar proyectos
- Facilitar la comunicación

#### Diagrama de clases

Es el diagrama más utilizado en POO.

Representa:
- Clases
- Atributos
- Métodos
- Relaciones
#### Estructura de una clase UML
| Persona           |
|:----------------- |
| - nombre: String  |
| - edad: int       |
|                   |
| + saludar(): void |
#### Significado de símbolos

| Símbolo | Significado |
| ------- | ----------- |
| +       | Público     |
| -       | Privado     |
| #       | Protegido   |

#### Ejemplo UML de herencia
![ejemplo de herencia](https://diagramasuml.com/wp-content/uploads/2018/08/clases6.png)

#### Herramientas para crear UML

- StarUML
- Enterprise Architect
- Visual Paradigm
- Draw.io
- Lucidchart
### 1.4. Herencia Simple

#### Definición

La herencia es un mecanismo mediante el cual una clase puede adquirir atributos y métodos de otra clase.

La clase que hereda se llama:

- Clase hija
- Subclase
- Clase derivada

La clase principal se llama:

- Clase padre
- Superclase
- Clase base

#### Sintaxis
```java
class Hija extends Padre {

}
```

#### Ejemplo práctico

#### Clase padre
```java
class Persona {
	String nombre;

	void mostrarNombre() {
		System.out.println("Nombre: " + nombre);
	}
}
```

#### Clase hija
```java
class Estudiante extends Persona {
	String carrera;
	
	void mostrarCarrera() {
		System.out.println("Carrera: " + carrera);
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {

		Estudiante est = new Estudiante();
		
		est.nombre = "Ana";
		est.carrera = "Ingeniería";
		
		est.mostrarNombre();
		est.mostrarCarrera();
	}
}
```

## Salida
```none
Nombre: Ana
Carrera: Ingeniería
```
#### Constructor y herencia
```java
class Animal {
	
	Animal() {
		System.out.println("Constructor Animal");
	}
}

class Perro extends Animal {
	
	Perro() {
		System.out.println("Constructor Perro");
	}
}
```

#### Uso de super

La palabra reservada `super` permite acceder a miembros de la clase padre.
```java
class Persona {
	String nombre;

	Persona(String nombre) {
		this.nombre = nombre;
	}
}

class Empleado extends Persona {
	double sueldo;

	Empleado(String nombre, double sueldo) {
		super(nombre);
		this.sueldo = sueldo;
	}
	void mostrar() {
		System.out.println(nombre + " " + sueldo);
	}
}
```
#### Ventajas de la herencia

- Reutilización de código
- Organización jerárquica
- Reducción de duplicidad
- Facilita mantenimiento

#### Desventajas

- Acoplamiento excesivo
- Jerarquías complejas

### 1.5. Polimorfismo
#### Definición

El polimorfismo permite que un objeto pueda comportarse de diferentes maneras.

#### **Tipos de polimorfismo**

#### Polimorfismo en tiempo de compilación

Se logra mediante:

- Sobrecarga de métodos

#### Polimorfismo en tiempo de ejecución

Se logra mediante:

- Sobrescritura de métodos
#### Sobrescritura de métodos (Override)
```java
class Animal {
	
	void hacerSonido() {
		System.out.println("El animal hace un sonido");
	}
}
```
#### Clase hija
```java
class Perro extends Animal {
	@Override
	void hacerSonido() {
		System.out.println("El perro ladra");
	}
}

class Gato extends Animal {
	@Override
	void hacerSonido() {
		System.out.println("El gato maúlla");
	}
}
```
#### Uso del polimorfismo
```java
public class Main {
	public static void main(String[] args) {
	
		Animal a1 = new Perro();
		Animal a2 = new Gato(); 
		
		a1.hacerSonido();
		a2.hacerSonido();
	}
}
```
#### Salida
```none
El perro ladra
El gato maúlla
```

#### Ventajas del polimorfismo
- Flexibilidad
- Reutilización
- Código más limpio
- Facilita extensibilidad

### 1.6. Clases abstractas
####  Definición

Una clase abstracta es una clase que no puede ser instanciada.
Sirve como base para otras clases.

Puede contener:
- Métodos abstractos
- Métodos concretos
- Atributos
#### Sintaxis
```java
abstract class Figura {

}
```
#### Método abstracto

Es un método que no tiene implementación.
```java
abstract void calcularArea();
```
### Ejemplo completo
```java
abstract class Figura {

	abstract void calcularArea();
}

class Cuadrado extends Figura {

	double lado;
	
	Cuadrado(double lado) {
		this.lado = lado;
	}

@Override
	void calcularArea() {
		double area = lado * lado;
		System.out.println("Área: " + area);
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	  
	Figura fig = new Cuadrado(5);
		fig.calcularArea();
	}
}
```
#### Salida
```none
Área: 25.0
```
#### Diferencia entre clase abstracta e interfaz

| Clase Abstracta               | Interface             |
| ----------------------------- | --------------------- |
| Puede tener atributos         | Solo constantes       |
| Puede tener métodos concretos | Métodos abstractos    |
| Se usa con extends            | Se usa con implements |

### Interface

#### Definición

Una interface define un conjunto de métodos que una clase debe implementar.

#### Características

- No puede instanciarse.
- Todos los métodos son públicos y abstractos.
- Permite herencia múltiple.

#### Sintaxis
```java
interface Animal {
	void sonido();
}
```

#### Implementación
```java
class Perro implements Animal {

	@Override
	public void sonido() {
		System.out.println("Guau Guau");
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	
		Animal perro = new Perro();
		perro.sonido();
	}
}
```

#### Implementar múltiples interfaces
```java
interface Volador {
	void volar();
}
interface Nadador {
	void nadar();
}

class Pato implements Volador, Nadador {

	@Override
	public void volar() {
		System.out.println("El pato vuela");
	}
	@Override
	public void nadar() {
		System.out.println("El pato nada");
	}
}
```
#### Ventajas de las interfaces

- Flexibilidad
- Bajo acoplamiento
- Reutilización
- Soporte para múltiples comportamientos
### 1.8. Relaciones entre clases

Las relaciones entre clases permiten representar cómo interactúan los objetos.

#### **1.8.1. Asociación**
#### Definición
La asociación representa una relación entre dos clases donde ambas pueden existir independientemente.

#### Ejemplo conceptual

- Un estudiante pertenece a una universidad.
- Un médico trabaja en un hospital.

#### Ejemplo en Java

```java
class Universidad {
	String nombre;
	
	Universidad(String nombre) {
		this.nombre = nombre;
	}
}
```

```java
class Estudiante {
	String nombre;
	Universidad universidad;

	Estudiante(String nombre, Universidad universidad) {
		this.nombre = nombre;
		this.universidad = universidad;
}

	void mostrar() {
		System.out.println(nombre + " estudia en " + universidad.nombre);
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	
		Universidad uni = new Universidad("UPEA");
		
		Estudiante est = new Estudiante("Jose", uni);
		
		est.mostrar();
	}
}
```
#### UML de asociación
```none
Estudiante -------- Universidad
```
### **1.8.2. Agregación**
#### Definición

La agregación es una relación "tiene un" donde una clase contiene objetos de otra clase, pero estos pueden existir independientemente.

#### Ejemplo conceptual

- Un equipo tiene jugador.
- Una biblioteca tiene libro.

Los jugadores pueden existir aunque el equipo desaparezca.

#### Ejemplo en Java

```java
class Jugador {
	String nombre;
	
	Jugador(String nombre) {
		this.nombre = nombre;
	}
}
```

```java
import java.util.ArrayList;

class Equipo {

	String nombre;
	ArrayList<Jugador> jugadores;
	
	Equipo(String nombre) {
		this.nombre = nombre;
		jugadores = new ArrayList<>();
	}

	void agregarJugador(Jugador jugador) {
		jugadores.add(jugador);
	}
	void mostrarJugadores() {
		for (Jugador j : jugadores) {
			System.out.println(j.nombre);
		}
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	
	Jugador j1 = new Jugador("Carlos");
	Jugador j2 = new Jugador("Luis");
	
	Equipo equipo = new Equipo("Bolivia FC");
	
	equipo.agregarJugador(j1);
	equipo.agregarJugador(j2);
	
	equipo.mostrarJugadores();
	}
}
```

#### UML de agregación
```none
Equipo ◇-------- Jugador
```

#### **1.8.3. Composición**

#### Definición

La composición es una relación fuerte entre clases.

Cuando el objeto principal se destruye, los objetos contenidos también desaparecen.

#### Ejemplo conceptual

- Una casa tiene habitaciones.
- Un automóvil tiene motor.

Si la casa deja de existir, las habitaciones también.

#### Ejemplo en Java
```java
class Motor {

	void encender() {
		System.out.println("Motor encendido");
	}
}
```

```java
class Auto {
	
	private Motor motor;
	
	Auto() {
		motor = new Motor();
	}
	
	void arrancar() {
		motor.encender();
		System.out.println("Auto arrancando");
	}
}
```
#### Uso
```java
public class Main {
	public static void main(String[] args) {
	
		Auto auto = new Auto();
		auto.arrancar();
	}
}
```

#### UML de composición
```none
Auto ◆-------- Motor
```
#### Diferencia entre agregación y composición

| Agregación                           | Composición                               |
| ------------------------------------ | ----------------------------------------- |
| Los objetos pueden existir separados | Los objetos dependen del objeto principal |
| Rombo vacío                          | Rombo lleno                               |



