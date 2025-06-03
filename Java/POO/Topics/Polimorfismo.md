# Polimorfismo

Permite que objetos de diferentes clases se comporten de manera similar. Se puede utilizar interface, clase abstracta y sobrecarga de métodos.

Ejemplo:

    //Interface que implementa un método
    interface Sonido {
        void sonido();
    }

    //Clase que hace contrato con la interface
    class Animal implements Sonido {
        private string nombre;

    public Animal(string nombre) {
            this.nombre = nombre;
        }

    @Override
        public void sonido() {
            print(nombre + " emite un sonido genérico");
        }
    }

    //Clase que hereda de la clase animal y el método
    class Pato extends Animal{
        Public Pato(string nombre) {
            super(nombre);
        }

    @Override
        public void sonido() {
            print("El pato hace Quack");
        }
    }
