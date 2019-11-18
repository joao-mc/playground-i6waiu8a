A string in C (also known as C string) is an array of characters, followed by a NULL character. To represent a string, a set of characters are enclosed within double quotes ("). The C string "Look Here" would look like as follows in memory:

-----------------------------------------
| L | o | o | k |  | H | e | r | e | \0 |
-----------------------------------------
It's an array of 10 characters.

In this tutorial, only single byte characters are considered. But same concept can be expanded for multi byte characters. That's useful for writing programs that uses non-English characters.

How to initialize a variable with C string
There are different ways to initialize a variable to access C string.

char *char_ptr = "Look Here";
This initializes char_ptr to point to the first character of the read-only string "Look Here". Yes, a C string initialized through a character pointer cannot be modified. When a C string is initialized this way, trying to modify any character pointed to by char_ptr is undefined behaviour. An undefined behaviour means that when a compiler encounters anything that triggers undefined behaviour, it is allowed to do anything it seems appropriate. For maximum portability of your program, make sure to avoid any undefined behaviour.

For example, the following C code crashes when compiled in Visual C++ 2017 when the commented out line is un-commented and the code is executed:

#include <stdio.h>

int main()
{
	char *char_ptr = "Look Here";

    /* Warning: uncommenting the following line will trigger undefined behaviour */
	/* char_ptr[4] = '_'; */
	printf(char_ptr);

	return 0;
}
A more convenient way to initialize a C string is to initialize it through character array:

char char_array[] = "Look Here";
This is same as initializing it as follows:

char char_array[] = { 'L', 'o', 'o', 'k', ' ', 'H', 'e', 'r', 'e', '\0' };
But the former one is more intuitive. Note that when a character array is initialized by char char_array[] = "Look Here";, the terminating NULL character is appended automatically.

Any character in the array can be modified. In other words, any character in the C string char_array can be modified:

#include <stdio.h>

int main()
{
	char char_array[] = "Look Here";

	char_array[4] = '_';
	printf(char_array);

	return 0;
}
Just like any other array, you can put the array size inside the [] of the declaration:

char char_array[15] = "Look Here";
Make sure that the size you put inside [] is large enough to hold all the characters in the string, plus the terminating NULL character. In this example the array indices 0 through 9 will be initialized with the characters and NULL character. Remaining indices (10 to 14) will be initialized with 0 (same as the NULL character when converted to char). In memory, the above array looks like as follows:

------------------------------------------------------------------
| L | o | o | k |  | H | e | r | e | \0 | \0 | \0 | \0 | \0 | \0 |
------------------------------------------------------------------
  0   1   2   3   4  5   6   7   8   9    10   11   12   13   14
A better approach of declaring character array (or in fact any array) is to define a constant for the array size, then use the constant as the size of the array:

#define ARRAY_SIZE 15
char char_array[ARRAY_SIZE] = "Look Here";
© 2019 GitHub, Inc.
Terms
Privacy
Security
Status
Help
Contact GitHub
Pricing
API
Training
Blog
About

