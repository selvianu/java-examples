________________
Overrriding
________________

Whatever method parent has by default available to the child throw inheritance if child class not satisfied with parent class implementation then child is allowed to redefine that mehtod based on its requirement this process is called overriding the parent class method which is overidden is called overridden method and child class method which is overriding is called overriding method.


e.g

class Parent{
	public void property(){
		System.out.println("cash|land|gold");
	}

	public void merrage(){				_
		System.out.println("abc|pqr|xyz");	 |
	}						 |
}							 |
							 |
class Child extends Parent{				 |_____________overidden methods
							 |
	public void property(){				 |
		System.out.println("efgh|lmno|uvwx");	 |
	}						_|
}


public class Test{
	public static void main(String... args){
		Parent p = new Parent();
		p.merrage();				//abc|pqr|xyz     parent class method
	
		Child c = new Child();
		c.merrage();				//efgh|lmno|uvwx  child class method

		Parent pc = new Child();
		pc.merrage();				//efgh|lmno|uvwx   child class method

	}
}

***** in overriding method resolution is always takes care by JVM based on runtime object and hence overriding is also considered as runtime polymorphism or dynamic polymorphism or late binding.

Rules for overriding : 
_______________________

1. in overriding method names and argument types must be matched. i.e. method signatures must be same 

2. in overriding return types must be same but this rule is applicable untile 1.4 version only from 1.5 version onwards we can take co-varient return types according to this child class method return type need not be same as parent method return type it's child type also allowed.

e.g 
class Parent{
	public Object method1(){
		return null;
	}
}

class Child extends Parent{
	public String method1(){		// it is invalid in 1.4 version but from 1.5 version it is valid
		return null;
	}
}


parent classmethod 
return type	-------Object				number		  	String			String			double
			  |				  |			  |			  |			  |
			  |				  |			  |			  |			  |
	   		  |                               |			  |			  |			  |
	   		  |				  |			  |			  |			  |
	   		  |				  |			  |			  |			  |
	   		  |				  |			  |			  |			  |
	   		  |				  |			  |			  |			  |
child class method ----Object|String|
return type		StringBuffer             Integer|Float|Double       Number|Integer		Object			int|float


			valid				valid			invalid			invalid			 invalid

1. Co-varient return type concept applicable only for object types but not for premitive types

2. parent class private methods not available to the child and hence overriding concept not applicable for private methods.

3. Based on our requirement we can define exactly same private method in child class it is valid but not overriding.

e.g

class Parent{
	private Object method1(){-------|
		return null;		|
	}				|
}					|----------valid but not overriding
					|
class Child extends Parent{		|
	private String method1(){-------|
		return null;
	}
}


4. we can't override parent class final method in child classes if we are trying to override we will get compile time error.
e.g
class Parent{
	public final void method1(){		//CE: can not override method1() in Parent overridden method is final 
	}										   ___________
}

class Child extends Parent{
	public void method1(){		
	}
}

5. parent class abstract method we should override in child class to provide implementation.
e.g
abstract class Parent{
	public abstract void method1(){
	}					
}

class Child extends Parent{
	public void method1(){		
	
	}
}

valid.

6. we can override non abstract method as abstract 

class Parent{
	public abstract void method1(){
	}					
}

abstract class Child extends Parent{
	public abstract void method1();	
}

valid.


the main Advantage of this approach is we can stop availability of parent method implementation in the next level child classes.

in overriding the following modifiers won't keep any restriction.
1. synchronized 2. native 3. strictfp 


parent class method ----final	      non final		abstract	     Synchronized		native		strictfp
			  |		  |		  |^			  |^			  |^		   |^
			  |		  |		  ||			  ||			  ||		   ||
	   		  |               |		  ||			  ||			  ||		   ||
	   		  |		  |		  ||			  ||			  ||		   ||
	   		  |		  |		  ||			  ||			  ||		   ||
	   		  |		  |		  ||			  ||			  ||		   ||
	   		  |		  |		 \/|			 \/|			 \/|		  \/|
child class method ----non-final|final  final	      non-abstract	   non-Synchronized	      non-native	not-strictfp


			invalid		valid		valid			 valid			 valid		   valid


7. while overriding we can't reduce scope of access modifier but we can increase the scope.

class Parent{
	public void m1(){}
}
class Child extends Parent{
	void m1(){}		// m1 in Child can't override m1() in Parent attempted to assign weaker access privileges was public
}


parent class method ----public	      protected			<default>     		     	     private		
			  |		  |		  	   |^			  		|^		
			  |		  |		  	   ||			  		||			  
	   		  |               |		  	   ||			  		||			  
	   		  |		  |		  	   ||			  		||			  
	   		  |		  |		  	   ||			  		||			  
	   		  |		  |		  	   ||			  		||			  
	   		  |		  |		 	  \/|			 		\/|			 
child class method ----public    public|protected	<default>|protected|pubic	   	overriding concept	      
											    	is not allowed

8. Exception in overriding
_________________________

if child class method throw any checked exception compulsory parent class method should throw the same checked exception or it's parent otherwise we will get compile time error but there are no restrictions for unchecked exceptions.

e.g

import java.io.*;

class Parent{
	public void m1() throws IOException
	{} 
}
class Child extends P{
	void m1() throws EOFException, InterruptedException
	{}
}

CE: m1() in Chile cannot override m1() in Parent overridden method does not throw java.lang.InterruptedException


1. Parent : public void m1() throws Exception					//valid
   Child : public void m1()

2. Parent : public void m1() 							//invalid
   Child : public void m1() throws Exception

3. Parent : public void m1() throws Exception					//valid
   Child : public void m1() throws IOException

4. Parent : public void m1() throws IOException					//invalid
   Child : public void m1() throws Exception

5. Parent : public void m1() throws IOException					//valid
   Child : public void m1() throws FileNotFoundException, EOFException

6. Parent : public void m1() throws IOException					//invalid
   Child : public void m1() throws EOFException, InterruptedException		

7. Parent : public void m1() throws IOException					//valid
   Child : public void m1() throws NPE, ArithmaticException, ClassCastException



Overriding with respect to static methods.

Static method overriding
__________________________

1. we can't override a static method as non-static otherwise we will get compile time error.
e.g 1.
class Parent{
	public static void m1(){

	}
}

class Child extends Parent{
	public void m1(){		// CE : m1() in Child cannot override m1() in Parent Overridden method is static

	}
}

2. Similarly we can't override as non static method as static 
e.g 2.
class Parent{
	public void m1(){

	}
}

class Child extends Parent{
	public static void m1(){		// CE : m1() in Child cannot override m1() in Parent Overriding method is static

	}
}

3. IF both parent class and child class methods are static then we won't get any compile time error it seems overriding concept applicable for static methods but it's not overriding and it is method hiding.

class Parent{
	public static void m1(){--------|
					|
	}				|
}					|-------------// it is method hiding but not overriding
					|
class Child extends Parent{		|
	public static void m1(){------- |		

	}
}



method hiding: all rules of method hiding are exactly same as overriding except the following differences.


	method hiding					overriding
___________________________________________________________________________________________
1. both parent and child class 			1.both parent and child class methods
methods should be static			  should be non static

2. Compiler is responsible for 			2.JVM is always responsible 
method resolution based 			  for method resolution based 
on reference type				  on runtime object

3. it is also known as 				3. Runtime polymorphism
   Compile time polymorphism			   or dynamic polymorphism
   static polymorphism			   	   or late binding.
   early binding.
_____________________________________________________________________________________________


class Parent{
	public static void m1(){--------------|
		System.out.println("parent"); |
	}				      |
}					      |-------------// it is method hiding but not overriding
					      |
class Child extends Parent{		      |
	public static void m1(){--------------|		
		System.out.println("child");
	}
}

class Test{
	public static void main(String[] args){
		Parent p = new Parent();
		p.m1();					//parent
	
		Child c = new Child();
		p.m1();					//child

		Parent p = new Child();
		p.m1();					//parent

	}
}

output:

parent
child
parent

if both parent and child class methods are non-static then it will become overriding

in this case output is 

parent
child
child

_____________________________________________
Overriding with respect to var-arg methods
_____________________________________________

we can override var-args method with another var-args method only if we are trying to override with normal method then it will become overloading but not overriding 

class P{
	public void m1(int... x){			|
		System.out.println("parent");		|--------------|
	}						|	       |
}								       |
								       |-----------is overloading but not overriding
class Child extends Parent{					       |
	public void m1(int x){				|	       |
		System.out.println("child");		|--------------|
	}						|
}

public class Test{
	public static void main(String[] args){
		Parent parent = new Parent();
		parent.m1(10);			//parent
		
		Child child = new Child();
		child.m1(10);			//child
	
		Parent parent = new Child();
		parent.m1(10);			//parent

	}
}

output:

parent
child
parent

in above program if we replace child method with var-arg method then it will become overriding in this case the output is

parent
child
child

overriding with respect to variables
_____________________________________

variable resolution always takes care by compiler based on reference type e-respective of whether the variable is static or non-static(overriding concept applicable only for methods but not for variables).

class P{
	int x = 888;
}								      
								      
class Child extends Parent{					      
	int x = 999;	
}

public class Test{
	public static void main(String[] args){
		Parent parent = new Parent();
		System.out.println(parent.x);	//888
		
		Child child = new Child();
		System.out.println(child.x);	//999
	
		Parent parent = new Child();
		System.out.println(parent.x);	//888

	}
}

output : 

888
999
888


p-->non-static		p-->static		p-->non-static		p-->static
c-->non-static		c-->non-static		c-->static		p-->static

     888		   888			   888			   888
     999		   999			   999			   999
     888		   888			   888			   888



Differences between overloading and overriding

property		overloading				overriding
____________________________________________________________________________________________

1. method names	  	must be same				must be same

2. argument types	must be different(atlist order)		must be same(including order)

3. method signatures	must be different			must be same

4. return types		no rule or no restriction		must be same until 1.4
								from 1.5 onwards co-varient return types allowed

5. private, static	can be overloaded			cannot be overridden
   final methods.

6. access modifiers	no restrictions				the scope of access modifier
								cannot be reduced but we can increase

7. throws class		no restriction				if child class method throws any checked exception 
								compulsory parent class method should throw the same
								checked exception or its parent. But no restriction for 
								unchecked exception

8. method resolution	always takes care by 			always takes care by jvm based on run-time object
			compiler based on reference		

9. it is also known 	compile time /static polymorphism	runtime time/ dynamic polymorphism
	as 		early binding				late binding
			type	

__________________________________________________________________________________________________________________________________

NOTE : in overloading we have to check only method names (must be same) and argument types (must be different) we are not required to check remaining like return types access modifiers etc.

But in overriding every thing we have to check like method name, argument types, return types access modifiers, throws class etc.


e.g
1. consider the following method in parent class
	
	public void m1(int x) throws IOException
	_________________________________________
	in the child class in following methods we can take
	
	a. public void m1(int i)			//overriding
	b. public static int m1(long l)			//overloading
	c. public static void m1(int i)			//invalid
	d. public void m1(int i) throws Exception	//invalid parent class should throws same or parent exception
	e. public static abstract void m1(double d)	//invalid CE: IllegalCombination of modifiers


Polymorphism:

one name but multiple forms is concept of polymorphism.

e.g 
1. method name is same but we can apply for different type of arguments (overloading)
e.g
abs(int i)
abs(long i)
abs(float i)

e.g 2. method signature is same but in parent class one type of implementation and in child class another type of implementation(overriding).

class P{
	public void marring(){
		System.out.println("abcd");
	}
}

class C extends P{
	public void marring(){
		System.out.println("xyz|pqr");
	}
}

usage of parent reference to hold child object is concept of polymorphism or is also considered as polymorphism

	List l = new ArrayList();
	List l = new LinkedList();
	List l = new Stack();
	List l = new Vector();

		Collection
		   |
		   |
		   |
		 List
		 / |\
		/  | \
	       /   |  \
	      /	   |	\
	ArrayList  LL	vector
			   |	
			   |
			   |
			Stack

parent class reference can be used to hold child object but by using that reference we can call only the methods available in parent class and we can't call child specific methods. 

e.g
P---> m1()
|
|
C---> m2()

P p = new C();

p.m1(); //valid
p.m2(); // invalid CE: cannot find symbol method m2() in class P

But by using child object reference we can call both parent and child class methods 

Child c = new Child();

c.m1()// valid
c.m2()// valid

When we should go for parent reference to hold child object.
____________________________________________________________

if we don't know exact return type of object then we should go for parent reference.
e.g the first element present in the array list can be any type. it may be student object, or customer, String, stringBuffer object hence the return type of get method is object, which can hold any object.

e.g Object o = list.get(0);


	Child c = new Child()			Parent p = new Child()
_________________________________________________________________________________


e.g ArrayList l = new ArrayList()		List l = new ArrayList();

1. we can use this approach if we know		we can use this approach if we don't know 
   exact runtime type of object.		exact runtime type of object.


2. by using child reference 			by using parent reference we can call
   we can call both parent and child		only parent class method 
   class methods(advantage)			we can't call child specific methods (disadvantage of this approach)
						

3. we can use child reference to hold		we can use parent reference 
   only particular child class object		to hold any child object
   (disadvantage of this approach)		(this is advantage of this approach)

_________________________________________________________________________________________



					    Encapsulation
						  |
						  |
						  |
						  |Security
						  |
						  |
						  |
						OOP's
						/  \
					      /	     \
				Flexibility /	       \Re-usability
					  /		 \
					/		   \
				   Polymorphism		Inheritance


				Fig. 3 pilers of oops



				Polymorphism
				     / \
				   /	 \
				 /	   \
			       /	     \
			     /		       \
			   /			 \
		Static polymorphism or	      Dynamic polymorphism
		compile-time polymorphism     Runtime pholymorphism
		early-binding		      late-binding

		    / \					|
		  /	\				|
		/	  \				|
	      /		    \				|
	overloading	method hidding		    overriding


Beautiful definition of polymorphism
_______________________________________

A BOY start love with word FRIENDSHIP, but GIRL ends LOVE with word FRIENDSHIP. Word is same but attitude is different. This beautiful concept of OOPS is nothing but polymorphism...