# JAVASCRIPT-DesignPatterns

### Design Patterns 
- Provide clean, scalable, and maintainable code
- Code solutions to common problems in software design.
- Patterns are blueprints to solving a particular design problem in your code using objects and classes.
- `3 Pattern Categories:` <br>

       1. CREATIONAL PATTERNS - how objects are created
       2. STRUCTURAL PATTERNS - how objects interac with each other
       3. BEHAVIORAL PATTERNS - how objects communicate with each other

### CREATIONAL DESIGN PATTERNS
 - Use these Pattern to control how objects are created
   - Factory
   - Singleton
   - Abstract Factory
   - Constructor
   - Prototype

#### FACTORY
- We don't use the `new` keyword to instantiate an object but a function or method.
- The Functions use a predefined template to return an object with properties and methods. The arguments construct the object.
###### - EG.
         function createBook(title, author, read = false) {
           return {
                      title: title,
                      author: author,
                      read: read,
           getDescription() {
                 console.log(`${this.title} was written by ${this.author}. I ${this.read ? "have" : "have not"} read it.`);
                   },
           readBook() {
               this.read = true;
                },
             }
          }
          
          const beloved = createBook("Beloved", "Toni Morrison");
          console.log(beloved);              /*
                                              {
                                              title: 'Beloved',
                                              author: 'Toni Morrison',
                                              read: false,
                                              getDescription: [Function: getDescription],
                                              readBook: [Function: readBook]
                                              }
                                             */
              
           // call the `.readBook()` method
              beloved.readBook();          // read is updated to true
              
           // modifies the property directly
              beloved.title = "I can change the property." 

#### SINGLETON
- An object that can only be instantiated once<br>
- 1st a method checks if an instance exists, and if not
- 2nd return a new object.
  
                class Singleton {
                   constructor() {
                       if (!Singleton.instance) {
                           Singleton.instance = this;
                       }
                       return Singleton.instance;
                     }
                   static getInstance() {
                        return this.instance;
                    }
                }
                     
                     const instance = new Singleton();
                     console.log(Singleton.getInstance());    // logs "Singleton {}"


### STRUCTURAL DESIGN PATTERNS
- Common Patterns:
       - Facade
       - Proxy
       - Flyweight
       - Adapter
       - Decorator
       - Composite
       - Bridge
  
#### PROXY
- Protects access to an object by acting as a placeholder
- It intercepts and redefines the operations of the target object.
- Useful in Network requests so it avoids redundant requests
- Proxy objects have built-in handler function objects, which are called traps.
- Traps modify access to the target object.
  
              const target = {
                  city1: "Marseille, France",
                  city2: "Mombasa, Kenya"
              };
              
              const handler = {
                  get: function (target, prop, receiver) {
                      if (prop === "city1") {
                          return "Montreal, Canada";
                      }
                      return Reflect.get(...arguments);
                  },
              };

              const proxy = new Proxy(target, handler);
              
              console.log(proxy.city1); // Montreal, Canada
              console.log(proxy.city2); // Mombasa, Kenya

#### FACADE
- Used in libraries to simplify interactions with APIs.
- It directs clients requests and hides low level code from user
  
              class VideoConverter {   //client only interacts with VideoConverter class
                  constructor() {}
                      convertNewVideo(...args) {
                      // This method can interact with `Audio`, `Video`, `Codec`, and `Compression`
                  }
              }

              class Audio {
                  constructor() {}
                  // complex subsystem code
              }
              
              class Video {
                  constructor() {}
                  // complex subsystem code
              }
              
              class Codec {
                  constructor() {}
                  // complex subsystem code
              }

### BEHAVIORAL DESIGN PATTERNS
- Decides how sender and receiver objects communicate with each other.
- Common Patterns:
       - Iterator
       - Mediator
       - Observer
       - Visitor

#### Observer Pattern
- A change in one object can affect the changes in many other objects
- Eg. Changing my Bday on one account but the change is made/pushed to many other accounts.

              class Account {
                  constructor() {
                      this.followers = [];
                      this.feed = [];
                  }
                  addToFollowers(follower) {
                      this.followers.push(follower);
                  }
                  removeFromFollowers(follower) {
                      this.followers.splice(this.followers.indexOf(follower), 1);
                  }
                  publish(post) {
                      this.followers.forEach(follower => follower.update(post));
                  }
                  update(post) {
                    this.feed.push(post);
                  }
              }

       let a = new Account();
       let b = new Account();
       let c = new Account();
       
       a.addToFollowers(b);
       a.addToFollowers(c);
       
       a.publish("Hello, world");

              console.log(a);   
              /* Output shows b and c objects listed in a's followers array:
              [
                Account { followers: [], feed: [ 'Hello, world' ] },
                Account { followers: [], feed: [ 'Hello, world' ] }
              ] 
              */
              
              console.log(b); 
              // Account { followers: [], feed: [ 'Hello, world' ] }

## Anti Patterns
Some common anti-patterns include:

`God Object: This name is given to an object that does or knows too much. It is an all-knowing and all-encompassing object. While it might seem easier at first to have all of your properties and methods in one place, doing so can cause issues down the line when you go to update and maintain the code base or collaborate with other developers.` <br>
`Big Ball of Mud/ Spaghetti Code: This is when your code lacks any perceivable architecture. It is hard to figure out where code for a specific functionality is located and what other code depends on it.` <br>
`Yo-Yo Problem: If you find yourself moving from class definition to class definition to understand inheritance and what is happening among classes, you are experiencing the yo-yo problem, which is named due to your head yo-yoing across the screen.` <br>
`Singleton: We’ll explore this below as a classic design pattern, but it’s worth noting that if used improperly, the Singleton pattern can take you into anti-pattern territory because of the restrictions it imposes.` <br>
`Polluting the global namespace (i.e. defining too many variables at the global scope level).` <br>
`Modifying or extending the Object class prototype. All objects in JavaScripts have a Prototype property that can be altered with methods and properties and all new objects inherit from this root Object by default. However, altering it is a huge no-no.` <br>
