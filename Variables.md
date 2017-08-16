# Variables
--------

> **Variable**
> A variable is a named storage that programs can manipulate, with each variable having a specific type

#### Primitive data types
- `byte` - A whole number, minimum -128, maximum 127
- `short` - A whole number, minimum -32768 and the maximum is the positive counterpart. Used to save memory, half the size of an integer.
- `int` - A whole number, minimum -2,147,483,648 and the maximum is the positive counterpart. **Decimals are not supported.**
- `long` - A whole number, minimum -2^63 and the maximum is the positive counterpart. **Decimals are not supported.**
- `float` - Single-precision floating point. Used to save memory in large arrays of FP numbers. **Never use this type for precise values.**
- `double` - Double-precision floating point. Used as the default for decimal numbers. **Never use this type for precise values.**
- `boolean` - One-bit datatype with only two possible values: `true` or `false`
- `char` - A single Unicode character

###### Examples
```
int a, b, c;         // Declares three unitialized ints, a, b, and c.
int a = 10, b = 10;  // Declares two initialized ints a and b with the value 10
byte B = 22;         // initializes a byte type variable B.
double pi = 3.14159; // declares and assigns a value of PI.
char a = 'a';        // the char variable a is initialized with value 'a'
```

### Kinds of Variables
There are three kinds of variables in Java. The three kinds are:
- Local variables
- Instance variables
- Class/Static variables

> **Local Variables**
> Local variables are declared in methods, constructors or blocks. They are created when the method, constructor or block is called and destroyed when the method, constructor or block exits. Access modifiers cannot be applied to local variables and are visible only within the declared scope.

> **Instance Variables**
> Instance variables are declared in the class itself, not inside a method, constructor or any block. They are initialized and destroyed when the 
containing object is initialized and destroyed, respectively.
> The variable can be declared at any position in the class, however it is common practice to declare all class-scoped variables at the top of the class, before any methods or constructors.
> The variable can be accessed directly within methods and constructors, however it is common practice to access these prefixed with `this` to avoid naming collisions.

> **Static Variables**
> Static variables are declared in the same way instance variables are, however they are prefixed with `static` **before** the type declaration.
> There is one copy of static variables per class, whereas instance variables are present as many times as there is an instance of the containing object.
> Static variables are stored in *static* memory, meaning they should be declared final.

> **Variable Initialization**
> Local variables require initialization to be interacted with, while instance and static variables are assigned a default value (falls back to null if there is no default value.)

##### Access modifiers
There are three levels of security that can be set for variables, methods etc.
- `private`: Only the containing class may interact with the variable directly
- `protected`: Only the classes in the containing package may interact with the variable directly
- `public`: All classes may interact with the variable directly

> **When setting access modifiers for variables, note that they can only be applied to instance and static variables.**

##### Examples

###### Local Variables
```
// Will run
public void pupAge() {
   int age = 7
   System.out.println("Puppy age is : " + age);
}
// Will NOT run
public void pupAge() {
   int age;
   age = age + 7;
   System.out.println("Puppy age is : " + age);
}

public static void main(String args[]) {
   Test test = new Test();
   test.pupAge();
}
```

###### Instance Variables
```
import java.io.*;
public class Employee {

   // this instance variable is visible for any child class.
   public String name;

   // salary  variable is visible in Employee class only.
   private double salary;

   // The name variable is assigned in the constructor.
   public Employee (String empName) {
      name = empName;
   }

   // The salary variable is assigned a value.
   public void setSalary(double empSal) {
      salary = empSal;
   }

   // This method prints the employee details.
   public void printEmp() {
      System.out.println("name  : " + name );
      System.out.println("salary :" + salary);
   }

   public static void main(String args[]) {
      Employee empOne = new Employee("Ransika");
      empOne.setSalary(1000);
      empOne.printEmp();
   }
}
```

### Static Variables
```
import java.io.*;
public class Employee {

   // salary  variable is a private static variable
   public static final double SALARY;

   // DEPARTMENT is a constant
   public static final String DEPARTMENT = "Development ";

   public static void main(String args[]) {
      SALARY = 1000;
      System.out.println(DEPARTMENT + "average salary:" + SALARY);
   }
}
// Meanwhile, in another class...
public class Company {
   private double averageWage;

   public Company() {
      averageWage = Employee.SALARY
   }
}
```
