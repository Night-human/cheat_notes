# Abstracción

Es el proceso de identificar las características esenciales de un objeto y omitir lo innecesario. Las clases proporcionan una forma de abstracción.

Ejemplo:

    //CLASE ABSTRACTA

    abstract class Animal {
        private string nombre;

        public Animal (String nombre) {
            this.nombre = nombre;
        }

        //Método abstracto que se implementara en la herencia para cada animal
        public abstract void sonido ();

        //Método compartido que aplica a todo animal
        public void dormir () {
            print(this.nombre + "esta durmiendo");
        }

    }

    //CLASE QUE HEREDA LA ABSTRACCIÓN

    class Gato extends Animal{
        public Gato (String nombre) {
            super(nombre);
        }

        //Método implementado en la herencia
        public void sonido() {
            print(getNombre() + "esta maullando");
        }
    }

    //CLASE MAIN

    public class Main {
        
        Animal gato = new Gato("Elly");
        gato.sonido();
        gato.dormir();

    }