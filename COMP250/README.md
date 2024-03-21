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
