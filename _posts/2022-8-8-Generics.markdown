---
layout: post
title:  "Generics"
date:   2022-08-08
categories: Java
---

# Generics class
- A class that can refer to any data type is known as generic class
- We can use T type parameters to create the generic class of a specific type

### Syntax
----------

class MyClass<T>{
  T obj;

  void add(T obj){
   this.obj = obj;
  }

  T get(){
     return obj;
  }
}

### Examples
```java
class MyClass<T> {
    T obj;

    void add(T obj) {
        this.obj = obj;
    }

    T get() {
        return obj;
    }
}

public class Demo3 {
    public static void main(String[] args) {
        MyClass<String> myClass = new MyClass<>();
        myClass.obj = "Hello";
        myClass.add("World");
        String str = myClass.get();
        System.out.println(str);
    }
}
```

This T can be replaced by any data type like Integer, string, employee

```java
class Test{
    <E> void printArray(E[] elements){
        for(E element : elements){
            System.out.println(element);
        }
    }
}

public class Demo4 {
    public static void main(String[] args) {
        Test test = new Test();

        Integer[] intArray = { 10, 20, 30, 40 };
        Character[] charArray = { 'A', 'B', 'C', 'D' };

        test.printArray(intArray);
        System.out.println("________________");
        test.printArray(charArray);
    }
}
```

### Customer Example

```java
class Customer{
    String name;

    public <T> Customer(T name){
        this.name = name.toString();
    }
}

public class Demo5 {
    public static void main(String[] args) {
        Customer customer1 = new Customer("mark");
        Customer customer2 = new Customer(123);

        System.out.println(customer1.name);
        System.out.println(customer2.name);
    }
}
```

# Types of parameters
T - type
E - element
K - Key
N - number
V - value


# Generic methods
like generic class we can also create generic method that can accept any type of parameter 
here the scope of the argument is limited to the method where it is declared

it allow to create static as  well non static methods


# wild card generics
? - question mark symbol represent the wild card element
it means any type
we can write <? extends Shape> it means any child class of shpe class can be use

```java
import java.util.ArrayList;
import java.util.List;

abstract class Shape{
    abstract void draw();
}

class Rectangle extends Shape{

    @Override
    void draw() {
        System.out.println("drawing rectangle...");
    }
}

class Circle extends  Shape{

    @Override
    void draw() {
        System.out.println("drawing circle...");
    }
}

class Cone{
    void draw(){
        System.out.println("drawing cone..");
    }
}

class Output{
    // creating a method that accept only child class of shape class
    public void drawShape(List<? extends Shape> list){
        for(Shape shape: list){
            shape.draw();   // calling a method of shape class by child class instance
        }
    }
}

public class Demo6 {
    public static void main(String[] args) {
        List<Rectangle> rectangles = new ArrayList<>();
        List<Circle> circles = new ArrayList<>();
        List<Cone> cones = new ArrayList<>();

        Output output = new Output();
        output.drawShape(rectangles);
        output.drawShape(circles);
        //output.drawShape(cones);
    }
}
```