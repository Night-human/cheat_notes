# Clases y objetos

Los objetos son instancias de clases. Las clases definen la estructura y comportamiento de los objetos.

## Características

> Atributos

Son las propiedades o características que describen a un objeto. También conocidos como variables de instancia.

> Métodos

Son las funciones o procedimientos asociados a la clase. Definen el comportamiento de los objetos y permiten manipular los atributos.

**Constructores**

Son métodos especiales utilizados para inicializar objetos. Pueden recibir argumentos e inicializar atributos cuando se crea la instancia de la clase.

> Modificadores de acceso

Los modificadores de acceso controlan el alcance y visibilidad de las **clases**, **atributos** y **métodos**

- **public**: Accesible desde cualquier parte del programa.
- **default**: Si no tiene modificador, la clase es accesible solo dentro del paquete donde se encuentra.
- **private**: Solo es accesible desde la propia clase.
- **protected**: Es accesible para las clases del propio paquete y por herencia.

Ejemplo:

- Clase: Coche
- Atributos: Marca, Modelo
- Métodos: arrancar, detener

public class Coche {

    public string marca;

    public string model;

    public void arrancar () {

    //Code

    }

    public void detener () {

    //Code

    }

}
