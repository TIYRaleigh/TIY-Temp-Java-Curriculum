So far we've discussed how classes define the properties and methods of object. These properties and methods are unique per _instance_ of an object. The name (Doug) of one `Person` instance is different from the name (Liz) of a different `Person` instance.

Java also allows you to create properties and methods that are shared between all instances of an object, or even without any instances at all. These are called _static_ properties or methods. 

Don't think too hard about the word "static". The word static implies something that is unchanging, but static properties can be changed and static methods do things. In this case the word static is related to the _lifetime_ of an object. 

An object only exists in memory as long as you're using it. After that, it's cleaned up by Java and all of it's properties - what makes up its state - disappear. 

![static methods and properties.png](https://tiy-learn-content.s3.amazonaws.com/cd5c0e00-static%20methods%20and%20properties.png)

By contrast, static properties exist across the lifetime of all instances and uses of a class. They are not tied to any one instance. The same is true for static methods.

One way to think of static properties is like parks or green-space in a neighborhood. Everyone has their own home; I can't just walk into your house and you can't park in my driveway without asking. But, we can both have a picnic in the common areas. 

![green space.jpg](https://tiy-learn-content.s3.amazonaws.com/e3d17e27-green%20space.jpg)
