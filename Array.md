Arrays : 
-----------------

1. Introduction.
2. Array declaration.
3. Array Creation.
4. Array initialization.
5. Array Declaration, Creation and initialization in a single line.
6. length vs length()
7. annonymus arrays.
8. Array element assignments,
9. array variable assignment.

_______________
Introduction
_______________

1. An array is an indexed collection of fixed number of homogenious data elements.
2. The main advantage of arrays is we can represent huge number of values by using single variables so that readability of the code will be improved.
	But main disadvantage of arrays is fixed in size that is once we creates an array there is no chance of increasing or decreasing the size based on our requirement. Hence to use arrays concept compulsary we should know the size in advance, which may not possible always.

_______________________
Array Declaration
_______________________


one dimentional array declaration.
____________________________________

int[] x; valid// recommanded because name is clearly seprated from type.

int []x; valid

int x[]; valid

at the time of declaration we can't specify the size otherwise we will get compile time error.

int[6] x; invalid

int[] x; valid

Two dimentional array declaration
_____________________________________

int[][] x;
int [][]x;
int x[][];
int[] []x;
int[] x[];
int []x[];

Q. which of the following are valid?

a. int[] a, b; valid a---> 1 dimention, b---> 1 dimention.
b. int[] a[], b; valid a---> 2 dimention, b---> 1 dimention.
c. int[] a[], b[]; valid a---> 2 dimention, b---> 2 dimention.
d. int[] []a, b; valid a---> 2 dimention, b---> 2 dimention.
e. int[] []a, b[]; valid a---> 2 dimention, b---> 3 dimention.
f. int[] []a, []b; invalid. CE : ';' Expected

1. if we want to specify dimention before the variable that facility is aplicable only for first variable in a declaration.
2. if we are trying to apply for remaining variable we will get compile time error.
e.g
int[] []a,  []b,    []c;
       |     |       |
       |     |       |
       |     |       |
       |     |       |
       |     |       |
     valid invalid invalid

Three dimentional array declaration
____________________________________

int[][][] a; valid
int [][][]a; valid
int a[][][]; valid
int[] [][]a; valid
int[] a[][]; valid
int[] []a[]; valid
int[][] []a; valid
int[][] a[]; valid
int [][]a[]; valid
int []a[][]; valid


Array Creation
____________________

Every array in java is an object only hence we can create arrays by using new operator.

e.g int[] a = new int[3]; valid

for every array type corresponding classes are available and thses classes are part of java language and not available to the programer level


e.g int[] a = new int[3]; valid

sop(a.getClass().getName());

output : 
[I


Array Type 			Corresponding class name

int[]					[I
int[][]					[[I
double[]				[D
short[]					[S
long[]					[L
byte[]					[B

boolean[]				[Z


1. At the time of array creation compulsary we should specify the size otherwise we will get compile time error.
e.g int[] x = new int[]; invalid	//CE : Array Dimension missing
int[] x = new int[6]; valid

2. It is legal to have an array with size 0 in java.

e.g int[] x = new int[0];

3. If we are trying to specify array size with some negative int value then we will get runtime exception saying negativeArraySizeException.

e.g int[] x = new int[-3]; invalid // Runtime Exception : NegativeArraySizeException


4. To specify array size allowed data types are 
1. byte, 2. short, 3. char, 4. int

if we are trying to specify any other type then we will get Compile time error.

int[] a = new int[10]; valid
int[] a = new int['c']; valid
byte b = 10;
int[] b = new int[b]; valid
short s = 10;
int b = new int[s]; valid

int[] a = new int[10l]; invalid CE : Possible loss of precision
					found : long 
					required : int

5. The maximum allowed array size in java is 2147483647 which is the maximum value of int data type.

int[] a = new int[2147483647]; valid
int[] a = new int[2147483648]; invalid CE: integer number too large.

6. even in the first case we may get runtime exception if sufficient heap memory not available.
OutOfMemoryError : Requested array size exceed vm limit

_________________________________
2 Dimentional array creation 
_________________________________

in java 2 dimentional array not implemented by using matrix style sun people followed array of arrays approach for multidimentional array creation.

the main advantage of this approach is memory utilization will be improved.

e.g 1. int[][] x = new int[5][];
x[0] = new int[2];
x[1] = new int[4];

e.g 2. int[][][] x = new int[2][][];
x[0] = new int[2][];
x[0][0] = new int[1];
x[0][1] = new int[2];
x[0][2] = new int[3];
x[1] = new int[2][2];


Q. which of the following array declarations are valid.

int[] a = new int[];		invalid
int[] a = new int[3];		valid
int[][] a = new int[][];	invalid
int[][] int = a new[3][];	valid
int[][] a = new int[][4];	invalid
int[][] a = new int[3][4];	valid
int[][][] a = new int[3][4][5];	valid
int[][][] a = new int[3][4][];	valid
int[][][] a = new int[3][][5];	invalid
int[][][] a = new int[][4][5];	invalid

_______________________
Array Initialization
_______________________

once we creates an array every element by default initialized with default values.

e.g 1. int[] x = new int[3];

SOP(s);
SOP(s[0]);

output : 
[I@2e4534
0


Note : Whenever we are trying to print any reference variable internally toString() method will be called.
which is implemented by default to return the string in the following form 

classname@Hashcode in hexadecimal form

e.g 2.
int[][] x = new int[3][2];

sop(x);
sop(x[0]);
sop(x[0][0]);

outpupt:
[[I@4F5f45
[I@45e4e45
0

e.g 3. int[][] x = new int[3][];
sop(x);
sop(x[0]);
sop(x[0][0]);

output : 
RuntimeException: NullPointerException

Note : 
if we are trying to perform any operation on null then we will get runtime exception saying NullPointerException.

once we creates an array every array element by default initialized with default values. If we are not satisfied with default values then
we can override these values with our customized values.

e.g
int[] x = new int[6];

x[0] = 10; valid
x[1] = 20; valid
x[2] = 30; valid
x[3] = 40; valid
x[4] = 50; valid
x[5] = 60; valid
x[6] = 60; invalid : RE : ArrayIndexOutOfBond
x[-6] = 60; invalid : RE : ArrayIndexOutOfBond
x[2.5] = 60; invalid : CE : Possible loss of precision
				required : int
				found : double

Note : if we are trying to access array element with outoff range index (either positive value or negative int value) then we will get 
runtime exception saying ArrayIndexOutofBoundException.


__________________________________________________________________
Array Declaration, Creation and initialization in a single line.
__________________________________________________________________

We can declare create and initialize an array in a single line(shortcut representation).

int[] x;
x = new int[3];
x[0] = 10;
x[1] = 10;
x[2] = 10;

for this we have to write only one line.

int[] x = {10,20,30};
char[] ch = {'a','e','i','o','u'};
String[] strarr = {"a", "aa", "aaa", "aaaa", "aaaaa"};

we can use this shortcut for multidimentional arrays also.

int[][] x = {{1,2,3},{4,5,6,7}};


int [][][] x = {{{10,20,30},{40,50,60}},{{70,80}{90,100,110}}}

Note : first represent above in memory representation form and then only solve it.


sop(x[0][1][2]); //output : 60
sop(x[1][0][1]); //output : 80
sop(x[2][0][0]); //RE : ArrayIndexOutOfBondException
sop(x[1][2][0]); //RE : ArrayIndexOutOfBondException
sop(x[1][1][1]); //output : 100
sop(x[2][1][0]); //RE : ArrayIndexOutOfBondException


if we want to use this shortcut compulsary we should perform all activities in a single line. If we are trying to devide in two multiple lines
then we will get compile time error.

e.g int[] x = {10,20,30}; valid

int[] x;
x = {10,20,30}; invalid CE:IllegalStartOfExpression
	
______________________
length vs length() :
______________________

length variable represents the size of the array.
length is a final variable applicable for arrays


e.g int[] x = new int[6];

sop(x.length());

output : 
CE: cannot find symbol method : length() in class [I type 

sop(x.length);

output : 6

length() method is a final method applicable for string objects length method returns number of characters present in the string.

e.g String s = "test";
sop(s.length());

CE:cannot find symbol Variable : length()
		location : java.lang.string.

sop(s.length);
output:
4


Note : length variable applicable for arrays but not for string objects where as length() method applicable for
string objects but not for arrays.

String[] s = {"a","aa","aaa"};

1. sop(s.length); valid
2. sop(s.length()); invalid // CE : Can't find symbol method : length() location : length
3. sop(s[0].length); invalid // CE : Can't find symbol variable : length location : java.lang.String
4. sop(s[0].length()); valid

in multi dimentional arrays length variable represents only base size but not total size 

e.g int[][] x = new int[6][3];

sop(x.length); // 6
sop(x[0].length); // 3

there is no direct way to find total  length of multidimentional array.

But indirectly we can find as follows.

x[0].length + x[1].length + ....

__________________________
Annonymous Arrays
__________________________

Some times we can declare an array without name, such type of nameless arrays are called annonymous arrays.
the main purpose of annonymous arrays is just for instant use (one time usage).

we can create annonymous array as follows 

new int[]{10,20,30,40};

while creating annonymous arrays we can't specify the size.
otherwise we will get compile time error.

new int[3]{10,20,30}; // invalid
new int[]{10,20,30}; // valid

we can create multidimentional annonymous arrays also 

new int[][] {{10,20}, {30,40,50}};

based on our requirement we can give the name for annonymous array then it is no longer annonymous 

int[] x = new int[]{10,20,30};

e.g

class TestAnnonymousArray{
	public static void main(String[] args){
		sum(new int[]{10,20,30});
	}

	public static void sum(int[] x){
		int total = 0;
		for(int i = 0; i < x.size; i++){
			total += x[i];
		}
		sop("the sum is : " + total);
	}
}

in the above example just to call sum() method we required an array. But after completing sum() method call we are not using that array any more
hence for this one time requirement annonymous array is the best choice.

__________________________
Array elements assignments
__________________________

case 1 :  in the case of premitive type array as array elements we can provide any type which can be implecitly promoted to declared type.
e.g
int[] x = new int[5]; valid
x[0] = 10; valid
x[0] = 'a'; valid
byte b = 30; valid
x[1] = 'b'; valid
short sh = 20; valid
x[1] = sh; valid
s[4] = 10l; invalid // CE : PLP Found : long
				required : int

e.g 2.

in the case of float type arrays allowed datatypes are byte, short, char, int, long, float.

case 2 : in the case of object type arrays as array elements we can provide either declared type objects or its child class objects.
e.g 1. Object[] a = new Object[10];
a[0] = new Object();		// valid
a[1] = new String("Test"); 	// valid
a[3] = new Integer(30);		// valid

e.g 2
Number[] n = new Number[10];
n[1] = new Integer(20); //valid
n[1] = new Double(20.5);//valid
n[2] = new String("test"); //invalid CE : incompaitable type found : java.lang.String required java.lang.Number.

case 3: for interface type array as array elements it's implementation class objects are allowed.

Runnable[] r = new Runnable[10];
r[0] = new Thread();// valid
r[1] = String("Test"); // invalid CE:incompatable types found java.lang.String required java.lang.Runnable

		Implements
Thread----------------------------->Runnable


Array type			Allowed element type

1. Premitive arrays		Any type which can be implecitly promoted to declared type.
2. object type arrays		Either declared type or its child class object
3. abstract class arrays	its child class objects are allowed.
4. Interface type arrays	its implementation class objects are allowed.


_______________________________
Array Variable assignments
_______________________________

Case 1 : element level promotions are not applicable at array level.

e.g char element can be promoted to int type. Wherer as char array cannot be promoted to int array.

e.g. int[] x = {10,20,30,40};
     char[] ch = {'a','b','c','d'};

int y = x;//valid
int n = ch;// invalid CE:Found char array required int array.

Q. Which of the following promotions will be performed automatically.

1. char -----> int.
2. char[] -----> int[].
3. int -----> double.
4. int[] -----> double[].
5. float -----> int.
6. float[] -----> int[].
7. String -----> Object.
8. String[] -----> Object[].

but in the case of object type arrays child class type array can be promoted to parent class type array

e.g String[] s = {"a","b","C","d"};
Object[] obj = s;

Whenever we are assigning one array to another array internal elements won't be compied just reference elements will be reassigned

int[] a = {10, 20, 30, 40};
int[] b = {50, 60};

a = b;// valid
b = a;// valid

Case 3 : whenever we are assigning one array to another array dimentions must be matched 

e.g in the place of one dimentional int array we should provide one dimentional array only if we are trying to provide any other dimention then we will get compile time error.

e.g int[][] a = new int[][];
a[0] = new int[][]; //invalid CE: incompatable type found: int[][] required : int[].
a[0] = 10;  //invalid CE: incompatable type found: int required : int[].
a[0] = new int[2]; valid

Note : whenever we are assigning one array to another array bothe dimentions and types must be matched but sizes are not required to match.
_______________
for SCJP       |
_______________|
e.g 1 

class Test{
	public static void main(String[] args){
		for(int i = 0; i <= args.length; i++){
			sop(args[i]);
		}
	}
}

While Execution : 

java Test a b c

RE : ArrayIndexOutOfBondException
java Test a b

RE : ArrayIndexOutOfBondException
java Test a

RE : ArrayIndexOutOfBondException

because of size of array is 3 and for loop will execute 4 times and at last iteration it will get failed.

e.g 2. 
class Test{
	public static void main(String[] args){
		String[] argh = {"x","y","b"};
		args = argh;------------------------------------------->observe this line
		for(int i = 0; i <= args.length; i++){
			sop(args[i]);
		}
	}
}

java Test a b c

output :
x
y
z
java Test a b

output :
x
y
z

java Test a 

output :
x
y
z

e.g 3.

int[][] a = new [4][5];
a[0] = new int[4];
a[1] = new int[3];

a = new int[3][2];

a. Total how many objects are created.

Ans : 11

b. Total how many objects are eligible for garbage collection?

Ans : 7

