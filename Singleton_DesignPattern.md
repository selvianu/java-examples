Singleton classes
___________________

For any java class if we are allowed to create only one object such type of class is called singleton class.

e.g Runtime
business deligate
service locator
etc.

Advantage of singletone class : 
_________________________________

if several people have same requirement then it is not recommanded to create seprate object for every requirement.
We have to create only one object and we can reuse same object for every similar requirement so that performance and memory utilizations will be improved.

This is the central idea of singleton classes.

e.g
Runtime r1 = Runtime.getRuntime();
Runtime r2 = Runtime.getRuntime();
.
.
.
.
Runtime rn = Runtime.getRuntime();

How to create our own singleton classes?
_________________________________________
we can create our own singleton classes for this we have to use private constructor and private static variable and public factory method.

approach 1. 

class Test{
	private static Test testSingleton = new Test();

	private Test(){

	}
	public static Test getTest(){
		return testSingleton;
	}
}

Test t1 = Test.getTest();
Test t2 = Test.getTest();
Test t3 = Test.getTest();

Note : Runtime class is internally implemented by using this approach.

Approach 2.

class Test{
	private static Test testSingleton;

	private Test(){

	}
	public static Test getTest(){
		if(testSingleton == null){
			testSingleton = new Test();
		}
		return testSingleton;
	}
}


At any point of time for test class we can create only one object hence test class is singleton class.

class is not final but we are not allowed to create child classes How it is possible.

by declaring every constructor as private we can restrict child class creation.

e.g

class P{
	private P(){}
}

for the above class it is impossible to create child class.s