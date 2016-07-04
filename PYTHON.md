# Simple operators
```
Operation Name			Operator			Explanation
less than				      <					  Less than operator
greater than			    >				  	Greater than operator
less than or equal		<=					Less than or equal to operator
greater than or equal	>=					Greater than or equal to operator
equal					        ==					Equality operator
not equal			        !=					Not equal operator
logical and			    	and					Both operands True for result to be True
logical or			      or					One or the other operand is True for the result to be True
logical not				    not					Negates the truth value, False becomes True, True becomes False
```

# Python list
```
[1,2,3,4,True,"shi"]

Operation Name			Operator			Explanation
indexing				      [ ]					Access an element of a sequence
concatenation			     +					Combine sequences together
repetition				     *					Concatenate a repeated number of times
membership				    in					Ask whether an item is in a sequence
length					      len					Ask the number of items in the sequence
slicing					    [ 1:3 ]				Extract a part of a sequence (including index 1, 2 not 3)

Methods Provided by Lists in Python
Method 					Name						        Use	Explanation
append					alist.append(item)			Adds a new item to the end of a list
insert					alist.insert(i,item)		Inserts an item at the ith position in a list
pop						  alist.pop()					    Removes and returns the last item in a list
pop						  alist.pop(i)				    Removes and returns the ith item in a list
sort					  alist.sort()				    Modifies a list to be sorted
reverse					alist.reverse()				  Modifies a list to be in reverse order
del						  del alist[i]				    Deletes the item in the ith position
index					  alist.index(item)			  Returns the index of the first occurrence of item
count					  alist.count(item)			  Returns the number of occurrences of item
remove					alist.remove(item)			Removes the first occurrence of item

list(range(5,10,2))
[5, 7, 9]
range(10) -> range(0, 10) -> 0,1,2,3,4,5,6,7,8,9
```

#String is a collection sequence as well
```
Methods Provided by Strings in Python
Method 					Name		      				Use	Explanation
center					astring.center(w)			Returns a string centered in a field of size w
count					  astring.count(item)		Returns the number of occurrences of item in the string
ljust					  astring.ljust(w)			Returns a string left-justified in a field of size w
lower					  astring.lower()				Returns a string in all lowercase
rjust					  astring.rjust(w)			Returns a string right-justified in a field of size w
find					  astring.find(item)		Returns the index of the first occurrence of item
split					 astring.split(schar)		Splits a string into substrings at schar
```

#List is mutable, but String, tuple, set is immutable
```
myTuple = (2,True,4.96)
mySet = {3,6,"cat",4.5,False}   (set() represents empty set; set does not allow duplicate and it is not sequential)

Operations on a Set in Python
Operation Name			Operator					  Explanation
membership				    in							  Set membership
length					      len							  Returns the cardinality of the set
|						      aset | otherset				Returns a new set with all elements from both sets
&						      aset & otherset				Returns a new set with only those elements common to both sets
-						      aset - otherset				Returns a new set with all items from the first set not in second
<=						    aset <= otherset			Asks whether all elements of the first set are in the second

Methods Provided by Sets in Python
Method Name				  Use							             Explanation
union					  aset.union(otherset)		         Returns a new set with all elements from both sets
intersection	  aset.intersection(otherset)	     Returns a new set with only those elements common to both sets
difference			aset.difference(otherset)	       Returns a new set with all items from first set not in second
issubset				aset.issubset(otherset)		       Asks whether all elements of one set are in the other
add						  aset.add(item)				           Adds item to the set
remove					aset.remove(item)			           Removes item from the set
pop						  aset.pop()					             Removes an arbitrary element from the set
clear					  aset.clear()				             Removes all elements from the set
```

#Dictionary
```
capitals = {'Iowa':'DesMoines','Wisconsin':'Madison'}
>>> phoneext.keys()
dict_keys(['brad', 'david'])
>>> list(phoneext.keys())
['brad', 'david']

Operators Provided by Dictionaries in Python
Operator				Use							Explanation
[]						myDict[k]					Returns the value associated with k, otherwise its an error
in						key in adict			Returns True if key is in the dictionary, False otherwise
del						del adict[key]		Removes the entry from the dictionary

Methods Provided by Dictionaries in Python
Method 					Name						  Use	Explanation
keys					adict.keys()				Returns the keys of the dictionary in a dict_keys object
values				adict.values()			Returns the values of the dictionary in a dict_values object
items					adict.items()				Returns the key-value pairs in a dict_items object
get						adict.get(k)				Returns the value associated with k, None otherwise
get						adict.get(k,alt)		Returns the value associated with k, alt otherwise
```

# Python input
```
aName = input('Please enter your name: ')
sradius = input("Please enter the radius of the circle ")
radius = float(sradius)

>>> print("Hello","World")
Hello World
>>> print("Hello","World", sep="***")
Hello***World
>>> print("Hello","World", end="***")
Hello World***>>>

String Formatting Conversion Characters
Character	Output Format
d, i		Integer
u			  Unsigned integer
f			  Floating point as m.ddddd
e			  Floating point as m.ddddde+/-xx
E			  Floating point as m.dddddE+/-xx
g			  Use %e for exponents less than −4−4 or greater than +5+5, otherwise use %f
c			  Single character
s			  String, or any Python data object that can be converted to a string by using the str function.
%			  Insert a literal % character

Additional formatting options
Modifier		Example				Description
number			%20d				  Put the value in a field width of 20
-						%-20d				  Put the value in a field 20 characters wide, left-justified
+						%+20d				  Put the value in a field 20 characters wide, right-justified
0						%020d				  Put the value in a field 20 characters wide, fill in with leading zeros.
.						%20.2f				Put the value in a field 20 characters wide with 2 characters to the right of the decimal point.
(name)			%(name)d			Get the value from the supplied dictionary using name as the key.

>>> print("The %(item)s costs %(cost)7.1f cents"%itemdict)
The banana costs    24.0 cents
>>> print("%s is %d years old." % (aName, age))
```

#Control Flow
```
>>> counter = 1
>>> while counter <= 5:
...     print("Hello, world")
...     counter = counter + 1

>>> for item in [1,3,6,2,5]:
...    print(item)

>>> for item in range(5):
...    print(item**2)

if score >= 90:
   print('A')
elif score >=80: 60:
   print('D')
else:
   print('F')

List comprehension
>>> sqlist=[x*x for x in range(1,11) if x%2 != 0]
>>> sqlist
[1, 9, 25, 49, 81]

try:
	******
except:
	raise RuntimeError("You can't use a negative number")

def function_name(arguments):
	***********

class Class_Name:
    def __init__(self,arg1,arg2,...):
 	  def __str__(self):
 	  def __add__(self, other_obj):
```

#Inheritance
```
 class Parent_Class:
  	def __init__(self,....):

 class Child_Class(Parent_Class):
  	def __init__(self,....):
    		Parent_Class.__init__(self,....)

if __name__ == '__main__':
```
