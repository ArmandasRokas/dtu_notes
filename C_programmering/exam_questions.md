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

