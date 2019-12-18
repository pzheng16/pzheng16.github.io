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



