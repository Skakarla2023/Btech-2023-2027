# 1 TwoSum

> Given an array of integers nums and an integer target,return indices of the 2 numbers such that they add up to target.


- 3 approaches to solve this problem:
1. Brute force
2. Better approach
3. Optimised

### Brute Force

In this we calculate all pairs and find the pair whose sum equals the target.

```
#include<stdio.h>
int main()
{
	int arr[]={2,5,11,7,14};
	int n=sizeof(arr)/sizeof(arr[0]);
	int tar=9;
	int i,j,f,s,sum;
	for(i=0;i<n-1;i++)
	{
		f=arr[i];
		for(j=i+1;j<n-1;j++)
		{
			s=arr[j];
			sum=f+s;
			if(sum==tar)
			{
				printf("%d,%d",i,j);
			}	
		}
	}
}
```

Output:
```
0,3
```

```
Time Complexity-O(n^2)
``` 


### Better Approach

> In this we'll first sort the array and then calculate the sum of first and last element,if sum equals the target,then return the indices,if sum>tar end--,if sum<tar st++.

```
#include<stdio.h>
int main()
{
	int arr[]={2,5,11,7,14};
	int n=sizeof(arr)/sizeof(arr[0]);
	int tar=9;
	int st=0,end=n-1,sum;
	while(st<end)
	{
		sum=arr[st]+arr[end];
		if(sum==tar)
		{
			printf("%d,%d",st,end);
			break;
		}
		if(sum>tar)
		{
			end--;
		}
		else if(sum<tar)
		{
			st++;
		}
		else
		{}
	}
}
```

Output:
```
0,3
```

```
Time Complexity-O(nlogn)
```

### Optimized Solution


```
class Solution {
public:
   vector<int> twoSum(vector<int>& arr,int tar)
   {
        unordered_map<int,int> m;
        vector<int> ans;

        for(int i=0;i<arr.size();i++)
        {
            int fir=arr[i];
            int sec=tar-fir;
            if(m.find(sec)!=m.end())
            {
                ans.push_back(i);
                ans.push_back(m[sec]);
                break;
            }
            m[fir]=i;
        }
            return ans;
    }
```


#### Line-by-line explaination

```

This C++ code snippet defines a function twoSum within a class named Solution. The function aims to find two numbers in a given array (arr) that add up to a specific target value (tar). Let's break down how it works step by step:

1. vector<int> twoSum(vector<int>& arr, int tar):

This line declares the twoSum function.
It takes two arguments:
vector<int>& arr: A reference to a vector of integers. This is the input array where we'll search for the two numbers. Using a reference avoids unnecessary copying of the potentially large vector.
int tar: An integer representing the target sum we are looking for.
It returns a vector<int>, which will contain the indices of the two numbers in the input array that sum to the target.

2. unordered_map<int, int> m;:

This line initializes an unordered_map named m.
An unordered_map is a hash table that stores key-value pairs. In this case:
The keys will be the elements encountered in the input array arr.
The values will be the index of each corresponding element in arr.
Using an unordered_map allows for efficient (average time complexity of O(1)) lookups to check if a particular number has been seen before.

3. vector<int> ans;:

This line initializes an empty vector of integers named ans.
This vector will store the indices of the two numbers that sum up to the target value.

4. for (int i = 0; i < arr.size(); i++):

This loop iterates through each element of the input array arr.
i is the index of the current element being considered.

5. int fir = arr[i];:

Inside the loop, this line assigns the value of the current element arr[i] to an integer variable fir (short for "first number").

6. int sec = tar - fir;:

This line calculates the value of the second number (sec) that, when added to the current number (fir), would equal the target (tar).

7.if (m.find(sec) != m.end()):

This is the core logic of the algorithm. It checks if the unordered_map m contains the value of sec as a key.
m.find(sec) searches for the key sec in the map.
If sec is found in the map, m.find(sec) returns an iterator to that element.
If sec is not found, m.find(sec) returns an iterator to m.end() (which represents the end of the map).
Therefore, m.find(sec) != m.end() evaluates to true if sec is present as a key in the map, meaning we have already encountered a number that, when added to the current number, equals the target.

8.ans.push_back(i);:

If the if condition is true (i.e., sec is found in the map), this line adds the current index i to the ans vector. This is the index of the fir number.

9.ans.push_back(m[sec]);:

This line retrieves the index of the sec number from the unordered_map m (where sec is the key and its index is the value) and adds it to the ans vector.

10.break;:

Once we have found the two numbers that sum to the target, we have found our solution. The break statement exits the loop, as we don't need to continue searching.

11.m[fir] = i;:

If the if condition in step 7 is false (meaning sec was not found in the map), this line adds the current number fir as a key to the unordered_map m, with its index i as the value. This ensures that as we iterate through the array, we keep track of the numbers we've seen and their indices, allowing us to efficiently check for the complement later.

12.return ans;:

> After the loop finishes (either by finding the pair or by iterating through the entire array), the function returns the ans vector, which contains the indices of the two numbers that sum to the target. If no such pair is found, the ans vector will likely be empty (though the problem statement usually assumes a solution exists).
In essence, this code uses a hash map to efficiently find the complement of each number encountered in the array. By storing each number and its index in the map, it can quickly check if the remaining value needed to reach the target has been seen before.

```
Output:
```
[1,0]
```

```
Time complexity:O(n)
```
