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
