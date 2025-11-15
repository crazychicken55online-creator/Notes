- Static methods are invoked using the class name, e.g., `Dog.makeNoise();`.
- Instance methods are invoked using an instance name, e.g., `maya.makeNoise();`.
- Static methods cannot access "my" instance variables as there is no "me".
	- In the `Dog` example, `Dog.makeNoise()` wouldn't be able to access `weightInPounds`, however `maya` can because `weightInPounds` is an instance variable.
	![[static-vs-non-static.png]]
	
- Note that classes can have a mix of static and non-static methods.
# Why Static Methods?
- Some classes are never instantiated.
- E.g., the `Math` class
## Code Example
```Java title=math-snippet.java
// this is a lot nicer
x = Math.round(5.6);
// than this
Math m = new Math();
x = m.round(x);
```
