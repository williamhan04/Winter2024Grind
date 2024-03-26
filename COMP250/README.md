# Introduction to computer science
## 1. Java syntax
-----
- High-level language
- Compiled and interpreted
    - Easy, fast and portable
### Statements
- Performs a basic operation
- Ends in a ;
### Printing to the console
- System.out.println() -with newline
- System.out.print() -without newline
- Java is case sensitive
### Variables
-----
1. Declaration :
int a;
2. Assignment :
a = 3;
3. New assignment ;
a = 5;
### Expressions and operators
------
#### + operator
- Between strings, it concatenates
- Between numbers, it adds them
- **Expressions are evaluated left from right**
#### Logical operators
- Produces a boolean
    - NOT !
    - AND &&
    - OR ||
#### Post increment
- x++
- x--


When used part of a statement, increment happens after the code is executed

### If-else
- Only one block is executed. Order matters!
- As soon as one is executed, rest is skipped
``` java
if (x > 0) {
    System.out.println("Positive");
} else if (x < 0) {
    System.out.println("Negative");
} else {
    System.out.println("Zero");
}
```
### While loop
Executed as long as statement is true
```java
while (condition) {
    //some code
}
```
### For loop
1. Initalizer is executed
2. If condition true, body executed. Otherwise end
3. Update executed and go back to 2.
```java
for (int i = 1; i <= 10; i++) {
    //some code
}  
```
### Void methods
When used part of method header, indicates that it returns nothing
### Value methods
- Declare type of return value
- At least one return statement
    - Code that appears after return statement is **dead code** 
    - If it reaches dead code, compile-time error
### Overloading
- More than one method with the same name
- Legal as long as different parameters
### Scope of a variable
It only exists inside the block it has been called
### Floating point
- Java distinguishes 1 and 1.0
- 1.0 is a double

## 2. Type Casting, Strings & Arrays
### char and unicode
-----
#### char
- primitive data type
- char letter = 'a';
- char appears in single quotes and contains only 1 character
- 16 bits in memory to store a value

escape sequences are char
- \n
- \' or \"
- \t
#### Unicode
International character set that java uses
- ASCII 7 bits can represent 128 characters
- UNICODE 16 bits 65536 characters
### Type casting
-----
#### Primitive type conversion
- when going from int to double(widening conversion), dont need explicit cast
- when going from double to int(narrowing conversion), need explicit cast
```java
int i = 3;
double d = 4.2;
d = i;
d = 5.3 * i
i = (int) d;
char c = (char) i;
```
### Strings
----
String is a class and string literal is an Object
#### Comparing strings
- equals(Object anObject)
- equalsIgnoreCase(String anotherString)
- those methods need to be called on a specific value and not on a class
```java
String course = "COMP 250";
String course2 = "comp 250";
boolean a = course.equals.course2
boolean b = course.equalsIgnoreCase.course2
```
**Do not use ==, =! on strings**
#### Other string methods
- s.length()
- s.charAt(i)
#### Converting types with strings
```java
// int or double to String
String s == "" + 4;
// String to int
int x = Integer.parseInt("54");
String s =  "5";
int y = Integer.parseInt(s);
//String to double
double z = Double.parseDouble("5.4");
```
### Arrays
Container that holds a **fixed number** of values of the **same type**
- values are called elements
- list of elements is indexed, order matters
- arrays are mutable
#### 1. Declaration
```java
type[] variable_name;
String[] days;
int[] grades;
```
#### 2. Initialization 
Method 1
```java
String[] days = {"Monday", "Tuesday", "Wednesday",
"Thursday", "Friday", "Saturday", "Sunday"};
```
Doesnt work if don't know lenght or values of program before program runs

Method 2
```java
String[] days = new String[7];
days[1] = "Tuesday";
days[0] = "Monday";
days[6] = "Sunday";
days[5] = "Saturday";
days[2] = "Wednesday";
days[3] = "Thursday";
days[4] = "Friday";
```
#### Default values
when we create and initialize an array, java assigns default values until we assign them
- numerical arrays: 0
- string/reference type arrays: null
- char arrays: char with ASCII value of 0
- boolean: false
#### Traversing arrays with for loop
```java
double sum = 0.0;
for (int i = 0; i <grades.length; i++){
    sum += grades[i];
}
double avg = sum/grades.length;
```
#### Comparing arrays
Import java.util.Arrays;

Arrays.equals(array1,array2);
#### Other useful methods
- Array.toString(x)
- Array.sort(x)
### Multidimensional arrays
Ways to create
```java
int[][] numbers = {{1},{1,2},{1,2,3}};
int[][] numbers = new int[3][2];
int[][] numbers = new int [3][];
```
#### Comparing inner arrays
Arrays.deepEquals(array1, array2)
### Reference type
Non-primitive types. They store a reference to the location in memory containing the value.

Any reference type value can have null value (absence of address)
#### Default values
Array elements are initialized with default values
- int/short/byte with 0
- double/float with 0.0
- boolean with false
- char with 0
- reference types with null
## 3. OOD1 Packages, Fields, Modifiers, and Constructors
### Packages
Packages>class>methods>commands

To define a package, write at the top of the file 
```java
package oogaBooga
```
#### Using a class outside my package in my program
```java
// Specify entire path everytime
animals.Dog myDog = new animals.Dog();
// Import the package member
import animals.Dog;
// Import the entire package
import animals.*;
```
### Random
```java
import java.util.Random;
Random randomGenerator = new Random();
Random otherGenerator = new Random(seed);
int randomNumber = randomGenerator.nextInt(100);
```
### Objects and Classes
Java is an object-oriented language. It uses objects to represent data and provides methods related to them.
#### Classes
Each time we define a class, we create a new object type with the same name.

A class is a blueprint for a type of object; it specifies what properties they have and what methods can operate on them. 

An object is an instance of some class.

#### Nested classes
Class within another class
- If a class is only usefull to another class
- Allows better control over data

### Fields
- Variables that denote the data stored by an object
- Declared at the beginning of the class definition
#### Modifiers
- Keyword that determines how they can be used
    - public
    - protected 
    - default (no keyword)
    - private
    - static 
    - final 
    - abstract
#### Private vs Public
Access control modifiers (determines where a method or variable can be accessed)
- private: is only accessible within the class where it was defined
- public: accessible from anywhere
- Outer classes can only be declared public or package private
#### Static vs Non-static
Non-access modifiers
- Static
    - Independent from one specific instance of the class
    - Class variables
    - Called with ClassName.methodName()
- Non-static
    - Belongs to an instance of the class
    - Instance variables
    - Called with obj.methodName()
#### Local variables vs fields
Local variables 
- are called inside a method or block
- only accessible within method or block it was 
- **CAN'T HAVE ACCESS MODIFIERS** Can't access from other classes or methods

Fields (class and instance variables) 
- are called inside a class but outside the method
- class variables accessible within any method of block in that class
- Instance variables accessible only within the class or from non-static methods of the class
- Can have access modifiers. Accessible from other classes if declared public
#### Initial values
When an object gets created, all the attributes are set by default. We need a constructor to specify initial values.
## 4. OOD2 Constructors, get/set methods, toString()
### Constructors
- Executed when a new object of that class is created
- Same syntax as other methods, **except**:
    - name of constructor must be the same as the name of the class
    - no return type (not even void)
    - is non-static
#### this Keyword
- refers to the object on which the method has been called
    - In the case of a constructor, this refers to the current object being created
- distinguishes attributes and local variables with the same name

Example
```java
public class Student{
    private String name;
    private int id;
    
    public Student(String name, int id) {
        this.name = name;
        this.id = id;
    }
}
```
#### this Keyword and static
NEVER makes sense to use them together; static method associated to the entire class, this keyword refers to an instance of the class
#### Overloading
We can overload methods in the same class, with the same name but different parameters  
- println method is overloaded and allows different type as inputs
- if we want a constructor to sometimes take input and sometimes not, we need to overload it
#### Other methods
If the method is static, it has access to the class variables. If it's non-static, it has access to both the class and instance variables
### Get/Set methods
#### Getters and setters
- Usually, all fields should be declared as private. We then declare public methods to regulate how they should be accessed
    - Those methods that give access to the value of a field are called accessors or getters
    - Those methods that allow you to modify the value of a field are called mutators or setters
```java
//most getters have this format
public <type> getField(){
    return this.field;
}
// most setters have this format
public void setField(<type> value){
    this.field = value;
}
```
### Encapsulation
Process of wrapping data and the code acting on that data in one unit to better control the data
- Make all fields private
- Provide getters and setters as needed
### toString()
#### Private and information display
- When fields are all private, it's hard to display contents of Object outside the class
- If we println, we just see a reference
#### toString()
- Each time we use println() with objects, it calls the method toString() on the object and displays the result
- By default, toString() on an object returns a String representing the address where the contents of the Object can be found
- **HOWEVER** , we can include toString() inside the class, to override default toString() and print a readable string
- We can use toString() in any class
```java
public String toString(){
    //returns a value of type String
}
```
## 5. OOD3 Mutable vs Immutable, UML Diagrams and Inheritance
### Mutable vs Immutable
- When all the fields are private in a class, it is an immutable type
- If the only way to assign values to a field is through the constructor, then the values of Object cannot be changed after it has been created
#### Mutable
Mutator methods change the contents of the object
```java
// If we add a second Cat variable referencing the same cat, then it gets changed too
Cat myCat = new Cat("Spritz");
Cat aCat = myCat;
myCat.setName("Small Cat");
```
#### Immutable
There is no method in String that allows us to set the value of a character
```java
String s = "cat";
String t = s;
t = "dog";
// The value of s does not change
```
#### Mutable vs Immutable
-  Mutable
    - More flexible and more efficient, but more error-prone
- Immutable
    - Easier to keep track of
    - Reference types behave like primitive data type
#### Guideline
- Don't write a constructor initializing a mutable reference without making a copy
- Don't add a get/set method to access/mutate a mutable reference type without making a copy
```java
public class Student{
    private String name;
    private int studentID;
    private String[] courses;

    public Student(String n, int id, String[] c){
        ...
    }
    public String[] getCourses(){
        //create a copy
        int n = courses.length;
        String[] copyCourse = new String[n];
        for (int i=0; i<n; i++){
            copyCourses[i] = courses [i];
        }
        return copyCourse;
    }
}
```
### Shallow vs Deep copy
- In a 2D array, a deep copy is created by copying the objects in the original to the new one one by one
- Nothing done to the deep copy can affect the original array   

### Final
If a variable is declared final, it's value cannot be changed after it has been initialized
```java 
final int x = 3;
x = 10 //compile-time error
```
However, we can still change the object that it points at, whithout changing its value
```java
final Cat myCat = new Cat("Small Cat");
myCat = new Cat("Spritz"); // compile time error

myCat.setName("Spritz"); // OK
```
- final fields must be initialized
    - If a class has a final instance variable, we must initialize it in every constructor
    - If a class has a final class variable, we must initialize it in place (on the same line of declaration)
### UML Diagrams
Unified Modeling Language provides a set of standart diagrams for graphically depicting language systems
- +if public
- -if private
- underline if static
### Inheritance
- a class derived from another class is a subclass
- the original one is a superclass
- a subclass inherits all public fields and methods from its superclass except its contructors
#### Object class
- Object class is the only one without a superclass
- Without any specific superclass, every class is implicitly a subclass of Object


Example
```java
public class Animal{
    private Date birth;
    
    public void eat(){
        System.out.println("HEHEHEHA");
        ...
    }
}
```
```java
public class Dog extends Animal {
    private Person owner;

    public void bark(){
        System.out.println("Woof!");
    }
} // Dog inherits eat from animal but not birth because its private. Dog also adds field owner and method bark
```
#### What can you do in a subclass
In a subclass you can use the inherited member as is, replace them or hide them. You can also add new members
- if you write a non-static method with the same signature and return type as the one from the superclass, you are overriding the method
- if you write a static method with same signature and return type, you are hiding the method
#### Overloading vs Overriding
- Overloading: two or more methods in same class with same name but different parameters (signature)
- Overriding: two instance methods with same signature and types, one in parent class and one in child
#### Constructors
- Constructors are not inherited. Each class has its own
- In the implementation of these constructors, you can invoke one of the constructors from the superclass
- If constructor doesn't specifically invoke a superclass constructor, then java inserts a call to the no-argument constructor of the superclass. If superclass doesnt have no argument constructor, compile time error
#### Super
- To access members of the superclass. Used in a similar way to this.
    - Refers to the object on which the non-static method was called
    - Refers to such object as an instance of the superclass
    - In general, not needed. **BUT** must be used if the method you want to access has been overriden or if the field has been hidden
- Inside the subclass constructor to invoke a constructor from the superclass
    - super(); or super(parameter list);
    ```java 
    public Dog(Person owner) {
        super();
        this.owner = owner;
    }
    ```
## 6. OOD4 Object, Type Conversion and Polymorphism
### Modifiers and Inheritance
#### Access control modifiers
- A class can be declared public or package private (no keyword)
- A class extends another class if and only if the latter is visible from where the former is locted
- All public classes can be extended even across packages
#### Nested classes
A nested class is not a subclass. Outer and inner classes have access to everything between them
#### final Keyword
A final class cannot be extended nor overriden
### Object class
Object is the only class in Java without a superclass
#### hashcode()
- returns a 32 bit integer associated to this object
- when invoked on same object more than once, must return the same integer every time
- if o1.equals(o2), then o1.hashCode()==o2.hashCode()
- two different objects can have the same hashcode
#### toString()
- returns string representation of object
- recommended that all subclasses override this method
#### equals()
obj1.equals(obj2) if and only if obj1==obj2
### Type Conversion
- we have seen that an object is of the type of the class from which it was instantiated
- Dog is a subclass of Animal which is a subclass of Object
- So dog is an Animal and also an Object, therefore we can use object of type Dog whenever objects of type Animal or Object are called for
#### Type Casting -Reference Types
- implicit upcasting is ok but downcasting needs to be explicit 
```java
Animal myPet = new Dog();
Dog myDog = myPet; // compile time error
Dog myDog = (Dog) myPet; // ok
```
#### instanceof
- operator used to test whether an object is an instance of the specified type
- returns true or false. If its a null variable, returns false
- we can use it to make sure that downcasting a subclass will not cause a run time error
```java
public static void myMethod(Dog myDog) {
    if(myDog instanceof Beagle) {
        Beagle b = (Beagle) myDog; //downcasting
        b.hunt();
    }
}
```
- Generally want to use instanceof as last resort
- Need to use it to override equals()
```java
public class Dog{
    Person owner;
    ...
    public boolean equals(Object obj){
        if (obj instance of Dog) {
            ...
        }
    }
}
```
### Polymorphism
- Each object can have different forms
- Java calls the appropriate method for the object that is referred to in each variable. It doesn't call the method that is defined by the variable's type
- favor polymorphism and dynamic binding to downcasting and instanceof

### Abstract
#### abstract Methods
- If you want a class to contain a particular method, but you would like the implementation of this method to be specified by the subclasses, then you can declare the method *abstract*
- An abstract method is declared without implementation
```java
public abstract double getArea();// no {} just ;
```
- the class containing the abstract method also needs to be abstract
- Every subclass of the current class must either override the abstract method or declare itself as abstract
#### abstract class
- declared using abstract keyword
- can have abstract and non-abstract methods
- cannot be instantiated
- can have constructors and static methods
- can have final methods which will force the subclass not to change the body of the method
- abstract classes with only non-abstract methods; create classes that cannot be instantiated, but can only be inherited
- we can define constructors; they are called when a subclass gets instantiated
## 7. Array Lists
### Arrays in Java
```java
// with primitive type
int[] myInts = new int[15];
myInts[3] = -732;
// with reference type
Shape[] myShapes = new Shape[428];
shapes[293] = new Shape(triangle);
```
### List 
An ordered set of elements
### ArrayList
- Use an array to store the elements of a list
- Keep track of how many elements we have inserted in the list
- Java's ArrayList creates an array of length 10
#### How to implement various operations
```java
public class ArrayList {
    private Shape[] arr;
    private int size;
    ...
    // get()
    public Shape get(int i) {
        if (i > 0 && i < size)
        return arr[i];
        //otherwise throw new IndexOutOfBoundsException();
    }
    //set
    public Shape set(int i , Shape e){
        if (i>=0 && i <size){
            Shape tmp = arr[i];
            arr[i] = e;
            return tmp;
        }
    }
    //add
    public void add(Shape e){
        if (arr.length == size)//if arr already full
        resize();

        arr[size] = e;
        size = size + 1;
    }
    private void resize(){
        Shape[] bigger = new Shape[arr.length*2]; //example
        for (int i=0, i<size ; i++) {
            bigger[i] = arr[i]
        }
        arr = bigger
    }
}
```
#### Overloading
- add(e)
- add(i,e)
- remove(e)
- remove(i)
#### How to implement
```java
list.add(3,e);
```
#### Java ArrayList class
- array as underlying data structure
- grows the array by 50% (not 100%) when array is full and new element is added
- need to use get set add methods to manipulate the list
- generic class with type parameter
- when create a object of type ArrayList, specify the type of elements by appending < Class Name > 
#### Wrapper classes 
- Integer, Double, and Character wrap a value of primitive type int, double, and char in an object (turn primitive to reference type) it is done automatically
#### Autoboxing and Unboxing
- Autoboxing is the automatic conversion between the primitive types and their corresponding object wrapper classes (int to Integer)
- The other way is unboxing
```java
Integer x = 5; //Autoboxing
Integer x = new Integer(5);
int y = x; //Unboxing
```
#### Immutable types
- Integer, Double, Character are immutable reference types(like String)
- With String, we are never changing the actual object, a new Object gets created every time we change a value
#### Why Wrapper Classes?
- easier in terms of code re-use to have ArrayList require the input to be an Object of reference type instead of primitive type
- eg. all reference types can be compared using .equals(), while == for primitive types
## 8. Linked Lists
Nodes and objects(elements) can be anywhere in memory
### Singly linked list
```java
//nodes
class Snode {
    Shape element;
    Snode next;
}
SNode myNode = new SNode();
myNode.element = new Shape(triangle);
```
A linked list is a sequence of nodes , with a reference to the first(head) and last(tail) nodes
```java
public class SLinkedList{
    private SNode head;
    private SNode tail;
    private int size;
    ...
    private class SNode {
        Shape element;
        Shape next;
    }
}

SLinkedList list = new SLinkedList();
```
#### Linked List Operations
- addFirst(e)
- removeFirst()
- addLast(e)
- removeLast(e)
- ...
#### Worst case time complexity (N = list size)
- For arraylist with N elements, recall that add(0,e) and remove(0) require a loop with N iterations
    - addFirst(), removeFirst(): O(N)
    - addLast(), removeLast(): O(1)
- For linked lists, those methods do not depend on the number of elements in the list
    - addFirst(), removeFirst(): O(1)
    - addLast(): O(1)
    - removeLast():
        - SLinkedList: O(N)
        - DLinkedList: O(1)
### Doubly linked lists
Each node has a reference to the next node **and** the previous node.
```java
class DNode{
    Shape element;
    DNode next;
    DNode prev;
}
DNode myNode = new DNode();
n.element = new Shape(triangle);
//Nodes
```
```java
public class DLinkedList{
    private DNode head;
    private DNode tail;
    private int size;
    ...
    private class DNode{
        Shape element;
        DNode next;
        DNode prev;
    }
}
// List
```
#### Other List Operations
- get(i)
- set(i,e)
- add(i,e)
- remove(i)
- ...
### Linked Lists
Suppose we want to access general node *i* in a linked list. Two issues:
1. Edge cases(i = 0, i = size - 1) require extra code. (long and can lead to errors)
2. How long does it take to access node *i*?
#### Dummy Nodes
```java
public class DLinkedList {
    private DNode dummyHead;
    private DNode dummyTail;
    private int size;
    ...
    public DLinkedList(){
        dummyHead = new DNode();
        dummyTail = new DNode();
        dummyHead.next = dummyTail;
        dummyTail.prev = dummyHead;
        size = 0;
    }
}
```
DummyHead is a permanent head node that does not hold an actual element. AddFirst() inserts the new node after DummyHead, so there is no need to check if head is null.
#### How to Access a Node
get()
```java
public Shape get(int i) {
    DNode node = getNode(i);
    return node.element;
}
private DNode getNode(int i){
    //verify that 0<=i<size omitted
    DNode node = dummyHead.next;
    for (int k=0; k<i; k++){
        node = node.next;
    }  
    return node
}
//faster method
private DNode getNode(int i){
    //verify that 0<=i<size omitted
    DNode node;
    if (i < size/2){
        node = dummyHead.next;
        for(int k = 0; k < 1; k++){
            node = node.next;
        }
    }
    else{
        node = dummyTail.prev;
        for(int k =size -1; k>i; k--){
            node = node.prev;
        }
    }
    return node;
}
```
### Java LinkedList Class
Uses a DLinkedList as the underlying data structure. Has methods that ArrayList doesnt have.
- addFirst()
- removeFirst()
- addLast()
- removeLast()
#### Time Complexity DLinkedList
- addFirst(): O(N)
- getNode(i): O(N<sup>2</sup>)
#### Space Complexity
ArrayList, SLinkedList and DLinkedList data structures all use O(N) for a list of size N. However, SLinkedList uses 2x and DLinkedList uses 3x.
#### ArrayList vs LinkedList
Array lists and linked lists both take O(N) time to add or remove from arbitrary position in the list. In practice, when N is large, array lists are faster.
## 9. Quadratic Sorting a List and Asymptotic Notations
### Sorting Algorithms
- O(N <sup>2</sup>)
    - Selection Sort
    - Bubble Sort
    - Insertion Sort
- Random Sort
- O(N*logN)
    - Heap Sort
    - Merge Sort
    - Quick Sort
### Bubble Sort
- Simplest sorting algorithm
- Repeatedly iterate through list and swap adjacent elements if in wrong order
- After first iteration:
    - Largest element at the end of list (N-1), so after each iteration, can stop one step earlier
    - Smallest anywhere except end
    - List is sorted when no swap in last iteration
```java
//pseudocode
sorted = false
i = 0
while (!sorted){
    sorted = true
    for j from 0 to list.length -i-2{
        if (list[j] > list [j+1]) {
            swap(list[j], list[j+1])
            sorted = false
        }
    }
    i++
}
```
### Selection Sort
- Consider list divided in two parts, one sorted and one unsorted
- Select smallest in unsorted and put it in first place of sorted, then sorted group bigger
```java
//pseudocode
for delim from 0 to N-2{
    min = delim
    for i from delim+1 to N-1{
        if(list[i]<list[min]{
            min = i
        })
    }
    if (min != delim){
        swap(list[min], list[delim])
    }
}
```
Inner loop iterates N*(N-1)/2
### Insertion Sort
- Two parts, sorted and unsorted
- Select first element of unsorted
- Put it in correct position in sorted
- Change where divide array 
- Similar to adding in array list: shift elements ahead by one, then fill the hole
```java
//pseudocode
for i from 0 to N-1{
    element = list[i]
    k=1
    while (k>0 && element<list[k-1]){
        list[k] = list[k-1]
        k--
    }
    list[k]=element
}
```
### Asymptotic notations
- Time taken by algorithm depends on the input and grows with size of each input. This is why running time of an algorithm described with a function of the size of its input
    - Input size: 
        - Can be number of elements in input
        - Can be number of bits required to represent the input
        - Can be described by multiple numbers rather than one
    - Running time is the number of primitive operations(evaluating expression, assigning value, return from method,...) executed
#### Big-Picture Approach
- When analysing algorithms, we look at growth rate of running time. We look at how running time increases with the size of the input in the limit, as the size of input increases without bound
- Find running time as function of input size
- Use asymptotic notation to express the function
- We will use asymptotic notations to describe running time of algorithms
#### Big OH
- Let T(n) be a function that describes time it takes for some algorith to terminate on input size n
- Want to describe how T(n) grows with n, as n becomes large i.e. asymptotic behavior
- Unlike with limits, want to say that T(n) grows like certain simpler function like log<sub>2</sub>n, n, n<sup>2</sup>, ..., 2<sup>n</sup>, etc
- Formal def: Given a function g(n) we denote by 𝑂(𝑔 𝑛 ) (“big-oh of 𝑔 of 𝑛”) the
following set of functions

𝑂(𝑔(𝑛)) = { 𝑓(𝑛): there exist positive constants 𝑐 and 𝑛<sub>0</sub> such that
𝑓(𝑛) ≤ 𝑐𝑔(𝑛) for all 𝑛 ≥ 𝑛<sub>0</sub> }
- We use the O-notation to describe an asymptotic upper bound
#### Observations
- We often write f(n) = O(g(n)) to indicate that fct f(n) is a member of the set O(g(n))
- We sometimes find O-notations used to describe asymptotically tight bounds, but by definition, it only claims asymptotic upper bounds
#### O(1)
We say f(n) is O(1), if there exists 2 positive constants n<sub>0</sub> and c such that, for all n>n<sub>0</sub>, f(n)<= c.
- Therefore f(n) is bounded by a constant
#### Back to insertion sort
The worst-case running time for insertion sort is an<sup>2</sup>+bn+c where a,b and c are constants. a,b>0, c<0. So T<sub>worst</sub>(n) is O(n<sup>2</sup>)
#### Observation on worst-case upper bounds
- When using asymptotic notation with fcts that represent the running time of an algorithm, we need to know which running time we are referring to (worst-case running time, running time regardless input, etc.)
- Since O-notation describes upper bound, when we use it to bound worst-time running time of an algorithm, we have a bound on the running time of the algorithm on every input
- T(n)<= T<sub>worst</sub>(n), if T<sub>worst</sub>(n) = O(g(n)), then T(n) = O(g(n))
#### Tight bounds 
- Since Big O is an upper bound, if f(n) is O(n), then it is also O(n<sup>2</sup>), O(n<sup>3</sup>), etc
- O(n) is a subset of O(n<sup>2</sup>), which is a subset of O(n<sup>3</sup>)
- When we ask for a tight upper bound on f(n) though, we want the simplest function g(n) such that O(g(n)) is the smallest set that f(n) belongs to
#### Common Functions
1 < log<sub>2</sub> n < n < n log<sub>2</sub> n <  n<sup>2</sup> < n<sup>3</sup> <...<2<sup>n</sup> < n!
#### Back to Tight Bounds
If we consider the function f(n) = 5n+7, then the tight upper bound for f is O(n) and not O(nlog<sub>2</sub>n)
#### General Observation
- Never write O(3n), O(5log<sub>2</sub>n),etc.
- Instead write O(n), O(log<sub>2</sub>n), etc.
- Because the point of O-notation is to avoid dealing with constant factors.
- Don't do it although it is still technically correct to write the above
#### Asymptotic lower bounds
Sometimes we want to say that algorithms take *at least* a certain time to run as a fct of the input size n
#### Formal Definition of Big Omega
Given a function g(n), we denote by &#937;(g(n)) the following set of fcts

 &#937;(g(n)) = { f(n): there exist positive constants c and n<sub>0</sub> such that f(n) $\ge$ cg(n) for all n $\ge$ n<sub>0</sub> }


We use &#937;-notation to describe an asymptotic lower bound
#### Back to insertion sort
The best-case running time for insertion sort is an+b where a,b are some constants. a>0, b<0.

 Therefore T<sub>best</sub>(n) is &#937;(n)
 #### Observation on Best-Case lower Bounds
 Since &#937;-notation describes a lower bound when we use it to bound the best-case running time of an algorithm, the we have a lower bound running time of the algorithm for every input.
 #### Insertion Sort
 - We computed T(n), T<sub>best</sub>(n), and T<sub>worst</sub>(n)
 - We have proved that T<sub>worst</sub> is O(n<sup>2</sup>) and T<sub>best</sub>(n) is &#937;(n)
 - Therefore, T(n) is both O(n<sup>2</sup>) and &#937;(n)

 #### Formal Definition of Big Theta
 Given a function g(n), we denote by &theta;(g(n)) the following set of fcts

 &theta;(g(n)) = { f(n): there exist positive constants c<sub>1</sub>, c<sub>2</sub> and n<sub>0</sub> such that c<sub>1</sub>g(n) $\ge$ f(n) $\ge$ cg(n) for all n $\ge$ n<sub>0</sub> }


We use &theta;-notation to describe an asymptotic tight bound
#### Theorem
For any two functions f(n) and g(n);

f(n) = &theta;(g(n)) $\iff$ f(n) = O(g(n)) and f(n) = &#937;(g(n))
#### Does Tight Bound always exist?
No, for example:

Let f(n)=
- n, if n is odd
- n<sup>2</sup> if n is even

f(n) is O(n<sup>2</sup>) but f(n) is not O(n)\
f(n) is &#937;(n), but is not &#937;(n<sup>2</sup>)\
Note that it is improper to say that T(n) is O(n<sup>2</sup>) (for instance), since for a given n, the actual running time varies, depending on the particular input. When we say that, we mean that there exists a function f(n) which is O(n<sup>2</sup>) and T is bounded above by f, no matter the particular input of size n.
## 10. Case Study on Linked Lists
### Case Study
#### Peer programming
- Driver:
    - Share screen and write code according to navigator's instructions
    - Ask questions when lack of clarity
    - Offer alternative solutions, while trusting navigator
- Navigator:
    - Dictates the code  to be written and communicate clearly
    - Explain why they chose this solution
- Tester:
    - Keep track of time and check for syntax/type errors
    - Come up with tests
#### Floyd's Tortoise and Hare Algorithm
- Detect cycles within a sequence of values (e.g. if a linked list contains a cycle)
- Two pointers that move through the sequence at different speeds
    - Start two pointers at beginning of sequence. Hare 2x as fast as tortoise
    - If there is a cycle, hare will eventually meet tortoise
## 11. Stacks
### Abstract Data Type(ADT)
An ADT is a model for data type. It defines it by its behavior from the user's perspective only. It describes the possible valuesand the set of possible operationson the data type.
- It ignores the details of the implementation
- Its more abstract than the data structure(concrete representation of data which includes implementation details)
#### List ADT
- get(i)
- set(i,e)
- add(i,e)
- etc.\
These operations can be defined abstractly, without specifying implementation details of the data structure(e.g. arraylist or linked list)
#### Stack ADT
- push(element): add element to top of stack
- pop(): remove element from top of stack
- peek(): returns top element without removing it
- isEmpty(): checks if stack is empty

A stack is a list. However, it typically does not have operations to access list element *i* directly. It can only access element at one of the ends of the list. Most recently added object is the first one to be removed.
#### How to Implement a Stack
- array list: 
    - push(e) = addLast(e)
    - pop() = removeLast()
- singly linked list:
    - push(e) = addFirst(e)
    - pop() = removeFirst()
- doubly linked list:
     - push() = addLast(e) or addFirst(e)
     - pop() = removeLast() or removeFirst()
#### Balencing parentheses
```java
//pseudocode see if parentheses are matched
while (there are more tokens){ //refer brackets as tokens, this is more general term used in string parsing
    token = get next token
    if token is a left parenthesis{
        push(token)
    }
    else{
        if stack is empty{
            return false
        }
        else{
            pop left parenthesis from stack
            if(popped left parenthesis doesnt match the right parenthesis){
                return false
            }
        }
    }
}
return stack empty //true if stack is empty, false if not
```
#### Stacks in Graphics
Go look notes
#### Overflow and Underflow
- Stack overflow: when a stack has finite capacity and we attempt to push
- Stack Underflow: when we attempt to pop empty stack
## 12. Queues and Interfaces
### Queues
#### ADT
- Queue
    - enqueue(e): add at back
    - dequeue(e): remove from front
- Unlike Stack, its first in, first out
#### How to Implement a Queue?
- Array list:
    - enqueue(e): addLast(e)
    - dequeue(): removeFirst() **SLOW!**
- Singly linked list:
    - enqueue(e): addLast(e)
    - dequeue(): removeFirst()
- Doubly linked list:
    - enqueue(e): any
    - dequeue(): any
#### Implementing a Queue with an Array List
Bad:
- requires shift with each dequeue(), so time complexity is O(n), making it inefficient for large queues
- requirese expansion when array full
- fixed size, can lead to wasted space
#### Implementing a Queue with an Expanding Array
Also bad:
- to dequeue: retrieve element at head and increase index head
- to enqueue: add element at tail +1
- still inefficient usage of space
#### Implementing a Queue with a Circular Array
Good:
- tail = (head+size-1)mod length
#### Increase Length of Array and Copy
Copy so that head remains in same position **Or** copy so that head moves to position 0
```java
enqueue(element) {
    if (size==queue.length){
        //increase size of array
        create a bigger array tmp[] //e.g. 2*length
        for i = 0 to queue.length -1{
            tmp[i] = queue[(head+i)mod queue.length]
        }
        head = 0
        queue = tmp
    }
    queue[(head+size)mod length] = element // we dont have tail variable here
    size++
}
```
```java
dequeue(){
    if size <= 0{
        raise error;
    }
    element = queue[head]
    size = size -1
    head = (head + 1) mod length
    return element
}
```
### Interfaces
- reserved keyword in Java
- like classes, interfaces can be declaredto be public or package private
- can have fields and methods **BUT**:
    - all methods are by default public and abstract
    - all fields public, static and final
- cannot be instantiated
```java
public interface myInterface{ //implicitly abstract no need for keyword abstract
    ...
}
```
Example
```java
public interface MonsterLike{
    public int spook();
    public void runAway(); //methods all implicitly abstract
}
```
#### Inheritance
- To use  an interface you first need a class that implements it.
- Specifies what a class must and not do. It is the blueprint of a class
- A class can implement one or more interfaces with keyword implements
- Interfaces are used to achieve subtyping
- If a class implements an interface but not all of its methods, then the class must be declared abstract
- Interfaces can extend another interface with keyword extends
#### Implements
```java
public class Dragon implements MonsterLike{
    ...
}
```
Inside class Dragon, methods spook() and runAway() must be implemented
#### Interface Instances
- Once a Java class implements a Java interface, an instance of that class can be used as an instance of the interface
#### Extends + Implement
Classes can extend at most one class, but can implement multiple interfaces
#### Interfaces vs Abstract Classes
Interfaces:
- methods abstract by default
- implicitly abstract
- no method can be implemented and only constants(final static fields) can be declared
- useful in situations that all properties should be implemented

Abstract classes:
- not all methods have to be abstract
- abstract keyword must be explicitly used
- can contain methods that have been implemented as well as instance variables
- useful when some general methods should be implemented and specialization behavior should be implemented by child classes
#### Post Java 8
From Java 8 onwards, interfaces can contain the following:
- Default, Static, Private and Private Static methods
#### Generics in Java
- A generic type is a class or interface that is parameterized over types. We use <> to specify the type parameter
```java
//example
public class Cage<T> {
    private T occupant;
    
    public void lock(T p) {
        this.occupant = p;
    }
    public T peek(){
        return this.occupant;
    }
    public void release(){
        this.occupant = null;
    }
}
```
```java
Cage<Dog> crate = new Cage<Dog>();
// now inside crate we can lock only Dogs!
Dog snoopy = new Dog();
crate.lock(snoopy);

Cage<Bird> birdcage = new Cage<Bird>();
// if we call lock on birdcage we must provide a Bird as input
Bird tweety = new Bird();
birdcage.lock(tweety);

// peek() called on crate returns a Dog
// peek() called on birdcage returns a Bird
Dog d = crate.peek();
Bird b = birdcage.peek();
```
#### Generic Types Naming Conventions
- Java Generic Type Naming convention helps us understand code easily
    - E Element
    - K Key (in Map)
    - N Number
    - T Type
    - V Value (in Map)
    - S,U,V, etc. 2nd 3rd 4th types
#### Bounded Type
- Sometimes we want to restrict the types that can be used to create a Cage (or a general parameterized type)
- We can do that using keyword extends or implements
- This will limit the types we can use to instantiate a generic type, but also allow us to use methods defined in the bounds
```java
//e.g.
public class Cage<T extends MonsterLike>{
    private T occupant;

    public T peek(){
        this.occupant.spook();
        return this.occupant;
    }
    public void release(){
        this.occupant = null;
        this.occupant.ranAway();
    }
}
```
```java
// e.g.
public class ArrayList<E> implements List<E>{
    boolean add(E e) {...}
    void add(int i, E e){...}
    boolean isEmpty(){...}
    E get(int i) {...}
    E remove(int i) {...}
    int size(){...}
    void ensureCapacity(int i){...}
    void trimToSize(){...}
//all methods inherited from List are implemented, in addition, others are declared and implemented in ArrayList
}
```
#### How are Interfaces Used?
- Interfaces define new data types
- We can create variables of those types and assign to them any value referencing to instances of classes that implement the specified interface
- Whenever an object of type List is required, any instance of any of the classes implementing List  can be used
#### Inheritance
Remember a class cannot extend more than one class
- Because if two superclass have implemented methods with same signature, which would be inherited by subclass?
## 13. Comparable
### Comparable
#### Java Comparable Interface
- used to define an ordering on objects of user-defined class
- if you have list of objects from a given class you might want to be able to sort it
- *comparable* is part of java.lang package and contains one method named compareTo(Object)
```java
public interface Comparable<T>{
    int compareTo(T o);
}
```
Some of the methods from certain Java classes use compareTo() in their implementation. They assume to be working with Comparable generic types
- sort() from Arrays and Collections
#### Classes that Implement Comparable
- Character, Integer, Float, Double, BigInteger, etc. all implement Comparable<T>
- You cannot compare objects of these classes using the < operator. Instead use compareTo()
#### How to Implement Comparable
- Add implements Comparable in the definition of the class
- Implement compareTo() in your class
```java
public class T implements Comparable<T>{
    public int compareTo(T o){...}
}
```
#### Requirement for Implementing compareTo()
Consider variable t1 and t2 or type T, then t1.compareTo(t2) returns: 
- negative int, if t1< t2
- 0, if t1=t2
- positive int, if t1 > t2

Their relation should be anticommutative and transitive. It is recommended to

(t1.compareTo(t2)==0) == (t1.equals(t2)) because if two objects are considered equal by compareTo() method, they should be equal according to equals() too
#### Example Circle
```java
public class Circle{
    private double radius;
    ...
}
```
How should we implement compareTo() and equals() in order to establish a natural ordering  between elements of type Circle?
- We can compare their radius (or area)
```java
public class Circle extends Shape implements Comparable<Circle>{
    private double radius = 5;

    public int compareTo(Circle c){
        if(this.radius < c.radius)
            return -1;
        else if(this.radius == c.radius)
            return 0;
        else 
            return 1;
    }
    public boolean equals(Object obj){
        return obj instanceof Circle && ((Circle) obj).radius ==  this.radius;
    }
}
```
#### Example Orc
What about orc? Not as straightforward as circle. What should they be compared on?
- we can use compareTo() to compare multiple characteristics
- generally, it is better to reuse existing code than writing our own, thus in this case, we can use compareTo() methods from other classes
```java
public class Orc implements Comparable<Orc>{
    private String name;
    private Integer height;
    private Weapon w;
    public int compareTo(Orc c){
        int result = this.w.compareTo(o.w);
        if (result == 0){
            result = this.height.compareTo(o.height);
        }
        if(result == 0){
            result = this.name.compareTo(o.name);
        }
        return result;
    }
}
```
## 14. Iterable and Iterator + Case Study on Interfaces
### Iterable and Iterator
#### For-each Loop
```java 
int[] numbers = {1,2,3,4,5};
for(int element: numbers){
    System.out.println(element);
}
```
Enhanced for loop can make code more readable and convenient. Not useful when need to refer to index. For certain data structures its the only loop we can use
#### Iterable and Iterator
- The use of a for-each loop is made possible by the use of these two interfaces
- Often confusing for beginners:
    - Objects of type Iterable are representations of a series of elements that can be iterated over (e.g. a specific ArrayList)
    - Objects of type Iterator allows you to iterate through objects that represent a collection(a series of elements)
#### Java Iterable Interface
- A class that implements Iterable needs to implement the iterator() method. It returns an object of type Iterator that can be used to iterate through the elements of this instance
- A class that implements Iterator needs to implement methods hasNext() and next()
```java 
public interface Iterable<T> {
    public Iterator<T> iterator();
}
```
```java
public interface Iterator<T>{
    boolean hasNext();
    T next(); //returns current and advances to next
}
```
The iterator() method returns an iterator to the start of the collection. Using hasNext() and next() you can move forward. If you want to traverse it again, you'll need a new Iterator
#### Iterable and For-each Loop
Implementing the Iterable interface allows an Object to make use of the for-each loop. It does that by calling internally the iterator() method on the object
#### How to Implement the Interfaces
- A class that implements an interface needs to implement every method of the interface
- When we write a class that implements Iterable, we also define an inner class Iterator because we need a class that can create it.
#### Example
```java
public class MyCollection<T> implements Iterable<T>{
    public MyIterator<T> iterator(){
        return new MyIterator<T>.(this);
    }
}
```
```java
public class MyIterator<E> implements Iterator<E>{
    public MyIterator(MyCollection<E> c) {
        ..
    }
}// generally if MyIterator only used by MyCollection, make it an inner class of MyCollection
```
#### SLinkedList
- iterator() returns an object of type Iterator that points to the head of the provided list
- next() returns the element of the list that the Iterator is currently referencing, then moves to the next node

For example check notes
#### List-Intersection Sort
- We want a static void method that takes as input two sorted lists and returns  an array list containing the cats the two lists had in common.
    - If we assume lists are sorted, use two parallel pointers and advance one or the other based on how the elements compare
## 15. Induction and Recursion
### Induction
#### Proofs
1+2+...+(n-1)+n 
- Consider n/2 pairs


1+2+...+n/2+(n/2 +1)+...+(n-1) + n
- If n is even, then adding up the pairs gives n/2*(n+1)
- If n is odd, then n-1 is even. So, 1+2+...+(n-1)+2 = ((n+1)/2)  *n

**look at notes**

#### Recursive(Inductive) Definition
1. Base clause: one or more basic/initial element of the set
2. One or more inductive clauses: Rules on how to generate new elements of the set from old ones
3. Final clause: states that no other element is part of the set
#### Example Natural Numbers
1. 0 is a natural number
2. If n is a natural number, n+1 is also a natural number
3. Nothing else is a natural number
#### Mathematical Induction
"For all n $\ge$ n<sub>0</sub>, P(n) is true"
where n<sub>0</sub> is some constant and proposition P(n) has value true or false for each n
- If n is an element of an inductively defined set, then the statement above can be proven using a technique called mathematical induction
#### Weak Mathematical Induction
1. Base case: Show that the property holds for the basic element of the set
2. Induction set: Assume the property holds for some element n (Induction Hypothesis). Show that the property also holds for any element generated from n using the inductive clauses/
3. Conclusion: The property holds for all elements
#### Proof by Mathematical Induction
We need to prove the following:
1. Base case: P(n<sub>0</sub>) is true, i.e. the property holds for n<sub>0</sub>, which in this case is 1.
2. Induction step: IH: Assume P(k) is true, i.e. the property holds for an element k. Prove that P(k+1) is true, i.e. the property holds for k+1
#### Strong Mathematical Induction
#### Fibonacci Numbers- Inductive Definition
Read notes
### Recursive Algorithms
```java
//example
public static void countdown(int n){
    if(n == 0){
        System.out.print("Go!");
    }
    else{
        System.out.print(n+"");
        countdown(n-1);
    }
}
``` 
countdown(3) prints 3 2 1 Go!
#### Recursive Definition
- Base case(s): one (or a finite number) of terminating scenario that does not use recursion to produce an asnwer
- Recursive or Inductive step(s): rules that determine how to produce an answer from simpler cases
#### Base cases
If there is no base case in a recursive method, or if its never reached, the execution will never end
#### Example: Factorial 
```java
//iterative: use loops to repeat some part of the code to progress through the data
public static int factorial(int n){
    int result = 1;
    for(int i=2; i<=n; i++){
        result= result * i;
    }
    return result;
}
```
```java
//recursive: call themselves in order to solve smaller instances of the same problem until they reach a base case
public static int factorial(int n){
    if (n == 0){
        return 1;
    }
    return n*factorial(n-1);
}
```
#### Example: Fibonacci
```java
//iterative
public static int fibonacci(int n){
    if (n==0 || n==1){
        return 1;
    }
    fib0=1;
    fib1=1;
    for(int i=2; i<=n; i++){
        fib2 = fib0 + fib1;
        fib0 = fib1;
        fib1 = fib2;
    }
    return fib2; 
} 
```
```java
//recursive
public static int fibonacci(int n) {
    if(n==0 || n==1){
        return 1;
    }
    return fibonacci(n-1)+fibonacci(n-2);
}
```
Recursive correct but inefficient. Computes the same quantity many times
## 16. Recursion 1
### Recursive Algorithms
#### Common mistakes
- Forget to handle base case, or one of them
- The recursive step does not reduce the problem to a smaller one, hence the base cannot be reached
#### Example: Tower of Hanoi
```java
tower(n, start, finish, other) {
    if(n==1){
        move from start to finish;
    }
    else{
        tower(n-1, start, other, finish)
        tower(1, start, finish, other)
        tower(n-1, other, finish, start)
    }
}
```
tower() algorithm is correct. 2<sup>n</sup>-1 moves
#### Recursion and Iteration
- Anything recursion can do, iteration can do and vice-versa
- Usually, for simple cases, iteration is easier and for complex cases, recursion is simpler
- The decision of using which might impact the impact of your program
#### Recursive Data Structure
- We can recursively define data structures
- Let's consider arrays
#### LinkedList
- LinkedList<E>class:
    - private E val;
    - private LinkedList<E> next;
#### Example: Recall: Decimal to Binary(Iterative)
A decimal number n requires approx log<sub>2</sub>n bits for its binary representation

**Read Notes**
#### Example: Power recursive
**Read Notes**
## 17. Recursion 2 (Binary Search + Mergesort)
### Binary Search
- Goal: find a given element in a list
- Solution: go through all the elements in the list and check whether solution is there(linear search)
- Could we do faster if list is sorted with?
- Inputs: 
    - A sorted list
    - The element we are looking for(the key)
- IDEA: First compare the key with th element in the middle of the list
    - If the key is less than the middle element, we only need to search the first half of the list, so we keep searching on this smaller list
    - If the key is bigger, we do same thing with second half of the list
    - If the key equals the middle element, we have a match and return its index
#### Implement binary search
- Idea: keep track of the left and right indices denoting the section of th elist that needs to be searched
- What is the index of the element that we compare to the key as a function of the left and right indices?
#### Example look notes
Look at middle element and compare mid=(left+right)/2 right = size-1

Keep doing until find it. If no return -1
#### Binary Search (Iterative)
```java
binarySearch(list, key){
    left = 0
    right = list.size() -1
    while(left<=right){//until there are elements to search
        mid = (left+right)/2
        if(list[mid] == key)
            return mid
        else{
            if (key<list[mid])
                right = mid-1
            else
                left = mid +1
        }
    }
    return -1 //key not in the list
}
```
#### Binary Search(Recursive)
```java
binarySearch(list, key, left, right){
    if(left<=right){
        mid = (left + right)/2
        if(list[mid] == key)
            return mid
        else{
            if(key<list[mid])
                return binarySearch(list,key, left, mid-1)
            else
                return binarySearch(list,key, mid+1, right)
        }
    }
    return -1
}
```
#### Time Complexity
Worst case: element cannot be found. Then the worst case is O(logn) because each time we are having approx half the list

O(logn):
- convert to binary
- binary search
- ...

O(n):
- List operations(findMax, remove)
- grade school addition
- ...

O(n<sup>2</sup>): 
- insertion/selection/bubble sort
- grade school multiplication
- ...
### Merge Sort
Merge Sort is a divide and conquer  algorithm
- Goal: Sort a list
- IDEA:
    - Partition list in two halves
    - Sort each half recursively
    - Merge the sorted half maintaining the order
#### Implementation
```java
mergesort(list){
    if (list.size() <= 1)
        return list
    else{
        mid = (list.size()-1) /2
        list1= list.getElements(0,mid)
        list2= list.getElements(mid+1, list.size()-1)
        list1= mergesort(list1)
        list2= mergesort(list2)
        return merge(list1, list2)
    }
}
```
#### Merging preserving order
Iterate through elements of the two sorted lists, depending on how they compare, decide which element comes first in the merged list.
- When one list is empty, copy remaining elements of other list
#### Implementation of merge
```java
merge(list1, list2){
    list = ... initialize with empty list
    while (!list1.isEmpty() && !list2.isEmpty()){
        if (list1.get(0) < list2.get(0))
            list.addlast(list1.removeFirst())
        else
            list.addlast(list2.removeFirst())
    }
    while (!list1.isEmpty())
        list.addlast(list1.removeFirst())
    while (!list2.isEmpty())
        list.addlast(list2.removeFirst())
    return list
}
```
#### SEE EXAMPLE OF EXECUTION IN NOTES
#### How many operations required to mergesort list of size n
O(nlogn)
#### Complexity
nlog<sub>2</sub>n is much close to n than n<sup>2</sup>
## 18. Recursion 3(Quicksort and Recurrences)
### Quick Sort
- Quick Sort is a divide and conquer algorithm
- Goal: Sort a list
- IDEA: 
    - Pick an element of the array(the pivot)
    - Partition the list moving the pivot to its correct position making sure that all the lower elements are on its left and all the larger on its right
    - Sort the left part and the right recursively
    - Keep doing until theres nothing left to sort
#### The Pivot
 Different versions of Quick Sort pick the pivot in different ways
- First element
- Last element
- Random element
- Median
#### EXAMPLES LOOK AT NOTES
#### Implementation
What do we need:
- A method that swaps two elements
- A way to refer to parts of the list
- A method that places the pivot in its correct position and moves the elements around so that all the lower elements are on the left, and all larger on the right. Call it placeAndDivide
- A method that implements QuickSort, that is:
    - Pick a pivot
    - placeAndDivide
    - quickSort left part
    - quickSort right part
#### Parts of the list
To denote part of the list:
- We can use same thing as binary search: keep track of left and right index denoting where the part begins and ends
#### Pseudocode
```java
quickSort(list, leftIndex, rightIndex){
    //Base case
    if(leftIndex >=rightIndex){
        return; //done
    }
    else{ //recursive step:
        int i = placeAndDivide(list, leftIndex, right Index)
        //i = index where the pivot is placed
        quickSort(list, leftIndex, i-1)
        quickSort(list, i+1, rightIndex)
    }
}
```
```java
placeAndDivide(list, leftIndex, rightIndex){
    //pick the right most element
    pivot <- list.get(rightIndex)
    //place wall to the left
    wall <- leftIndex -1
    // go through all elements and compare them to the pivot
    for(int i =leftIndex; i<rightIndex;i++){
        if(list.get(i)<pivot){
            wall++; //move wall
            swap list.get(i) list.get(wall)//move element behind wall
        }
    }
    swap list.get(rightIndex) list(wall+1) //move pivot next to wall
    return wall+1;
}
```
#### Mergesort vs Quicksort
- Mergesort typically uses an extra list. More space can hurt performance for big lists
- Worst case performance of quicksort will be discuseed later
- Depends which is better
### Recurrences
#### Algorithm Analysis
- We would like to find a function T(n) that describes the running time of an algorithm given an input size n
- It is relatively easy to determine T(n) when our algorithms only have loops (e.g. insertion sort)
- But how do we determine T(n) for a recursive algorithm?
#### Recurrences
A recurrence is an equation or inequality that describes a function in terms of its value on smaller inputs. E.g. Fibonacci

We use recurrences to express the overall running time T(n) of an algorithm with input size n in terms of the running time on smaller inputs. Note that for Fibonacci number n is an input value not the input size
```java
//example
reverse(list){
    if(list.size()==1){ //Base case
        return; //T(1) = b
    }
    first Element= list.removeFirst(); //recursive step
    reverse(list) //now the list has n-1 elements
    list.addLast(firstElement); //T(n) = c+T(n-1)
}
```
We assume removeFirst() and addLast can be executed in constant time (not true if we use ArrayList)
#### How to solve a recurrence
- Forward substitution
- Back substitution
- Recursion-tree method
- Master Theorem
#### Solving the Recurrence using Back Substitution
T(n) = c+T(n-1)
= c+c+T(n-2)
= c+c+c+T(n-3)
= 3c+T(n-3) = ... = kc+T(n-k) = ... = (n-1)c + T(1) = (n-1)c+b = c * n+(b-c)\
Which is &Theta;(n)
#### Example: Sorting a List
```java
sort(list){
    if(list.size() == 1){
        return; //Base case T(1)=a
    }
    minElement= list.removeMin();
    sort(list);
    list.addFirst(minElement); //Recursive step T(n) = b + cn + T(n-1)
}
```
- Assume addFirst() can be executed in constant time
- It would be ok if this step uses time proportionnal to n because removeMin() already takes time proportional to n
#### Solving Recurrence using Back Substitution
T(n) = cn + T(n-1) = cn + c(n-1) + T(n-2) = cn + c(n-1) +c(n-2) +T(n-3) = c[n+(n-1)+(n-2)+...+(n-k)]+T(n-k-1) = c[n+(n-1)+...+2]+T(1), when k=n-2 = 0.5cn<sup>2</sup> +0.5cn-c+a\
which is &theta;(n<sup>2</sup>)
#### Example: Tower of Hanoi 
Look notes
#### You should know
- 1+2+3+...+k= k(k+1)/2
- 1+2+4+8+...+2<sup>k</sup>= 2<sup>k+1</sup>-1
- 1+x+x<sup>2</sup>+x<sup>3</sup>+...+x<sup>k</sup>=(1-x<sup>k+1</sup>)/(1-x)
#### Example: Binary Search
Look notes
#### Exampe: Mergesort
Look notes
## 19. Rooted Trees