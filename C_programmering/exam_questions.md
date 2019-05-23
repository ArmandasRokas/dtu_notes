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












```

```
