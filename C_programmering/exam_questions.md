### 1. Write four different C statements that each add 1 to integer variable z

- `z++;`
- `++z;`
- `z = z + 1;`
- `z += 1;`

### 2. Identify and correct the errors in each of the following.

#### a)

```c
int x = 1, product = 0; // product should be changed to 1
while(x <= 10)
{
    product *= x;// multiplication of 0. pruduct never get bigger than 0
    ++x;
}
```

- If there are a goal to get the product of all positive integers less than or equal to 10.
#### b) 
```c
// is x, total variables is declered somewhere?
while(x <= 100) // can be fixed by while(++x <= 100) or surrounding code block
    total =+ x; //total is set to be the last x value and not the summation of all positive integers less than or equal to 100.  because of =+ wrong order. Fix: +=
    ++x; // infinitive loop. Outside while. 

```

### 3.What does the following program print

```c
#include<stdio.h>
int main(void)
{
    int y;
    int x = 1;
    int total = 0;
    while( x <= 5){
        y = x * x * x;
        printf("%d\n", y);
        total += y;
        ++x;
    }
    printf("The total is %d\n", total);
}
```

- total = $$\sum_{x=1}^{5} x^3$$
- summation of all cubed positive integers less than or equal to 5 
- plus it prints the current cubed x

### 4. Write single pseudocode statement (or C statement) that indicates each of the following:
#### a) Display the message "Enter two numbers"
```C
printf("Enter two numbers\n")
```

#### b) Assign the sum of variables x,y and z to variable p

```C
int p = x + y + z;
```

#### c) The following condition is to be tested in an if..else selection statement: The current value of variable m is greater than twice the current value of variable v

```C
if(m>2v){
    statement;
}
```

#### d) Obtain values for variables s, r and t from keyboard

```C
int s, r, t;
scanf("%d %d %d", &s, &r, &t);
```

### 5. What does the following program print? 

```c
#include <stdio.h>
int main(void)
{
    int x = 1, total = 0, y;
    while(x <= 10){
        y = x*x;
        printf("%d\n", y);
        total += y;
        ++x;
    }
    printf("Total is %d\n", total);
    return 0;
}
```
- total = $$\sum_{x=1}^{10} x^2$$
- summation of all squared positive integers less than or equal to 10
- plus it prints the current squared x

### 6. What does the following program print?
```C
#include <stdio.h>

int main(void)
{
	int outer_count = 1;
	while (outer_count <= 10){
        int inner_count = 1;
        while(inner_count <= outer_count){ // obs: first iteration: 1 <= 1, so print one star. Last 1 <= 10, which gives 10 stars 
            printf("*");
            inner_count++;
        }
        printf("\n");
        outer_count++;
	}
}
```
- Output:
```
*
**
***
****
*****
******
*******
********
*********
**********
```

### 7 .What are the values of i and j after this loop terminates?
```c
int j;
for(int i=20, j=300; i<=j; i+=2, j -=2)
	printf("%d\n", i+j);
```

Answer:

```
i: 162, j: 158
```

- Last time it pass test condition is `i:160 j:160` , but `i+=2, j -=2` will be executed at the end of the last iteration, so it gives `i: 162, j: 158`

### 8. Answer following questions
#### How many times is a do while loop guaranteed to loop?

- One time
#### In switch statement what keyword covers unhandled possibilties?
- `default`

#### What separates particular elements at function parameter list?

- `,` comma

### 9. How do you open a file for binary IO? 

```C
FILE * file;
file fopen("filename", "mode");
```
```
Modes for binary IO:
"rb" open an existing binary file for reading.
"wb" creates a binary file for writing.
"ab" opens an existing binary file for appending.
"r+b" opens an existing binary file for reading or writing.
"w+b" creates a binary file for reading or writing.
"a+b" opens or creates a binary file for appending.
```


### 10. What is the output of the following code?
```c
int a[2][3] = {1, 2, 3, 4 ,5};
int i = 0, j = 0;
for (i = 0; i < 2; i++){
	for(j = 0; j < 3; j++){
		printf("%d", a[i][j]);
	}
}
```

- `int a[rows][columns]`
```
1 2 3
4 5 0
```
- So the answer is `1 2 3 4 5 0`

### 11. Consider the following C program. What is the output of the program?
```c
void mystery(int *ptra, int *ptrb) //pointers is just local variables
{
	int *temp;
	temp = ptrb; // temp point to b
	ptrb = ptra; // swaps pointers
	ptra = temp; // b points to a and b points to a
}
int a = 2018, b = 0, c = 4, d = 42;
mystery(&a, &b);
if (a < c)
	mystery(&c, &a);
mystery(&a, &b);
printf("%d\n", a);
```

- Answer: `2018`, because `mystery` just play around with pointers inside the function. It does not affect anything outside that including address values of `a`, `b`.  

### 12. If a variable has to store the address of the address of a character, what must be the type of its definition?
```c
char a = 'z';
char *ptra = &a;
char **ptrb = &ptra;
```
- short answer: `char **ptrb`
### 13. What is the output of the following code?
```C
union myUnion {
	int x, y;
}
union myUion u;
u.x = 2;
u.y = 10;
printf("X: %d, Y:%d\n", u.x u.y);
```
- Output: `X: 10, Y:10`
- Because  only **one** member can contain a value at given time
- They points to the same memory address
- Does not make a sense to make union here???

### 14. An array with four 4-bytes integers is defined as int array[4] and is stored starting at position 100 in memory. The following code is executed. In which memory address is stored the first element of the array?
```c
array[0] = 20;
array[1] = 30;
array[2] = 10;
array[3] = 0;
```
- Answer: `100`

```
x[0] and &x		100
x[1]			104
x[2]			108
x[3]			112
```

### 15. What is the output of the following code?
```C
struct Course{
	int id;
	char *name;
}
struct Student{
	char *name;
	struct Course courses[3];
}
struct Student student1 = {"Alice"}, student2 = {"Bob"};
struct Course course1 = {62409, "C programming"},
				course2 = {62410, "C++ Programming"},
				course3 = {62411, "Java"};
student1.courses[0] = course1;
student1.courses[1] = course2;
student1.courses[2] = course3;
student2.courses[0] = course1;
student2.courses[2] = student1.courses[2];
printf("%s", student2.courses[2].name);
```
- Answer `Java`
- student1 and student2 courses[2] points to two different address location. It has copied the values. 

### What is the output of the following c code?
```C
#include <stdio.h>
#include <stdlib.h>
struct Node{
	int data;
	struct Node * next;	
};
void printList(struct Node *n){
	while(n != NULL){
		printf("%d", n ->data);
		n = n -> next;
	}
}

int main(int argc, char ** argv){
	struct Node* item1 = NULL;
	struct Node* item2 = NULL;
	struct Node* item3 = NULL;
	//allocate 3 nodes on the heap
	item1 = (struct Node*) malloc(sizeof(struct Node));
	item2 = (struct Node*) malloc(sizeof(struct Node));
	item3 = (struct Node*) malloc(sizeof(struct Node));
	item1->data = 3;
	item1->next = item2;
	item2->data = 2;
	item2->next = item3;
	item3->data = 1;
    item3->next = NULL;
    printList(item1);
    return (EXIT_SUCCESS);
}
```
- Answer `3 2 1`

### 17. Answer each of the following questions:
#### a) What is the difference between passing arguments by value and passing arguments by reference?
- Passing arguments **BY VALUE**

  - value is idempotent, does not change the value of the original variable, which was passed to function 
  - function will have its **own copy of the argument**.  The value of the argument is copied from the caller to the callee. 
  - **Allocates new local variable** and values which was passed to the function is assigned to that new variable 
  - Should **return a value** to caller

- Passing arguments **BY REFERENCE**
  - points to the **same memory location**, which means all changes affects the original variable outside the function 
  - **avoid the overhead** of passing the of passing the object by value
  - **no need to return a value**
  - receives an address of an integer variable, stores the address locally in pointer variable
  - it is not necessary to include **names** of pointers in **function prototypes**
  -  the parameter inside the function **refers to the same object** that was passed in.
  -  It turns out that **any changes operated on the object from inside the function will be seen outside as well**
  -   **define pointer parameter** 
  -  **Dereferencing operator** `*` May be used in the function **to modify** the value at that location in the caller's memory

#### b) What values does the rand function generate?

- The rand function generates an integer between `0` and `RAND_MAX` 

- `RAND_MAX` is a symbolic constant defined in the <stdlib.h> header. At least `32767`, which is the maximum value for a two-byte (16bit) integer



#### c) How do you randomize a program? How do you scale or shift the values produced by the rand function?
- needs to be **randomized** with `srand(time(NULL))`

  -  seeds function rand **to produce a different sequence of random numbers** for each execution of the program.

  - This causes the computer to read its clock to obtain the value for the seed automatically. Function time returns the number of seconds that have passed since midnight on January 1, 1970. This value is converted to an unsigned integer and used as the seed to the random number generator. The function prototype for time is in <time.h>.
- First **Scaling** with modulus
- Than **Shifting** with addition, because it gives values from zero
- `1 + ( rand() % 6 )`

#### d) What is a recursive function? Show (write down) C example of recursive function

- A **recursive function** is a function that calls itself either directly or indirectly through another function.
- recursion keeps producing simpler versions of the original problem until the base case is reached.

- stack overflow
- Recursion has many **negatives**. It repeatedly invokes the mechanism, and consequently the overhead, of function calls. This can be expensive in both processor time and memory space. Each recursive call causes another copy of the function (actually only the function’s variables) to be created; this can consume considerable memory. Iteration normally occurs within a function, so the overhead of repeated function calls and extra memory assignment is omitted.
- A recursive approach is normally chosen in preference to an iterative approach when the recursive approach more naturally mirrors the problem and results in a program that’s easier to **understand and debug**.


```c
int sum(int n){
    if(n == 0){ // base case. 
        return 0;
    }
    return n + sum(n-1);
}
```

### 18. What does the following c program do?
```c
#include <stdio.h>
#include <stdlib.h>

void main()
{
	fprintf(stdout, "Error, program terminated! \n");
}
```
- **Answer**: just prints in console "Error, program terminated!"
- Function `fprintf` is equivalent to `printf` except that `fprintf` also receives as an argument a file pointer for the file to which the data will be written. Function `fprintf` can output data to the standard output by using `stdout` as the file pointer.
- `stdout` is a pointer to a `FILE` stream that represents the default output device for the application. Declared in `stdio.h`
### 19. There is something wrong with this piece of code. What it is?
```c
FILE *fptr;
char b = 'b';
char *c  = &b;
if (fptr = fopen("file.txt","r" )) != NULL) // open in read mode
{
    // while not end of file
	while(!feof(fptr)) // if it uses with fwrite, so it runs infinitely  
	{
		fwrite(c, sizeof(char), 1, fptr); // Cannot write in read mode
		printf("Character: %c", *c);
	}
	fclose(fptr);
}
```
- It works with `fwrite` and `w` mode. Although it is very weird. In text editor it shows `b`
- It writes as binary, although it open with mode `w`
	- As I understood `b` is optional, but it is good idea to write this anyway to indicate, that the file will be treated as binary
- Function `fwrite` writes a block of bytes to a file.
- Solutions :
  - Can be changed `fwrite` to `fread` (most reasonable, because of `while` loop)
  - Or `fopen` mode to `wb` or `w` . And remove `while` loop

```c
/**
 * Solution to read from file
 */

#include <stdio.h>

int main(){
	char c; // not a pointer
	FILE *file;
	if((file = fopen("outputs/fwrite.txt", "rb") != NULL)
	{
		fread(&c, sizeof(char), 1, file); // extra fread to avoid print twice first line
		while(!feof(file)){
			printf("Character: %c", c); // not address
			fread(&c, sizeof(char), 1, file); // adress of c
		}
	}
	fclose(file);
}
```
#### What does the following expression do?

```C
fopen("text.bin", "r+b");
```

- opens an existing binary file for reading or writing
- will overwrite existing, because the pointer is at the beginning of the file
- The file must exists

### 20. What will be the output of the following program?

```c
#include <stdio.h>
int main()
{
    int t[4] = {10,20,30,40};
    int *ad[4]; // array of int pointers
    int i;
    for(i=0; i<4; i++) ad[i]=t+i;
    for(i=0; i<4; i++) printf("%d", *ad[i]); // need to be dereferenced in order to get integer
    printf("\n");
    printf("%d %d\n", *(ad[1]+1), *ad[1]+1); // obs. parentheses 
    return 0;
}
```
```
Output:
10
20
30
40

30 21
```

- both arrays refers to the same memory location. So by changing `*ad[1] = 123;`,  `t[1] ` will be `123` too 

### 21. What will be the output of the following code?

```c
#include <stdio.h>
#include <stdlib.h>

void main(void)
{
    char * s = "Hello, world";
    while(*s != NULL)
        printf("%c", *s++);
}
```

- Strings are arrays of char whose **last element is a null** character '\0' with an ASCII value of 0. 
- **length** must be one larger than the length of the string to accommodate the terminating null character '\0' 
- When initialized, a **pointer to a string points to the first character**. Increment or add an offset to the pointer to access subsequent characters

### 22. Consider following program. Determine initial value for j so the program will print out 18
```c
main (void){
	int j = ?;
	printf("%d\n", (j<<1)&j);
}
```
- Answer: `27`
```
32 16 8 4 2 1
 0  1 1 0 1 1
				<<1
 1  1 0 1 1 0   
				 &
 0  1 0 0 1 0  
```
### 23. What function is used to release (free) memory that is no longer needed and has been allocated by calloc().

- `free(ptr)`
	- deallocates memory
	- the memory is returned to the system so that it can be reallocated in the future.
- indirectly `relloc(ptr, size)`
  - `realloc` takes care to release the old one if needed (and is therefore undefined behavior to access or free it yourself

### 24. Assume an 8bit register. When reading from the register, if the bit is 1 - indicates the LED is on and when the bit is 0 - indicates the led is off. The current value of the register has been read to be `00001100` or in decimal `12`. Which of the bitwise operation/operand will keep the `LED blue` on, while turning all other `LEDs` off? Resulting the register having the value of 8 - `00001000` in binary.

![register](pics/register.png)

- Answer: `&= 8`. `AND`

### 25. What values can be used to initialize a pointer?

- A pointer may be initialized:
	-  `NULL`
	-  `0`
	- `address`

### 26. What is the output of the following code?

```C
enum day {
    Mo, Tu, We, Th, Fr, Sa, Su // gives an error if there is trying to declare for.ex. Mo igen in another enum  
};
int i;
for(i = Su; i >= Mo; i--){ //can be used alone without enum day 
    printf("%d", i);
}
```

```
Output:
6543210
```

- Are unique **integer data types**
- May only contain a specified list of values
- Values are specified as **symbolic constants**
- **Ordered list of constants**
- Each label's values is **one greater** than the previous label

### 27. Assume a compiler occupies 4 bytes for an integer. What will be the output of the following code?

```c
enum{ // No type name is available to declare additional variables of the enum type later in code
    x = 0,
    y = 20,
    z = 5
} coordinate;
coordinate = z;
printf("Size of coodinate is: %d bytes", sizeof(coordinate));
```

- Answer: `Size of coordinate is: 4 bytes`
- because it is just integer
- Does definition take some memory?
  -  No. These are constants and doesn't take any memory nor they have address. In fact `SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY` doesn't exist anywhere in `mmemory`. But you can check that the type `enum` itself takes a memory of size of an `int` (the choice of type is implementation defined).

### 28.  Assume a compiler occupies 2 bytes for short, 4 bytes for float and 8 bytes for long. What is the size of the following struct? 

```c
struct{
    union {
        short x;
        float y;
        long z;
    } u;
}struct1;
```

- Answer: `8`

```c#
//assigning a value to the struct
struct1.u.z = 1111;
printf("%ld\n", struct1.u);
```

### 29. What does the following program do?

```c
#include <stdio.h>

int mystery(unsigned int bits); // prototype

int main(void)
{
    unsigned int x;
    puts("Enter an integer: ");
    scanf("%u", &x);
    printf("The result is %d\n", mystery(x));
}
// What does this function do?
int mystery (unsigned int bits)
{
    unsigned int mask = 1 << 31; // initialize mask
    unsigned int total = 0; // initialize total
    
    for(unsigned int i = 1; i <= 32; ++i, bits <<= 1){
        if((bits&mask) == mask){
            ++total;
        }
    }
    return !(total % 2) ? 1 : 0; 
}
```

- Answer: check if the amount of bits of the entered number is even or odd.

```
0000 0000 0000 0000 0000 0000 0000 0001
After 1<<31
1000 0000 0000 0000 0000 0000 0000 0000

The entered number is shifting one by one to left and 
check runs AND operator 

1000 mask
1111 bits
	AND
1000 == mask, so total++

Another case
1000 mask
0111 bits
	AND
0000 != mask, so do not add to the total 

At the end it checks if the total is a odd or an even number.
If its even, so return 1. Otherwise return 0
```




###  30. Consider following program on 32-bit machine. The output of  first line is "0x62ff10 10 10 20". What is the output for next lines?

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int X[2], *ptr;
    ptr=X;
    X[0]=10; X[1]=20;
    printf("0x%6x %d %d %d \n", ptr, *ptr, X[0], X[1]);
    ptr= ptr+1;
    printf("0x%6x %d %d %d \n", ptr, *ptr, X[0], X[1]);
    *ptr=*ptr+1;
    printf("0x%6x %d %d %d \n", ptr, *ptr, X[0], X[1]);
}
```

```C
Output:
0x62ff10 10 10 20
0x62ff14 20 10 20
0x62ff14 21 10 21
```

- `6x` just minimum length. All missing characters will be filled with white spaces. 
- because 4 bytes integer

```

```