Literals
----------------------


A constant value which can be assigned to the variable is called literal

e.g int x = 10;

x is identifier

10 is constant value or literal
____________________
Integral literals
--------------------

For integeral datatypes(byte, short, int, long) we can specify litral value in the following ways.

1. Decimal litral(base 10 ) : allowed degits are 0 to 9.

   e.g int x = 10;

2. Octal form (base 8) : allowed digits are 0 to 7

litral value should prefixed with 0.
e.g int x = 010.

3. HexaDecimal form (base 16) allowed digits are 0 to 9, a to f 

Note : for extra degits (a to f) we can use both lower case and upper case characters. This is one of very few areas where java is not case sentisitive the litral value should prefixed with '0X' or '0x'.

int x = 0x10;
int x = 0X10;

these are only possible ways to specify litral valuefor integral data types


which of the following declarations are valid

int x = 10; valid
int x = 0786; invalid CE: integer number too large.
int x = 0777; valid
int x = 0xFace; valid considered as hexadecimal digits
int x = 0xBeef; valid considered as hexadecimal digits
int x = 0xBeer; invalid CE: ';' required.


e.g 2. 
programmer having choice to specify valid in octal,decimal or hexadecimal but jvm print these values in decimal form

e.g 
public class Test{
	public static void main(String[] arg){

		int x = 10;
		int y = 010;
		int z = 0x10;

		System.out.println(x+ "..." + y + "..." + z);
	}
}

by default every integral literal is of int type but we can specify explicitly as long type by suffixed with 'l' or 'L'.

e.g 
int x = 10; valid
long l = 10l; valid
int x = 10l; invalid CE: possible loss of precision found : long required : int. 
long l = 10;

there is no direct way to specify byte and short litrals explicitly but indirectly we can specify
whenever we are assigning integral litral to the byte variable and if the value within the range of byte then compiler treats it automatically as byte literal similarly short literal also

byte b = 10 ; valid
byte b = 127; valid
byte b = 128; CE: PLP found int required : byte

short s = 32767; valid
short s = 32768; CE:PLP found int required short;

floating point literals
___________________________


by default every floatting literal is of double type and hence we can't assign directly to float variable. 
but we can specify floating point literal as float type by sufixed wiht 'f' or 'F'.

e.g
float f = 123.456; CE: PLP found:double
			   required: float

float f = 123.456F; valid
double d = 123.456; valid

we can specify explicitly floating point lieral as double type by sufixed with 'd' or 'D'.
offcurse this convension is not required.

e.g double d = 123.456d; valid
float f = 123.456d;valid CE: PLP found : double required : float
float f = 123.456D;valid CE: PLP found : double required : float

we can specify floating point literals only in decimal form and we can't specify in octal and hexadecimal forms.

e.g double d = 123.456; valid
double d = 0123.456; valid treated as double decimal value
double d = 0x123.456; invalid malformed floating point literals.

we can assign integral literal directly to floating point variables and that integeral literal can be specified either in decimal or octal or hexadecimal forms.

e.g double d = 0786; invalid; CE : inetger number too large
double d = 0xFACE; valid;
double d = 0786.0; valid
double d = 0xFace.0; invalid;
double d = 010;
double d = 0777;

 
we can't assign floating point literals to integral types.

e.g 
double d = 10;
int x = 10.0; invalid CE: PLP found: double Required : int

we can specify floating point literal even in exponential form(scientific notation e.g 12.332e2).

double d = 1.2e3;
sop(d);

outptu:
--------------
1200.0

float f = 1.2e3; CE : PLP found : double required : float
float f = 1.2e3f; valid


Boolean literals : 
___________________

the only allowed values for boolean data type are true or false.

boolean b= true;

boolean b = 0; incompatable type : found : int required : boolean

boolean b = True; CE : Cannot find symbol.
			symbol : variable True
			location : class Test.

boolean b = "true";
		CE:incompatible type 
		found : java.lang.String.
		required : boolean

int x = 0;

if (x) {		CE : incompatable type				while(1){		
	sop("Hello");--->	Found : int	  <---------------------	sopln("Hello");
} else {			Required : boolean			}
	sop("hi");
}

Char Literals
_________________

we can specify char literal as single character within single codes 
char ch = 'a'; valid

char ch = a; invalid CE : can not find symbol
			Symbol : variable a
			location : Test

char ch = "a"; invalid : CE:incompatable type 
			found : j.l.String
			required : char

char ch = 'ab'; invalid : CE1 :  unclosed char literal (for first ');
			  CE1 :  unclosed char literal (for second ');
			  CE1 :  not a statement;

we can specify char literal as integral literal which represents unicode value of the character and that integral literal can be specified either in decimal or octal or hexadecimal forms but allowed range is 0 to 65535

e.g 
char ch = 0xFace;valid considered as hexadecimal
char ch = 0777; vlaid considered as octal value
char ch = 65535;valid 
char ch = 65536; CE : PLP found : int 
			required : char

3. we can represent char literal in unicode representation which is nothing but '\uxxxx'(4 digit hexadecimal number).
e.g char ch = '\u0061';
sop(ch);

output : a

4. every escape character is a valid char literal.

e.g char ch = '\n'; valid
char ch = '\t'; valid
char ch = '\m'; invalid CE: illegal escape character 



Escape character 		Description

\n			New Line
\t			horizontal tab
\r			carriage return  (next line first cell)
\b 			back space
\f			form freed(as like replace)
\'			single quote
\"			double quote
\\			back slash



which of the following are valid?

a. char ch = 65536;	invalid
b. char ch = 0xBeer;	invalid
c. char ch = \uFace;	invalid
d. char ch = '\uBeef';	valid
e. char ch = '\m';	invalid
f. char ch = '\iFace';	invalid

String literals : 
------------------------

Any sequence of characters within double codes is treated as string literal.

e.g
String s = "test abc";


1.7 version inhancement with respect to lierals

1. Binary literals : 

for inegral data types until 1.6 version we can specify lieral value in following ways.

1. Decimal form 2. octal form 3. hexa decimal form

but from 1.7 version onwards we can specify literal value even in binary form also.
allowed degits for binary form are 0 and 1.

Literal value should be prefixed with '0b' or '0B'
e.g int x = 0b1111;

Sop(x);

output : 15

use of '_' symbol in numeric literals.
-----------------------------------------

from 1.7 version onwards we can use '_' symbol between digits of numeric literal

e.g double d = 123456.789; how we can werite
double d = 123_456.7_8_9;

the main advantage of this approach is readability of code will be improved.

at the time of compilation these '_' symbols will be removed automatically hence after compilation the above lines will become 

double d = 123456.789;

we can use more than one '_' symbol also between digits.

e.g 
double d = 1__23_4_56.7_8_9; valid

we can use '_' symbol only between digits if we are using anywhere else we will get compile time error.

double d = _1_23_456.7_8_9; invalid
double d = 1_23_456_.7_8_9; invalid
double d = 1_23_456.7_8_9_; invalid



byte---------->short \
		      \
		       \
			\
			int----------> long --------------> float ----------> double
			/
		       /
		      /
		     /
		char

Note : 8 byte long value we can assign to 4 byte float variable because both are following different memory representations internally.

e.g

float f = 10l;
sop(f);

output : 
10.0;