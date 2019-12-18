----
layout:     post                   
title:      Learning Java              
subtitle:   Gatech
date:       2019-12-16           
author:     BY PZ                   
header-img: img/post-bg-2015.jpg    
catalog: true                       
tags:                               
    - Java
---


> Written with [StackEdit](https://stackedit.io/).
> ## [Java](https://classroom.udacity.com/courses/ud283) Difference with C++

> Parameter and Arguments

**Parameter is in the definition of functions, Arguments is in the calls of functions.**

> Function Definition

**public void functionname(){..};**

> *Random Numbers*

`math.random();`  returns a random decimal value between 0 and 1, includes 0 but not 1;  `math.random()*10`  returns a range between 0 to 10;  `(int) randomNUmber`  Cast it to an int;

```
// Using the sides parameter, change this code so that it returns
// the correct range of roll values no matter the number of sides provided.
// ex. For an 8-sided dice the numbers returned should be integers between 1-8

public int rollDice(int sides){
        // random num between 0 and (almost) 1
        double randomNumber=Math.random();

        // change range to 0 to (almost) 6
        randomNumber=randomNumber*6;

        // shift range up one
        randomNumber=randomNumber+1;

        // cast to integer (ignore decimal part)
        // ex. 6.998 becomes 6
        int randomInt=(int)randomNumber;

        // return statement
        return randomInt;
        }

```

> Arrays

`double [] fracNumbers = {3.2,1.2,2.2}; int [][] grades`

> Compile

      & javac helloworld.java 
      & java helloworld

> CamelCase and camelCase

**Class use CamelCase like Book, Pokemon**

**Object use camelCase like lordOfTheRing**

In summary, **objects** are to **Classes** what **variables** are to **Data types**.


> The main method
```
public static void main(String [] args){
   // Start my program here
}

```

Let's break it down:

-   **`public`**: Means you can run this method from anywhere in your Java program (we will talk more about public and private methods later
-   **`static`**: ***Means it doesn't need an object to run,*** which is why the computer starts with this method before even creating any objects (we will also talk more about static methods later on)
-   **`void`**: Means the main method doesn't return anything, it just runs when the program starts, and once it's done the program terminates
-   **`main`**: Is the name of the method
-   **`String [] args`** : Is the input parameter (array of strings) which we will cover how to use it later in this lesson as well!

### Creating a constructor

Creating a constructor is very much like creating a method, except that:

1.  Constructors don't have any return types
2.  Constructors have the same name as the class itself

They can however take input parameters like a normal method, and you are allowed to create multiple constructors with different input parameters.

```
class Game{
   int score;
   // Default constructor
   Game(){
      score = 0;
   }
   // Constructor by starting score value
   Game(int startingScore){
      score = startingScore;
   }
}
```
##### The  `new`  keyword

To create an object of a certain class, you will need to use the  `new`  keyword followed by the constructor you want to use, for example:

```
Game darts = new Game(501);
```
#### Default constructor

A Default constructor is one that doesn't take any input parameters at all!

However, this privilege goes away once you create any constructor of your own! Which means ***if you create a parameterized constructor and want to also have a default constructor, you will have to create that default constructor yourself as well.***

### Self Reference

**this**  is a reference to the current object — the object whose method or constructor is being called. You can refer to any field of the current object from within a method or a constructor by using  `this`.

##### Using  `this`  with a Field

The most common reason for using the  `this`  keyword is because a field has the same name as a parameter in the method or construct
```
class Position {
   int row = 0;
   int column = 0;

    //constructor
   Position(int row, int column) {
      this.row = row;
      this.column = column;
   }
}
```

### Fields

-   Always try to declare all fields as  **private**
-   Create a constructor that accepts those private fields as inputs
-   Create a public method that  _sets_  each private field, this way you will  _know_  when you are changing a field. These methods are called  **setters**
-   Create a public method that  _returns_  each private field, so you can read the value without mistakingly changing it. These methods are called  **getters**

private members can only be accessed by members within the class,
**classname.area is not permitted**

 -   Set all your classes to  **public**
 -   Set all your fields to  **private**
 -   Set any of your methods to  **public**  that are considered actions
 -   Set any of your methods to  **private**  that are considered helper methods


> **Systems input and output**

```
System.out.println("Hello World!");
```
```
import java.util.Scanner;
Scanner scanner = new Scanner(System.in);
```
It will continue to read whatever the user is typing until they hit "enter" then the program continues to execute.

Once the scanner object has been created, you can use it to read a String, an integer or an entire line.

Calling the method  `nextLine()`  in that scanner object will return a String that contains everything the user has typed in before they hit "enter".

```
scanner.nextLine();
```
```
System.out.println("Enter your grade: ");
Scanner scanner = new Scanner(System.in);
int grade = scanner.nextInt();
if(grade > 90){
   System.out.println("Wow! you did well!");
}else{
   System.out.println("Not bad, but you can do better next time!");
}
```

### Read Files

```
File file = new File("expenses.txt");
Scanner fileScanner = new Scanner(file);
```
```
while (input.hasNextLine()) {
   String line = input.nextLine();
   // Use that line to do any calculations, processing, etc ..
}
```

Word Count


```
while (input.hasNextLine()) {
   String line = input.nextLine();
   wordCounts += line.split(" ").length;
}
Systems.out.println("The file contains: " + words + " words.");
```

#### Command line arguments
starts from 0 not including classname

```
public static void main(String [] args){
   if(args.length==0) {
      System.out.println("Please specify a location");
   }
   else {
      String location = args[0];
      int temperature = 60 + (int)(Math.random()*10);
      System.out.println("The weather in "+location+" is "+ temperature);
   }
}
```

#### Runtime Error
only happends occasionally, and while the program is running;
while (file.exists())
{
}

**Exceptions:**
A formal definition of a potential problem;

Inside the  `catch`  block you have the choice of either handling the situation quietly (like printing an error message or showing a warning popup)

```
try{
   openFile("somefile.txt");
} catch(FileNotFoundException exception) {
   // Handle the situation by letting the user know what happened
   System.out.println("Cannot find that file");
}

```

OR you can elude the situation and just re-throw the exception:

```
try{
   openFile("somefile.txt");
} catch(FileNotFoundException exception) {
   // Running away from the responsibility 
   throw exception;
}
```
### Polymorphism

**Parent item = new Child();**
funcition (Parent item)
the arguments can be type of any children
function(child1);

### Override

When a class extends another class, all public methods declared in that parent class are automatically included in the child class without you doing anything.

However, you are allowed to  **override**  any of those methods. Overriding basically means re-declaring them in the child class and then re-defining what they should do.

It is important to note that once you override a method, **you basically ignore everything that was in the parent class** and instead have your own custom implementation in the child class (literally overwriting it)!

```
class Rock extends Piece{
   boolean isValidMove(Position newPosition){
      if(newPosition.column == this.column || newPosition.row == this.row){
         return true;
      }
      else{
         return false;
      }
   }
}
```
## super

SUPER! Not only because you managed to solve that exercise, but "super" is actually another Java keyword that we will be using next!
In our case, we don't want to throw away the parent implementation. **We actually want to continue to use the original method, and ADD the extra checks for each child class individually.**

This is where we get to use the "super" keyword!

```
super.isValidMove(position);
```

Using the keyword super here means that we want to run the actual method in the super (or parent) class from inside the implementation in "this" class.

```
class Rock extends Piece{
   boolean isValidMove(Position newPosition){
      // First call the parent's method to check for the board bounds
      if(!super.isValidMove(position)){
         return false;
      }
      // If we passed the first test then check for the specific rock movement
      if(newPosition.column == this.column && newPosition.row == this.row){
         return true;
      }
      else{
         return false;
      }
   }
}
```

ou can also use  `super()`  **to call the parent's constructor.** This is usually done when implementing the child's constructor. Typically you would want to first run everything in the parent's constructor then add more code in the child's constructor:

```
class Rock extends Piece{
   // default constructor
   public Rock(){
      super(); // this will call the parent's constructor
      this.name = "rock";
   }
}
```

### Interface -- multiple inheritance

-   It is used to achieve total abstraction.
-   Since java does not support multiple inheritance in case of class, but by using interface it can achieve multiple inheritance .
-   It is also used to achieve loose coupling.
-   Interfaces are used to implement abstraction. So the question arises why use interfaces when we have abstract classes?
    
    The reason is, abstract classes may contain non-final variables, whereas variables in interface are final, public and static.

```
public class Book implements Comparable<Book>{
   public int compareTo(Book specifiedBook) {
      // First check if they have different page counts
      if(this.numberOfPages != specifiedBook.numberOfPages){
         // this will return a negative value if this < specified but will return a positive value if this > specified
         return this.numberOfPages - specifiedBook.numberOfPages;
      }
      // If page counts are identical then check if the titles are different
      if(!this.title.equals(specifiedBook.title){
         return this.title.compareTo(specifiedBook.title);
      }
      // If page titles are also identical then return the comparison of the authors
      return this.author.compareTo(specifiedBook.author);
    }
}
```

### Final

if you want to **protect your method from being overridden** in a child class you can prefix it with the keyword `final`.

A final method **can still be accessed by the child class (if the permissions allow so) but cannot be overridde**n, hence you can guarantee that any final method will behave exactly like the parent's implementation.

If you want a subclass to have access to a superclass method that needs to remain  `private`, then  `protected`  is the keyword you're looking for.

-   `Private`  allows only the class containing the member to access that member.
-   `Protected`  allows the member to be accessed within the class and all of it's subclasses.
-   `Public`  allows anyone to access the member.
- 
### Final fields

The  `final`  keyword can also be used to describe fields. However, unlike with methods, a final field has nothing to do with inheritance!

A final field is simply a **constant variable!** In other words, a variable that is only to be set once and is not allowed to change ever again!

## Static

The  **static keyword**  in Java is used for memory management mainly. We can apply java static keyword with variables, methods, blocks and nested class. The static keyword belongs to the class than an instance of the class.

The static can be:

1.  Variable (also known as a class variable)
2.  Method (also known as a class method)
3.  Block
4.  Nested class

The static variable **can be used to refer to the common property of all objects** (which is not unique for each object), for example, the company name of employees, college name of students, etc.

The static variable gets memory only once in the class area at the time of class loading.

```
public class Person {
    public static int instanceCount;
    public int localCount;
    public Person(){
        instanceCount++;
        localCount++;
    }
}
```
```
public static void main(String[] args) {
   Person person1 = new Person();
   Person person2 = new Person();
   Person person3 = new Person();
   Person person4 = new Person();
   // Print the values of both counters
   System.out.println("(" + person4.localCount + "," + Person.instanceCount + ")");
}
```
**The result would be (1,4)**

### Static Function

Just like static fields, static methods also **belong to the class** rather than the object.

It's ideally used to create a method that **doesn't need to access any fields** in the object, in other words, a method that is a standalone function.
A static method takes input arguments and returns a result based only on those input values and nothing else.

However, **a static method can still access static fields,** that's because static fields also belong to the class and are shared amongst all objects of that class.

```
public class Calculator {

    public static int add(int a, int b) {
        return a + b;
    }

    public static int subtract(int a, int b) {
        return a - b;
    }

}
```
# Lists

A  `List`  in Java is an interface that behaves very similarly to an array

-   It's an ordered collection (also known as a sequence).
-   The user of this interface has precise control over where each item is inserted in the list.
-   The user can access items by their integer index (position in the list).
-   The user can search for items in the list by looping over the items in it.

In fact, the most common class that implements the  `List`  interface uses an array internally and is even called  `ArrayList`

# ArrayList

An  `ArrayList`  is a class that implements the interface  `List`. It's simply a wrapper around an array, but provides really powerful methods that make dealing with the array much simpler.

**Note:**  An item in an ArrayList is known as an element

Let's have a look at some of the ArrayList's methods:

-   **add(E element):**  Appends the specified element to the end of this list.
-   **add(int index, E element):**  Appends the specified element to the specified index of this list.
-   **get(int index):**  Returns the element at the specified position in this list.
-   **contains(Object o):**  Returns true if this list contains the specified element.
-   **remove(int index):**  Removes the element at the specified position in this list.
-   **size():**  Returns the number of elements in the list.

For the full list of methods check out the documentation  [here](https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html)

To create and initialize an ArrayList:

```
ArrayList grades = new ArrayList();
```

Then you can add elements by calling the  `add()`  method:

```
grades.add(100);
grades.add(97);
grades.add(85);
```

To access the first item in the list:

```
grades.get(0)
```

This will return the value stored at index 0 (in this case: "100")

At any point, you can check the size of an array using the  `size()`  method:

```
System.out.println(grades.size().toString());
```

This will print the number of elements in the list (in this case: "3")

You can also remove items by index:

```
grades.remove(0);
```

Which will remove the first item in the list with index=0 ("100"), and then shift the other 2 items ("97" and "85") to have the indices (0 and 1) respectively

You can even clear the entire list by calling the  `clear()`  method:

```
grades.clear();
```

Some of these methods save us from writing extra code (loop and if checks) that we used to do with arrays. That's because the ArrayList already has such code implemented internally.

For example, when adding an element to the end of an array you will need to keep track of the index pointing to that last slot, and continue to increment that index every time you add a new item. But with ArrayLists, all you have to do is call the method add() with the item and it will take care of finding the correct index and inserting it in the right place.

**Also, notice that we don't need to specify the initial size of an ArrayList:**

```
ArrayList myArrayList = new ArrayList();
```

Unlike what we used to do with arrays:

```
int[] myArray = new int[100];
```

This is because the ArrayList class takes care of resizing the internal array every time it runs out of space, which is all done behind the scenes so you don’t have to worry about implementing any of that.

Everything can be defined as：
***Something item = new Something();***

## Stack

The Stack class includes these five methods:

```
Stack newsFeed = new Stack();
```
-   **push(E item):**  Adds an item onto the top of this stack
-   **pop():**  Removes the object at the top of this stack and returns that object
-   **peek():**  Returns the object at the top without removing it from the stack.
-   **empty():**  Checks if this stack is empty.
-   **search(Object o):**  Searches for an object in this stack and returns its position.

## Queue

***The Queue is only an Interface and not a Class by itself,*** however, it defines 2 important methods for all classes that do implement the Queue interface.

-   **add(E element):**  Inserts the specified element into this queue
-   **poll():**  Retrieves and removes the head of this queu

A special type of Queues is known as  `Deque`  which is a double-ended queue. Meaning that you can add or remove elements from either end of a  `Deque`  (Front or End).

Along with the 2 Queue methods, a Deque also offers these methods:

-   **addFirst(E element):**  Inserts the specified element at the front of this deque
-   **addLast(E element):**  Inserts the specified element at the end of this deque
-   **pollFirst():**  Retrieves and removes the first element of this deque
-   **pollLast():**  Retrieves and removes the last element of this deque

Java also provides a few classes that implement the Queue Interface, perhaps the most popular of all is the  `LinkedList`

Here's an example on how to create and use a LinkedList object:

```
Queue orders = new LinkedList();
orders.add("Order1");
orders.add("Order2");
orders.add("Order3");
System.out.print(orders.poll());
System.out.print(orders.poll());
System.out.print(orders.poll());
```

## Generics

In a nutshell, Generics enable classes to accept parameters when defining them, much like the more familiar parameters used in method declarations.

#### Generics in Collections

For example: ArrayLists use Generics to allow you to specify the data type of the elements you're intending to add into that ArrayList.

The way to do so is by defining that data type between  `<>`  when declaring the ArrayList variable:

```
ArrayList<String> listOfStrings = new ArrayList();
```

This is explicitly saying that you want to create an ArrayList of Strings, and hence the compiler will only allow Strings to be inserted into this ArrayList and will show you an error if you try to insert something else.

```
List<String> list = new ArrayList<String>();
list.add("hello");
String s = list.get(0);   // no cast
```
## Collections & Polymorphism

    ArrayList<Media> playlist = new ArrayList();
    Any children of media can be put into, like Video, or Audio
    playlist.add(someVideo)
    playlist.add(someAudio);
    Media media = playlist.get(0)
    media.play();

## ArrayList Methods

```
for(int i=0; i<cities.size(); i++){
   if(cities.get(i).equals("Sydney")){
      return true;
   }
}
```
```
cities.indexOf("Sydney");
```
This method returns the index of **the first occurrence** of the specified element in this list, **or -1** if this list does not contain the element.

## HashMaps

A HashMap is another type of collection that was introduced in Java to speed up the search process in an ArrayList.

In some sense, it's just another collection of items (Strings or Integers or any other Object), but the way it stores those items is unique.

HashMaps **allow you to store a key for every item you want to add**. This key has to be unique for the entire list, very much like the index of a typical array, except that this key can be any Object of any Type!

```
import java.util.HashMap;
```

This is how you declare a HashMap:

```
public class Library{
   HashMap<String, Book> allBooks;
}
```

To initialize this hash map, use the default constructor like so:

```
allBooks = new HashMap<String, Book>();
```

Then, to add items to the HashMap:

```
Book taleOfTwoCities = new Book();
allBooks.put("9781539687399", taleOfTwoCities);
```
