#Inheritance

Inheritance is the ability for an object to inherit some of its properties and characteristics from another class.

Continuing with our shape examples, let's think about a Sphere.  We can think about a Sphere as being the child of a Circle.  It has some of the same properties (radius and circumference), but has some unique properties of its own (surface area and volume).

If we were to create a Sphere class on its own, it would look something like below (missing documentation):

```Java
class Sphere {

    private float radius;
    
    Sphere() {
        radius = 0;
    }
    
    Sphere(float radius) {
        this.radius = radius;
    }
    
    float circumference() {
        return Math.PI * radius * 2.0;
    }
    
    float surfaceArea() {
        return 4.0 * Math.PI * radius * radius;
    }
    
    float volume() {
        return 4.0 / 3.0* Math.PI * pow(radius, 3);
    }
}
```

