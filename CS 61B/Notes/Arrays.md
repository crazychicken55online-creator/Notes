See also: [[Lists]].
Arrays are a restricted version of the [[Lists|list abstract data type]].
- Arrays are more performant when compared to lists:
	- Reading and writing from them is faster.
	- Uses less memory.
It has the following properties (in Java):P
- Size must be declared at the time the array is created.
- Size cannot change.
- All items must be of the same type.
- No methods.
- Uses square bracket notation in order to access array entries, e.g., `x[0]`.
# Code Example
```java title=ArrayDemo.java
public class ArrayDemo {
	public static void main(String[] args) {
		// creates an array x of size 5
		String[] x = new String[5];
		// first index of x = "a"
		x[0] = "a";
		// second index of x = "b"
		x[1] = "b";
		System.out.println(x[0]);
	}
}
```
