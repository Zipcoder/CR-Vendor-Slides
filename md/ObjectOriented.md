#Introduction to Object-Oriented Programming
-
-

###Introduction to Object-Oriented Programming

* Yesterday you had a lecture on procedural programming, which has its place in the world. The issue the bigger the problems get, the harder it is to manage the code base.

-


###Introduction to Object-Oriented Programming

* Breaking the problem down into small logical objects that have a single responsibility is an easier way of managing larger problems, and scalability of solutions over time.

* It is also allows for greater testability of code.

-
-
# Classes
*  A class is a blueprint or a template for an object. Consider a blind person, the only way they can comprehend what something looks like , is via a verbal description. The computer knows the shape or composition of an object via its class definition.

-
-
# Encapsulation
* *Encapsulation* - encapsulation is simply combining data and behavior in one package and hiding the implementation details from the users of the objects.

-

##Objects are services

*  Object oriented programming objective is having objects providing services to other objects via messages or their public methods.

-

##Single Responsibility

* How an object completes the task that it is asked to do is no ones business but its own. The only thing that asking object cares about is the correct answer, how that answer is generated is irrelevant. Single Responsibility.

-

##Single Responsibility

* Think about a printer in an office. Do you care how the printer works, or do you only care about the documents you asked it to make?

* Its not your job to print the documents, so you don’t need to or care about how its done. Only that it gets done.

-
##Single Responsibility

* Thats the major premise behind encapsulation,  how an implements the tasked asked of it, is on a need to know basis.

-
-

##Defense

* Encapsulation is also important in defensive programming.  Object methods should only be able to change and interact with field objects of the same class they belong to. This way you can control the probability of unintended bugs in the future.

-

##Defense

* If a object needs to change the value of a field in another object, it should ask to do so via a method.

-

##Defense

* The value of this is you have the flexibility of changing how a class produces or implements an action, without directly effecting the other classes in the program. It also allows for you to write clear and comprehensive test for every intended action that object could be expected to do.

-
-

#Objects
As stated before all objects have 3 major parts

* **Identity** - how that object is distinguished from other objects of the same type
* **State** - the value of the member of objects this object contains.
* **Behavior** - what services or actions this object can perform.

-
##Proper names
* Objects should be named after nouns, and the actions they perform should be associated with verbs.

-
-

##Relationships between Classes

* **Dependence** (“Uses-a”) - Think about the objects a class needs to complete its job.

-

##Relationships between Classes

* Objects are containers.

* Think about this scenario you have a time keeping application that has the following objects:
	* Employee
	* TimeCard
	* TimeClock  

-

##Relationships between Classes

* For the TimeCard object to function properly it needs the TimeClock object to be created and in scope.

* Employee and TimeClock can exist and function without knowledge of TimeCard.

-
-

##Aggregation
* **Aggregation** (“has-a”) - the objects that are contained inside the class

-

###Aggregation

* Programs by nature should avoid complexity, keep things as simple as possible.

* The objects that you create, and the objects that you use should have a SINGLE-RESPONSIBLITY. They should have one task to do, and do it well.

* Complexity is achieved by creating container classes, which are comprised of simple objects working together to achieve one objective.

-
##Inheritance
* **Inheritance** (“is-a”) - this relationship is polymorphic in nature this relationship talks about what the object is extended from

* Remember that all objects in java are extended from **Object.class** except for primitives.

-
-

#Objects and Object Variables
* The **new**  keyword is the magic word that tells the JVM to add a new object to the heap.

-

###Objects and Object Variables

* Your job as a program is to avoid NULL values. OOP is all about Objects talking to Objects by sending messages to each other.

* **Null** means that there is a message being sent to an object that doesn’t exist, and that will lead to a error.

-

###Constructors
* **Constructors** - the do not have a TYPE they just have a name which is the same as the class name.

	* public CustomClass( )
	* A **constructor** has the same name as the class
	* A class can have more than one **constructor**.
	* A **constructor** has no return value
	* A **constructor** is always called with the **new** keyword

-

##Mutator and Accessor
* A **Mutator** is an action or method that changes the STATE of a object

* This can be a dangerous event, because if other objects have a dependency on that object, and things are changed unexpectedly or unintentionally this could lead to false results.

-

###Mutator and Accessor

* **Accessors** - are the privileges we assign to field objects , methods, and functions we define in our classes.
    * Public
    * Private
    * Protected
    * Default

-
-

##Implicit and Explicit Parameters

* Objects communicate with each other via the Interfaces which are the public methods defined in their classes.
    * **Implicit** - implied though not plainly expressed.
    * **Explicit** - stated clearly and in detail, leaving no room for confusion or doubt.

-

###Implicit and Explicit Parameters
```
Public Class SpiderMan extends Hero {

    // Constructor
    public SpiderMan( ){…}

    public shootWebAtTarget(Target target) { …. }

    public selectTargetAndShootWeb( ){
        Target target = new Target( );
        shootWebAtTarget(target);
    }
}
```

-
###Implicit and Explicit Parameters

* Lets look at the method ***shootWebAtTarget( )*** . This method has two parameters and Implicit parameter which is SpiderMan object.

* The SpiderMan object is not explicitly called , but is implied by the compiler when this program is executed.
* The target object is explicitly stated parameter which has to be stated each time the method is called.

-
-

##Benefits of encapsulation
* Life is full of enough problems, lets avoid them in our programs. We do that by making things as simple as possible. Simplicity is your friend!

-
###Benefits of encapsulation

* There is already a possibility of the logic we create to be flawed and results in errors or unintended results. Encapsulation can’t save us from the issues with our own personal logic, but it can help us avoid issues from unintended side effects of other objects.

-
##Single-Responsiblity
* **Single-Responsiblity**  when you are defining your objects think about the nature of that object. Lets think about a program that Controls a ATM. Here are the objects that exist in the program:

	* Bank
	* User
	* UserAccount
	* Dollar

-
###Single-Responsiblity

* The User object would like to withdraw 100 dollars from his/her account. This should only be allowed if the UserAccount associated with that User has more than or equal to 100 Dollars in it.

-

###Single-Responsiblity
* If it was up to the User , they would take the 100 dollars even if their account did not have the amount in it. It would be awesome if we lived in a world that everyone could get what they wanted when they wanted it. Yet we don't.

* The User should not be allowed to take what ever they wanted, they should only be able to ASK for it.

-

####So who should the User ask for the Money?

* Bank ???
* UserAccount ???
* Dollar ????

-

####So who should the User ask for the Money?

* It makes the most sense for the User to Ask the Bank for the money. Even though the UserAccount is Dependent on the User object, the User object is not Dependent on the UserAccount.

* So since its not dependent on it, it has no reason to know it even exist. In the real world the User would ask the Bank or the Automated Teller Machine at the bank for money.

-

####So who should the User ask for the Money?

*For the Bank to decide if they can provide the User with the money the User is asking for, it is Dependent on the UserAccount object. The Bank must ask the UserAccount object if there is enough money in it.

-

####So who should the User ask for the Money?

* A bank can have multiple users, which could become very complicated.
* Keep things simple by making a object to manage user information.
* The bank will ask the UserAccount for how much money is available.
* The UserAccount will have the amount of Dollars stored in it.

-

####So who should the User ask for the Money?

* If this field is public and any object can have access to it, whats to stop the User object for simply changing the value of Dollars in their account??

-

##Encapsulation

* **Encapsulation** comes in here! The field inside of UserAccount called dollars will be set to private. Only the UserAccount will have access to Mutate that field and change the amount. **SINGLE RESPONSIBILITY**.

-

###Encapsulation

*  When something goes wrong, and only one object has the ability to change or MUTATE the fields, finding out who is responsible and where the error exist becomes extremely fast.

-
-

#Private Methods
* Every object has an Interface the interface is the public methods and fields that it comprised of.
* Yet there are times when we need a method in our object, that accomplishes a helper task.
* Functions should have a **SINGLE RESPONSIBILITY** (have you heard that term enough?)

-

###Private Methods
```
public String canIBorrowMoney(Person person, Double amount ){
    // First Action
    if ( this.person.equals(person) ) {
       return “no";
    }

    // Second Action
    if ( person.like != true ) {
       return “no;
    }

     // Third Action
    if ( this.amount > amount ) {
       return “Sure things";
    } else { // Fourth Action
        return “no”;
    }

}
```

-

###Private Methods

* The problem with this function is we can’t test it, its doing too much!

	* So how do we fix it?
	* Take each action and make it a private function.
	* We make them private because they only exist to help us answer the one question our interface is making available, *canIBorrowMoney(~)*.

-
###Private Methods

```
private void doIKnowYou(Person person){
    if (!this.person.equals(person)){
        throw new Exception("I don’t know you");
    }
}

private void doILikeYou( Person person){
    if (!person.like){
        throw new Exception("I don’t like you");
    }
}

private void doIHaveEnough( ){
    if ( this.amount < amount ) {
      throw new Exception("I am broke you give me money!");
    }
}

public String canIBorrowMoney(Person person, Double amount ){
    doIKnowYou(person);
    doILikeYou(person);
    doIHaveEnough( );
    return “Sure thing playa”;
}
```
-
###Private Methods

* It doesn’t make sense for these methods to be called by any object accept for the one that owns it, so its private. We don’t want to allow outside objects change or mutate any values that could effect our decision and the way we want to respond to the question being asked to us.

-
-

##The Final Key Word
* **Immutable** - unchanging over time or unable to be changed.
* There are going to be times when we need to guarantee consistency and stability. There are going to be objects in our programs that have values which should NEVER be changed, because it could cause unintended results.

-

##First rule of programming
* **EVERYONE ELSE IS STUPID!!!!** If you don’t explicitly stop someone from doing something, they will eventually do it.

-

* Lets say we are creating a application that is dependent on the value of pi 3.14159. This program will guide a drone around a defined circle .

* Its important for this drone to fly with a high level of precision.

-

* All of the test we did to validate this precision is based off of the value of pi to the 5th power.

* All of the objects that help the drown navigate operate off of pi to the 5th power.

-

* If that value changes during the flight it could and would lead to a collision.

* So its important that once in flight that value NEVER changes.

* this is where the final keyword comes into play

-

##Final
* **Final** is how we define a value as constant or consistent from the start of the application to the end of the application. The value of this variable is set at the start of the application, and can not be mutated, by any object at all.

```
private final Float pi = 3.1489;
```
-
-

##Static Fields and Methods
* **static** - lacking in movement, action, or change.

-

###Static Fields and Methods

* The change part is a little misleading when in the context of java. The term Static in java is reference to the field or method in relation to the class its defined in. When something is defined as static that means :

	* It does not need an instance of an object to be called or used.
	* The static field or method is a singularity for that class. There is only one of it in existence and its shared by all objects of that type.

-
###Static Fields and Methods

```
public class Hobbit{
    private static boolean hasRing;

    public void loseRing (){
        Hobbit.hasRing = false;
    }

    public boolean doWeHaveTheRing(){ return Hobbit.hasRing;}
    public Hobbit( ){
        hasRing = true;
    }

}
```

-

* When a class has a static method or field the state is shared by every instance of that class.

```
public class Journey{

    public static void main(String[] args){
        Hobbit frodo = new Hobbit( );
        Hobbit samWise = new Hobbit( );
        // Will Print True
        System.out.println(“Do you have the ring?”
        + frodo.doWeHaveTheRing().toString());
        samWise.loseRing( );
        // Will print False
        System.out.println(“Do you have the ring?”
        + frodo.doWeHaveTheRing().toString());
    }
}
```

-
-

###Static Constants
* Static variables are very rare.
* Static values violate Object Oriented Principles and **SINGLE RESPONSIBILITY**

-

###Static Constants

* Static Constants are common
* If objects all share the same constant values, there is no need for each instant of that object to have its own value.

```
private final Float pi = 3.1489;
//every instant will have a copy of this value that can never change.

private static final Float pi = 3.1489;
// there will only be one copy shared between any instance created.
```
-
-
##Static Methods
* Static methods are also sometimes referred to and factory methods. They are methods that do not do any direct operations on a object.

```
public class Calculator {
    public int add (int x, int y) {
        return (x+y);
    }
}
```
-
###Static Methods

* Do we really need to create a instance of the object Calculator for the method add to do its job?
* No we do not, we can just call *Calculator.add(x,y)*;
* Static methods unlike instance methods are available as soon as the program is started, and are available until the program has completed.

-
-

##The main Method

* The main method is the entry point for your application. Remember you do not have any direct access to the heap where object exist in memory. So the only way to set the stage for our application to function is to use a static method.

-
##Main

* **main** is a reserved word that the JVM looks for to start our programs. Every java program has a main method.

```
static void main(String[] args) { ... }
```

-
###Main
* Some projects have multiple objects with main methods. The compiler will use the main method of the class file you choose when you decide to run.

-
-

##Method Parameters
* **call by value** - means that the method gets just the value that caller provides.
* **call by reference** - means that the method gets the location of the variable that the caller provides.
* So what does Java do???

-
###Method Parameters

* Java does manipulate objects by reference, and all object variables are references.

* However, Java doesn't pass method arguments by reference; it passes them by value.

-

###Method Parameters

* The reason for this is that the JVM is always optimizing the Heap. There is no guarantee that the memory block the object is in at one moment, will be the same in the next

-
-

##Object Construction  
* Objects are containers, the objects we use and create are composed of other objects.

* As stated before , we are in a eternal value to avoid null. Object oriented programming is objects talking to other objects, if we send a message to a object that doesn’t exist our programs will fail.

-
###Constructors
* This is where constructors come in. We use constructors to control the creation of our objects, and guarantee that the member objects or fields that our object is comprised of exist, are available, and are at the state we need for them to do their job.

-
####Constructors

* Java does manipulate objects by reference, and all object variables are references. However, Java doesn't pass method arguments by reference; it passes them by value.

-
##Overloading
**Overloading** is when we have methods that have the

* same name
* return the type
* but take different parameters.

-

###Overloading

* There are times when we need to construct our objects under different circumstances, we can use overloading to create multiple versions of methods.

-
###Overloading

```
public class Superman( ){
    private boolean dressedLikeClarkKent;

    // By default we start off in disguise
    public Superman( ) { dressedLikeClarkKent = true; }

    // Allows us to create this object and set the state.
    public Superman(boolean inDisguise){  dressedLikeClarkKent = inDisguise; }
}
```

-

### Default Constructors

* There is always a constructor, even if you do not provide one. When you do not explicitly write a constructor, the compiler will implicitly use the constructor from the class it inherited from. Remember all objects inherit from *Object.class*

```
public Superman() {}
```

-
-

##Default Field Initialization

* If you don’t set a field explicitly in a constructor, it is automatically set to a default value: numbers to 0, boolean values to false, and object references to null.
* Some people consider it poor programming practice to rely on the defaults. Certainly, it makes it harder for someone to understand your code if fields are being initialized invisibly.

-
-

##Naming conventions

* Life is already hard enough, lets not add complexity where there need not be any. Name things what they are. Sure we all love the idea of naming every variable after our favorite 80s cartoon characters, but eventually we will forget what String panthero5000 is in reference too.

-
-

##this keyword

* The this keyword is used to force a object to call itself. Even though its considered poor form to use it to reference instance variables unless its essential for clarity.

```
public void setValue(String value){
    /* Here it makes sense because we have two values
       of the same name to explicitly say this.
       If there is not a conflict in naming you should
       let the compiler implicitly associate it.*/
    this.value = value;
}
```
-

* There are times when you might want to call a constructor from inside of another constructor

```
public class Superman( ){
    private boolean dressedLikeClarkKent;

    //By default we start off in disguise
    public Superman( ) {
	      /* we are calling the constructor and
	      setting the default value we would
	      like set*/
         this.Superman(true);
    }

    // Allows us to create this object and set the state.
    public Superman(boolean inDisguise){  dressedLikeClarkKent = inDisguise; }
}
```
-
-

##Initialization Blocks

* Its important to set the values of fields before we reference them. We use constructors to do that for instance fields, but what about class level or static fields?

-
###Initialization Blocks

* This is where Initialization Blocks come in, they are used to run a set of instructions when the Class is constructed, before any objects are ever created. This

```
public Superman ( ){
    private static boolean manOfSteel;

    // When the program starts this code is run before any objects are created
   //  and the constructor is called
    {
        manOfSteel = true;
    }
}
```
-

The static block is ONLY run once when the class is loaded for the first time in the JVM

-
-

###Object Destruction and the finalize method

* Once you break the connection between the reference which lives in the stack, and the instance which lives in the heap. There is no way to reconnect with that object, even though it will not be removed until the next Garbage Collection Cycle, as far as you are concerned , its gone.

-

###Object Destruction and the finalize method

* There will be times when you want to make sure and validate that an object performs a action before it is removed from GC. For instance , if you are working with sensitive information or connection, and need to make sure that things are closed properly. Thats where the finalize method comes in.

```
public class Superman( ){
    protected void finalize ( ) throws Throwable {
        // Fly back to the fortress of solitude
    }
}
```

-
-

##Packages
* A **namespace** is a declarative region that provides a scope to the identifiers (the names of types, functions, variables, etc) inside it. Namespaces are used to organize code into logical groups and to prevent name collisions that can occur especially when your code base includes multiple libraries.

-

###Packages

* What happens when you have two classes called Superman? How do you tell the compiler which Superman you want used when creating new objects? You do that by calling the Package that the class Superman you desire lives in.

```
import dc.action.comics.Superman;
//or
import dc.man.of.steel.Superman;
```

-
-
