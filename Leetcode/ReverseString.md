# 344 Reverse string in C

```
#include<stdio.h>
void reverse(char str[],int size)
{
	int l=0;
	int r=size-1;
	while(l<r)
	{
		char temp=str[l];
		str[l]=str[r];
		str[r]=temp;
		l++;
		r--;
	}
	int i;
	for(i=0;i<size;i++)
	{
		printf("%c",str[i]);
	}
	printf("\n");
}
int main()
{
	char str[]={'h','e','l','l','o'};
	int size=sizeof(str)/sizeof(str[0]);
	int l,r;
	reverse(str,size);
	return 0;
}
```

## Line-by-line explaination of above code

- This program reverses a character array (in this case, {'h','e','l','l','o'}) and prints the reversed version (olleh).

```
1. #include<stdio.h>
Includes the Standard Input/Output library for functions like printf.

2. void reverse(char str[], int size)
Defines a function reverse that takes:

char str[] → The character array to reverse.

int size → The length of the array.

3. int l = 0;
Initializes the left pointer (l) at the start of the array (index 0).

4. int r = size - 1;
Initializes the right pointer (r) at the end of the array (index size-1).

5. while (l < r)
Runs a loop until the left pointer crosses the right pointer (ensures we only swap until the middle).

6. char temp = str[l];
Temporarily stores the character at the left index (str[l]).

7. str[l] = str[r];
Replaces the left character with the right character.

8. str[r] = temp;
Places the stored left character (temp) at the right position.

9. l++; r--;
Moves the left pointer forward and the right pointer backward to process the next pair.

10. for (i = 0; i < size; i++)
Loops through the reversed array to print each character.

11. printf("%c", str[i]);
Prints the character at index i.

12. printf("\n");
Prints a newline after the reversed string.

main() Function Breakdown
1. char str[] = {'h','e','l','l','o'};
Declares a character array str with the letters 'h','e','l','l','o'.

2. int size = sizeof(str) / sizeof(str[0]);
Calculates the length of the array:

sizeof(str) → Total bytes occupied by str (5 chars = 5 bytes).

sizeof(str[0]) → Size of one element (1 byte for char).

Result: 5 / 1 = 5 → size = 5.

3. reverse(str, size);
Calls the reverse() function to reverse the array in-place.

4. return 0;
Indicates successful execution.
```

- Key Takeaways:
1. Two-pointer technique (l and r) efficiently swaps characters from both ends.
2. In-place reversal (modifies the original array without extra memory).

```
Output
olleh
```
