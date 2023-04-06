
![enter image description here](https://developer.electricimp.com/sites/default/files/2020-09/impt-test.png)
# Final Assignment ISE
by Nhlonipho Khathutshelo Marwala 
(21308921)

Introduction to Software Enginnering (ISAD1000)
***
## Introduction
In this assignment I was tasked with creating a library for mathematical functions that involve square numbers, fibonacci numbers and range categorisation. I then selected suitable testing methods to varify the functionality of the functions. Using White Box, Equivelence Partitioning, and Boundary Value Analysis I exposed the limitations of the functions as well as semantic errors that would otherwise be difficult to gage. This was supposed to be done using good version control practices and the implementation of git to record code changes. 
***
## Module Description
1. Check if a number entered is in the Fibonacci Sequence not.
    > When I 1st encounterd this question assumed that function could expressed explicitly and arithmetically. I had assumed that using the explicit formula would have a more efficient time complexity, but the use of Binet's formulation was not as simple to implement. I had decided to implement this function by storing the previous two numbers needed to calculate the next fibonnaci number. I then delgated the functionality to the find_next _fibonacci() function
    
	    def check_Fibonacci(val):
		    return find_next_Fibonacci(val) == val

2. If an entered number is not in the Fibonacci Sequence, indicate the next larger number in the Fibonacci Sequence closest to the given number.
    > This function similar to function 1 was itterate through the fibonacci sequence and is used in the check_Fibonacci() function. If it comes across a fibonacci number larger than the number it returns that Fibonacci number. Or it will return the number entered signifying that the number entered was a Fibonacci number. My first approach to this function was to delegate the Fibonacci iteration to the 1st function but I discorvered it would have to to work the other way round.
    
		def find_next_Fibonacci(val):
			if val == None:
				val = int(input("\nEnter a # for find_next_Fibonacci()"))
			if val <= 0:
				return 0
			if val <= 1 :
				return 1
			s = [1, 1]
			while(True):
				if (val == (s[0] + s[1])):
					return val
				elif (val < s[1]):
					return s[1]
				else:
					s[1] += s[0]
					s[0] = s[1] - s[0]
	    
3. Check If a number is an integer or not.
    > This function is design determine whether an entered number is an integer. My first approach was to simply check the datatype of the value entered but soon the programing class integer would not work well in determining the actual definition of an integer. As 1.00 and 1 are both integer. So I used the modulo to determine wheather the number is divisible by one. 
    
	    def check_Integer(val):
		    try:
		        return val % 1 == 0
		    except:
		        return False
    
4. Given a series of numbers, check which one of them are in the Fibonacci Sequence or not.
    > The find_Fibonacci() function is supposed to find all the Fibonacci numbers in a set of number. My 1st assumption when approaching this algorithym is that the reurn type would have to be a list. This approach has carrried through to my final version of the function. It loops through the given loop delegating the checking of the namubers to the chack_Fibonacci() function and ensure that there are no repetitions in the returned list. 

		def find_Fibonacci(s):
		    f = []
		    for x in s:
		        if check_Fibonacci(x) and not (x in f):
		            f.append(x)
		    return f
    
5. Check if a given number is a square number or not.
    > The check_Square() function takes in a number determines whether its square is an integer to determine wheather is a square number. In my fist iteration I had caused a reduncy as I used the algorythm present in check_Integer() function. I later modified the code to delegate the checking to the check_Integer() function.

		def check_Square(val):
		    if val == None:
		        val = int(input("\nEnter a # for checkSquare()"))
		    if val < 0:
		        return False
		    return check_Integer(val**(0.5))

    
6. Check if a given number is both a square number and in Fibonacci Sequence.
    > This function is a combination of check_Square() and check_Fibonacci() functions. In its implementation I return a boolean expression.

		def check_Fib_Sqr(val):
		    return check_Fibonacci(val) and check_Square(val)
    
7. Converts a given percentage into a grading remark.
    > This function ranks a given mark based preditermined ranges and returns a generic string text based on the categgory of the mark.
    
	    def get_Grade(p):
		    if p > 100 or p < 0:
		        return "-"
		    elif p > 91:
		        return "Brillient"
		    elif p >= 80:
		        return "Excellent"
		    elif p >= 70:
		        return "Great"
		    elif p >= 20:
		        return "Good"
		    else:
		        return "you can do better"
    
8. Removes all the non square numbers from a files
	> The remove_Squares() function read through a given text and removes all values in the text file that are not perfect squares. It does this by reading the contents of the file filtering out everything but perfect square numbers and overwrighting the files data with the list of square numbers. I chose to implement this function because it encorperated both reading and writing and was suitable to the theme of the functions.  
	
		def remove_Squares(path):
		    i = []
		    o = []
		    with open(path, "r") as ifile:
		        for l in ifile.readlines():
		            i.append(float(l))
		        for x in i:
		            if check_Square(x):
		                o.append(str(int(x)))
		                
		    with open(path, "w") as ofile:
		        for oe in o:
		            ofile.write(str(oe) + "\n")

***
## Modularity
### Running Program

I ran my test code in an Ubuntu operation system, but the use of the pragram is translatable to a Windows environment. In order to run the test one will need a functioning version of Python with unittesting module available for use. One must also have the dependancies of the file in order all the python files should be in one direcory. 

To run the code type "python3 mathlib.py" into terminal 

	nhlonipho@nhlonipho-VirtualBox:~$ cd Documents\\...\src
	nhlonipho@nhlonipho-VirtualBox:~$\...\src>python3 mathlib.py
	a(#) = check_Fibonacci(#)
	b() = find_next_Fibonacci(#)
	c(#) = check_Integer(#)
	d[#,...] = find_Fibonacci([#,...])
	e = check_Square()
	f(#) = check_Fib_Sqr(#)
	g(#) = get_Grade(#)
	q = quit
	>


If on a windows system type "python mathlib.py":

	Microsoft Windows [Version 10.0.22621.1413]
	(c) Microsoft Corporation. All rights reserved.
	C:\Users\nkmar>cd ./C:\Users\...\src
	C:\Users\...\src>python mathlib.py
	a(#) = check_Fibonacci(#)
	b() = find_next_Fibonacci(#)
	c(#) = check_Integer(#)
	d[#,...] = find_Fibonacci([#,...])
	e = check_Square()
	f(#) = check_Fib_Sqr(#)
	g(#) = get_Grade(#)
	q = quit
	>
To use the program enter the desired function with its correct structure. The program will then display the output of function select.

#### CheckList
 - [x] Aren't any repeated code segments
 - [x] Functions don't have more than one purpose
 - [x] Functions don't have control flags as parameters
 - [x] Few functions are dependant on functions from multiple seperate modules
 - [x] Functions do not require unnessacary parameters
 - [x] There are not any non constant global variables

In the implementation of my code I made sure avoid the flaws written in my checklist. I made use of the funcionality that I had defined in other functions to avoid rudundency and made sure that all my functions had singular functionality. I also made sure that made sure my functions didn't have unessacary parameters or global variables, keeping the maximum parameters below three. Due my code on consisting of two modules coupling was kept to low. This also increased the cohesion of the code.

***
## Testing
The test code makes use of the unittest module to test all of the production code. I chose to use this module because it allowed to use a number of enhanced assertion functions, delegating the assertion to this module allowed for a higher level simplicity and modularity, and resulted in the overall reduction of the total code.
### White Box Testing
#### check_Square
This is a simple function that mainly consists of one flow control statement. That being the if statement. This simplicity and use of white box compatible control flows makes it a suitable function to test with white box testing.
<table>
  <thead>
    <tr>
      <th>Boundary</th>
      <th>Data</th>
      <th>Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Enters the if</td><td>-1</td><td>False</td>
    </tr>
    <tr>
      <td rowspan=2>Doesn't enter if</td><td>3</td><td>False</td>
    </tr>
    <tr>
      <td>4</td><td>True</td>
    </tr>
  </tbody>
</table>


#### find_next_Fibonacci
This is suitable for white box testing because it makes use of while loops and if statements, which means that white box test cases can work well on this particular function. This function can also accept input from the input stream which is another reason why it useful to white box test fixtures.
|Path|Test Data|Result|
|--|--|--|
|Enters if| 2 | 2|
|Doesn't enter if| 9 | 13|

***

### Black Box Testing
#### check_Fibonacci
>parameters = (val : Integer)

The function check_Fibonacci returns a boolean expression which is suitable for testing with Equivelence Partitioning. Although the I/O can be displayed as having boundaries the function would have infinite boundaries which is why a BVA wouldn't be useful

|Category|I|O|
|--|--|--|
|val < 0|-1|False|
|val > 0 & not Fib|7|False|
|val >= 0 & Fib|1|True|

#### check_Integer
>parameters = (val : Integer)

This function has a binary set of outputs which is suitable for testing with Equivelence Partitioning. Although the I/O can be displayed as having boundaries the function would have infinite boundaries which is why a BVA wouldn't be useful

|Category|I|O|
|--|--|--|
|val ∈ Z|-1|True|
|val ∉ Z|7.5|False|

#### find_Fibonacci
>parameters = (s : Integer)

For the find_Fibonacci function, the function takes in a set and returns the set of Fibonacci numbers that intersect with the set given. This means that it suitable to use Equivilence Partitioning as a test method 

|Category|I|O|
|--|--|--|
|set s ∩ ∅|[]|[]|
|set s doesn't ∩ with set Fib #|[-1, 4, 6, 7]|[]|
|set s ∩ with set Fib #|[-1, 0, 4, 3, 6, 1, 7]|[0, 3, 1]|

#### check_Fib_Sqr
>parameters = (val : Integer)

I used Equivalence Partitioning to  test this function. I chose to use this because of the small set of possible answers which could be translated to a trace table and EP test cases 

|Category|I|O|
|--|--|--|
|val is square number & val > 0|4|True|
|val is not square number & val > 0|3|False|
|val < 0|-2|False|

#### remove_Squares

For the remove_Squares function, the function takes in a set and returns the set of remove_Squares that intersect with the set given. This means that it suitable to use Equivilence Partitioning as a test method 

|Category|I|O|
|--|--|--|
|set s ∩ ∅|[]|[]|
|set s doesn't ∩ with set Square #|[10, 8, 7, 6, 5]|[]|
|set s ∩ with set Square #|[10, 4, 9, 6, 16]|[4, 9, 16]

#### getGrade
I used Boundary Value analysis to assess this function. I chose this method of testing because the function returns based on percentage ranges that form boundaries with each other.
<table>
	<thead>
		<tr>
			<th>Boundary</th><th>Data</th><th>Result</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan=2>-/Brillient</td><td>100.0001</td><td>getGrade()="-"</td>
		</tr>
		<tr>
			<td>100</td><td>getGrade()="Brillient"</td>
		</tr>
		<tr>
			<td rowspan=2>Brillient/Excellent</td><td>91.0001</td><td>getGrade()="Brillient"</td>
		</tr>
		<tr>
			<td>91</td><td>getGrade()="Excellent"</td>
		</tr>
		<tr>
			<td rowspan=2>Excellent/Great</td><td>80</td><td>getGrade()="Excellent"</td>
		</tr>
		<tr>
			<td>79.9999</td><td>getGrade()="Great"</td>
		</tr>
		<tr>
			<td rowspan=2>Great/Good</td><td>70</td><td>getGrade()="Great"</td>
		</tr>
		<tr>
			<td>69.9999</td><td>getGrade()="Good"</td>
		</tr>
		<tr>
			<td rowspan=2>Good/you can do better</td><td>20</td><td>getGrade()="Good"</td>
		</tr>
		<tr>
			<td>19.9999</td><td>getGrade()="you can do better"</td>
		</tr>
		<tr>
			<td rowspan=2>you can do better/-</td><td>0</td><td>getGrade()="you can do better"</td>
		</tr>
		<tr>
			<td>-0.0001</td><td>getGrade()="-"</td>
		</tr>
	</tbody>
</table>

***
## Test implementation and execution
### Running Program

I ran my test code in an Ubuntu operation system, but the use of the pragram is translatable to a Windows environment. In order to run the test one will need a functioning version of Python with unittesting module available for use. One must also have the dependancies of the file in order all the python files should be in one direcory. 

To run the code type "python3 -m unittest" into terminal 

	nhlonipho@nhlonipho-VirtualBox:~$ cd Documents\\...\src
	nhlonipho@nhlonipho-VirtualBox:~$\...\src>python3 -m unittest
	......
	Enter a # for checkSquare() 
	Enter a # for checkSquare()
	Enter a # for checkSquare().
	Enter a # for find_next_Fibonacci()
	Enter a # for find_next_Fibonacci().
	----------------------------------------------------------------------
	Ran 8 tests in 0.006s
	 
	OK


If on a windows system type "python -m unittest":

	Microsoft Windows [Version 10.0.22621.1413]
	(c) Microsoft Corporation. All rights reserved.
	C:\Users\nkmar>cd ./C:\Users\...\src
	C:\Users\...\src>python -m unittest
	......
	Enter a # for checkSquare() 
	Enter a # for checkSquare()
	Enter a # for checkSquare().
	Enter a # for find_next_Fibonacci()
	Enter a # for find_next_Fibonacci().
	----------------------------------------------------------------------
	Ran 8 tests in 0.006s
	 
	OK
### Test Results
In my versions, I had no problem with my test code. This is because I integrated my function into my test code sequencially. The use of the code in examples; this helped in testing th basic functionality of the function. For each of the 8 test, all eight were successful. After complete a particular function I would still come back to revise my code based on the new code added in other function. This allowed to monitor the overall modularity of the code. My improvements to the code did cause any change in the tests. I had also change my test cases to purpusefully cause an error, this was to verify whether the unittesting module was engaging the code properly.

|Module name|BB test design(EP)|BB test design ( BVA)|WB test design|EP test code (implement ed/ run)|BVA test code (implemented /run)|White-Box testing (implemente d/run)|
|--|--|--|--|--|--|--|
|check_Fibonacci|done|not|not|done|not|not|
|find_next_Fibonacci|not|not|done|not|not|done|
|check_Integer|done|not|not|done|not|not|
|test_EP_find_Fibonacci|done|not|not|done|not|not|
|check_Square|not|not|done|not|not|done|
|check_Fib_Sq|done|not|not|done|not|not|
|check_Square|not|done|not|not|done|not|
|remove_Squares|done|not|not|done|not|not|
***
## Version Control
### Commit logs
	0000000000000000000000000000000000000000 ce4a6bf6a51783765d603700ea62ee0daed6459d Nhlonipho <nkmarwala@gmail.com> 1679404980 +0400	commit (initial): initial commit
	ce4a6bf6a51783765d603700ea62ee0daed6459d 3398c8aa370632b0ea1da39f1984cbb2f2e58311 Nhlonipho <nkmarwala@gmail.com> 1679408728 +0400	commit: succesfully implemented functions {a, b, and c}
	3398c8aa370632b0ea1da39f1984cbb2f2e58311 6824357177f9fd06dc1006d9a7d0c154d1f62436 Nhlonipho <nkmarwala@gmail.com> 1679411978 +0400	commit: succesfully implemented functions {d, e, f}
	6824357177f9fd06dc1006d9a7d0c154d1f62436 552aab75245e5f64459d6900e38a308024aa0001 Nhlonipho <nkmarwala@gmail.com> 1680450860 +0400	commit: get grade function completed
	552aab75245e5f64459d6900e38a308024aa0001 3808b66458f014189efb77f2060b38698df01199 Nhlonipho <nkmarwala@gmail.com> 1680452278 +0400	commit: tting up loose ends
	3808b66458f014189efb77f2060b38698df01199 b429f8475745531ce1f3719630f7fc0d9a5f9a34 Nhlonipho <nkmarwala@gmail.com> 1680452913 +0400	commit: making comments
	b429f8475745531ce1f3719630f7fc0d9a5f9a34 b429f8475745531ce1f3719630f7fc0d9a5f9a34 Nhlonipho <nkmarwala@gmail.com> 1680601074 +0400	checkout: moving from master to EPtesting
	b429f8475745531ce1f3719630f7fc0d9a5f9a34 8007268f3e2a05dcf129059499b0632dd7716c1f Nhlonipho <nkmarwala@gmail.com> 1680624391 +0400	commit: Equivilance Partitioning testing complete
	8007268f3e2a05dcf129059499b0632dd7716c1f b429f8475745531ce1f3719630f7fc0d9a5f9a34 Nhlonipho <nkmarwala@gmail.com> 1680624795 +0400	checkout: moving from EPtesting to master
	b429f8475745531ce1f3719630f7fc0d9a5f9a34 f541affa7746e53d4f7441387ffd8d1039f3b215 Nhlonipho <nkmarwala@gmail.com> 1680629398 +0400	commit: edits
	f541affa7746e53d4f7441387ffd8d1039f3b215 33afe75cc63e560af4af007392110fed9776d057 Nhlonipho <nkmarwala@gmail.com> 1680629645 +0400	commit: creating test file
	33afe75cc63e560af4af007392110fed9776d057 8007268f3e2a05dcf129059499b0632dd7716c1f Nhlonipho <nkmarwala@gmail.com> 1680629653 +0400	checkout: moving from master to EPtesting
	8007268f3e2a05dcf129059499b0632dd7716c1f 33afe75cc63e560af4af007392110fed9776d057 Nhlonipho <nkmarwala@gmail.com> 1680630635 +0400	checkout: moving from EPtesting to master
	33afe75cc63e560af4af007392110fed9776d057 717d9a67a595655165a32b614bbd38fd5f07c3b4 Nhlonipho <nkmarwala@gmail.com> 1680642593 +0400	commit: White Box testing completed
	717d9a67a595655165a32b614bbd38fd5f07c3b4 2b81d7fdd9e1a0dfd20c73b74c7cdcef61c1563e Nhlonipho <nkmarwala@gmail.com> 1680643115 +0400	commit (merge): merge fixxes for EPtesting and WBtesting
	2b81d7fdd9e1a0dfd20c73b74c7cdcef61c1563e 8007268f3e2a05dcf129059499b0632dd7716c1f Nhlonipho <nkmarwala@gmail.com> 1680643163 +0400	checkout: moving from master to EPtesting
	8007268f3e2a05dcf129059499b0632dd7716c1f 2b81d7fdd9e1a0dfd20c73b74c7cdcef61c1563e Nhlonipho <nkmarwala@gmail.com> 1680643342 +0400	checkout: moving from EPtesting to master
	2b81d7fdd9e1a0dfd20c73b74c7cdcef61c1563e de25ec12bb7a1c04e5d5f85abf42bde80b0987f6 Nhlonipho <nkmarwala@gmail.com> 1680644358 +0400	commit: making running proccess clearer
	de25ec12bb7a1c04e5d5f85abf42bde80b0987f6 3e38c9144a84fbd06b099c14ee9a76ea476b573a Nhlonipho <nkmarwala@gmail.com> 1680644558 +0400	commit: finalising EP & WB
	3e38c9144a84fbd06b099c14ee9a76ea476b573a b429f8475745531ce1f3719630f7fc0d9a5f9a34 Nhlonipho <nkmarwala@gmail.com> 1680644620 +0400	checkout: moving from master to BVAtesting
	b429f8475745531ce1f3719630f7fc0d9a5f9a34 19dc2223940d62f2ecfa7325636d742a9cb1586a Nhlonipho <nkmarwala@gmail.com> 1680645891 +0400	commit: Boundary Value Analysis testing complete
	19dc2223940d62f2ecfa7325636d742a9cb1586a 10b12e356243c97ac673ba6cd787eb82ed7e9af6 Nhlonipho <nkmarwala@gmail.com> 1680646082 +0400	commit (merge): Integrating BVA into main
	10b12e356243c97ac673ba6cd787eb82ed7e9af6 7e2bd4d962287190c74f739e4a2ab4f7ba72cf3c Nhlonipho <nkmarwala@gmail.com> 1680685930 +0400	commit: finalise program
	7e2bd4d962287190c74f739e4a2ab4f7ba72cf3c 3e38c9144a84fbd06b099c14ee9a76ea476b573a Nhlonipho <nkmarwala@gmail.com> 1680685949 +0400	checkout: moving from BVAtesting to master
	3e38c9144a84fbd06b099c14ee9a76ea476b573a 7e2bd4d962287190c74f739e4a2ab4f7ba72cf3c Nhlonipho <nkmarwala@gmail.com> 1680686039 +0400	merge BVAtesting: Fast-forward
	7e2bd4d962287190c74f739e4a2ab4f7ba72cf3c 488a7e0b65c8483f316b483ecb0119dcdbd46f32 Nhlonipho <nkmarwala@gmail.com> 1680686316 +0400	commit: Assignment code completed
	488a7e0b65c8483f316b483ecb0119dcdbd46f32 709f3c0a93c51eb3027891d60ed720507e162080 Nhlonipho <nkmarwala@gmail.com> 1680717702 +0400	commit: last commit
### Graph of commits
	* commit 709f3c0a93c51eb3027891d60ed720507e162080 (HEAD -> master)
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Wed Apr 5 22:01:42 2023 +0400
	|
	|     last commit
	|
	* commit 488a7e0b65c8483f316b483ecb0119dcdbd46f32
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Wed Apr 5 13:18:36 2023 +0400
	|
	|     Assignment code completed
	|
	* commit 7e2bd4d962287190c74f739e4a2ab4f7ba72cf3c
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Wed Apr 5 13:12:10 2023 +0400
	|
	|     finalise program
	|
	*   commit 10b12e356243c97ac673ba6cd787eb82ed7e9af6
	|\  Merge: 19dc222 3e38c91
	| | Author: Nhlonipho <nkmarwala@gmail.com>
	| | Date:   Wed Apr 5 02:08:02 2023 +0400
	| |
	| |     Integrating BVA into main
	| |
	| * commit 3e38c9144a84fbd06b099c14ee9a76ea476b573a
	| | Author: Nhlonipho <nkmarwala@gmail.com>
	| | Date:   Wed Apr 5 01:42:38 2023 +0400
	| |
	| |     finalising EP & WB
	| |
	| * commit de25ec12bb7a1c04e5d5f85abf42bde80b0987f6
	| | Author: Nhlonipho <nkmarwala@gmail.com>
	| | Date:   Wed Apr 5 01:39:18 2023 +0400
	| |
	| |     making running proccess clearer
	| |
	| *   commit 2b81d7fdd9e1a0dfd20c73b74c7cdcef61c1563e
	| |\  Merge: 717d9a6 8007268
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Wed Apr 5 01:18:35 2023 +0400
	| | |
	| | |     merge fixxes for EPtesting and WBtesting
	| | |
	| | * commit 8007268f3e2a05dcf129059499b0632dd7716c1f
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Tue Apr 4 20:06:31 2023 +0400
	| | |
	| | |     Equivilance Partitioning testing complete
	| | |
	| * | commit 717d9a67a595655165a32b614bbd38fd5f07c3b4
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Wed Apr 5 01:09:53 2023 +0400
	| | |
	| | |     White Box testing completed
	| | |
	| * | commit 33afe75cc63e560af4af007392110fed9776d057
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Tue Apr 4 21:34:05 2023 +0400
	| | |
	| | |     creating test file
	| | |
	| * | commit f541affa7746e53d4f7441387ffd8d1039f3b215
	| |/  Author: Nhlonipho <nkmarwala@gmail.com>
	| |   Date:   Tue Apr 4 21:29:58 2023 +0400
	| |
	| |       edits
	| |
	* | commit 19dc2223940d62f2ecfa7325636d742a9cb1586a
	|/  Author: Nhlonipho <nkmarwala@gmail.com>
	|   Date:   Wed Apr 5 02:04:51 2023 +0400
	|
	|       Boundary Value Analysis testing complete
	|
	* commit b429f8475745531ce1f3719630f7fc0d9a5f9a34
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 20:28:33 2023 +0400
	|
	|     making comments
	|
	* commit 3808b66458f014189efb77f2060b38698df01199
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 20:17:58 2023 +0400
	|
	|     tting up loose ends
	|
	* commit 552aab75245e5f64459d6900e38a308024aa0001
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 19:54:20 2023 +0400
	|
	|     get grade function completed
	|
	* commit 6824357177f9fd06dc1006d9a7d0c154d1f62436
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Tue Mar 21 19:19:38 2023 +0400
	|
	|     succesfully implemented functions {d, e, f}
	|
	* commit 3398c8aa370632b0ea1da39f1984cbb2f2e58311
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Tue Mar 21 18:25:28 2023 +0400
	|
	|     succesfully implemented functions {a, b, and c}
	|
	* commit ce4a6bf6a51783765d603700ea62ee0daed6459d
	  Author: Nhlonipho <nkmarwala@gmail.com>
	  Date:   Tue Mar 21 17:23:00 2023 +0400

	      initial commit
	(END)
	| * | commit 717d9a67a595655165a32b614bbd38fd5f07c3b4
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Wed Apr 5 01:09:53 2023 +0400
	| | |
	| | |     White Box testing completed
	| | |
	| * | commit 33afe75cc63e560af4af007392110fed9776d057
	| | | Author: Nhlonipho <nkmarwala@gmail.com>
	| | | Date:   Tue Apr 4 21:34:05 2023 +0400
	| | |
	| | |     creating test file
	| | |
	| * | commit f541affa7746e53d4f7441387ffd8d1039f3b215
	| |/  Author: Nhlonipho <nkmarwala@gmail.com>
	| |   Date:   Tue Apr 4 21:29:58 2023 +0400
	| |
	| |       edits
	| |
	* | commit 19dc2223940d62f2ecfa7325636d742a9cb1586a
	|/  Author: Nhlonipho <nkmarwala@gmail.com>
	|   Date:   Wed Apr 5 02:04:51 2023 +0400
	|
	|       Boundary Value Analysis testing complete
	|
	* commit b429f8475745531ce1f3719630f7fc0d9a5f9a34
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 20:28:33 2023 +0400
	|
	|     making comments
	|
	* commit 3808b66458f014189efb77f2060b38698df01199
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 20:17:58 2023 +0400
	|
	|     tting up loose ends
	|
	* commit 552aab75245e5f64459d6900e38a308024aa0001
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Sun Apr 2 19:54:20 2023 +0400
	|
	|     get grade function completed
	|
	* commit 6824357177f9fd06dc1006d9a7d0c154d1f62436
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Tue Mar 21 19:19:38 2023 +0400
	|
	|     succesfully implemented functions {d, e, f}
	|
	* commit 3398c8aa370632b0ea1da39f1984cbb2f2e58311
	| Author: Nhlonipho <nkmarwala@gmail.com>
	| Date:   Tue Mar 21 18:25:28 2023 +0400
	|
	|     succesfully implemented functions {a, b, and c}
	|
	* commit ce4a6bf6a51783765d603700ea62ee0daed6459d
	  Author: Nhlonipho <nkmarwala@gmail.com>
	  Date:   Tue Mar 21 17:23:00 2023 +0400

	      initial commit
	~
	(END)
***
## Ethics
The production of a math module can have some ethical concernes and in a few scenarios, the unethical developement of the program could lead to desasters. If proper testing was not completed the system might fail when in the user's possession. This a physical and proffessional ethical concern. This could lead to a loss pecuniary value and reputation of both developer and user. This could also indirectly psychological effects on the user such as stress and worry due to delay, loss of productivity, and/or a damaged reputation. For example if the functions in this module was one used in a life support system and an error in the code caused an incorrect output the developer might indirectly be responsible for the health complication of the patients using that life support system. 
***
## Reflection
This assignment helped in developing my familiarity with version control. Getting to use white box testing made my undersanding of End of File errors more proficient and how simulating input can complicate the production code despite it not depend on the test code where input simulation occurs. The project also improve in assessing where to implement whic kind of testing. It showed me the usefulnes of git commits and version control as it is easier to roll back semantic errors.

The project definately assisted in developing fundemental skills for any future work in software developement. A few ways I would improve my code in the future would be to clean the menu code in the main function and to incorperate multiple testing methods for functions like the find_next_Fibonacci() function. 
