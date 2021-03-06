#Objects & Classes

###Processing Example

Think of an object that you can hold.  Let's say, a tennis ball.  At the manufacturer they use a template to create a tennis ball.  Let's keep this in mind as we go through what Objects and Classes are in Processing and then in Java.

Previous you might have seen code that looks like this in Processing.

```processing
//Example #Objects-1

float x, y; //x and y coordinates for the moving circle
float xspeed, yspeed; //speed and direction of motion for the circle

void setup() {
    size(500, 500);
    x = width/2;
    y = height/2;
    xspeed = random(-5, 5);
    yspeed = random(-5, 5);
}

void draw() {
    display();
    update();
    checkEdges();
}

void display() {
    ellipse(x, y, 50, 50);
}

void update() {
    x = x + xspeed;
    y = y + yspeed;
}

void checkEdges() {
    if (x > width || x < 0) {
        xspeed = xspeed * -1;
    }
    if (y > height || y < 0) {    
        yspeed = yspeed * -1;
    }
}
```

To recreate this code using objects and classes, you would do the following:

```processing
//Example #Objects-2

MovingCircle mc;

void setup() {
    size(500, 500);
    mc = new MovingCircle();
}

void draw() {
    mc.display();
    mc.update();
    mc.checkEdges();
}

class MovingCircle {
    float x, y; //coordinates of this Moving Circle
    float xspeed, yspeed; //movement direction of this Moving Circle
    
    MovingCircle() { //Constructor for a Moving Circle
        x = width/2;
        y = height/2;
        xspeed = random(-5, 5);
        yspeed = random(-5, 5);
    }
    
    void display() {
        ellipse(x, y, 50, 50);
    }

    void update() {
        x = x + xspeed;
        y = y + yspeed;
    }

    void checkEdges() {
        if (x > width || x < 0) {
            xspeed = xspeed * -1;
        }
        if (y > height || y < 0) {    
            yspeed = yspeed * -1;
        }
    }
} //end of class
```

Now think of this ```class MovingCircle``` as a template.  In this example we have created one single ```MovingCircle```; however, with the way this has been set up, it is simple to create a second or more ```MovingCircle```.  See the example below for creating 2 different ```MovingCircle``` objects.

```processing
//Example #Objects-3

MovingCircle mc, mc2;

void setup() {
    size(500, 500);
    mc = new MovingCircle();
    mc2 = new MovingCircle();
}

void draw() {
    mc.display();
    mc.update();
    mc.checkEdges();
    
    mc2.display();
    mc2.update();
    mc2.checkEdges();
}

class MovingCircle {
    float x, y; //coordinates of this Moving Circle
    float xspeed, yspeed; //movement direction of this Moving Circle
    
    MovingCircle() { //Constructor for a Moving Circle
        x = width/2;
        y = height/2;
        xspeed = random(-5, 5);
        yspeed = random(-5, 5);
    }
    
    void display() {
        ellipse(x, y, 50, 50);
    }

    void update() {
        x = x + xspeed;
        y = y + yspeed;
    }

    void checkEdges() {
        if (x > width || x < 0) {
            xspeed = xspeed * -1;
        }
        if (y > height || y < 0) {    
            yspeed = yspeed * -1;
        }
    }
} //end of class
```
As you can see, we didn't have to change anything in the ```MovingCircle``` class to accommodate a second moving circle.  The only changes was to create a second **object** based on the ```MovingCircle``` **class**.

Now, let's break down how a class is setup in comparison to what it was as a functional program:
* All classes are named with a capital letter to start.  This is to distinguish it from a variable (which we always start with a small letter).
* We moved all of the variable outside of the ```draw()``` and ```setup()``` into the class, but not inside any method.  These are now called **instance variables**.
* We moved everything that was inside ```setup()``` that had to do with the circle into ```MovingCircle()```. This special method is called the **constructor**.  A constructor is called whenever an object is first created, like in the line ```mc = new MovingCircle();```.  A constructor tells the program what to do whenever an object is _first created_.
* We moved all of the functions from outside the ```draw()``` and ```setup()``` functions inside the ```MovingCircle``` class.  These are now called **methods** of this particular class (or things this class can do).
 
When you are first creating classes from scratch, you will want to think of the different ways that you want to use the class.  This will help with the characteristics (typically instance variables) and abilities (typically methods) of the class you are making.

###Converting to Java
Converting the ```MovingCircle``` class from above into Java is rather simple.  Let's just jump in and see what this same class would look like in Java (including Javadocs).

```java
//Example #Objects-4

/**
 * This class is used for a Moving Circle
 *
 * @author Mr. Seidel
 * @since JDK 8
 * @since October 5, 2015
 * @version 1.0
 */
public class MovingCircle {

    private float x, y;           //coordinates of this Moving Circle
    private float xspeed, yspeed; //movement direction of this Moving Circle
    
    /** 
     * This is the default constructor
     * It sets all instance variable to zero
     *
     */
    public MovingCircle() { 
        x = 0;
        y = 0;
        xspeed = 0;
        yspeed = 0;
    }
    
    /** 
     * Takes in the x and y coordinates of the MovingCircle
     *
     * @param x the initial value of the x coordinate
     * @param y the initial value of the y coordinate
     */
    public MovingCircle(float x, float y) { 
        this.x = x;
        this.y = y;
        xspeed = 0;
        yspeed = 0;
    }
    
    /** 
     * Takes in the x and y coordinates of the MovingCircle, as well as the initial speeds
     *
     * @param x the initial value of the x coordinate
     * @param y the initial value of the y coordinate
     * @param xspeed the initial value of the x-speed
     * @param yspeed the initial value of the y-speed
     */
    public MovingCircle(float x, float y, float xspeed, float yspeed) { 
        this.x = x;
        this.y = y;
        this.xspeed = xspeed;
        this.yspeed = yspeed;
    }
    
    
    /**
     * This method displays the MovingCircle to the screen
     * 
     */
    public void display() {
        //insert a way to draw the circle here
    }

    /**
     * This method updates the position of the MovingCircle
     *
     */
    public void update() {
        x = x + xspeed;
        y = y + yspeed;
    }

    /**
     * Checks to see if the MovingCircle has his the boundaries
     *
     */
    public void checkEdges() {
        if (/* insert information about the screen here for left and right sides */) {
            xspeed = xspeed * -1;
        }
        if (/* insert information about the screen here for top and bottom sides */) {    
            yspeed = yspeed * -1;
        }
    }
    
    /**
     * Gets the value of the private instance variable x
     *
     * @return the value of x as a float
     */
    public float getX() {
        return x;
    }
    
    /**
     * Gets the value of the private instance variable y
     *
     * @return the value of y as a float
     */
    public float getY() {
        return y;
    }
    
    /**
     * Sets the value of the private instance variable x
     *
     * @param x  the value to set the instance variable x to
     */
    public void setX(float x) {
        this.x = x;
    }
    
    /**
     * Sets the value of the private instance variable y
     *
     * @param y  the value to set the instance variable x to
     */
    public void setY(float y) {
        this.y = y;
    }
} 
```

```NOTES: Make mention of public static void main (String [] args) {} ```

There are new ideas and concepts introduced in the Java version, and we'll go over those one at a time:
* **public vs. private**: Typically anything that is information that you do not want automatically accessible to other parts of your program, you will set these items to **private**.  Anything you want accessible to anyone you would set these items to **public**.
* **Multiple Constructors**: When you want to have different ways of building an object, you can have multiple constructors as long as they have different parameter lists.  In this example, there is a default one with no parameters, one taking in the set of coordinates, and the final one that takes in the set of coordinates and the speeds as well.
* **this**: Refers to the instance variable or the instance method; whereas a variable or method that is not referred to with ```this``` written in front of it can refer to any other variable or method.  This allows us to use the same name for variables in parameter lists as variables inside the classes (```this.x = x;``` as an example).
* **getter and setter methods**: These types of methods allow you to access particular private variables that you want to give access to in a safe way.  One reason this is safer than just setting the variables to public is when you are working with conditional statements.  For example, if you were to type ```if (mc.x = 5) {``` by accident, this would set the variable x to the value of 5; whereas, if you were to use ```if (mc.getX() = 5) {``` this would flag an error stating this is not possible.

###Documentation for Classes
As you will notice above in Example #Objects-4, there are some new options regarding [Javadocs](./javadocs.md) which we'll go over below:
* ```@since``` is used to describe what timeframe, and what Java version was used in creating the class
* ```@author``` describes who the author was for this class
* ```@version``` gives the class a version number

###Exercises
1. Take a Processing program that does not use objects and classes, and convert it into one that does.
2. Take one of your Processing programs and convert it into a Java program.