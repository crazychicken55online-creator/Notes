- Locality is the tendency for programs to access code in localized regions.
	- Programs tend to access and be around the same "memory region" like a small set of variables or instructions before moving on to another region.
#### There are two main types of locality: Temporal Locality and Spatial Locality.
- Temporal Locality (Time-based).
	- If a program accesses a piece of data or code once, it is likely to access it again soon. ```
```C title=Temporal_Locality_Example.c
#include <stdio.h>
int main() {
    int x = 10;
    int y;
    // First access to x
    y = x + 5;
    // Later, we reuse x again (same memory location)
    y = y + x;
    printf("y = %d\n", y);
    return 0;
}
```
- Spatial Locality (Space-based).
	- If a program accesses one memory location, it is likely to access nearby memory locations soon.
```C title=Spatial_Locality_Example.c
#include <stdio.h>
int main() {
    int array[5] = {1, 2, 3, 4, 5};
    int sum = 0;
    for (int i = 0; i < 5; i++) {
        sum += array[i]; // accesses array[0], array[1], array[2], etc.
		// (all in adjacent memory locations)
    }
    printf("sum = %d\n", sum);
    return 0;
}
```