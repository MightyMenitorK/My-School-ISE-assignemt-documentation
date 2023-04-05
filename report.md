
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
    
    

2. If an entered number is not in the Fibonacci Sequence, indicate the next larger number in the Fibonacci Sequence closest to the given number.
    > This function similar to function 1 was itterate through the fibonacci sequence and is used in the check_Fibonacci() function. If it comes across a fibonacci number larger than the number it returns that Fibonacci number. Or it will return the number entered signifying that the number entered was a Fibonacci number. My first approach to this function was to delegate the Fibonacci iteration to the 1st function but I discorvered it would have to to work the other way round.
    
3. Check If a number is an integer or not.
    > This function is design determine whether an entered number is an integer. My first approach was to simply check the datatype of the value entered but soon the programing class integer would not work well in determining the actual definition of an integer. As 1.00 and 1 are both integer. So I used the modulo to determine wheather the number is divisible by one. 
    
4. Given a series of numbers, check which one of them are in the Fibonacci Sequence or not.
    > The find_Fibonacci() function is supposed to find all the Fibonacci numbers in a set of number. My 1st assumption when approaching this algorithym is that the reurn type would have to be a list. This approach has carrried through to my final version of the function. It loops through the given loop delegating the checking of the namubers to the chack_Fibonacci() function and ensure that there are no repetitions in the returned list. 
    
5. Check if a given number is a square number or not.
    > The check_Square() function takes in a number determines whether its square is an integer to determine wheather is a square number. In my fist iteration I had caused a reduncy as I used the algorythm present in check_Integer() function. I later modified the code to delegate the checking to the check_Integer() function.
    
6. Check if a given number is both a square number and in Fibonacci Sequence.
    > This function is a combination of check_Square() and check_Fibonacci() functions. In its implementation I return a boolean expression.
    
7. Converts a given percentage into a grading remark.
    > This function ranks a given mark based preditermined ranges and returns a generic string text based on the categgory of the mark.
    
8. Removes all the non square numbers from a files
	> The remove_Squares() function read through a given text and removes all values in the text file that are not perfect squares. It does this by reading the contents of the file filtering out everything but perfect square numbers and overwrighting the files data with the list of square numbers. I chose to implement this function because it encorperated both reading and writing and was suitable to the theme of the functions.  

***
## Modularity
### Running Program
I ran my test code in an Ubuntu operation system, but the use of the pragram is translatable to a Windows environment. In order to run the test one will need a functioning version of Python with unittesting module available for use. One must also have the dependancies of the file in order all the python files should be in one direcory. 

To run the code code type python3 -m unittest 
***
## Testing
The test code makes use of the unittest module to test all of the production code. I chose to use this module because it allowed to use a number of enhanced assertion functions, delegating the assertion to this module allowed for a higher level simplicity and modularity, and resulted in the overall reduction of the total code.
### White Box Testing
#### check_Square
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

***
## Version Control

***
## Ethics

***
## Reflection
