______________________
OOPs Conceptes	      |
______________________|

1. Data Hiding
2. Abstraction
3. Encapsulation
4. Tightly encapsulate class
5. Is A relationship
6. Has a relationship
7. Method signature
*8. Overloading
*9. Overriding
*10. Static control flow
*11. Instance Control flow
*12. Constructor
13. Coupling
14. Cohesion
15. Type-Casting


__________________
1. Data Hiding
__________________

Outside person can't access our internal data directly or our internal data should not go out directly this oop feature is nothing but data hiding. After validation or authentication outside person can access our internal data

e.g 1. After providing proper user name and password we can able to access our gmail in-box information.
2. even though we are valid customer of the bank we can able to access our account information and we can't access others account information

By declaring data member (variables) as private we can achieve data hiding 

e.g public class account{
	private double balance;
	public double getBalance(){
		//if person valid
		return balance;
	}
}

the main advantage of data hiding is security 
Note : it is highly recommended to declare data member(variable) as private 
________________
2.Abstraction
________________

Hiding internal implementation and just highlight the set of services what we are offering is the concept of abstraction.
throw bank ATM gui screen bank people are highlighting the set of services what they are offering without highlighting internal implementation 

 the main advantages of abstraction are 
1. we can achieve security because we are not highlighting our internal implementation.
2. without affecting outside person we can able to perform any type of changes in our internal system and hence enhancement will become easy.
3. it improves maintainability of the application.
4. it improves easiness to use our system.
5. by using interfaces and abstract classes we can implement abstraction.

__________________
3. encapsulation
__________________

The process of binding data and corresponding methods into a single unit is nothing but encapsulation

e.g class Student{
	//data members (instance variables) + methods (behavior) 
}

as like codact capsul

if any component follows data hiding and abstraction such type of component is said to be encapsulated component

encapsulation = datahiding + abstraction;

public class Account{
	private double balance;
	
	public double getBalance(){ 					 _______________________
		// validation						 | 			|
									 |			|
		return balance;----------------------------------------->| Balance inquiry	|
	}								 |			|
	public void setBalance(double balance){				 |			|
		this.balance = balance;--------------------------------->| Update balance	|
	}								 |			|
}									 |			|
									 |______________________|
									  perform GUI operations	


The main advantages of encapsulation are
1. security
2. enhancement become easy : it improves maintainability of the application

The main advantage of encapsulation is we can achieve security but the main disadvantage of encapsulation is it increase length of the code and slows down execution.

___________________________
Tightly encapsulated class
___________________________
A class is said to be tightly encapsulated if and only if each and every variable declared as private. 
whether class contains corresponding getter and setter methods are not and whether these methods are declared as public or not these things we are not required to check.

e.g public class Account{
	private double balance;

	public double getBalance(){
		return balance;
	}
}


Q. which of the following classes are tightly encapsulated.

ans: a.
class A{------------------------------------> valid
	private int x = 10;
}

class B extends A{--------------------------> invalid
	int y = 20;
}

class c extends B{--------------------------> valid
	private int z = 30;
}

b. 
class A{------------------------------------> invalid
	int x = 10;
}

class B extends A{--------------------------> invalid
	int y = 20;
}

class c extends B{--------------------------> invalid
	private int z = 30;
}


Note: if the parent class is not tightly encapsulated then no child class is tightly encapsulated  


______________________
Is-A relationship
______________________

1. It is also known as inheritance.
2. The main advantage of is-a relationship is code re-usability.
3. By using extends keyword we can implement is-a relationship.

class P{
	public void m1(){
		sopln("parent");
	} 
}
class C extends P{
	public void m2(){
		sopln("child");
	}
}

1. P p1 = new P();

p1.m1();// valid
p1.m2();// invalid CE: cannot find symbol p1.m2() symbol: method m1() location : Variable p2() of type Parent

2. C c1 = new C();

p1.m1();// valid
p1.m2();// valid

3. P p1 = new C();

p1.m1();// valid
p1.m2();// invalid : CE: cannot find symbol p2.m2() symbol : method m1() location : Variable p2() of type Parent

4. C p1 = new P();
CE: incompatible types found : P required : C

1. whatever methods parent has by default available to the child and hence on the child reference we can call both parent and child methods.
2. whatever methods child has by default not available to the parent and hence on the parent reference we can't call child specific methods.
3. parent reference can be used to hold child object but using that reference we can't call child specific methods but we can call the methods present in parent class.
4. Parent reference can be used to hold child object but child reference can't used to hold parent object.

Without inheritance:

class vahicleLoan{
	//300 methods
}

class HomeLoan{
	//300 methods
}

class PersonalLoan{
	//300 methods
}

With niheritance : 

class Loan{
	//250 methods
}

class VehicleLoan extends Loan{
	//write remaining 50 methods
}

class HousingLoan extends Loan{
	//write remaining 50 methods
}

class PersonalLoan extends Loan{
	//write remaining 50 methods
}

Note : the most common methods which applicable for any type of child, we have to define in parent class.
the specific methods which are applicable for a particular child we have to define in child class.

Total java API is implemented based on inheritance concept 

The most common methods which are applicable for any java object are defined in object class.

and hence every class in java is the child class of object either directly or indirectly so that object class methods by default available to every java class without rewriting due to this Object class access root for all java classes.

Throwable class defines the most common methods which are required for every exception and error classes hence this class acts as root for java exception hierarchy.




				  		 Object
						  /| \
						/  |   \
					      /    |     \
					    /	   |       \
					  /	   |	     \
					/	   |	       \
				      /		   |		 \
				    /		   |		   \
				  /		   |		     \
				/		   |		       \
			      /			   |			 \
			    /			   |			   \
			String			StringBuffer		Throwable
									    /\
									  /    \
									/	 \
								      /		   \
								    /		     \
								  /		       \
								Exception	      Error
								   /\
								 /    \
							       /	\
							     RE	     Exception	

______________________
Multiple Inheritance  |
______________________|

A java class can't extends more than one class at a time hence java won't provide support for multiple inheritance in classes 

e.g
class A extends B,C{

}

output : invalid CE:

Note : 1. if our class doesn't extend any other class then only our class is direct child class of object 
class A{

}
  child of
A--------------->object

if our class extends other class then our class is indirect child class of object.
e.g
class A{

} 

class B extends A{

}
      child of
B----------------->A
      child of
B----------------->Object //invalid

      child of		child of
B----------------->A----------------->Object//valid

Note : either directly or indirectly java won't provide support for multiple inheritance with respect to classes.

Q. Why java won't provide support for multiple inheritance.
____________________________________________________________

there may be a chance of ambiguity problem hence java won't provide support for multiple inheritance.


p1.m1()			p2.m1()
\			/
  \		      /
    \		    /
      \		  /
  	\	/
	  \   /
	   \/
	   C
ambiguity problem

But interface can extends any number of interfaces simultaneously hence java provides support for multiple inheritance with respect to interfaces.

e.g

interface A{
}

interface B{
}

interface C extends A, B{
}

Q. why ambiguity problem won't be there in interfaces?
_________________________________________________________
Ans : 

	PI1.m1()		PI2.m1()
	\			/
	  \		      /
	    \		    /
	      \		  /
	  	\	/
		  \   /
		   \/
		   CI----->m1()
		   |
		   |
		   |
		   |
		   |
		   |
	     Implementation ---------> m1(){}
		 Class

Even though multiple method declarations are available but implementation is unique and hence there is no chance of ambiguity problem in interfaces.

Note : strictly speaking throw interfaces we won't get any inheritance.
_____________________
Cyclic Inheritance   |
_____________________|
cyclic inheritance is not allowed in java off-course it's not required
e.g
class A extends A{}//CE: Cyclic inheritance is not allowed in java, it's not required

class A extends B{}//CE: Cyclic inheritance is not allowed in java, it's not required

class B extends A{}//CE: Cyclic inheritance is not allowed in java, it's not required



