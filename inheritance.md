#Inheritance

Inheritance is the ability for an object to inherit some of its properties and characteristics from another class.

Continuing with our shape examples, let's think about a Sphere.  We can think about a Sphere as being the child of a Circle.  It has some of the same properties (radius and circumference), but has some unique properties of its own (surface area and volume).

If we were to create a Sphere class on its own, it would look something like below (missing documentation):

```Java
//Example Inheritance-1
class Sphere {

    private float radius;
    
    public Sphere() {
        radius = 0;
    }
    
    public Sphere(float radius) {
        this.radius = radius;
    }
    
    public float circumference() {
        return Math.PI * radius * 2.0;
    }
    
    public float surfaceArea() {
        return 4.0 * Math.PI * radius * radius;
    }
    
    public float volume() {
        return 4.0 / 3.0* Math.PI * pow(radius, 3);
    }
}
```

Now we are going to look at how this information can be pared down, while taking advantage of the Circle class (found on the [Interfaces](./interfaces.md) page).  There will be explanations of new terms after the newly built Sphere class, and how it works.

```Java
//Example Inheritance-2
class Sphere extends Circle {

    public Sphere() {
        super();
    }
    
    public Sphere(float radius) {
        super(radius);
    }
    
    public float surfaceArea() {
        return 4.0 * Math.PI * radius * radius;
    }
    
    public float volume() {
        return 4.0 / 3.0* Math.PI * pow(radius, 3);
    }
}
```

As you can see, the Sphere class is much smaller now that we have taken advantage of what was already written for the Circle class.  Now the question is, what does the Sphere class actually have available to it, and how does this work?

Let's look at the new keywords that showed up in the inherited version of the Sphere
* ```extends```: This keyword states to Java that we are going to be grabbing all of the information from the Circle class as we are creating a sub-class of it.  The Circle class is then considered the **super** class.
* ```super()```: This keyword tells the compiler to go up to the super class and grab the constructor from there.
* ```super(radius)```: This is the same as the ```super()``` keyword but it grabs a different constructor based on the parameters given.

Now, where is the missing information?  Where is ```radius``` and ```circumference()```?  Am I still able to use them?  The answer is **yes!!**  Because this information is taken from the super class, the Sphere has full access to the items, **as long as they are not _private_**.

Let's take a look at how we have to make slight changes to the Circle class in order to accommodate inheritance.

```Java
//Example Inheritance-3
public class Circle implements Shape2D {

    protected double radius;
    
    //...rest of class stays the same
}
```

Note the use of the word ```protected```.  This is how to make a variable **private to itself and it's children**.  If you want a private variable that is only visible to a single class, and **not** to its children, then you would still use the word ```private```.