# BEHAVIOUR PATTERN – ABSTRACT FACTORY

## QUESTION

Create a program that sends different types of notifications: **"email", "sms", and "push"**. Use the **Abstract Factory Pattern** to generate the appropriate notification sender and call its `notifyUser()` method.

## AIM

To develop a Java program using the **Abstract Factory Pattern** to create different types of notification senders such as Email, SMS, and Push, and call the appropriate `notifyUser()` method based on user input.

## ALGORITHM

1. Define a `Notification` interface with a method `notifyUser()`.
2. Implement three classes `EmailNotification`, `SMSNotification`, and `PushNotification`.
3. Override the `notifyUser()` method in each notification class.
4. Define a `NotificationFactory` interface with a method `createNotification()`.
5. Create `EmailFactory`, `SMSFactory`, and `PushFactory` classes.
6. Each factory implements the `NotificationFactory` interface.
7. Each factory creates and returns its corresponding notification object.
8. Read the notification type from the user.
9. If the input is `"email"`, create an `EmailFactory` object.
10. If the input is `"sms"`, create an `SMSFactory` object.
11. If the input is `"push"`, create a `PushFactory` object.
12. Use the selected factory to create the appropriate notification object.
13. Call the `notifyUser()` method.
14. Display an error message for an invalid notification type.
15. Continue reading input until `"exit"` is entered.
16. Close the scanner after exiting the loop.

## PROGRAM

```java
/*
Program to implement Abstract Factory Pattern using Java
Developed by: SANKAR S
RegisterNumber: 212224040291
*/
```

## SOURCE CODE

```java
import java.util.Scanner;

interface Notification {
    void notifyUser();
}

class EmailNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending Email Notification");
    }
}

class SMSNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending SMS Notification");
    }
}

class PushNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending Push Notification");
    }
}

interface NotificationFactory {
    Notification createNotification();
}

class EmailFactory implements NotificationFactory {
    public Notification createNotification() {
        return new EmailNotification();
    }
}

class SMSFactory implements NotificationFactory {
    public Notification createNotification() {
        return new SMSNotification();
    }
}

class PushFactory implements NotificationFactory {
    public Notification createNotification() {
        return new PushNotification();
    }
}

public class Main {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        while (true) {

            String input = sc.nextLine();

            if (input.equalsIgnoreCase("exit")) {
                break;
            }

            NotificationFactory factory = null;

            if (input.equalsIgnoreCase("email")) {
                factory = new EmailFactory();
            }
            else if (input.equalsIgnoreCase("sms")) {
                factory = new SMSFactory();
            }
            else if (input.equalsIgnoreCase("push")) {
                factory = new PushFactory();
            }
            else {
                System.out.println("Invalid notification type: " + input);
                continue;
            }

            Notification notification = factory.createNotification();
            notification.notifyUser();
        }

        sc.close();
    }
}
```


## OUTPUT:

![java45](https://github.com/ABINAYA-27-76/19AI307_ODD-25-26-/blob/c6316a5904f4a174dd995f6b7d7c47b65f677921/19AI307_JAVA(25-26)/Module-04/DAY-5/java45.png)

## RESULT:
Thus, the program demonstrating the Behavioral Pattern using Factory Method to generate different notification types was successfully implemented and executed.




