# DESIGN PATTERN — ABSTRACT FACTORY

## QUESTION

Create a program that sends different types of notifications such as **Email, SMS, and Push** using the **Abstract Factory Pattern**. Use the appropriate factory to create the required notification sender and call its `notifyUser()` method.

## AIM

To develop a Java program using the **Abstract Factory Pattern** to create different types of notification senders such as Email, SMS, and Push and send notifications based on the user input.

## ALGORITHM

1. Define a `Notification` interface with a method `notifyUser()`.
2. Implement `EmailNotification`, `SMSNotification`, and `PushNotification` classes.
3. Each class overrides the `notifyUser()` method with its specific notification message.
4. Define an abstract `NotificationFactory` interface with a method to create notification objects.
5. Create separate factory classes for Email, SMS, and Push notifications.
6. Each factory creates the corresponding notification object.
7. Read the notification type from the user.
8. Select the appropriate factory based on the input.
9. Use the selected factory to create the notification object.
10. Call the `notifyUser()` method.
11. Display an error message if the notification type is invalid.
12. Continue reading input until `exit` is entered.
13. Close the scanner after exiting the loop.

## PROGRAM

```text
/*
Program to implement Abstract Factory Pattern using Java
Developed by: SANKAR S
RegisterNumber: 212224040291
*/
```


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

<img width="943" height="423" alt="image" src="https://github.com/user-attachments/assets/4bf885fa-c016-47dd-bfe0-edf37e8a39e5" />


## RESULT:

Therefore the program successfully creates and sends the appropriate notification type using the Factory Pattern.
