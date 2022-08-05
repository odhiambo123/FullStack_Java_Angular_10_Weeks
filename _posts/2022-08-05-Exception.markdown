---
layout: post
title:  "Exception"
date:   2022-07-30
categories: Java 
---
![image](https://user-images.githubusercontent.com/8829018/183101852-c57d615a-1cc8-49b4-899d-23fac36a34d7.png)


An exception is an event that occurs during the execution of a program that caused the application or program
to terminate inappropriately

We can handle the exception using
1. try
2. catch
3. finally
4. throw
5. throws

# Type of exception
there are mainly two type of exceptions that are checked and unchecked
however there are some error which also consider as uncheck exceptions
1. check
2. unchecked
3. error

# check exception
as also known as compile time exception, which means these exception we must handle at compile time
ex: IOException, SQLException

# Unchecked exception
as know runtime exception, which means these exception are dangerous and if we have not handled it may cause
your application to terminate inappropriately
ex: NullPointerException, ArrayIndexOutOfBoundException unchecked exception are not checked at 
compile time, but they are checked at runtime

#Errors
Errors are irrecoverable eg: OutOfMemoryError, VirtualMachineError


# try
any code or statement which we feel is risky or can cause an exception we will write inside the try block

# Catch
whenever any exception happens, it will get the control and you can add any alternative or error handling
code in the catch block

# finally
no matter exception happen or not it will give you a guarantee to execute the code 
when you want to execute any piece code, even exception ot not we can write inside the finally block

example: open the connection and we want to make sure the connection get closed so we can write connection
closing code inside the finally block


# throw
it is a keyword that is used to throw an exception explicitly
we can use throw keyword to either throw checked or unchecked exception in java
