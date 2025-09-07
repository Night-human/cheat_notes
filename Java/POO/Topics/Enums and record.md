# Enum

Enumeration is a special data type used to define a fixed set of constants. It is useful when you have a variable that should only take a limited number of possible values.

Key features

- Type-safe constants: prevents unwanted values to being assigned.
- Methods and fileds: enums can have constructors, methods, and fields.
- switch state compatibility: Easily used in switch-case statements.
- Singleton-like behaviour: enum instances are implicitly public static final.


        public enum Day {
            SUNDAY, MONDAY, TUESDAY, WEDNSDAY, THURSDAY,  FRIDAY, SATRUDAY
        }

        print(Day.SUNDAY); // SUNDAY


        public enum Light {
            ON("Light is on"), OFF("Light is off");

            private String description;

            Light(String description) {
                this.description = description;
            }

            public String getDescription() {
                return description;
            }
        }

        print(Light.ON.getDescription()); // Light is on

Interface implementation

    interface Greetable {
        void greet();
    }

    public enum Mood implements Greetable {
        HAPPY {
            public void greet() {
                System.out.println("Im happy");
            }
        },
        SAD {
            public void greet() {
                System.out.println("Im sad");
            }
        }
    }

    Mood.SAD.greet(); // Im sad

## Record

A record is a special type of class. Records are designed to be immutable data carriers, making them perfect for modeling simple data structurews without needing to write boilerplate code.

Key features

- Automatic toString(), equals(), and hashCode() implementations.
- Immutable fileds.
- Compact constructor syntax. Automatic getters and no setters are created since records are immutable.

        public record Person(String name, int age){
            public String greet(){
                return "Hello world";
            }
        }

        Person p = new Person("Su", 20);
        System.out.println(p.name()); // Su
