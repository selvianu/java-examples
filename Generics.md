Generics 

1. Introduction
2. Generic clause
3. Bounded Type
4. Generic Methods and wold-car character(?)
5. Communication with non Generic code
6. Conclusions
___________________________
 __________________________________________________________________________________________________
|The main objectives of generics are to provide type-safety and to resolve type casting problems.  |
|__________________________________________________________________________________________________|

Arrays are type-safe i.e we can give the guaranty for the type of elements present inside array.

e.g.

if our programming requirement is String to hold only String type of objects we can choose String array. By mistake if we are trying to add any other type of objects we will get compile-time error.

String[] s = new String[10000];

s[0] = "Durga";
s[1] = "Ravi";

s[2] = new Integer[10];---------->// CD : Incompatible Type : Found java.lang.Integer
					  required : java.lang.String

Hence String array can contain only String type of objects due to this we can give the guaranty for the type of elements present inside array. Hence arrays are safe to use with respect to type. i.e. arrays are type-safe.

But collections are not type-safe i.e. we can't give the guaranty for the type of elements present inside collection.

e.g. if our programming requirement is to hold only string type of objects, and if we choose array-list, by mistake if we are trying to add any other type of object we won't get any compile time error but the program may fail at run-time.

ArrayList l = new ArrayList();

l.add("Durga");
l.add("Ravi");
l.add(new Integer(10));

.
.
.

String name1 = (String) k.get(0);
String name2 = (String) k.get(1);
String name3 = (String) k.get(2);	--------->RE : ClassCastException : 

Hence we can't give the guaranty for the type of elements present inside collection. Due to this collections are not safe to use. With respect to type. i.e. collections are not type-safe.

__________
Case 2:
__________

Type-casting.

In the case of arrays at the time of retrieval its not required to perform type-casting because there is a guaranty for the type of elements present inside array. 

String[] s = new String[1000];

s[0] = "Durga";

String name1 = s[0];----------> type casting not required.

but in the case of collections at the time of retrieval compulsory we should perform type-casting. Because there is no guaranty for the type of elements present inside collection.

ArrayList l = new ArrayList();

l.add("Durga");

String name = l.get(0);  CE: Incompatible types : found: java.lang.Object
				required : java.lang.String
				
		Type-casting is mandatory.
		
Hence type casting is a bigger headache in collections.

to overcome above problems of collections sun people introduced generics-concepts in 1.5 version.

Hence the main objectives of generics are to provide type-safety to resolve type-casting problems.

For e.g to hold only string type of objects we can create generic version of array-list object as follows.


ArrayList<String> l = new ArrayList<String>();

for this array list we can add only String objects by mistake if we are trying to add any other type then we will get compile time error.

l.add("Durga");
l.add("Ravi");
l.add(new Integer(10));	// CD : 
l.add("Shiva");

Hence throw generics we are getting type-safety.

At the time of retrieval we are not required to perform type-casting.

e.g. ArrayList<String> l = new ArrayList<String>();
l.add("Durga");

String s = l.get(0);-------->Type casting not required.

Hence Throw generics we can solve type-casting problem.

___________________________________________________________________________________________________
ArrayList l = new ArrayList();		|	ArrayList<String> l = new ArrayList<String>();
________________________________________|__________________________________________________________
					|
1. It is a non-generic version of 	| 1.It is a generic version of ArrayList object
ArrayList object			|
					|
2. For this array list we can add any	| 2. for this arrayList we can add only String type
type of object hence it is not		|    Objects and hence it is type-safe.
type-safe.				|
					|
3. at the time of retrieval compulsory	| 3. at the time of retrieval type-casting is not
we have to perform Type-casting is      |    required.
required.				|
________________________________________|___________________________________________________________

Conclusion 1 : Polymorphism concept applicable only for the base type but not for parameter type.(usage of parent reference to hold child object is the concept of polymorphism.).

e.g.

ArrayList<String> l = new ArrayList<String>();

List<String> l = new ArrayList<String>();

Collection<String> l = new ArrayList<String>();

ArrayList<Object> l = new ArrayList<String>();--------> CE : Incompatible types : found : ArrayList<String>
										 Required: ArrayList<Object>

Conclusion 2 : for type parameter we can provide any class or interface name. But not primitives if we are trying to provide primitive then we will get compile time error.

e.g. ArrayList<int> x = new ArrayList<int>();-----------> CE : unexpected type : found : int 
								required reference.
								
Generic classes.
__________________

Until 1.4 version a non generic version of arrayList class is declared as follows.

class ArrayList{
	void add(Object){}
	
	Object get(int position){}
}


The argument to add() method is object and hence we can add any type of object to the arrayList due to this we are missing type-safety.

the return type of get() method is Object hence at the time of retrieval we have to perform type-casting.

but in 1.5 version if generic version of arrayList class is declared as follows.

class ArrayList<E>{	//E----->Element
	
	add(E){}
	E get(int index){}
}

based on our run-time requirement T will be replaced with our provided type.

for example to hold only String type of objects a generic version of ArrayList of object can be created as follows.

ArrayList<String> l = new ArrayList<String>();

for this requirement compiler considered version of ArrayList class is as follows.

class ArrayList<String>{	//T----->Type
	
	add(String){}
	String get(int index){}
}

The argument to add method is String type. Hence we can add only String type of Objects. By mistake if we are trying to add any other type we will get compile time error.

l.add("Test");
l.add(new Integer(10));----> CE : 	cannot find symbol: method add(Integer) 
						Location : class AL<String>

hence throw generics we are getting type safety.

The return type of get() method is String and hence at the time of retrieval we are not required to perform type casting.

String name1 = l.get(0);--------->Type casting is not required

in generics we are associating a type parameter to the class such type of parameterized classes are nothing but generic classes or template classes.

Based on our requirement we can define our own generic classes also.

e.g. class Account <T>{
	
}

Account<Gold> a1 = new Account<Gold>();
Account<Platinum> a2 = new Account<Platinum>();

class Gen<T>{
		T ob;
		
		Gen(T ob){
			this.ob = ob;
		}
		
		public void show(){
			system.out.println("The type of Ob " + 	ob.getClass().getName());
		}
		
		public T getOb(){
			return ob;
		}
}


public class Test{

	public static void main(String[] args){
		Gen<String> g1 = new Gen<String>("Durga");//The type of ob java.lang.String
		g1.show();				
		System.out.println(g1.getOb());	//Durga

		Gen<Integer> g1 = new Gen<Integer>(100);//The type of ob java.lang.Integer
		g1.show();				
		System.out.println(g1.getOb());	//100

		Gen<Double> g3 = new Gen<Double>(100.0);//The type of ob java.lang.Double
		g3.show();				
		System.out.println(g3.getOb());	100.00
	
	}
}

___________________
Bounded Types
___________________

We can bound the type parameter for a particular range by using extends keyword. Such types are called bounded types.

class Test<T> {
	
}

as the type parameter we can pass any type and there are no restrictions and hence it is unbounded type

Test<Integer> t1 = new Test<Integer>();
Test<String> t2 = new Test<String>();

___________________________
Syntax for bounded type
___________________________

class Test<T extends X>{

}

x can be either class or interface if X is a class then as the type parameter we can pass either X type or its child classes. If X is an interface then as the type parameter we can pass either X type or its implementation classes.


class Test<T extends Number> {				
	
}

Test<Integer> t1 = new Test<Integer>();
Test<String> t1 = new Test<String>();-------->Type parameter java.lang.String is not within its bound.

class Test<T extends Runnable> {				
	
}


Test<Runnable> t1 = new Test<Runnable>();
Test<Thread> t1 = new Test<Thread>();

Test<Number> t1 = new Test<Number>();------------> Type parameter java.lang.Integer is not within its bound.

we can define bounded types even in combination also.

e.g
class Test<T extends Number & Runnable>{

}

as the type parameter we can take anything which should be child class of Number and should implements Runnable interface.

class Test<T extends Runnable & comparable>{}----------> Valid
class Test<T extends Number & Runnable & comparable>{}----------> valid

class Test<T extends Runnable & Number>{}----------------->Invalid		because we have to take class first followed by interface name

class Test<T extends Number & Thread>{}------------------->Invalid		because we can't take more than one class simultaneously

Note : 
_________

1. we can define bounded types only by using extends keyword and we can't use implements and super keywords. But we can replace implements keyword purpose with extends keyword.

class Test<T extends>{}----------> Valid
class Test<T implements Runnable>{}----------> invalid
class Test<T extends Runnable>{}----------> Valid
class Test<T super String>{}----------> invalid

As the type parameter 'T' we can take any valid java Identifier but it is conversion to use T.

2.
class Test<T> {}--------->Valid
class Test<x> {}--------->Valid
class Test<A> {}--------->Valid
class Test<Testing> {}--------->Valid

3. Based on our requirement we can declare any number of type parameters and all these type parameters should be separated with ',' comma.

e.g class Test<A,B> {}--------->Valid
class Test<X,Y,z> {}--------->Valid
class HashMap<K, V> {}--------->Valid

_____________________________________________
Generic methods and wild-card character (?)
_____________________________________________

1. m1(ArrayList<String> l){}-------->valid

a. we can call this method by passing ArrayList of only String type.

b. But within the method we can add only String Type of objects to the List. By mistake if we are trying to add any other type then we will get compile time error.

m1(ArrayList<String> l){
	l.add("a");
	l.add(null);
	l.add(10);--------->CE
}

2. m1(ArrayList<?> l){}-------->valid

m1(ArrayList<?> l){}

we can call this method by passing arrayList of any unknown type or any type.

But within the method we can't add anything to the list except null because we don't know the type exactly. null is allowed because it is valid value for any type.

m1(ArrayList<?> l){
	l1.add(10.5);------------->invalid
	l1.add("a");------------->invalid
	l1.add(10);------------->invalid
	l1.add(null);------------->valid
}

this type of methods are best suitable for read only operations.

3. m1(ArrayList<? extends X> l){}-------->valid

X can be either class or interface if X is a class then we can call this method by passing arrayList of either X type or its child classes.
if X is an interface then we can call this method by passing arraylist of either X type or its implementation classes.

but within the method we can't add anything to the list except null. because we don't know the type of X exactly. This type of methods also best suitable for read-only operations 

4. m1(ArrayList<? super X> l){}-------->valid

X can be either class or interface if X is a class then we can call this method by passing ArrayList of either X type or its super classes.

if X is an interface then we can call this method by passing arrayList of either X type or super class or implementation class of X.

					
		Object			Runnable
		   \			    /
		    \			   /
		     \			  /
		      \			 /
		       \		/
		        \	       /
		         \	      /
			  \	     /
			   \	    /		
			    \	   /
			     Thread
			   
but within the method we can add X type of objects and null to the list.

ArrayList<String> l = new ArrayList<String>();

ArrayList<?> l = new ArrayList<String>();

ArrayList<?> l = new ArrayList<Integer>();

ArrayList<? extends Number> l = new ArrayList<Integer>();

ArrayList<? extends Number> l = new ArrayList<String>();------->Incompatible types found : ArrayList<String> required :ArrayList<?extends 																	Integer>();
ArrayList<? super String> l = new ArrayList<String>();

ArrayList<?> l = new ArrayList<?>();---------------------------> CE : Unreported Type found : ?	required : class or interface without bound

ArrayList<?> l = new ArrayList<? extends Number>();------------> CE : Unreported Type found : ?	extends Number required : class or interface without bound

we can declare type parameter either at class level or at method level declaring type parameter at class level
___________________________________________________________

class Test<T>{
	we can use T
	within this class
	based on our requirement.
}

Declaring type parameter at method level. We have to declare type parameter just before return type.

class Test{
	public <T>void m1(T ob){
		we can use T 
		anywhere this method
		based on our requirement 
	}
}

we can define bounded types even at method level also 
    
public <T> void m1(){}

public <T extends Number> 			  void m1(){}
public <T extends Runnable> 			  void m1(){}
public <T extends Number & Runnable> 		  void m1(){}
public <T extends comparable & Runnable> 	  void m1(){}
public <T extends Number & comparable & Runnable> void m1(){}
public <T extends Runnable & Number> 		  void m1(){}---------------->First we have to take class and then interface.
public <T extends Number & Thread> 		  void m1(){}---------------->we can't extends more than one class.

______________________________________
Communication with non-generic code.
______________________________________

if we send generic object to non-generic area then it starts behaving like non-generic object similarly if we send non-generic object to generic area then it starts behaving like generic object i.e. the location in which object present based on that behavior will be defined 

e.g.

class Test{
	public static void main(String[] args){					//in same Test class below method
		ArrayList<String> al = new ArrayList<String>();			public static void m1(ArrayList al){
		
		al.add("Durga");							al.add(10);-------------|
		al.add("Ravi");								al.add(10.5);		|----->non-generic area
//generic	//al.add(10);-------->CE : 						al.add(true);-----------|
//area		m1(al);
		System.out.println(al);						}
		//al.add(10.5);------>CE : 
		al.add("Durga");
	}
}

the main purpose of generics is to provide type-safety and to resolve type-casting problem. Type safety and type-casting both applicable at compile time hence generic concept also applicable only at compile time but not at run-time. At the time of compilation as last step generic syntax will be removed and hence for the JVM generic syntax won't be available hence the following declarations are equal.

ArrayList al = new ArrayList<String>();---------|
ArrayList al = new ArrayList<Integer>();	|--all are equal
ArrayList al = new ArrayList<Double>();		|
ArrayList al = new ArrayList();-----------------|


e.g ArrayList l = new ArrayList<String>();

l.add(10);
l.add(10.5);
l.add(true);

The following declarations are equal.0

e.g ArrayList<String> l = new ArrayList<String>();
ArrayList<String> l = new ArrayList<String>();------->both are equal

for these ArrayList objects we can add only String type of objects.

class Test{
	public void m1(ArrayList<String> l){}
	public void m1(ArrayList<Integer> l){}---------> CE : name clash : both method having same erasure 
}

at compile time

1. compile code normally by considering generic syntax

2. remove generic syntax

3. compile once again resultant code.