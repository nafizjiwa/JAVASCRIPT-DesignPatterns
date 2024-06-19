# JAVASCRIPT-DesignPatterns

### Design Patterns 
- Provide clean, scalable, and maintainable code
- Code solutions to common problems in software design.
- Patterns are blueprints to solving a particular design problem in your code using objects and classes.
- `3 Pattern Categories:` <br>

       1. Creational - how objects are created
       2. Structural - how objects relate to each other
       3. Behavioral patterns.- how objects communicate with each other

### Creational Design Patterns
 - Different ways to create objects.




## Anti Patterns
Some common anti-patterns include:

`God Object: This name is given to an object that does or knows too much. It is an all-knowing and all-encompassing object. While it might seem easier at first to have all of your properties and methods in one place, doing so can cause issues down the line when you go to update and maintain the code base or collaborate with other developers.`
`Big Ball of Mud/ Spaghetti Code: This is when your code lacks any perceivable architecture. It is hard to figure out where code for a specific functionality is located and what other code depends on it.`
`Yo-Yo Problem: If you find yourself moving from class definition to class definition to understand inheritance and what is happening among classes, you are experiencing the yo-yo problem, which is named due to your head yo-yoing across the screen.`
`Singleton: We’ll explore this below as a classic design pattern, but it’s worth noting that if used improperly, the Singleton pattern can take you into anti-pattern territory because of the restrictions it imposes.`
`Polluting the global namespace (i.e. defining too many variables at the global scope level).`
`Modifying or extending the Object class prototype. All objects in JavaScripts have a Prototype property that can be altered with methods and properties and all new objects inherit from this root Object by default. However, altering it is a huge no-no.`
