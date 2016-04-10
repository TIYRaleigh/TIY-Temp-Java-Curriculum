Properties are used to hold an object's _state_. State is the exact set of values that we are using to describe an object at any point in time. 

```java
// create a Person for Doug
Person doug = new Person();
```

As soon as I instantiate a new Person object it has state. The state is that the person has no name, is 0 years old, and is 0 feet tall. This is the default state. 

However, when I set an object's properties, I change its state. 

```java
doug.name = "Doug";
doug.age = 38;
doug.height = 6.0;
```

This code updates the Person's state. Now the person is named Doug, is 38, and 6 feet tall. An object's state stays constant until changed by code.
