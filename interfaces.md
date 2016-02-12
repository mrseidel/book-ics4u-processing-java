#Interfaces

Interfaces are a way to ensure that classes **implement** certain methods.  Interfaces are useful in a team environment as they will help all programmers to follow a predefined agreed-upon standard.  This can illustrated best by using an example.

Below we have the ```Shape2D``` interface.  This interface defines methods that exist in all two-dimensional shapes (circles, rectangles, etc.).  We can then use this interface to force anyone who is creating a class for the same project to use these methods.

```java
//Example #Interface-1

public interface Shape2D {

    public double perimeter();
    public double area();

}
```

See the below ```Circle``` class to see how to implement an interface.  Some of the code is missing, as are all of the [Javadocs](./javadocs.md).  

```java
//Example #Interface-2

public class Circle implements Shape2D {

    public double radius;
    
    public Circle() {
        //set an initial value to the radius
    }
    
    //required to implement
    //since this method is in the interface
    public double perimeter() {
        return Math.PI * 2 * radius;
    }
    
    //required to implement
    //since this method is in the interface
    public double area() {
        return Math.PI * Math.pow(radius, 2);
    }
}
```

###Documentation for Interfaces
You would document an interface similarly to a [Class](./objects.md#Documentation-for-Classes)