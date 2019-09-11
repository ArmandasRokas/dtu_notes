### Exercise 2.1 from book

#### a) All number-strings that have the value 42

0*42

???? Hvad betyder 0* her?  Hvad med 1421? Er det også gyldig?

[0-9]* 42 [0-9]*

#### b) All number-strings that do not have the value 42

The number must either be a one-digit number, a two-digit number different from 42 or have at least three significant digits

0*([0-9] | [1-3] [0-9] | 4[0-1] | 4[3-9] | [5-9] [0-9] | [1-9] [0-9] [0-9]^+^ )

#### c) All number-strings that have a value that is strictly greater than 42

The number must either be a two-digit number greater than 42 or have have at least three significant digits

0* (4[3-9] | [5-9] [0-9] | [1-9] [0-9] [0-9]^+^)

### Exercise: Clock time



TIME: (HOUR ':'? MIN) |('24':'?''00')

HOUR : (NUM | 1 NUM | 2[0-3])

MIN: [0-5] [0-9]

NUM : [0-9]

Smart med regular expressions, fordi man kan finde nogen mønster, som kan simplificeres.



