File I/O

1.File
2. FileWriter
3. FileReader
4. BufferedWriter
5. BufferedReader
4. PrintWriter

File
___________

File f = new File("abc.txt");
this line won't create any physical file 1st it will check is there any physical file named with "abc.txt" is available or not if it is available then 'f' simply refers that file. If it is not available then we are just creating java file object to represent the name abc.txt.


File f = new File("abc.txt");

sopln(f.exists()); false

f.createNewFile();

sopln(f.exists()); true

1st run-----> false  true

2nd run-----> true true

we can use java file object to represent directory also.

File f = new File("durga123");

sopln(f.exist());//false

f.mkdir();

sopln(f.exist());//true


Note: in unix every thing is treated as a file java file I/O concept is implemented based on Unix operating system. Hence java file Object can be used to represent both files and directories. 

File class Constructors
__________________________

1. File f = new File(String name);

it creates a java file object to represent name of the file or directory in current working directory. 

2. File f = new File(string subDirName, String name);

it creates a java file object to represent name of the file or directory present in specified sub directory 

3. File f = new File(File subDir, String name)

same as above.

e.g. 1. Write code to create a file name with abc.txt in current working directory.

File f = new File("abc.txt");
f.createNewFile();

2. Write code to create a directory named with "Durga123" in current working directory, and create a File name with "demo.txt" in that directory  

File f = new File("abc.txt");
f1.mkdir();
File f1 = new File("Durga123","demo.txt");

File f1 = new File(f, "demo.txt");

f1.createNewFile();

e.g 3.Write code to create a file named abc.txt in E:\xyz folder.

File f = new File ("E://xyz", "abc.txt");

f.createNewFile();

Assume that E://xyz folder already available in out system.

Important methods present in file class:
_____________________________________________

1. boolean exist(); Returns true if the specified file or directory available.
2. boolean createNewFile() : First this method will check whether the specified file is already available or not. If it is already available then this method returns false without creating any physical file. 
	If the file is not already available then this method will creates new file and returns true.
3. boolean mkdir() : same as above.

4. boolean isFile() : Returns true if the specified file object pointing to physical file.

5. boolean isDirectory() : Returns true if f pointing to directory.

6. String[] list() : this method returns the names of all files and sub directories present in specified directory.

7. long length() : returns number of characters present in specified file.

8. boolean delete() : to delete specified file or directory 

Write a program to display the names of all files and directories present in C:/test

import java.io.*;

class Test{
	public static void main(String[] args){
		int count =  0;
		
		File f = new File("C:\\durga_classes");
		String[] s = f.list();
		for(String s1 : s){
		count++;
			System.out.println(s1);
		}		
		System.out.println("The total number : " + count);
	}
}

To display only file names : 
__________________________________
int count = 0;
File f = new File("C://durgasoft");
String[] s1 = f.list();

for(String s1 : s){
	File f = new File(s1);
	if (f.isFile()){
		count++;
		sopln(f, s1);
	}
}

To display only Directory names:
__________________________________

int count = 0;
File f = new File("C://durgasoft");
String[] s1 = f.list();

for(String s1 : s){
	File f = new File(s1);
	if (f.isDirectory()){
		count++;
		sopln(f, s1);
	}
}

The above fileWriters ment for overriding of existing data. Instead of overriding if we want append operation then we have to create FileWriter by using the following constructors.

3. FileWriter fw = new FileWriter(String fileName, boolean append);

4. FileWriter fw = new FileWriter(File f, boolean append);

Note : if the specified file is not already available then all the above constructors will create that file.

1. Write(int ch) to write a single character

2. Write(char[] ch) to write a array of characters.

3. write(String s) to write an string to the file

4. flush() to give guaranty that total data including last character will be return to the file. 

5. close() to close the writer.

FileWriter
_______________
we can use fileWriter to write character data to the file 

Constructors: 
_____________
FileWriter fw = new FileWriter(String fileName);

FileWriter fw = new FileWriter(File f);

import java.io.*;

class FileWriterDemo2{
	public static void main(String[] args) throws IOException{
		FileWriter fw = new FileWriter("abc.txt");
		fw.write(100);
		fw.write("urg\nsoftwaresolutions");
		fw.write('\n');
		char[] ch1 = {'a','b','c'};
		fw.write(ch1);
		fw.write('\n');
		fw.flush();
		fw.close();
	}
}

output : 
durga
softwaresolution
abc

In the above program fileWriter can perform overriding of existing data instead of overriding if we want append operation then we have to create fileWriter object as follows.

FileWriter fw = new FileWriter("abc.txt", true);

Note : The main problem with FileWriter is we have to insert line separator (\n) manually which is varied from System to System. It is difficulty to the programmer. We can solve this problem by using BufferedWriter and PrintWriter classes.

FileReader
_______________
We can use FileReader to read character data from file 

Constructors : 

1. FileReader fr = new FileReader(String fileName);
2. FileReader fr = new FileReader(File f);

Methods : 

1. int read():it attempts to read next character from the file and  returns its uni-code valueif next character not available then this method returns -1. As this method returns unicode value (int value), at the time of printing we have to perform typecasting. 

FileWriter fr = new FileWriter("abc.txt");
int i = fr.read();
while(i != -1){
	soprint((Char)i);
	i = fr.read();
}

2. int read(char[] ch);

It attempts to read enough characters from the file into char array. And returns number of characters copied from the file.

File f = new File("abc.txt");
char[] ch = new Char[(int) f.length];
FR fr = new FR(f);
fr.read(ch);

for(Char ch1 : ch){
	sopln(ch1);
}

3. void close();

import java.io.*;

class FileReaderDemo{
	public static void main(String[] args){
		File f = new File("abc.txt");
		FileReader fr = new FileReader(f);
		char[] ch = new char[(int) f.length()];
		fr.read(ch);
		for(char ch1 : ch){
			System.out.print(ch1);
		}
		System.out.println("**************************");
		FileReader fr1 = new FileReader("abc.txt");
		int i = fr1.read();
		while(i!= -1){
			System.out.println((char)i);
			i = fr1.read();
		}
	}
}

Note : By using FileReader we can read data character by character which is not convenient to the programmer.

Usage of FileWriter and FileReader is not recommended because 

1. while writing data by fileWriter we have to insert line seprator(\n) manually which is varied from System to system it is difficult to the programmer.

2. By using FileReader we can read data character by character, which is not convenient to the programmer.

3. To overcome these problems we should go for BufferedReader and BufferedReader.

4. BufferedWriter : we can use BufferedWriter to write character data to the file.

Constructors : 
________________

1. BufferedWriter bw = new BufferedWriter(Writer w);
2. BufferedWriter bw = new BufferedWriter(Writer w, int BufferSize);

Note : BufferedWriter can't communicate directly with the file. it can communicate via some Writer object. 

Q. Which of the following are valid 

1. BufferedWriter bw = new BufferedWriter("abc.txt");//invalid
2. BufferedWriter bw = new BufferedWriter(new File("abc.txt"));//invalid
3. BufferedWriter bw = new BufferedWriter(new FileWriter("abc.txt"));//valid
4. BufferedWriter bw = new BufferedWriter(new BufferedWriter(new FileWriter("abc.txt"))); //valid


Methods
__________

1. write(int ch) 
2. write(char[] ch) 
3. write(String s) 
4. flush()
5. close()
6. newLine(); To insert a line separator.

Q. When compared with the FileWriter which of the following capability available extra in method form in BufferedWriter.

1. Writing data to the file
2. close the file
3. flushing the file
4. inserting a new line character.

import java.io.*;
class BufferedWriterDemo{
	public static void main(String[] args) throws IOException{
		FileWriter fw = new FileWriter("abc.txt");
		BufferedWriter bw = new BufferedWriter(fw);
		bw.writer(100);
		bw.newLine();
		char[] ch1 = {'a','b','c','d'};
		bw.write(ch1);
		bw.newLine();
		bw.write("durga");
		bw.newLine();
		bw.write("Software solutions");
		bw.flush();
		bw.close();
	}
}

output:

d
abcd
durga
SoftwareSolutions


Note : Whenever we are closing BufferedWriter automatically internal FileWriter will be closed and we are not required to close explicitly.

bw.close();	fw.close();	bw.close();
				fw.close();
				
valid		invalid		invalid

_____________________
BufferedReader
_____________________
we can use BufferedReader to read character data from the file.
The main advantage of BufferedReader when compared with FileReader is we can read data line by line in addition to character by character.

Constructors
_______________

1. BufferedReader br = new BufferedReader(Reader r);
2. BufferedReader br = new BufferedReader(Reader r, int bufferSize);

Note : BufferedReader can't communicate directly with the file and it can communicate via some Reader object.

Methods 
_________
1. int read();
2. int read(char[] ch)
3. void close();
4. String readLine(); It attempts to read next line from the file and returns it. If the next line not available then this method returns null.

import java.io.*;

class BufferedReaderDemo{
	public static void main(String[] args) throws IOException{
		FileReader fr = new FileReader("abc.txt");
		String line = br.readLine();
		while(line != null){
			System.out.println(ln);
			line = br.readLine();
		}
		br.close();
	}
}

Note : Whenever we are closing BufferedReader automatically underlying FileReader will be closed and we are not required to close explicitly.

Note : The most enhanced reader to read character data from the file is BufferedReader. 

_____________
PrintWriter
_____________

It is the most enhanced writer to write character data to the file. The main advantage of PrintWriter over FileWriter and BufferedWriter is we can write any type of primitive directly to the file
_____________________
Constructors :
_____________________

1. PrintWriter pw = new PrintWriter(String fileName);
2. PrintWriter pw = new PrintWriter(File f);
3. PrintWriter pw = new PrintWriter(Writer w);

Note : PrintWriter can communicate with directly with the file and can communicate via some writer object also.

Methods : 
__________

1. write(int ch)
2. write(String s)
3. write(Char[] ch)
4. flush();
5. close();

print(char ch);
print(int i);
print(double d);
print(String s);
............

println(char ch);
println(int i);
println(double d);
println(String s);
............

class PrintWriterDemo1{
	public static void main(String[] args) throws IOException{
		FileWriter fw = new FileWriter("abc.txt");
		PrintWriter out = new PrintWriter(fw);
		out.write(100);
		out.println(100);
		out.println(true);
		out.println('c');
		out.println("durga");
		out.flush();
		out.close();
	}
}

output:

d100
true
c
durga

Q. What is the difference between write(100) and print(100).

Ans. In the case of write(100) the corresponding character d will be added to the file but in the case of print(100) the int value 100 will be added to the file directly.

Note : the most enhanced writer to write character data to the file is PrintWriter where as the most enhanced reader to read character data from the file is BufferedReader.



Note : In general we can use Readers and Writers to handle character data(text data), where as we can use streams to handle binary data(like images, PDF files, Video files, Audio files etc.)

we can use outputStream to write Binary data to the file, inputStream to read Binary data from the file.

	                      Object
				/\
			       /  \
			      /	   \
			     /	    \
			    /	     \
			   /	      \
			  /	       \
			 /		\
			/		 \
		       /		  \
		    Writer(ac)		Reader(AC)
		      /|\		   / \
		     / | \		  /   \
		    /  |  \		 /     \
		   /   |   \		/       \
		  /    |    \	       /         \
		 /     |     \	      /           \
		/      |      \	     /             \
	       /       |       \    /               \
	      /	       |        \  /                 \
	Output	     Buffered Print Input  	BufferedReader		   
        Stream	     Writer  Writer Stream
        Writer			    Reader
	  |				|
	  |				|
	  |				|
	  |				|
	FileWriter		     FileReader


Q. Write a program to Merge a data from two files in a third file.


import java.io.*;

class FileMerger{
	public static void main(String[] args)throws IOException{
		PrintWriter pw = new PrintWriter("File3.txt");
		BufferedReader br = new BufferedReader(new FileReader("file1.txt"));
		String line = br.readLine();
		while(line != null){
			pw.println(line);
			line = br.readLine();
		}
		br = new BufferedReader(new FileReader("File2.txt"));
		line = br.readLine();
		while(line != null){
			pw.println(line);
			line = br.readLine();
		}
		pw.flush();
		br.read();
		pw.close();
	}
}

aaa	222
bbb	333
ccc	444
	555
	
	aaa
	bbb
	ccc
	222
	333
	444
	555

Write a program to perform file merge operation where merging should be done line by line alternatively.

import java.io.*;

class FileMerger2{
	public static void main(String[]args)throws IOException{
		PrintWriter pw = new PrintWriter("File.txt");
		BufferedReader br1 = new BufferedReader(new FileReader("file1.txt"));
		BufferedReader br2 = new BufferedReader(new FileReader("file2.txt"));
		String line1 = br1.readLine();
		String line2 = br2.readLine();
		
		while((line1 != null)||(line2!= null)){
			if(line1 != null){
				pw.println(line1);
				line1 = br1.readLine();
			}
			if(line2 != null){
				pw.println(line2);
				line2 = br2.readLine();
			}
		}
		
		pw.flush();
		br1.close();
		br2.close();
		pw.close();
	}
}

file 1		file2
AAA		222
BBB		333
ccc		444
		555
		
	AAA
	222
	BBB
	333
	CCC
	444
	555
	

