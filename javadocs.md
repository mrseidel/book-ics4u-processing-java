# Documentation in Java/Processing (Javadocs)

In the previous course, you created documentation by using in-line documentation.  In this course, you will learn how to create Javadocs for your functions and objects.

In the [Functions](./functions_beyond_void.md) chapter, there was an example as written below:

```processing
//Example #Docs-1

float addition(float firstNumber, float secondNumber) {
    return firstNumber + secondNumber;
}
```

Using this example as a place to springboard our introduction to Javadocs, we will re-write it with proper documentation:

```processing
//Example #Docs-1

/** 
 *  This function takes in two float values and returns the sum of those two values
 *
 *  @param first   This is the first float of the sum
 *  @param second  This is the second float of the sum
 * 
 *  @return        The return value is the sum of first and second as a float value
 */
float addition(float firstNumber, float secondNumber) {
    return firstNumber + secondNumber;
}
```

Creating documentation makes it easier to understand the purpose behind your functions, methods, and objects.  Let's go through the format of the Javadocs above.
* The first section is the description of what the function is for.
* The `@param` is used to describe what each parameter is.
* The `@return` portion describes what is going to be returned from the function

Typically, these above is all we will be using in this course for any functions or methods.  There are some other documentation items that we use for classes instead.  There are examples of this documentation in the [Objects](./objects.md) and [Inheritance](./inheritance.md) sections of the text.

###Exercises
1. Go back to the exercise(s) you completed in the [Functions](./functions_beyond_void.md) section.