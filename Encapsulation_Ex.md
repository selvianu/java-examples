CHALLENGE DESCRIPTION:  
  Create a class and demonstrate proper encapsulation techniques 
  The class will be Printer
  It will simulate a real Computer Printer 
  It should have fields for the toner Level, number of pages printed, and 
  Also whether its a duplex printer (capable of printing on both sides of the paper).
  Add methods to fill up the toner (up to a maximum 100%), another method to simulate printing a page(which should increase the number of pages printed)
  Decide on the scope, whether to use constructors, and anything else you think is needed. 
  ```java
  public class Printer {
	private int tonerLevel;
	private int pagesPrinted;
	private boolean duplex;

	public Printer(int tonerLevel, boolean duplex) {

		if (tonerLevel > -1 && tonerLevel <= 100) {
			this.tonerLevel = tonerLevel;
		} else {
			this.tonerLevel = -1;
		}
		this.duplex = duplex;
		this.pagesPrinted = 0;
	}

	public int addToner(int tonerAmount) {
		if (tonerAmount > 0 && tonerAmount <= 100) {
			if (this.tonerLevel + tonerAmount > 100) {
				return -1;
			}
			this.tonerLevel += tonerAmount;
			return this.tonerLevel;
		} else {
			return -1;
		}
	}

	public int printPages(int pages) {
		int pagesToPrint = pages;
		if (this.duplex) {
			pagesToPrint = (pages / 2) + (pages % 2);
			System.out.println("Printing in duplex mode");
		}
		this.pagesPrinted += pagesToPrint;
		return pagesToPrint;
	}

	public int getPagesPrinted() {
		return pagesPrinted;
	}
}
```

```java
	public class PrinterTest {
		 public static void main(String [] args) {
		      
		      Printer printer = new Printer(50, false);
		      System.out.println("Initial page count = " + printer.getPagesPrinted());
		      
		      int pagesPrinted =  printer.printPages(4);
		      System.out.println("Pages printed was " + pagesPrinted + " new total print count for printer = "+ printer  + " " + printer.getPagesPrinted());
		                         
		      pagesPrinted = printer.printPages(2);
		      System.out.println("Page printed was " + pagesPrinted + " new total print count for printer = " + printer.getPagesPrinted());
		    
		    }
	}
    
```