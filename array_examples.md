####Program to add the numbers in the array
```java
	public static void main(String[] args) {
		  int [] array = new int [] {1, 2, 3, 4, 5,6,7,8,9};  
	        int sum = 0;    
	        for (int i = 0; i < array.length; i++) {  
	           sum = sum + array[i];  
	        }  
	        System.out.println("Sum of all the elements of an array is: " + sum);    

	}
```
####Program to print the reverse of the given aray.
```java
 int [] a = new int [] {1, 2, 3, 4, 5,6,7,8,9,10};  
	        System.out.println(" Array Values: ");  
	        for (int i = 0; i < a.length; i++) {  
	            System.out.print(a[i] + " ");  
	        }  
	        System.out.println();  
	        System.out.println("Reverse order: ");   
	        for (int i = a.length-1; i >= 0; i--) {  
	            System.out.print(a[i] + " ");  
	        } 

```
####Program to find the samllest and greatest number in the given array.
```java
int large,small,i;
		int a[] = new int[]{12, 2, 37, 4, 59,6,7,8,9,100};
		int n = a.length;
		large=small=a[0];
		for(i=1;i<n;++i)
		{
		if(a[i]>large)
		large=a[i];

		if(a[i]<small)
		small=a[i];
		}

		System.out.println("The smallest element is " + small );
		System.out.println("The largest element is " + large );

```
####Program to separate Odd and Even number of an array
```java 
	int a[] = { 1, 2, 5, 6, 3, 2, 8, 20 };
		System.out.println("Odd Numbers:");
		for (int i = 0; i < a.length; i++) {
			if (a[i] % 2 != 0) {
				System.out.println(a[i]);
			}
		}
		System.out.println("Even Numbers:");
		for (int i = 0; i < a.length; i++) {
			if (a[i] % 2 == 0) {
				System.out.println(a[i]);
			}
		}           

```
####Program to find positive and negative numbers in the given array
```java
int size, i;
	    Scanner sc = new Scanner(System.in);
	    System.out.print(" Enter Number of elements in an array : ");
	    size = sc.nextInt();  
	    int [] a = new int[size];
	    System.out.print("Enter " + size + " elements of an Array  : ");
	    for (i = 0; i < size; i++)
	    {
	      a[i] = sc.nextInt();
	    }   
	    for(i = 0; i < size; i++)
	    {
	      if(a[i] >= 0)
	      {
	        System.out.println("Positive Number:"+a[i]);
	      }
	      else
	      {
	        System.out.println("Negative Number:"+a[i]);
	      }
	    } 
```

