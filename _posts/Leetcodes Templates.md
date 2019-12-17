---
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

## Java Difference with C++

> Parameter and Arguments

**Parameter is in the definition of functions, Arguments is in the calls of functions.**

> Funciton Definition

**public void funcitonname(){..};**

> Random Numbers

`math.random();`
returns a random decimal value between 0 and 1, includes 0 but not 1;
`math.random()*10`
returns a range between 0 to 10;
`(int) randomNUmber`
Cast it to an int;


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

`double [] fracNumbers = {3.2,1.2,2.2};
int [][] grades`

> Compile

**javac helloworld.java
java helloworld**
