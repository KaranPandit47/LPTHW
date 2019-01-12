## Python Basics
Reference :  [Python-The Big Picture](https://app.pluralsight.com/library/courses/python-big-picture/table-of-contents)
  **Introduction**
 **What is Python ?**
 - High Level Language
 - Open Source
 - Dynamic Type Checking : Code is not compiled but interpreted at Run-time
 - Multi-paradigm : Supports both object-oriented and structure-oriented programming
 - Created by Guido Van Rossum in 1991

**Python Applications**
- Linux Scripting and Administration
	- Reading and Writing Files
	- Monitor processes running on a system
- Web Development
	- API development: **Flask**, Bottle Pyramid
	- Websites: **Django**, web2py
	- WebApps: Plone, django-cms
- Application Scripting
	- Blender ( 3-D modelling)
- Data Science
	- Big Data , Machine Learning

**First Steps**
1. Install Python : www.python.org
2. Python REPL : Read Evaluate Print Loop
3. pip : Install 3rd party libraries
4. IPython: Robust Interactive shell

## Python Getting Started
Reference : [Python: Getting Started](https://app.pluralsight.com/library/courses/python-getting-started/table-of-contents)
Reference:  [Python Fundamentals](https://app.pluralsight.com/library/courses/python-fundamentals/table-of-contents)
 - Check if python is installed
	```
	python --version
	```

|Statements| Description  |
|--|--|
|Integer and Floats| answer = 42 ; pi = 3.14159 ; **int(pi)** = 3 ; **float(answer)** = 42.0|
|Strings|'Hello World' = "Hello World" = """Hello World"""; |
||``"hello".capitalize() = "Hello"``|
||``"hello".replace('e','a') = "hallo"``|	
||``"hello".isalpha() = True``|
||``"123".isdigit() = True``|
||``"some,csv,values".split(",") = ["some","csv","values"]``|
||``print("Nice to meet you {0}".format(name)) print(f"Nice to meet you {name}") ``|
|Boolean and None| True = 1; False = 0; Aliens_found = None|

 - **if statement**
	```python
	number = 25
	if number == 25:
		print("Number is 25)
	else:
		print("Number is not 25)
	
	#Ternary If Statement
	a = 1
	b = 2
	"bigger" if a > b else "smaller"
	```
 - **Lists**
	```python
	# Empty List
	student_names = []
	student_names = ["Mark","Katarina", "Jessica"]
	student_names[0] == "Mark"
	student_names[-1] == "Jessica"
	student_names.append("Homer")
	"Mark" in student_names == True 
	
	# How many elements in list
	len(student_names) == 4
	
	# Delete element from list and shift to left
	del student_names[2] # Remove Jessica
	
	# List slicing
	student_names[1:] == "Katarina" , "Homer"
	```
 - **Loops**
	```python
	#Print all elemnts of a Lists using Loops
	for name in student_names:
		print("Name is {0}".format(name))
	
	# Range Function
	for index in range(x,y,z) #x=start, y=end, z=increment by
	
	# While Loop
	x = 10
		while x <= 10:
			print("Count is {0}".format(x))
			x += 1
	```
- **Dictionaries**
	```python
	student = {
		"name" : "Mark",
		"student_id" : 12345,
		"feedback": None
		}
	student["name"] = "Mark"
	student.keys() = ["name", "student_id", "feedback"]
	student.values() = ["Mark",12345, None]
	```
- **Exceptions**
	```python
	try:
		last_name = student["last_name"]
	except KeyError:
		print("Error occured")
	except TypeError:
		print("Type error")
	except Exception:	# Handles all types of Errors
		print("Unknown Error")
	```
- **Functions**
	```python
	students = []
	# Function returning a value
	def get_students_titlecase():
		student_titlecase = []
		for student in students:
			student_titlecase = students.title()
		return student_titlecase
	
	# Function calling another function
	def print_student_titlecase():
		student_titlecase = get_students_titlecase()
		print(student_titlecase)
	
	# Function accepting arguments with default argument value
	def add_student(name, student_id=332):
		students.append(name)
	
	# Function with variable number of arguments 
	def var_args(name, *args): 		#*args is stored as a list
		print(name)
		print(args)
	
	def var_kwargs(name, **kwargs):		#kwargs stored as dictionary
		print(name)
		print(kwargs["last_name"],kwargs["age"]
		# Function call: 0var_kwargs("Karan",last_name="Pandit",age=18)	
	```
- **Modularity**
	- Special variables in python are represented by double underscores
	- When a modules is imported \_\_name\_\_ evaluates to name of the module
	- When a module is executed as an independent script \_\_name\_\_ evaluates to '\_\_main\__' 
	```python
	# Filename: words.py
	import sys
	from urllib.request import urlopen	# Blank line after import statement	
	
	def fetch_words(url):
	#Doc strings
	"""	Fetch a list of words from URL.
	Args:
		url: A URL to an UTF-8 Text document
	Returns:
		A list of strings containing the words from the document
	""" 
		with urlopen(url) as story:
			story_words = []
			for line in story:
				line_words = line.decode('utf-8').split()
				for word in line_words:
					story_words.append(word)
		return story_words
	
	def print_items(items):
		for item in items:
			print(item)
	
	def main(url):
		words = fetch_words(url)
		print_items(words)
		
	if __name__='__main__':
		main(sys.argv[1])
	```
- **Generator Functions - Yield**
	- Yield acts as a function return value for each iteration within the function
	```python
	def read_file():
		try:
			f = open("student.txt","r")
			for student in read_students(f):
				students.append(student)
		except Exception:
			print("Could not read file")
	
	def read_students(f):
		for line in f
			yield line
	```
- **Lamda Functions**
	- Anonymous functions that do not have a name, 'def' keyword
	- Help save space and time for small functions
	```python
	def double(x):
		return x * 2
	#Equivalent Lamda function
	double = lamda x: x * 2
	```
## Object - oriented programming
- **Class**
	- A logical group of objects and associated attributes and methods
	```python
	# Class name first character should be upper case
	class Student:
		schoolname = "Springfield Elementary" # Class Attribute (Static)
		
		# __init__ is the Constructor for the class
		def __init__(self, name, student_id=332):
			self.name = name    # Instance Attribute
			self.student_id = student_id
			students.append(self)
		
		# Defines what to be done in case object is printed
		# By default print(student) shows memory location where object is stored. __str__ function overrides this behaviour
		def __str__(self):
			return "Student"+ self.name

	class Highschoolstudent(Student): #Inheritance
		schoolname = "Springfield Highschool"	
	```
## Tips and Tricks
- Working with Virtual Environemnts
	- Allow to setup independent python environments for different applications
	- Each of the environments work in isolation
	- Ex. Use django 1.8 for a new application and django 1.1 for legacy application
	- install virtualenv package
	```python
		virtualenv --python=python2.7 pluralsight
		source /home/pythonbo/virtualenv/pluralsight activate
	```
- Debugging Python Code
- Create an Executable File
	- pyinstaller: A package that converts Python code to an executable (.exe) 
		- pip install pyinstaller
		- pyinsaller main.py
			- This creates a number of folders (main, dist) alongwith a main.exe to run the application
		- pyinstaller --onefile main.py
			- This creates a single main.exe file without any sub folders but the file size is large
	- Creating a setup wizard is a better solution then sending an .exe file
		- Download and install inno setup tool




