#UML

UML (Unified Modeling Language) is a general-purpose language to model and visualize designs for a system.  UML will be used in this class extensively before you start the coding process for the larger projects.

In this class, we will be learning the basics of UML class diagrams to plan out our programming projects.  For a more in-depth look into UML and the various other diagrams involved, you can check for other resources online.

##Purpose
In previous years, we focused on flowcharting which helped with the direction and flow of the project.  This year we will be looking at the UML class diagrams to help us plan our projects.  Class diagrams help to ensure encapsulation as well as give us a good overview of the work to complete before starting on our code.

##Structure
A class diagram is set up into 3 different sections.  The class name, the instance variables, and the methods that exist within that object.

| BankAccount |
|------|
|owner : String <br/> balance : float = 0 |
|deposit (amount : float) <br/> withdrawal (amount : float) |

The above is a basic example of a class diagram that could be used for a bank account.

The first section contains the class name `BankAccount`.  The next section contains the instance variables `owner` and `balance` as well as their datatypes and their default starting values (if necessary).  The last section contains the various methods a `BankAccount` can have: `deposit` and `withdrawal`.  It also contains each of the method's parameter lists, which happen to contain 1 item `amount` of type `float`.

