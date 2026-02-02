# What is Time Complexity?
- Time complexity is a way to estimate the amount of time an algorithm takes to run.
- It is expressed in terms of the input size `n`.
- We look at how the number of primitive operations grows as the input size grows.
	- Which is to say that we are working in the [[1-23-2026 - Asymptotic Notation#Real Computers vs Ram Model|Random Access Model]].
>[!example] Time Complexity Trace
> ![[Time Complexity Trace Example 1.png]]
# Insertion Sort
- Build a sorted array from the left, the new element is inserted in the current sorted array.
- **Best-case Time Complexity:** $O(n)$ when the input array is already sorted. Only one comparison is made per element.
- **Worst-case Time Complexity:** $O(n^2)$ when the input array is in reverse order, each element needs to be compared with every other element in the sorted portion.


