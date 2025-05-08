# Transform and Conquer
> This is a problem solving technique in which we modify or simplify the instance of the problem, so that it can be solved using the existing problem solving techniques or algorithms.

We have three instances or implementations of transform and conquer.They are:
1. Instance Simplification
2. Representation change
3. Problem Reduction

## Instance Simplification
> This problem solving technique involves simplifying the input instance of the problem without simplifying the problem itself. And the solution technique will be applied to the instance wich can further be extended to the main problem.

Example for Instance Simplification is Presorting.

### Presorting

Presorting is an old technique in computer science, any problems related to arrays can be solved easily if the array is sorted.

eg: Uniqueness of an Array

Observe the following algorithm

```
for i=0 to n-2
  if A[i]==A[i-1]
    return false
  return true
```

- The brute force approach for this problem is to loop through the array until we find 2 similar elements or we reach the end of the array, the worst case time complexity for this is O(n^2).
- In Presorting, we first sort the array and then if any element has more than one occurences in the array, it will be right next to the element, this loop will be executed (n-1) times.
- For sorting the time-complexity is O(nlogn) and for scanning the time complexity is O(n-1).
- and the overall time complexity will be O(nlogn)+O(n-1)=O(nlogn).


## Representation Change

> Transforming to a different representation of the same instance.

Example for Representation Change is Guass Elimination.

### Guass Elimination

