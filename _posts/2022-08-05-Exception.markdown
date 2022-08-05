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
```java
public class Demo1 {
    public static void main(String[] args) {
        int a = 40;
        int b = 0;
        int c = a / b;
        System.out.println(c);
    }
}
//result: Exception in thread "main" java.lang.ArithmeticException: / by zero
	//at ExceptionHandl.Exceptions1.main(Exceptions1.java:8)

```
`THE FIX` 
```java
public class Demo2 {
    public static void main(String[] args) {
        int a = 20;
        int b = 0;
        int c = 0;

        try{
            c = a / b;
        }
        catch (ArithmeticException ex){
            System.out.println("invalid number");
        }
        catch (Exception ex){
            System.out.println("exception occur");
        }
        System.out.println(c);



    }
}
```

#Errors
Errors are irrecoverable eg: OutOfMemoryError, VirtualMachineError


# try
any code or statement which we feel is risky or can cause an exception we will write inside the try block

# Catch
Whenever any exception happens, it will get the control and you can add any alternative or error handling
code in the catch block

# finally
no matter exception happen or not it will give you a guarantee to execute the code 
when you want to execute any piece code, even exception ot not we can write inside the finally block

# Examples 
    ```java
    public class Demo4 {
    public static void main(String[] args) {
        // Case 1: exception not occur
        try {
            int c = 10 / 5;
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
        } finally {
            System.out.println("Case 1: finally called");
        }

        // Case 2: exception occurs but not handled
//        try{
//            int c = 10 / 0;
//        }finally {
//            System.out.println("Case 2: finally called");
//        }

        // Case 3: exception occur and handled
        try {
            int c = 10 / 0;
        } catch (Exception exc) {
            System.out.println(exc.getMessage());
        } finally {
            System.out.println("Case 3: finally called");
        }
    }
}
    ```

example: open the connection and we want to make sure the connection get closed so we can write connection
closing code inside the finally block

```java
class Authentication {
    public void login(String email, String password) {
        if (email.equals("admin") && password.equals("123")) {
            System.out.println("login successfull");
        } else {
            System.out.println("login failed, try again");
        }
    }
}

public class Demo6 {
    public static void main(String[] args) {
        Authentication auth = new Authentication();
        auth.login("admin", "123");

        auth.login("admin", "123");
    }
}
```


# throw
it is a keyword that is used to throw an exception explicitly
we can use throw keyword to either throw checked or unchecked exception in java

# Demo - finally
Case 1: exception doesn't occur
Case 2: exception occurs and not handled
Case 3: exception occurs and handled

# Examples:

```java
class InSufficientFundException extends Exception{ //custom Exception
    public InSufficientFundException(){
        System.out.println("Insufficient amount requested");
    }

    public InSufficientFundException(String message){
        System.out.println(message);
    }
}

class BankAccount{
    private int _balance = 0;
    private int _accountNumber;

    public BankAccount(int _accountNumber){
        _accountNumber = _accountNumber;
    }

    public void deposit(int amount){
        _balance += amount;
        System.out.println("amount credited: "+ amount);
    }

    public void withdraw(int amount) throws InSufficientFundException {
        if(amount <= _balance){
            _balance -= amount;
            System.out.println("amount debited: "+ amount);
        }else{
            throw new InSufficientFundException();
        }
    }

    public int getBalance(){
        return _balance;
    }

    public int getAccountNumber(){
        return _accountNumber;
    }
}



public class Demo5 {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(123456);
        System.out.println(account.getBalance());
        account.deposit(5000);
        try {
            account.withdraw(2000);
        } catch (InSufficientFundException e) {
            System.out.println(e.getMessage());
        }
        account.deposit(1000);
        try {
            account.withdraw(10000);
        } catch (InSufficientFundException e) {
            System.out.println(e.getMessage());
        }
    }
}
```