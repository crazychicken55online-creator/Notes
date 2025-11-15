The typical class in Java has multiple parts.
- The instance variable.
- The constructor.
- A non-static, instance, method.
- Classes can have data (not just functions).
- Classes can be instantiated as objects.
- Objects can be stored in arrays.
# Instance Variable
Just a variable within in the class, if it has the `public` keyword then it can be accessed outside of the class, if it has the `private` keyword then it can only be used within the class.
- Can have as many of these as you'd like.
# Constructor
Very similar to a method, but not a method.
It determines how to instantiate the class.
# Non-static/Instance method
If the method is going to be used by the instance of the class (like `Dog dog = new Dog()`, here `dog` is an instance of the `Dog` class) then it should be non-static.
In general, if the method needs to use a class specific instance variable then the method has to be non-static.
# Code Example
```java title=Dog.java
public class Dog{
	// this is the instance variable (also is the data within in the class).
	public int weightInPounds; 
	// this is the constructor
	public Dog(int startingWeight){
		weightInPounds = startingWeight;
	}
	// this is the non-static method
	public void makeNoise(){
		if (weightInPounds < 10){
			System.out.println("yipyipyip!");
		}
		else if (weightInPounds < 30){
			System.out.println("bark.bark.");
		}
		else {
			System.out.println("woof!");
		}
	}
}
```
# Classes can be instantiated as objects
- We just created a `Dog` class, we can now use that `Dog` class and create multiple instances of `Dog`.
- Note hat we **cannot** add new instance variables to `Dog` from `DogLauncher` the instance of `Dog` must follow the blueprint that is in `Dog.java`.
- Note that the dot notation means that we want to use a method or variable belonging to that instance of an object, or more concisely, the member of an instance of an object.
## Code Example
```java title=DogLauncher.java
public class DogLauncher {
	public static void main(String[] args) {
		// declaration of a Dog variable (small Dog is currently empty)
		Dog smallDog;
		// instantiation of the Dog class as a Dog Object
		new Dog (20);
		// instantiation of the Dog class with size 5 and assigning it to smallDog (previously empty, now has value of Dog Object)
		smallDog = new Dog(5);
		// declaring hugeDog as a Dog variable, instantiating a new Dog with weight 150 and assigning it to hugeDog
		Dog hugeDog = new Dog(150);
		// changed weight to 50lbs.
		hugeDog.weightInPounds = 50;
		// illegal (name doesn't exist in class Dog).
		hugeDog.name = "frank";
		// invoking the hugeDog's makeNoise method
		hugeDog.makeNoise();
		// invoking the smallDog's makeNoise method (note that the output will be different from hugeDog)
		smallDog.makeNoise();
	}
}
```
# Arrays of Objects
To create an array of objects:
- First use the `new` keyword to create the array.
- Then use `new` again for each object that you want to put in the array.
## Code Example
```java array_of_objects_code_snippet.java
// creates an array of Dogs of size 2
Dog[] dogs = new Dog[2];
dogs[0] = new Dog(8);
dogs[1] = new Dog(20);
// should yip
dogs[0].makeNoise();
```
- Note that this code won't actually compile and run because it doesn't have a main and stuff.