## ¿Que es un patron de diseño?
Un patron de diseño es un ejemplo escrito de codigo PHP, en el cual se muestra una estructura a seguir para evitar posibles errores en la creacion de software.
## ¿En que consiste?
Son una serie de instrucciones echas en un codigo PHP, que se usan para comprobar y asegurar que todo esta acorde a lo establecido sin necesidad de reescribir el codigo al completo y solo modificando aquello que pueda resultar problematico, esto tambien puede ser ajustado por el usuario para adaptarlo aun programa que ya este funcionando.
## ¿Porque aprender sobre patrones?
Los patrones de diseño a largo plazo son muy utiles, ya que al estar predifinidos estan libres de posibles errores que puedan ocurrir, si por un casual nosotros queremos desarrollar un software los patrones de diseño nos permiten enfocarnos en que clase de programa vamos a realizar y si es funcional lo que estamos desarrollando.
## Ejemplos de uso
En mi explicacion hare uso de este codigo el patron de diseño que he usado es el Composite ya que a partir de la estructura que ya tenia se cumplian algunos de los parametros.
- Lo primero es crear una clase con los correspondientes valores en este caso Person a partir de este se ira generando los valores que nunca cambiaran y se almacenaran de forma predefinida.
- Despues crearemos la clase Employee que sera una extension de Person, con esto conseguimos que los valores que posee Person sean utilizados en Employee sin necesidad de volver a indicarlos.
- Tras ello al llamar a la clase Employee con los parametros que le hayamos incorporado nos mostrara el resultado que indicamos al final del todo.
- Cabe destacar que el ejemplo de Composite que se usaba en la pagina de Patrones de diseño de php hacia un ejemplo en el que se indicaba el acceso a un DOM, por lo que a partir de este codigo PHP veo un ejemplo un poco mas basico de la estructura de Composite "Un almacenamiento de datos de una Persona que se de de alta como un Empleado" el cual si se quisiera podria tener otra rama que fuera Boss(Jefe) y darle un enfoque mas extenso pudiendo mejorarse o incluso acortarse con algunos ajustes.
```php
<?php
    /**
     * Obtencion de datos de una persona
     * @autor 10691
     * @parametrosPersona Valores que tendran en general cada uno
     * @parametrosEmployee Valores que tendran especificamente los que sean empleados
     * @muestraEmployee Selecciona los valores que se le indicaron y los devuelve
     */
    class Person {
        /*Si se pone public esta no necesitara el setName y cuando se coloque private si ademas
        de un getName y setName*/
        protected $name;
        protected $age;
        private $dni;
        private $social;
        public $direccion;
        public function getName() {
            return $this->name;
        }
        public function setName($name)
        {
            $this->name = $name;
        }
        private function privateNameAge() {
            return "{$this->name} is {$this->age} years old";
        }
        protected function protectedNameAge() {
            return "{$this->name} is {$this->age} years old";
        }
    }
    /** 
     * Esta clase es una extension de Person ya que recoge datos de la anterior clase.
    */
    class Employee extends Person {
        private $designation;
        private $salary;
        public $cargo;
        private $aseguradora;
        public function __construct($name, $age, $dni, $social, $direccion, $cargo, $salary, $designation, $aseguradora) {
            $this->name=$name;
            $this->age=$age;
            $this->dni=$dni;
            $this->social=$social;
            $this->direccion=$direccion;
            $this->cargo=$cargo;
            $this->salary=$salary;
            $this->designation=$designation;
            $this->aseguradora=$aseguradora;
        }
        public function getAge() {
            return $this->age;
        }
        public function getdni() {
            return $this->dni;
        }
        public function getsocial() {
            return $this->social;
        }
        public function getdireccion() {
            return $this->direccion;
        }
        public function getDesignation() {
            return $this->designation;
        }
        public function getSalary() {
            return $this->salary;
        }
        public function getcargo() {
            return $this->cargo;
        }
        public function getaseguradora() {
            return $this->aseguradora;
        }
        public function getNameAge() {
            return $this->protectedNameAge();
        }
    }
    $employee = new Employee('Bob Smith', 50, '34890890P', 'Santander',  'Calle Esperanza Nº3', 'Supervisor', '30k', 'Programas S.A', 'Santander');
    echo "Nombre: ",$employee->getName(); // prints 'Bob Smith'
    echo "<br>"; 
    echo "Edad: ",$employee->getAge(); // prints '30' 
    echo "<br>"; 
    echo "Designado: ",$employee->getDesignation(); // prints print Programas.S.A
    echo "<br>"; 
    echo "Salario: ",$employee->getSalary(); // prints '30K'
    echo "<br>"; 
    echo "DNI: ",$employee->getdni(); // print 34890890P
    echo "<br>"; 
    echo "Seguridad Social: ",$employee->getsocial(); // print Santander
    echo "<br>"; 
    echo "Direccion: ",$employee->getdireccion(); // print Calle Esperanza Nº3
    echo "<br>"; 
    echo "Cargo: ",$employee->getcargo(); // print supervisor
    echo "<br>"; 
    echo "Aseguradora: ",$employee->getaseguradora(); // print Santander
    echo "<br>"; 
    echo $employee->getNameAge(); // prints 'Bob Smith is 30 years old.' 
?>
```

