# Herencia

Permite que una clase herede atributos y métodos de otra. Fomenta la reutilización de código y la creación de jerarquías de clase.

Ejemplo:

- clase: Recipiente
- Atributos: nombre, material
- Métodos: llenar, vaciar

  //Super clase
  public class Recipiente {
  protected String nombre;
  private String material;

  public Recipiente(String nombre, String material) {
  this.nombre = nombre;
  this.material = material;
  }

  abstract void llenar(string producto);

  public void vaciar() {
  print(nombre + " se ha vaciado");
  }
  }

  //Subclase
  public class Taza extends Recipiente {

  public Taza(string nombre, string material) {
  super(nombre, material);
  }

  @Override
  public void llenar(string producto) {
  print(this.nombre + " se ha llenado con " + producto);
  }

  }
