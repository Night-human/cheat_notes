# Encapsulamiento

Se ocultan los detalles internos de un objeto y se exponen los necesarios con los modificadores de acceso. Acceso controlado a atributos y métodos.

Ejemplo:

Clase: CuentaBancaria
Atributos: titular, saldo
Métodos: Retirar, Depositar

    public class CuentaBancaria {
        //Se limita el acceso a los atributos

        private String titular;
        private double saldo;

        public CuentaBancaria(String titular, double saldoInicial) {
            this.titular = titular;
            
            if(saldoInicial >= 0) {
                this.saldo = saldoInicial;
            }
        }

        //Solo se permite manipular el saldo mediante retiro y deposito

        public void retirar(double cantidad) {
            if(cantidad > 0 && cantidad <= this.saldo) {
                this.saldo -= cantidad;
            }
        }

        public void depositar(double cantidad) {
            if(cantidad > 0) {
                this.saldo += cantidad;
            }
        }

        //Se permite solo la lectura de los atributos

        public String getTitular() {
            return this.titular;
        }

        public double getSaldo() {
            return this.saldo;
        }
    }
