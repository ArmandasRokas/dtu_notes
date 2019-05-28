## Preprocessor

- **Preprocessor** **--->** **Compiler** **--->** **Assembler** **--->** **Linker**  **--->** **Executable**

- **Preprocessor directives begin with #**

- **Preprocessor performs**:
  - `Inclusion of other files in the file being compiled`
  - `Symbolic constants` - constants - is a type of macro
  - `Macros` 
  - `Conditional compilation`  

### Macros

Marcos is operations defined as symbols. However, functions are more safe.  

> In the past, macros were often used to replace function calls with inline code to eliminate the function-call overhead (running costs). Today’s optimizing compilers often inline function calls for you, so many programmers no longer use macros for this purpose. 

**Watch out with marcos**

```C
result = CIRCLE_AREA( ++radius );
```

is expanded to 

```C
result = ( ( 3.14159 ) * ( ++radius ) * ( ++radius ) );
```

which increments radius twice in the statement.

## Data types
- `unsigned long long int` is at least the [0, +18,446,744,073,709,551,615]


## Unions
- Special data type allows to store different data types in the same memory location
- Because  only **one** member can contain a value at given time
- The same memory location for **multiple-purose**


## Pointers
- `&`  address operator
- A pointer may be initialized:
	-  `NULL`
	-  `0`
	- `address`


## Formatted Input/Output
### Format specifier
#### %d vs %i

They are the same when used for output, e.g. with `printf`.

However, these are different when used as input specifier e.g. with `scanf`, where `%d` scans an integer as a signed decimal number, but `%i` defaults to decimal but also allows hexadecimal (if preceded by `0x`) and octal if preceded by `0`.

So `033` would be 27 with `%i` but 33 with `%d`.

#### %6x
- just minimum length. All missing characters will be filled with white spaces. 





## C Files processing

- Files are used for long term data storage (vs to temporary storage in array, variables)
- In C each file is a sequential stream of bytes
- Each file ends with EOF (end of file marker)
- `FILE` structure
  -  File descriptor -  `int` value, index into OS array open file table 
  - File position pointer (file offset )
- `fopen()` returns pointer to `FILE` structure  
```c
MODES:	
Sequential-access:
"r" opens an existing text file for "ONLY reading".
"w" creates a text file for writing. "will overwrite existing"
"a" opens an existing or creates text file for appending. "ONLY WRITES"
"r+" opens an existing text file for reading or writing. "will overwrite existing and The file must exists" 
"w+" creates a text file for reading or writing. "will overwrite existing"
"a+" opens or create a text file for appending. "For read and write"
Random-access:
"rb" opens an existing binary file for "ONLY reading".
"wb" creates a binary file for writing. "will overwrite existing"
"ab" opens an binary or creates text file for appending. "ONLY WRITES"
"r+b" opens an existing binary file for reading or writing. "will overwrite existing and The file must exists" 
"w+b" creates a binary file for reading or writing. "will overwrite existing"
"a+b" opens or create a binary file for appending. "For read and write"
```



### Sequential-access file processing

- Representation of integer 25 in main memory and in text file – not the same 

```c
Decimal		Main memory bit pattern		Text file bit pattern
-------------------------------------------------------------
25			0000 0000 0001 0001			0011 0010|0011 0101
    									---------|----------
  										ASICII	 | ASCII
  										for 2	 | for 5
```



- Need for operations in order to take value from memory and copy into disk text file format-`fprintf()` 
- we read file from text file we need to convert to format use in Main memory 
- Because writing and reading to binary files is much faster than writing and reading to text files,  programs that requires significant movement in and out of files during execution should use binary files instead of text files 

### Random-access file processing
- Individual records of a random-access file are normally fixed in length and may be **accessed directly** (and thus quickly) without searching through other records.
- Fixed-length records enable **data to be inserted** in a random-access file **without destroying other data**. 
- Data stored previously can also be **updated or deleted without rewriting the entire file** 
- `fwrite`
  - transfers a specified number of bytes beginning at a specified location in memory to a file
- `fread`
  - Function fread reads a specified number of bytes from a file into
    memory. 
- The third argument of both `fread` and `fwrite` is the number of elements to process in the array 
- `int fseek(FILE * stream, long int offset, int whence);`
  - **sets the file position pointer** for a given file to a specific position in the file. 
  - its possible to use with sequential-access files too
  - **stream** − This is the pointer to a FILE object that identifies the stream.
  - **offset** − This is the number of bytes to offset from whence.
  - **whence** − This is the position from where offset is added. It is specified by one of the following constants
    - `SEEK_SET` - Beginning of file
    - `SEEK_CUR` -  Current position of the file pointer
    - `SEEK_END` - End of file

### Arrays
- **NOT WORKING** `int * arr = {1,2,3,4}`, but fine `char *str = "test" `

### Dynamic Memory Allocation
- the ability for a program to **obtain more memory space at execution time** to hold new nodes, and to release space no longer needed.

#### malloc

- **takes** as an argument the number of **bytes to be allocated** and **returns** a pointer of type **void *** (pointer to void) to the allocated memory
- The allocated memory is **not initialized**.
- If **no memory** is available, malloc returns **NULL**


#### free

- deallocates memory
- the memory is returned to the system so that it can be reallocated in the future.

#### calloc

- dynamically allocates memory for an array
- two arguments:
  - `nmemb` - number of elements
  - `size` - size of each element 
- **initializes** the elements of the array **to zero**.
- The primary difference between `malloc` and `calloc` is that `calloc` clears the memory it allocates and malloc does not.

#### relloc

- changes the size of an object 
- contents are not modified, if amount of memory allocated is larger than the amount allocated previously. Otherwise, the contents are unchanged up to the size of the new object. 
- two arguments:
  - `ptr` - pointer to the original object
  - `size` - the new size of the object