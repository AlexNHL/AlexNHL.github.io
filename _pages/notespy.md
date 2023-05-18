---
layout: archive
title: "Notes for Python"
permalink: /notespy/
author_profile: true
redirect_from:
---

Created by Ng Hon Lam.

- Basic commends
    
    ```python
    # Windows PC
    C:\Users\Your Name>python --version
    
    # Mac
    python --version
    
    # Quickstart to run a python file
    C:\Users\Your Name>python name.py
    
    # Python Command Line
    # test a short amount of code
    C:\Users\Your Name>python
    C:\Users\Your Name>py
    # code
    exit()
    ```
    

- Syntax
    - Indentation
        - spaces at the beginning of a code line
        - to indicate a block of code
        
        ```python
        # error if skip the indentation
        # Syntax Error:
        if 5 > 2:
        print("Five is greater than two!")
        
        # number of spaces is free
        if 5 > 2:
         print("Five is greater than two!") 
        if 5 > 2:
                print("Five is greater than two!")
        # Five is greater than two!
        # Five is greater than two!
        
        # use the same number of spaces in the same block of code
        # Syntax Error:
        if 5 > 2:
         print("Five is greater than two!")
                print("Five is greater than two!")
        ```
        
    - Comments
        
        ```python
        # Multi Line Comments
        # not quite as intended, use a multiline string
        # Python will ignore string literals that are not assigned to a variable
        # multiline string (triple quotes)
        """
        This is a comment
        written in
        more than just one line
        """
        print("Hello, World!")
        ```
        
    - Variables
        - Basic
            
            Rules for Python variables:
            
            - must start with a letter or the underscore character
            - cannot start with a number
            - can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
            - case-sensitive (age, Age and AGE are three different variables)
            
            ```python
            # Casting
            # specify the data type of a variable with casting
            x = str(3)    # x will be '3'
            y = int(3)    # y will be 3
            z = float(3)  # z will be 3.0
            
            # data type
            x = 5
            y = "John"
            print(type(x))
            print(type(y))
            # <class 'int'>
            # <class 'str'>
            
            # String : either by using single or double quotes:
            x = "John"
            # is the same as
            x = 'John'
            
            # Case-Sensitive
            a = 4
            A = "Sally"
            # A will not overwrite a
            
            # Illegal variable names:
            2myvar = "John"
            my-var = "John"
            my var = "John"
            
            # assign values to multiple variables
            x, y, z = "Orange", "Banana", "Cherry"
            # number of variables matches the number of values
            
            # One Value to Multiple Variables
            # assign the same value to multiple variables
            x = y = z = "Orange"
            
            # Unpack
            # extract a collection of values in a list, tuple into variables
            fruits = ["apple", "banana", "cherry"]
            x, y, z = fruits
            
            # Output Variables
            print() # function
            
            # output multiple variables, separated by a comma
            x = "Python"
            y = "is"
            z = "awesome"
            print(x,y,z)
            # Python is awesome
            # already added space
            # support different data types
            x = 5
            y = "John"
            print(x, y)
            # 5 John
            
            # + operator to output multiple variables
            x = "Python "
            y = "is "
            z = "awesome"
            print(x + y + z)
            # Python is awesome
            # space character after "Python " and "is "
            
            # + character works as a mathematical operator
            
            # cannot combine a string and a number with the +
            ```
            
        - Global and local variables
            - created outside of a function
            - can be used by everyone, both inside of functions and outside
            
            ```python
            x = "awesome" # Create a variable outside of a function
            def myfunc():
              print("Python is " + x) # use it inside
            myfunc()
            # Python is awesome
            
            # create a variable with the same name inside a function
            # will be local, only be used inside
            # global with same name will remain the orignal value
            x = "awesome"
            
            def myfunc():
              x = "fantastic"
              print("Python is " + x)
            
            myfunc()
            # Python is fantastic
            print("Python is " + x)
            # Python is awesome
            
            global # create a global variable inside a function
            def myfunc():
              global x
              x = "fantastic"
            
            myfunc()
            print("Python is " + x)
            # Python is fantastic
            # x has not been declared outside
            
            # to change a global variable inside a function
            x = "awesome"
            def myfunc():
              global x
              x = "fantastic"
            
            myfunc()
            print("Python is " + x)
            # Python is fantastic
            ```
            
        - Scope
            - variable is only available from inside the region it is created
            
            ```python
            # Local Scope
            # variable created inside a function belongs to the local scope 
            # and can only be used inside that function
            def myfunc():
              x = 300
              print(x)
            myfunc()
            # 300
            # variable x is not available outside the function
            # available for any function inside the function
            
            # Function Inside Function
            # local variable can be accessed from a function within the function
            def myfunc():
              x = 300
              def myinnerfunc():
                print(x)
              myinnerfunc()
            myfunc()
            # 300
            
            # Global Scope
            # variable created in the main body is a global variable
            # belongs to the global scope
            # available from within any scope, global and local
            x = 300
            def myfunc():
              print(x)
            myfunc()
            # 300
            print(x)
            # 300
            
            # Naming Variables
            # operate with the same variable name inside and outside of function
            # treat them as two separate variables
            # one available in the global scope (outside the function)
            # one available in the local scope (inside the function)
            x = 300
            def myfunc():
              x = 200
              print(x)
            myfunc()
            # 200
            print(x)
            # 300
            
            # Global Keyword
            # create global variable, but are stuck in the local scope
            global # makes the variable belongs to the global scope
            def myfunc():
              global x
              x = 300
            myfunc()
            print(x)
            # 300
            
            # make a change to a global variable inside a function
            x = 300
            def myfunc():
              global x
              x = 200
            myfunc()
            print(x)
            # 200
            ```
            

- Types of data types
    - Basic types
        
        
        | Text Type: | str |
        | --- | --- |
        | Numeric Types: | int, float, complex |
        | Sequence Types: | list, tuple, range |
        | Mapping Type: | dict |
        | Set Types: | set, frozenset |
        | Boolean Type: | bool |
        | Binary Types: | bytes, bytearray, memoryview |
        | None Type: | NoneType |
        
        | Collections | ordered | changeable | duplicate members |
        | --- | --- | --- | --- |
        | List | YES | YES | YES |
        | Tuple | YES | NO | YES |
        | Set | NO | NO | NO |
        | Dictionary | YES | YES | NO |
        
        - Casting
            - specify a type on to a variable
            - uses classes to define data types, including its primitive types
            - `int()` - constructs an integer number from an integer literal, a float literal (by removing all decimals), or a string literal (providing the string represents a whole number)
            - `float()` - constructs a float number from an integer literal, a float literal or a string literal (providing the string represents a float or an integer)
            - `str()` - constructs a string from a wide variety of data types, including strings, integer literals and float literals
            
            ```python
            x = int(1)   # x will be 1
            y = int(2.8) # y will be 2
            z = int("3") # z will be 3
            
            x = float(1)     # x will be 1.0
            y = float(2.8)   # y will be 2.8
            z = float("3")   # z will be 3.0
            w = float("4.2") # w will be 4.2
            
            x = str("s1") # x will be 's1'
            y = str(2)    # y will be '2'
            z = str(3.0)  # z will be '3.0'
            ```
            
        
        ```python
        x = "Hello World"	# str	
        
        x = 20	# int	
        x = int(20)
        
        x = 20.5	# float	
        x = float(20.5)
        
        x = 1j	# complex	
        x = complex(1j)
        
        x = ["apple", "banana", "cherry"] #	list	
        x = list(("apple", "banana", "cherry"))
        
        x = ("apple", "banana", "cherry")	# tuple	
        x = tuple(("apple", "banana", "cherry"))
        
        x = range(6) # range	
        
        x = {"name" : "John", "age" : 36}	# dict	
        x = dict(name="John", age=36)
        
        x = {"apple", "banana", "cherry"}	# set	
        x = set(("apple", "banana", "cherry"))
        
        x = frozenset({"apple", "banana", "cherry"}) # frozenset	
        
        x = True # bool	
        x = bool(5)
        
        x = b"Hello" # bytes	
        x = bytes(5)
        
        x = bytearray(5) # bytearray	
        
        x = memoryview(bytes(5)) # memoryview	
        
        x = None # NoneType
        ```
        
    - Numeric
        - `int`: without decimals, of unlimited length
        - `float`: containing one or more decimals
        - `complex`: written with a "j" as the imaginary part
        
        ```python
        # convert to others with int(), float(), and complex()
        
        # scientific numbers with an "e" to indicate the power of 10
        x = 35e3
        y = 35E3
        # x,y are the same
        
        x = 3+5j
        y = 5j
        z = -5j
        
        ```
        
        ```python
        # Random Number (built-in module)
        import random
        
        print(random.randrange(1, 10))
        # random number between 1 and 9
        ```
        
    - String
        - Basic
            - surrounded by either single quotation marks, or double quotation marks
            
            ```python
            # assign multiline string to a variable by using three quotes
            a = """Lorem ipsum dolor sit amet,
            consectetur adipiscing elit,
            sed do eiusmod tempor incididunt
            ut labore et dolore magna aliqua."""
            # or using '''   '''
            # line breaks are inserted at the same position as in the code
            
            # Strings are arrays of bytes representing unicode characters
            # does not have a character data type
            # single character is a string with a length of 1
            
            a = "Hello, World!"
            print(a[1])
            # e
            
            # loop through the characters in a string
            for x in "banana":
              print(x)
            # b
            # a
            # n
            # a
            # n
            # a
            
            len() # to get the length
            a = "Hello, World!"
            print(len(a))
            # 13
            
            in ; not in
            # wheather a certain phrase or character is present in a string
            "sting" in "string"
            
            txt = "The best things in life are free!"
            print("free" in txt)
            # True
            
            txt = "The best things in life are free!"
            if "free" in txt:
              print("Yes, 'free' is present.")
            # Yes, 'free' is present.
            
            txt = "The best things in life are free!"
            print("expensive" not in txt)
            # True
            
            txt = "The best things in life are free!"
            if "expensive" not in txt:
              print("No, 'expensive' is NOT present.")
            # No, 'expensive' is NOT present.
            ```
            
        - Slicing
            - return a part of the string
            
            ```python
            # Slicing, return a part of the string
            # position 2 to position 5 (not included)
            b = "Hello, World!"
            print(b[2:5])
            # llo
            
            # The first character has index 0.
            
            # Slice From the Start
            # the start to position 5 (not included)
            b = "Hello, World!"
            print(b[:5])
            # Hello
            
            # Slice To the End
            # position 2, and all the way to the end
            b = "Hello, World!"
            print(b[2:])
            # llo, World!
            
            # Negative Indexing
            # start the slice from the end of the string
            # From: "o" in "World!" (position -5)
            # To, but not included: "d" in "World!" (position -2)
            b = "Hello, World!"
            # 	     987654321
            print(b[-5:-2])
            # orl
            ```
            
        - Modify
            
            ```python
            # built-in methods
            
            upper() # string in upper case
            a = "Hello, World!"
            print(a.upper())
            # HELLO, WORLD!
            
            lower() # string in lower case
            a = "Hello, World!"
            print(a.lower())
            # hello, world!
            
            strip()
            # removes any whitespace from the beginning or the end
            a = "  Hello, World!  "
            print(a.strip())
            # Hello, World!
            # whitespace in the middle will be remained
            
            replace() # replaces string with another string
            a = "Hello, World!"
            print(a.replace("o", "0"))
            # Hell0, W0rld!
            
            split()
            # returns a list 
            # where text between the specified separator becomes list items
            a = "Hello, World!"
            b = a.split(",")
            print(b)
            # ['Hello', ' World!']
            
            a = "Hello, World!"
            b = a.split("o")
            print(b)
            # ['Hell', ', W', 'rld!']
            # will not include the separator
            
            b = a.split()
            print(b)
            # ['Hello,', 'World!']
            # speparator default to be whitespace
            
            # Concatenation
            # + opeator to combine two strings
            # Merge a with b
            a = "Hello"
            b = "World"
            print(a+b)
            # HelloWorld
            
            # add a space between
            a = "Hello"
            b = "World"
            c = a + " " + b
            print(c)
            # Hello World
            ```
            
        - Format
            
            
            | :< | Left aligns the result (within the available space) |
            | --- | --- |
            | :> | Right aligns the result (within the available space) |
            | :^ | Center aligns the result (within the available space) |
            | := | Places the sign to the left most position |
            | :+ | Use a plus sign to indicate if the result is positive or negative |
            | :- | Use a minus sign for negative values only |
            | :  | Use a space to insert an extra space before positive numbers (and a minus sign before negative numbers) |
            | :, | Use a comma as a thousand separator |
            | :_ | Use a underscore as a thousand separator |
            | :b | Binary format |
            | :c | Converts the value into the corresponding unicode character |
            | :d | Decimal format |
            | :e | Scientific format, with a lower case e |
            | :E | Scientific format, with an upper case E |
            | :f | Fix point number format |
            | :F | Fix point number format, in uppercase format (show inf and nan as INF and NAN) |
            | :g | General format |
            | :G | General format (using a upper case E for scientific notations) |
            | :o | Octal format |
            | :x | Hex format, lower case |
            | :X | Hex format, upper case |
            | :n | Number format |
            | :% | Percentage format |
            
            ```python
            # cannot combine strings and numbers
            age = 36
            txt = "My name is John, I am " + age
            print(txt)
            # TypeError: must be str, not int
            
            format() # to combine them
            # takes the passed arguments, formats them
            # places them in the string where the placeholders {} are
            age = 36
            txt = "My name is John, and I am {}."
            print(txt.format(age))
            # or
            print(txt.format(36))
            # My name is John, and I am 36.
            
            # unlimited number of arguments
            quantity = 3
            itemno = 567
            price = 49.95
            myorder = "I want {} pieces of item {} for {} dollars."
            print(myorder.format(quantity, itemno, price))
            # I want 3 pieces of item 567 for 49.95 dollars.
            
            # index numbers {0} assign the place of arguments
            myorder = "I want to pay {2} dollars for {0} pieces of item {1}."
            print(myorder.format(quantity, itemno, price))
            
            txt1 = "My name is {fname}, I'm {age}".format(fname = "John", age = 36)
            txt2 = "My name is {0}, I'm {1}".format("John",36)
            txt3 = "My name is {}, I'm {}".format("John",36)
            
            txt = "For only {price:.2f} dollars!"
            print(txt.format(price = 49))
            # or 
            txt = "For only {:.2f} dollars!"
            print(txt.format(49))
            # For only 49.00 dollars!
            
            # if name is defined, need to use the variable name
            ```
            
        - Escape character
            - backslash `\` followed by the character that want to insert
            
            | Code | Result |
            | --- | --- |
            | \' | Single Quote |
            | \\ | Backslash |
            | \n | New Line |
            | \r | Carriage Return |
            | \t | Tab |
            | \b | Backspace |
            | \f | Form Feed |
            | \ooo | Octal value |
            | \xhh | Hex value |
            
            ```python
            # example of an illegal character :
            # double quote inside a string that is surrounded by double quotes
            txt = "We are the so-called "Vikings" from the north."
            # error
            
            # escape character \"
            txt = "We are the so-called \"Vikings\" from the north."
            
            txt = "This will insert one \\ (backslash)."
            # This will insert one \ (backslash).
            
            txt = "Hello\tWorld!"
            # Hello   World!
            
            # one character (backspace)
            txt = "Hello \bWorld!"
            # HelloWorld!
            
            txt = "\110\145\154\154\157"
            # Hello
            
            txt = "\x48\x65\x6c\x6c\x6f"
            # Hello
            ```
            
        - Built-in methods
            
            
            | Method | Description |
            | --- | --- |
            | capitalize() | Converts the first character to upper case |
            | casefold() | Converts string into lower case |
            | center() | Returns a centered string |
            | count() | Returns the number of times a specified value occurs in a string |
            | encode() | Returns an encoded version of the string |
            | endswith() | Returns true if the string ends with the specified value |
            | expandtabs() | Sets the tab size of the string |
            | find() | Searches the string for a specified value and returns the position of where it was found |
            | format() | Formats specified values in a string |
            | format_map() | Formats specified values in a string |
            | index() | Searches the string for a specified value and returns the position of where it was found |
            | isalnum() | Returns True if all characters in the string are alphanumeric |
            | isalpha() | Returns True if all characters in the string are in the alphabet |
            | isdecimal() | Returns True if all characters in the string are decimals |
            | isdigit() | Returns True if all characters in the string are digits |
            | isidentifier() | Returns True if the string is an identifier |
            | islower() | Returns True if all characters in the string are lower case |
            | isnumeric() | Returns True if all characters in the string are numeric |
            | isprintable() | Returns True if all characters in the string are printable |
            | isspace() | Returns True if all characters in the string are whitespaces |
            | istitle() | Returns True if the string follows the rules of a title |
            | isupper() | Returns True if all characters in the string are upper case |
            | join() | Joins the elements of an iterable to the end of the string |
            | ljust() | Returns a left justified version of the string |
            | lower() | Converts a string into lower case |
            | lstrip() | Returns a left trim version of the string |
            | maketrans() | Returns a translation table to be used in translations |
            | partition() | Returns a tuple where the string is parted into three parts |
            | replace() | Returns a string where a specified value is replaced with a specified value |
            | rfind() | Searches the string for a specified value and returns the last position of where it was found |
            | rindex()| Searches the string for a specified value and returns the last position of where it was found |
            | rjust() | Returns a right justified version of the string |
            | rpartition() | Returns a tuple where the string is parted into three parts |
            | rsplit() | Splits the string at the specified separator, and returns a list |
            | rstrip() | Returns a right trim version of the string |
            | split() | Splits the string at the specified separator, and returns a list |
            | splitlines() | Splits the string at line breaks and returns a list |
            | startswith() | Returns true if the string starts with the specified value |
            | strip() | Returns a trimmed version of the string |
            | swapcase() | Swaps cases, lower case becomes upper case and vice versa |
            | title() | Converts the first character of each word to upper case |
            | translate() | Returns a translated string |
            | upper() | Converts a string into upper case |
            | zfill() | Fills the string with a specified number of 0 values at the beginning |
            
        - String format()
            
            ```python
            format() # format selected parts of a string
            
            price = 49
            txt = "The price is {} dollars"
            print(txt.format(price))
            # The price is 49 dollars
            
            # add parameters inside the curly brackets
            # Format the price to be displayed with two decimals
            price = 49
            txt = "The price is {:.2f} dollars"
            print(txt.format(price))
            # The price is 49.00 dollars
            
            # Multiple Values
            print(txt.format(price, itemno, count))
            
            # add more placeholders
            quantity = 3
            itemno = 567
            price = 49
            myorder = "I want {} pieces of item number {} for {:.2f} dollars."
            print(myorder.format(quantity, itemno, price))
            # I want 3 pieces of item number 567 for 49.00 dollars.
            
            # Index Numbers
            # (a number inside the curly brackets {0})
            # sure the values are placed
            quantity = 3
            itemno = 567
            price = 49
            myorder = "I want {0} pieces of item number {1} for {2:.2f} dollars."
            print(myorder.format(quantity, itemno, price))
            # I want 3 pieces of item number 567 for 49.00 dollars.
            
            # refer to the same value more than once
            age = 36
            name = "John"
            txt = "His name is {1}. {1} is {0} years old."
            print(txt.format(age, name))
            # His name is John. John is 36 years old.
            
            # Named Indexes
            # use named indexes by entering a name inside the curly brackets {carname}
            # must use names when pass the parameter values txt.format(carname = "Ford")
            myorder = "I have a {carname}, it is a {model}."
            print(myorder.format(carname = "Ford", model = "Mustang"))
            # I have a Ford, it is a Mustang.
            ```
            
    - Boolean
        - `True`or `False`
        
        ```python
        # evaluate any value
        print(bool("Hello")) # True
        print(bool(15)) # True
        
        # Any string is True, except empty strings
        # Any number is True, except 0
        # Any list, tuple, set, and dictionary are True, except empty ones
        
        # False
        # (), [], {}, ""
        # number 0, and value None
        bool(False)
        bool(None)
        bool(0)
        bool("")
        bool(())
        bool([])
        bool({})
        
        # One more value, or object evaluates to False
        # object that is made from a class with a __len__ function
        # returns 0 or False
        class myclass():
          def __len__(self):
            return 0
        myobj = myclass()
        print(bool(myobj))
        # False
        
        # functions that returns Boolean
        def myFunction() :
          return True
        print(myFunction())
        
        def myFunction() :
          return True
        if myFunction():
          print("YES!")
        else:
          print("NO!")
        
        isinstance() # built-in function return boolean
        # which used to determine if an object is of a certain data type
        print(isinstance(200, int))
        # True
        ```
        
    - Operation
        - Arithmetic operators
            
            
            | Operator | Name | Example |
            | --- | --- | --- |
            | + | Addition | x + y |
            | - | Subtraction | x - y |
            | * | Multiplication | x * y |
            | / | Division | x / y |
            | % | Modulus | x % y |
            | ** | Exponentiation | x ** y |
            | // | Floor division | x // y |
            
        - Assignment Operators
            
            
            | Operator | Example | Same As |
            | --- | --- | --- |
            | = | x = 5 | x = 5 |
            | += | x += 3 | x = x + 3 |
            | -= | x -= 3 | x = x - 3 |
            | *= | x *= 3 | x = x * 3 |
            | /= | x /= 3 | x = x / 3 |
            | %= | x %= 3 | x = x % 3 |
            | //= | x //= 3 | x = x // 3 |
            | **= | x **= 3 | x = x ** 3 |
            | &= | x &= 3 | x = x & 3 |
            | ^= | x ^= 3 | x = x ^ 3 |
            | >>= | x >>= 3 | x = x >> 3 |
            | <<= | x <<= 3 | x = x << 3 |
        - Comparison Operators
            
            
            | Operator | Name | Example |
            | --- | --- | --- |
            | == | Equal | x == y |
            | != | Not equal | x != y |
            | > | Greater than | x > y |
            | < | Less than | x < y |
            | >= | Greater than or equal to | x >= y |
            | <= | Less than or equal to | x <= y |
        - Logical Operators
            
            
            | Operator | Description | Example |
            | --- | --- | --- |
            | and  | Returns True if both statements are true | x < 5 and  x < 10 |
            | or | Returns True if one of the statements is true | x < 5 or x < 4 |
            | not | Reverse the result, returns False if the result is true | not(x < 5 and x < 10) |
        - Identity Operators
            - `False` if they are equal only, `==`
            - `True` if actually the same object, with same memory location
            
            | Operator | Description | Example |
            | --- | --- | --- |
            | is  | Returns True if both variables are the same object | x is y |
            | is not | Returns True if both variables are not the same object | x is not y |
        - Membership operators
            
            
            | Operator | Description | Example |
            | --- | --- | --- |
            | in  | Returns True if a sequence with the specified value is present in the object | x in y |
            | not in | Returns True if a sequence with the specified value is not present in the object | x not in y |
        - Bitwise Operators
            
            
            | Operator | Name | Description |
            | --- | --- | --- |
            | &  | AND | Sets each bit to 1 if both bits are 1 |
            |  ^ | XOR | Sets each bit to 1 if only one of two bits is 1 |
            | ~  | NOT | Inverts all the bits |
            | << | Zero fill left shift | Shift left by pushing zeros in from the right and let the leftmost bits fall off |
            | >> | Signed right shift | Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off |
            
    - List
        - Basic
            - store multiple items in a single variable
            - created using square brackets `[]`
            - ordered, changeable, and allow duplicate values
            
            ---
            
            - items have a defined order, and that order will not change
            - new items will be placed at the end of the list
            - lists can change, add, and remove items in a list after it has been created
            - lists can have items with the same value
            
            ```python
            thislist = ["apple", "banana", "cherry"]
            print(len(thislist))
            # 3
            
            # can be of any data type
            list1 = ["apple", "banana", "cherry"]
            list2 = [1, 5, 7, 9, 3]
            list3 = [True, False, False]
            
            # contain different data types
            list1 = ["abc", 34, True, 40, "male"]
            
            mylist = ["apple", "banana", "cherry"]
            print(type(mylist))
            # <class 'list'>
            
            list() # constructor to create a list
            thislist = list(("apple", "banana", "cherry")) 
            # note the double round-brackets
            print(thislist)
            # ['apple', 'banana', 'cherry']
            ```
            
        - Access
            
            ```python
            # Negative indexing means start from the end
            # -1 refers to the last item
            # -2 refers to the second last item
            thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]
            print(thislist[-1])
            # mango
            
            # start at 2 (included) and end at 5 (not included)
            print(thislist[2:5])
            # ['cherry', 'orange', 'kiwi']
            
            # from the beginning to, but NOT including, "kiwi"
            print(thislist[:4])
            # ['apple', 'banana', 'cherry', 'orange']
            
            # from "cherry" to the end
            print(thislist[2:])
            # ['cherry', 'orange', 'kiwi', 'melon', 'mango']
            
            # from "orange" (-4) to, but NOT including "mango" (-1)
            # from left to right only
            print(thislist[-4:-1])
            # ['orange', 'kiwi', 'melon']
            
            # if "  " in "  ":
            if "apple" in thislist:
              print("Yes, 'apple' is in the fruits list")
            # Yes, 'apple' is in the fruits list
            ```
            
        - Change
            
            ```python
            # Change a Range of Item Values
            thislist = ["apple", "banana", "cherry", "orange", "kiwi", "mango"]
            thislist[1:3] = ["blackcurrant", "watermelon"]
            # ['apple', 'blackcurrant', 'watermelon', 'orange', 'kiwi', 'mango']
            
            # more items than replace
            # remaining items will move accordingly
            # Change the second value 
            # by replacing it with two new values
            thislist = ["apple", "banana", "cherry"]
            thislist[1:2] = ["blackcurrant", "watermelon"]
            # ['apple', 'blackcurrant', 'watermelon', 'cherry']
            # length of the list will change
            # when number of items inserted does not match number of items replaced
            
            # less items than you replace
            # remaining items will move accordingly
            # Change the second and third value 
            # by replacing it with one value
            thislist = ["apple", "banana", "cherry"]
            thislist[1:3] = ["watermelon"]
            # ['apple', 'watermelon']
            ```
            
        - Modify
            
            ```python
            insert()
            # inserts an item at the specified index
            # insert new list item, without replacing any of existing values
            thislist = ["apple", "banana", "cherry"]
            thislist.insert(2, "watermelon")
            # ['apple', 'banana', 'watermelon', 'cherry']
            
            append()
            # add an item to the end of the list
            thislist = ["apple", "banana", "cherry"]
            thislist.append("orange")
            # ['apple', 'banana', 'cherry', 'orange']
            
            extend()
            # append elements from another list to the end of the list
            thislist = ["apple", "banana", "cherry"]
            tropical = ["mango", "pineapple", "papaya"]
            thislist.extend(tropical)
            # ['apple', 'banana', 'cherry', 'mango', 'pineapple', 'papaya']
            
            # able to add any lterable (turples, sets, dictionaries)
            # Add elements of a tuple to a list
            thislist = ["apple", "banana", "cherry"]
            thistuple = ("kiwi", "orange")
            thislist.extend(thistuple)
            # ['apple', 'banana', 'cherry', 'kiwi', 'orange']
            
            remove() # Remove Specified Item
            thislist = ["apple", "banana", "cherry"]
            thislist.remove("banana")
            # ['apple', 'cherry']
            # only removes the first occurrence of the specified value
            
            pop() # Remove Specified Index
            thislist = ["apple", "banana", "cherry"]
            thislist.pop(1)
            # ['apple', 'cherry']
            
            # If do not specify the index, the pop() removes last item
            thislist = ["apple", "banana", "cherry"]
            thislist.pop()
            # ['apple', 'banana']
            
            del # also removes the specified index
            thislist = ["apple", "banana", "cherry"]
            del thislist[0]
            # ['banana', 'cherry']
            
            # del can also delete the list completely
            thislist = ["apple", "banana", "cherry"]
            del thislist
            print(thislist)
            # this will cause an error because list is succsesfully deleted
            
            clear() # empties the list
            # list still remains, but it has no content
            thislist = ["apple", "banana", "cherry"]
            thislist.clear()
            # []
            ```
            
        - Loop
            
            ```python
            # Loop Through a List
            # Print all items in the list, one by one
            for x in thislist:
              print(x)
            # apple
            # banana
            # cherry
            
            # Loop Through the Index Numbers
            range(); len() # to create a suitable iterable
            for i in range(len(thislist)):
              print(thislist[i])
            # apple
            # banana
            # cherry
            
            range(3) # same as range(0,3)
            x = range(3, 20, 21)
            # 3 (only the first item)
            
            # loop by using a while loop
            i = 0
            while i < len(thislist):
              print(thislist[i])
              i = i + 1
            # apple
            # banana
            # cherry
            
            # Looping Using List Comprehension
            # offers the shortest syntax for looping
            # for loop that will print all items in a list
            [print(x) for x in thislist]
            # apple
            # banana
            # cherry
            ```
            
        - List comprehension
            - offers a shorter syntax
            
            ```python
            # create new list, contain only with letter "a"
            # for statement with a conditional test inside
            fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
            
            newlist = []
            for x in fruits:
              if "a" in x:
                newlist.append(x)
            print(newlist)
            # ['apple', 'banana', 'mango']
            
            # with list comprehension
            newlist = [x for x in fruits if "a" in x]
            print(newlist)
            # ['apple', 'banana', 'mango']
            
            # Syntax
            newlist = [exp. for item in iterable if cond. == True]
            # return a new list, leaving the old list unchanged
            
            # condition : filter out the True items
            # Only accept items that are not "apple"
            newlist = [x for x in fruits if x != "apple"]
            # ['banana', 'cherry', 'kiwi', 'mango']
            
            # without condition (if statement)
            newlist = [x for x in fruits]
            # ['apple', 'banana', 'cherry', 'kiwi', 'mango']
            
            newlist = [x for x in range(10)]
            # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
            
            newlist = [x for x in range(10) if x < 5]
            # [0, 1, 2, 3, 4]
            
            # expression
            # Set the values in the new list to upper case
            newlist = [x.upper() for x in fruits]
            # ['APPLE', 'BANANA', 'CHERRY', 'KIWI', 'MANGO']
            
            # Set all values in the new list to 'hello'
            newlist = ['hello' for x in fruits]
            # ['hello', 'hello', 'hello', 'hello', 'hello']
            
            # Return "orange" instead of "banana"
            newlist = [x if x != "banana" else "orange" for x in fruits]
            # ['apple', 'orange', 'cherry', 'kiwi', 'mango']
            # Return item if it is not banana, banana return orange
            ```
            
        - Sort
            - sort the list alphanumerically, ascending
            
            ```python
            thislist = ["orange", "mango", "kiwi", "pineapple", "banana"]
            thislist.sort()
            # ['banana', 'kiwi', 'mango', 'orange', 'pineapple']
            
            thislist = [100, 50, 65, 82, 23]
            thislist.sort()
            # [23, 50, 65, 82, 100]
            
            reverse = True # sort descending 
            thislist.sort(reverse = True)
            # ['pineapple', 'orange', 'mango', 'kiwi', 'banana']
            
            thislist.sort(reverse = True)
            # [100, 82, 65, 50, 23]
            
            # Customize Sort Function
            # how close the number is to 50
            def myfunc(n):
              return abs(n - 50)
            thislist = [100, 50, 65, 82, 23]
            thislist.sort(key = myfunc)
            # [50, 65, 23, 82, 100]
            
            # case sensitive
            # resulting in all capital letters being sorted before lower case letters
            thislist = ["banana", "Orange", "Kiwi", "cherry"]
            thislist.sort()
            # ['Kiwi', 'Orange', 'banana', 'cherry']
            
            thislist.sort(key = str.lower)
            # ['banana', 'cherry', 'Kiwi', 'Orange']
            
            reverse() # reverse the current sorting order of elements
            thislist.reverse()
            # ['cherry', 'Kiwi', 'Orange', 'banana']
            ```
            
        - Copy
            
            ```python
            list2 = list1 # cannot copy a list simply
            # list2 will only be a reference to list1
            # changes made in list1 will automatically be made in list2
            
            copy() # make a copy
            thislist = ["apple", "banana", "cherry"]
            mylist = thislist.copy()
            # ['apple', 'banana', 'cherry']
            
            list()
            thislist = ["apple", "banana", "cherry"]
            mylist = list(thislist)
            # ['apple', 'banana', 'cherry']
            ```
            
        - Join
            
            ```python
            # + operator
            list1 = ["a", "b", "c"]
            list2 = [1, 2, 3]
            list3 = list1 + list2
            # ['a', 'b', 'c', 1, 2, 3]
            
            # Append list2 into list1
            for x in list2:
              list1.append(x)
            print(list1)
            # ['a', 'b', 'c', 1, 2, 3]
            # no need to create a new list
            
            extend() # add list2 at the end of list1
            list1.extend(list2)
            # ['a', 'b', 'c', 1, 2, 3]
            ```
            
        - Built-in methods
            
            
            | Method | Description |
            | --- | --- |
            | append() | Adds an element at the end of the list |
            | clear() | Removes all the elements from the list |
            | copy() | Returns a copy of the list |
            | count() | Returns the number of elements with the specified value |
            | extend() | Add the elements of a list (or any iterable), to the end of the current list |
            | index() | Returns the index of the first element with the specified value |
            | insert() | Adds an element at the specified position |
            | pop() | Removes the element at the specified position |
            | remove() | Removes the item with the specified value |
            | reverse() | Reverses the order of the list |
            | sort() | Sorts the list |
        - Arrays
            - Python does not have built-in support for Arrays, but Lists
            - Store multiple values in one single variable
            
            ```python
            # array containing car names
            cars = ["Ford", "Volvo", "BMW"]
            # ['Ford', 'Volvo', 'BMW']
            
            # array is a special variable
            # hold more than one value at a time
            # An array can hold many values under a single name
            # and can access the values by referring to an index number
            ```
            
    - Tuple
        - Basic
            - store multiple items in a single variable
            - ordered and **unchangeable**, and allow duplicate values
            - written with round brackets `()`
            
            ```python
            thistuple = ("apple", "banana", "cherry")
            
            # Allow Duplicates
            # tuples are indexed, having items with the same value
            thistuple = ("apple", "banana", "cherry", "apple", "cherry")
            
            # Create Tuple With One Item
            # have to add a comma after the item
            # otherwise Python will not recognize it as a tuple
            thistuple = ("apple",)
            print(type(thistuple))
            # <class 'tuple'>
            
            #NOT a tuple
            thistuple = ("apple")
            print(type(thistuple))
            # <class 'str'>
            
            # store any data type
            tuple1 = ("apple", "banana", "cherry")
            tuple2 = (1, 5, 7, 9, 3)
            tuple3 = (True, False, False)
            tuple1 = ("abc", 34, True, 40, "male")
            
            tuple() # to make a tuple
            thistuple = tuple(("apple", "banana", "cherry")) 
            # note the double round-brackets
            
            # index -4 (included) to index -1 (excluded)
            thistuple = ("apple", "banana", "cherry", "orange", "kiwi", "melon", "mango")
            print(thistuple[-4:-1])
            # ('orange', 'kiwi', 'melon')
            ```
            
        - Update
            - Tuples are unchangeable : cannot change, add, or remove items once created
            
            ```python
            # convert the tuple into a list
            # change the list
            # convert the list back into a tuple
            x = ("apple", "banana", "cherry")
            y = list(x)
            y[1] = "kiwi"
            x = tuple(y)
            # ("apple", "kiwi", "cherry")
            
            # Since tuples are immutable
            # do not have a build-in append() method
            
            # 1. Convert into a list
            thistuple = ("apple", "banana", "cherry")
            y = list(thistuple)
            y.append("orange")
            thistuple = tuple(y) # update thistuple
            # ('apple', 'banana', 'cherry', 'orange')
            
            # 2. Add tuple to a tuple
            # allowed to add tuples to tuples
            # create a new tuple with the item(s), and add it
            thistuple = ("apple", "banana", "cherry")
            y = ("orange",)
            thistuple += y
            # ('apple', 'banana', 'cherry', 'orange')
            # tuple with only one item, add a comma after the item
            
            # cannot remove items in a tuple
            thistuple = ("apple", "banana", "cherry")
            y = list(thistuple)
            y.remove("apple")
            thistuple = tuple(y)
            # ('banana', 'cherry')
            
            # delete the tuple completely
            thistuple = ("apple", "banana", "cherry")
            del thistuple
            print(thistuple) 
            # this will raise an error because the tuple no longer exists
            
            # multiply the content of a tuple a given number of times
            fruits = ("apple", "banana", "cherry")
            mytuple = fruits * 2
            # ('apple', 'banana', 'cherry', 'apple', 'banana', 'cherry')
            ```
            
        - Unpack
            
            ```python
            # "packing" a tuple:
            # When create a tuple, normally assign values to it
            fruits = ("apple", "banana", "cherry")
            
            # "unpacking"
            # extract the values back into variables
            fruits = ("apple", "banana", "cherry")
            (green, yellow, red) = fruits
            print(green)
            # apple
            print(yellow)
            # banana
            print(red)
            # cherry
            # number of variables must match the number of values
            # if not, must use an asterisk to collect remaining values as a list
            
            # Using Asterisk*
            # number of variables is less than the number of values
            # add an * to the variable name 
            # the values will be assigned to the variable as a list
            
            # Assign the rest of the values as a list called "red"
            fruits = ("apple", "banana", "cherry", "strawberry", "raspberry")
            (green, yellow, *red) = fruits
            print(green)
            # apple
            print(yellow)
            # banana
            print(red)
            # ['cherry', 'strawberry', 'raspberry']
            
            # Add a list of values the "tropic" variable
            fruits = ("apple", "mango", "papaya", "pineapple", "cherry")
            (green, *tropic, red) = fruits
            print(green)
            # apple
            print(tropic)
            # ['mango', 'papaya', 'pineapple']
            print(red)
            # cherry
            ```
            
        - Built-in methods
            
            
            | Method | Description |
            | --- | --- |
            | count() | Returns the number of times a specified value occurs in a tuple |
            | index() | Searches the tuple for a specified value and returns the position of where it was found |
    - Set
        - Basic
            - *unordered*, *unchangeable**, *unindexed, do not allow duplicate values*
            - Set *items* are unchangeable, but you can remove items and add new items
            - written with curly brackets `{}`
            
            ```python
            thisset = {"apple", "banana", "cherry"}
            print(thisset)
            # {'cherry', 'banana', 'apple'}
            # Note: the set list is unordered
            # meaning: the items will appear in a random order
            
            # cannot be referred to by index or key
            # cannot change the items after the set has been created
            # but can remove items and add new items
            # cannot have two items with the same value
            thisset = {"apple", "banana", "cherry", "apple"}
            # {'cherry', 'banana', 'apple'}
            
            myset = {"apple", "banana", "cherry"}
            print(type(myset))
            # <class 'set'>
            
            set() # to make a set
            thisset = set(("apple", "banana", "cherry")) 
            # note the double round-brackets
            # {'cherry', 'apple', 'banana'}
            ```
            
        - Access
            - cannot access items in a set by referring to an index or a key
            
            ```python
            # Loop through the set
            thisset = {"apple", "banana", "cherry"}
            for x in thisset:
              print(x)
            # apple
            # cherry
            # banana
            
            # Check if "banana" is present in the set
            thisset = {"apple", "banana", "cherry"}
            print("banana" in thisset)
            # True
            ```
            
        - Change
            - cannot change its items, but can add or remove items
            
            ```python
            add() # Add an item to a set
            thisset = {"apple", "banana", "cherry"}
            thisset.add("orange")
            # {'cherry', 'orange', 'apple', 'banana'}
            
            update()
            # add items from another set into the current set
            thisset = {"apple", "banana", "cherry"}
            tropical = {"pineapple", "mango", "papaya"}
            thisset.update(tropical)
            # {'apple', 'mango', 'cherry', 'pineapple', 'banana', 'papaya'}
            
            # can be any iterable object (tuples, lists, dictionaries etc.)
            thisset = {"apple", "banana", "cherry"}
            mylist = ["kiwi", "orange"]
            thisset.update(mylist)
            # {'banana', 'cherry', 'apple', 'orange', 'kiwi'}
            # output is still set
            
            remove() ; discard() # remove an item in a set
            # If the item to remove does not exist, error
            # Remove "banana"
            thisset = {"apple", "banana", "cherry"}
            thisset.remove("banana")
            # {'cherry', 'apple'}
            # or
            thisset = {"apple", "banana", "cherry"}
            thisset.discard("banana")
            
            pop() # to remove an item
            # remove the last item
            # sets are unordered, so will not know what item that gets removed
            thisset = {"apple", "banana", "cherry"}
            x = thisset.pop()
            print(x) # removed item
            # cherry
            print(thisset) # the set after removal
            # {'banana', 'apple'}
            
            clear() # empties the set
            thisset = {"apple", "banana", "cherry"}
            thisset.clear()
            # set()
            
            del # delete the set completely
            thisset = {"apple", "banana", "cherry"}
            del thisset
            # error
            ```
            
        - Join
            
            ```python
            union() 
            # returns a new set containing all items from both sets
            update() 
            # inserts all the items from one set into another
            
            union() # returns a new set with all items from both sets
            set1 = {"a", "b" , "c"}
            set2 = {1, 2, 3}
            set3 = set1.union(set2)
            # {3, 'b', 'c', 1, 2, 'a'}
            
            update() # inserts the items in set2 into set1
            set1 = {"a", "b" , "c"}
            set2 = {1, 2, 3}
            set1.update(set2)
            # {'b', 3, 'c', 1, 'a', 2}
            # union() and update() will exclude any duplicate items
            
            intersection_update() 
            # Keep ONLY the Duplicates
            # Keep the items that exist in both set x and y
            x = {"apple", "banana", "cherry"}
            y = {"google", "microsoft", "apple"}
            x.intersection_update(y)
            # {'apple'}
            
            intersection() 
            # return a new set
            # only contains the items that are present in both sets
            # contains the items that exist in both set x, and set y
            z = x.intersection(y)
            # {'apple'}
            
            # Keep All, But NOT the Duplicates
            symmetric_difference_update()
            # keep only the elements that are NOT present in both sets
            x.symmetric_difference_update(y)
            # {'google', 'banana', 'microsoft', 'cherry'}
            
            symmetric_difference()
            # return a new set
            # contains only the elements that are NOT present in both sets
            z = x.symmetric_difference(y)
            # {'google', 'banana', 'microsoft', 'cherry'}
            ```
            
        - Built-in methods
            
            
            | Method | Description |
            | --- | --- |
            | add(element) | Adds an element to the set |
            | clear() | Removes all the elements from the set |
            | copy() | Returns a shallow copy of the set |
            | difference(other_set, ...) | Returns a set containing the difference between the set and one or more other sets |
            | difference_update(other_set, ...) | Removes the items from the set that are also included in one or more other sets |
            | discard(element) | Remove the specified element from the set |
            | intersection(other_set, ...) | Returns a set that is the intersection of the set and one or more other sets |
            | intersection_update(other_set, ...) | Removes the items from the set that are not present in one or more other sets |
            | isdisjoint(other_set) | Returns whether the set and another set have an intersection or not |
            | issubset(other_set) | Returns whether the set is a subset of another set or not |
            | issuperset(other_set) | Returns whether the set is a superset of another set or not |
            | pop() | Removes and returns an arbitrary element from the set |
            | remove(element) | Removes the specified element from the set. Raises a KeyError if the element is not present |
            | symmetric_difference(other_set) | Returns a set with the symmetric differences of the set and another set |
            | symmetric_difference_update(other_set) | Inserts the symmetric differences from the set and another set |
            | union(other_set, ...) | Returns a set containing the union of the set and one or more other sets |
            | update(other_set, ...) | Updates the set with the union of the set and one or more other sets |

    - Dictionaries
        - Basic
            - store data values in key : value pairs
            - ordered, changeable and do not allow duplicates
            
            ```python
            # Create and print a dictionary
            thisdict = {
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964
            }
            print(thisdict)
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 1964}
            
            # Print the "brand" value of the dictionary
            print(thisdict["brand"])
            # Ford
            
            # items have a defined order, and that order will not change
            # can change, add or remove items after the dictionary has been created
            # Duplicates Not Allowed
            
            # cannot have two items with the same key
            thisdict = {
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964,
              "year": 2020
            }
            print(thisdict)
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 2020}
            
            print(len(thisdict))
            # 3
            
            thisdict = {
              "brand": "Ford",
              "electric": False,
              "year": 1964,
              "colors": ["red", "white", "blue"]
            }
            # {'brand': 'Ford', 'electric': False, 'year': 1964,
            #  'colors': ['red', 'white', 'blue']}
            
            print(type(thisdict))
            # <class 'dict'>
            ```
            
        - Access
            - access items of a dictionary by referring to its key name, inside square brackets
            
            ```python
            thisdict = {
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964
            }
            # Get the value of the "model" key:
            x = thisdict["model"]
            # Mustang
            
            get() 
            x = thisdict.get("model")
            # Mustang
            
            keys() # return a list of all the keys in the dictionary
            x = thisdict.keys()
            # dict_keys(['brand', 'model', 'year'])
            
            # Add a new item to the original dictionary
            x = car.keys()
            print(x) # before the change
            # dict_keys(['brand', 'model', 'year'])
            car["color"] = "white"
            print(x) # after the change
            # dict_keys(['brand', 'model', 'year', 'color'])
            
            values() # return a list of all the values in the dictionary
            # x = thisdict.values()
            # dict_values(['Ford', 'Mustang', 1964])
            
            # Make a change in the original dictionary
            x = car.values()
            print(x) # before the change
            # dict_values(['Ford', 'Mustang', 1964])
            car["year"] = 2020
            print(x) # after the change
            # dict_values(['Ford', 'Mustang', 2020])
            
            # Add a new item to the original dictionary
            x = car.values()
            print(x) # before the change
            # dict_values(['Ford', 'Mustang', 1964])
            car["color"] = "red"
            print(x) # after the change
            # dict_values(['Ford', 'Mustang', 1964, 'red'])
            
            items()
            # return each item in a dictionary, as tuples in a list
            x = thisdict.items()
            # dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])
            
            # Make a change in the original dictionary
            x = car.items()
            print(x) # before the change
            # dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])
            car["year"] = 2020
            print(x) # after the change
            # dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 2020)])
            
            # Add a new item to the original dictionary
            x = car.items()
            print(x) # before the change
            # dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964)])
            car["color"] = "red"
            print(x) # after the change
            # dict_items([('brand', 'Ford'), ('model', 'Mustang'), ('year', 1964), ('color', 'red')])
            
            # determine if a specified key is present in a dictionary use the in keyword
            if "model" in thisdict:
              print("Yes, 'model' is one of the keys in the thisdict dictionary")
            # Yes, 'model' is one of the keys in the thisdict dictionary
            ```
            
        - Change
            - change the value of a specific item by referring to its key name
            
            ```python
            thisdict =	{
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964
            }
            thisdict["year"] = 2018
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 2018}
            
            update() 
            # update the dictionary with the items from the given argument
            # argument must be dictionary, or an iterable object with key:value pairs
            # update the "year" of the car
            thisdict.update({"year": 2020})
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 2020}
            
            # Adding Items
            # using a new index key and assigning a value to it
            thisdict["color"] = "red"
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 1964, 'color': 'red'}
            
            # Update Dictionary
            update()
            # If the item does not exist, the item will be added
            # argument must be a dictionary, or an iterable object with key:value pairs
            thisdict.update({"color": "red"})
            # {'brand': 'Ford', 'model': 'Mustang', 'year': 1964, 'color': 'red'}
            
            # Remove Dictionary Items
            pop() 
            # removes the item with the specified key name
            thisdict = {
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964
            }
            thisdict.pop("model")
            # {'brand': 'Ford', 'year': 1964}
            
            popitem() # removes the last inserted item
            thisdict.popitem()
            # {'brand': 'Ford', 'model': 'Mustang'}
            
            del # removes the item with the specified key name
            del thisdict["model"]
            # {'brand': 'Ford', 'year': 1964}
            
            # can also delete the dictionary completely
            del thisdict
            print(thisdict) 
            # cause an error because "thisdict" no longer exists
            
            clear() # empties the dictionary
            thisdict.clear()
            # {}
            ```
            
        - Loop
            
            ```python
            thisdict =	{
              "brand": "Ford",
              "model": "Mustang",
              "year": 1964
            }
            # loop all key names in the dictionary
            for x in thisdict:
              print(x)
            # brand
            # model
            # year
            
            # loop all values in the dictionary
            for x in thisdict:
              print(thisdict[x])
            # Ford
            # Mustang
            # 1964
            
            values() # to return values of a dictionary
            for x in thisdict.values():
              print(x)
            # Ford
            # Mustang
            # 1964
            
            keys() # to return the keys of a dictionary
            for x in thisdict.keys():
              print(x)
            # brand
            # model
            # year
            
            items() # Loop through both keys and values
            for x, y in thisdict.items():
              print(x, y)
            # brand Ford
            # model Mustang
            # year 1964
            ```
            
        - Nested Dictionaries
            - dictionary contain dictionaries
            
            ```python
            # a dictionary that contain three dictionaries
            myfamily = {
              "child1" : {
                "name" : "Emil",
                "year" : 2004
              },
              "child2" : {
                "name" : "Tobias",
                "year" : 2007
              },
              "child3" : {
                "name" : "Linus",
                "year" : 2011
              }
            }
            # {'child1': {'name': 'Emil', 'year': 2004}, 
            #  'child2': {'name': 'Tobias', 'year': 2007}, 
            #  'child3': {'name': 'Linus', 'year': 2011}}
            
            # add three dictionaries into a new dictionary
            # Create three dictionaries
            # create one dictionary that contain other three dictionaries
            child1 = {
              "name" : "Emil",
              "year" : 2004
            }
            child2 = {
              "name" : "Tobias",
              "year" : 2007
            }
            child3 = {
              "name" : "Linus",
              "year" : 2011
            }
            
            myfamily = {
              "child1" : child1,
              "child2" : child2,
              "child3" : child3
            }
            # {'child1': {'name': 'Emil', 'year': 2004}, 
            #  'child2': {'name': 'Tobias', 'year': 2007}, 
            #  'child3': {'name': 'Linus', 'year': 2011}}
            ```
            
        - Built-in methods
            
            
            | Method | Description |
            | --- | --- |
            | clear() | Removes all the elements from the dictionary |
            | copy() | Returns a shallow copy of the dictionary |
            | fromkeys(keys, value) | Returns a new dictionary with the specified keys and value |
            | get(key, default=None) | Returns the value of the specified key. If the key does not exist, returns the default value |
            | items() | Returns a list containing a tuple for each key-value pair in the dictionary |
            | keys() | Returns a list containing the dictionary's keys |
            | pop(key, default=None) | Removes and returns the value for the specified key. If the key is not found, returns the default value |
            | popitem() | Removes and returns the last inserted key-value pair as a tuple |
            | setdefault(key, default=None) | Returns the value of the specified key. If the key does not exist, inserts the key with the specified value |
            | update(other) | Updates the dictionary with the key-value pairs from another dictionary or iterable |
            | values() | Returns a list of all the values in the dictionary |

- Functions
    - If ... Else
        
        ```python
        # If statement:
        if test expression:
        	statement
        
        if b > a:
          print("b is greater than a")
        # indentation (whitespace at the beginning) to define scope in the code
        
        elif
        # if previous conditions were not true, try this condition
        if b > a:
          print("b is greater than a")
        elif a == b:
          print("a and b are equal")
        
        else 
        # catches anything which isn't caught by the preceding conditions
        if b > a:
          print("b is greater than a")
        elif a == b:
          print("a and b are equal")
        else:
          print("a is greater than b")
        
        # can also have an else without the elif
        
        # Ternary Operators, or Conditional Expressions
        # Short Hand If
        # only one statement to execute
        # can put it on the same line as the if statement
        if test expression: statement
        # One line if statement:
        if a > b: print("a is greater than b")
        
        # Short Hand If ... Else
        # one for if, and one for else
        statement_A if test expression else statement_B
        # One line if else statement:
        print("A") if a > b else print("B")
        
        # multiple else statements on the same line
        # One line if else statement, with 3 conditions
        print("A") if a > b else print("=") if a == b else print("B")
        # same as
        if a > b:
        	print("A")
        elif a == b:
        	print("=")
        else:
        	print("B")
        
        and
        if a > b and c > a:
          print("Both conditions are True")
        
        or
        if a > b or a > c:
          print("At least one of the conditions is True")
        
        # Nested If
        # have if statements inside if statements
        if x > 10:
          print("Above ten,")
          if x > 20:
            print("and also above 20!")
          else:
            print("but not above 20.")
        
        # pass Statement
        # if statements cannot be empty
        # if statement with no content
        # put in the pass statement to avoid getting an error
        if b > a:
          pass
        ```
        
    - While Loop
        
        ```python
        # Print i as long as i is less than 6
        i = 1 # while loop requires relevant variables to be ready
        while i < 6:
          print(i)
          i += 1
        # increment i, or else the loop will continue forever
        
        break
        # stop the loop even if the while condition is true
        # Exit the loop when i is 3
        i = 1
        while i < 6:
          print(i)
          if i == 3:
            break
          i += 1
        # 1
        # 2
        # 3
        
        continue
        # stop the current iteration, and continue with the next
        # Continue to the next iteration if i is 3
        i = 0
        while i < 6:
          i += 1
          if i == 3:
            continue
          print(i)
        # Note that number 3 is missing in the result
        # 1
        # 2
        # 4
        # 5
        # 6
        
        # else Statement
        # run a block of code once when the condition no longer is true
        i = 1
        while i < 6:
          print(i)
          i += 1
        else:
          print("i is no longer less than 6")
        # 1
        # 2
        # 3
        # 4
        # 5
        # i is no longer less than 6
        
        ```
        
    - For Loop
        - iterating over a sequence (that is either a list, a tuple, a dictionary, a set, or a string)
        - for loop does not require an indexing variable to set beforehand
        
        ```python
        # Print each fruit in a fruit list
        fruits = ["apple", "banana", "cherry"]
        for x in fruits:
          print(x)
        
        # strings are iterable objects, contain sequence of characters
        for x in "banana":
          print(x)
        # b
        # a
        # n
        # a
        # n
        # a
        
        break
        # stop the loop before it has looped through all the items
        fruits = ["apple", "banana", "cherry"]
        for x in fruits:
          print(x)
          if x == "banana":
            break
        # apple
        # banana (print, before break)
        
        # Exit the loop when x is "banana"
        # but the break comes before the print:
        fruits = ["apple", "banana", "cherry"]
        for x in fruits:
          if x == "banana":
            break
          print(x)
        # apple
        
        continue 
        # stop the current iteration of the loop
        # continue with the next
        fruits = ["apple", "banana", "cherry"]
        for x in fruits:
          if x == "banana":
            continue
          print(x)
        # apple
        # cherry
        
        range() 
        # returns a sequence of numbers
        # starting from 0, and increments by 1 (by default)
        # ends at a specified number
        for x in range(3):
          print(x)
        # 0
        # 1
        # 2
        # range(3) is not values of 0 to 3, but values 0 to 2
        
        range(2, 6) # values from 2 to 6 (but not including 6)
        for x in range(2, 6):
          print(x)
        # 2
        # 3
        # 4
        # 5
        
        range(2, 30, 3) # specify the increment value by adding third parameter
        for x in range(2, 17, 3):
          print(x)
        # 2
        # 5
        # 8
        # 11
        # 14 (17 is not included)
        
        # Else in For Loop
        # specifies block of code to be executed when the loop is finished
        
        # Print numbers from 0 to 2
        # print a message when the loop has ended
        for x in range(3):
          print(x)
        else:
          print("Finally finished!")
        # 0
        # 1
        # 2
        # Finally finished!
        
        # else block will NOT be executed 
        # if the loop is stopped by a break statement
        for x in range(6):
          if x == 3: break
          print(x)
        else:
          print("Finally finished!")
        # 0
        # 1
        # 2
        
        # Nested Loops
        # "inner loop" will be executed one time 
        # for each iteration of the "outer loop"
        # Print each adjective for every fruit
        adj = ["red", "big", "tasty"]
        fruits = ["apple", "banana", "cherry"]
        for x in adj:
          for y in fruits:
            print(x, y)
        # red apple
        # red banana
        # red cherry
        # big apple
        # big banana
        # big cherry
        # tasty apple
        # tasty banana
        # tasty cherry
        
        pass 
        # for loop with no content
        # put pass statement to avoid getting an error
        for x in [0, 1, 2]:
          pass
        #
        ```
        
    - Basic setting
        - A parameter is the variable listed inside the parentheses in the function definition.
        - An argument is the value that is sent to the function when it is called.
        
        ```python
        def fun(): # Creating a Function
        
        def my_function():
          print("Hello from a function")
        my_function()
        # Hello from a function
        
        # Arguments are specified after function name, inside parentheses
        # function with one argument (fname)
        def my_function(fname):
          print(fname + " Refsnes")
        my_function("Emil")
        # Emil Refsnes
        
        # function must be called with the correct number of arguments
        def my_function(fname, lname):
          print(fname + " " + lname)
        my_function("Emil", "Refsnes")
        # Emil Refsnes
        my_function("Emil")
        # error
        
        # do not know how many arguments that will be passed
        # add * before the parameter name
        
        # function will receive a tuple of arguments
        # can access the items accordingly
        def my_function(*kids):
          print("The youngest child is " + kids[2])
        my_function("Emil", "Tobias", "Linus")
        # The youngest child is Linus
        
        # Keyword
        # arguments with the key = value syntax
        # order of the arguments does not matter
        def my_function(child3, child2, child1):
          print("The youngest child is " + child3)
        my_function(child1 = "Emil", child2 = "Tobias", child3 = "Linus")
        # The youngest child is Linus
        
        # Arbitrary Keyword Arguments, **kwargs
        # do not know how many keyword arguments that will be passed
        # add two asterisk: ** before the parameter name
        # function will receive a dictionary of arguments
        def my_function(**kid):
          print("His last name is " + kid["lname"])
        my_function(fname = "Tobias", lname = "Refsnes")
        # His last name is Refsnes
        
        # Default Parameter Value
        def my_function(country = "Norway"):
          print("I am from " + country)
        my_function("Sweden")
        # I am from Sweden
        my_function()
        # I am from Norway
        
        # Passing a List as an Argument
        # can send any data types of argument to function (string, number, list, dictionary)
        # treated as the same data type inside the function
        
        # send a List as an argument
        # it will still be a List when it reaches the function
        def my_function(food):
          for x in food:
            print(x)
        fruits = ["apple", "banana", "cherry"]
        my_function(fruits)
        # apple
        # banana
        # cherry
        
        return # return a value
        def my_function(x):
          return 5 * x
        print(my_function(3))
        # 15
        
        # avoid getting an error, if function is empty
        def myfunction():
          pass
        
        # Recursion
        # k variable as the data
        # which decrements (-1) every time we recurse
        # The recursion ends when the condition is not greater than 0
        def tri_recursion(k):
          if(k > 0):
            result = k + tri_recursion(k - 1)
            print(result)
          else:
            result = 0
          return result
        print("\n\nRecursion Example Results")
        tri_recursion(6)
        # 
        # 
        # Recursion Example Results
        # 1
        # 3
        # 6
        # 10
        # 15
        # 21
        ```
        
    - Lambda
        - small anonymous function
        - take any number of arguments, but can only have one expression
        
        ```python
        lambda arguments : expression
        
        # Add 10 to argument a, and return the result
        x = lambda a : a + 10
        print(x(5))
        # 15
        
        # numbers of arguments
        # Multiply argument a with argument b and return the result
        x = lambda a, b : a * b
        print(x(5, 6))
        # 30
        
        # Summarize argument a, b, and c and return the result
        x = lambda a, b, c : a + b + c
        print(x(5, 6, 2))
        # 13
        
        # anonymous function inside another function
        
        # takes one argument
        # and that argument will be multiplied with an unknown number
        def myfunc(n):
          return lambda a : a * n
        
        mydoubler = myfunc(2)
        print(mydoubler(11))
        # 22
        print(myfunc(2))
        # <function myfunc.<locals>.<lambda> at 0x2ab333e77f70>
        
        mytripler = myfunc(3)
        print(mytripler(11))
        # 33
        
        # Use lambda when an anonymous function is required for a short period of time
        ```
        
    - Try Except
        - `try`block : test a block of code for errors
        - `except`block : handle the error
        - `else`block : execute code when there is no error
        - `finally`block : execute code, regardless of the result of the try- and except blocks
        
        ```python
        # The try block will generate an error
        # because x is not defined:
        
        try:
          print(x)
        except:
          print("An exception occurred")
        # An exception occurred
        
        # Since the try block raises an error
        # the except block will be executed
        
        # Without the try block
        # the program will crash and raise an error
        
        # many exception blocks
        # Print one message if the try block raises NameError and other errors
        # The try block will generate a NameError
        # because x is not defined:
        try:
          print(x)
        except NameError:
          print("Variable x is not defined")
        except:
          print("Something else went wrong")
        # Variable x is not defined
        
        else
        # define a block of code to be executed 
        # if no errors were raised
        # try block does not generate any error
        try:
          print("Hello")
        except:
          print("Something went wrong")
        else:
          print("Nothing went wrong")
        # Hello
        # Nothing went wrong
        
        finally 
        # if specified, 
        # will be executed regardless if the try block raises an error or not
        # finally block gets executed no matter
        # if the try block raises any errors or not:
        try:
          print(x)
        except:
          print("Something went wrong")
        finally:
          print("The 'try except' is finished")
        # Something went wrong
        # The 'try except' is finished
        
        # useful to close objects and clean up resources
        # Try to open and write to a file that is not writable
        # will raise an error when trying to write to a read-only file:
        try:
          f = open("demofile.txt")
          try:
            f.write("Lorum Ipsum")
          except:
            print("Something went wrong when writing to the file")
          finally:
            f.close()
        except:
          print("Something went wrong when opening the file")
        # Something went wrong when writing to the file
        
        raise 
        # choose to throw an exception if a condition occurs
        
        # Raise an error and stop the program if x is lower than 0:
        x = -1
        if x < 0:
          raise Exception("Sorry, no numbers below zero")
        # error
        # Traceback (most recent call last):
        #  File "demo_ref_keyword_raise.py", line 4, in <module>
        #    raise Exception("Sorry, no numbers below zero")
        # Exception: Sorry, no numbers below zero
        
        raise
        # is used to raise an exception
        # define what kind of error to raise
        # and the text to print to the user
        
        # Raise a TypeError if x is not an integer:
        x = "hello"
        if not type(x) is int:
          raise TypeError("Only integers are allowed")
        # error
        # Traceback (most recent call last):
        #   File "demo_ref_keyword_raise2.py", line 4, in <module>
        #     raise TypeError("Only integers are allowed")
        # TypeError: Only integers are allowed
        ```
        

- Classes & objects
    - Basic
        - object oriented programming language
        - Almost everything in Python is an object, with its properties and methods
        - Class is like an object constructor, or a "blueprint" for creating objects
        
        ```python
        
        class # create a class
        # Create a class named MyClass, with a property named x
        class MyClass:
          x = 5
        print(MyClass)
        # <class '__main__.MyClass'>
        
        # use the class named MyClass to create objects
        # Create an object named p1, and print value of x
        p1 = MyClass()
        print(p1.x)
        print(MyClass().x)
        print(MyClass.x)
        # 5
        
        __init__() 
        # All classes have a function called __init__()
        # always executed when the class is being initiated
        # Use __init__() to assign values to object propertiesor or operations 
        # that are necessary to do when the object is being created
        
        # Create a class named Person
        # use the __init__() function to assign values for name and age
        class Person:
          def __init__(self, name, age):
            self.name = name
            self.age = age
        
        p1 = Person("John", 36)
        # p1 is a object of the class Person
        
        print(p1.name)
        # John
        print(p1.age)
        # 36
        
        # __init__() is called automatically every time
        # when the class is being used to create a new object
        
        # Object Methods
        # Methods in objects are functions that belong to the object
        
        # Insert function that prints a greeting, and execute it on the p1 object
        class Person:
          def __init__(self, name, age):
            self.name = name
            self.age = age
        
          def myfunc(self):
            print("Hello my name is " + self.name)
        
        p1 = Person("John", 36)
        p1.myfunc()
        # Hello my name is John
        
        # self parameter is a reference to the current instance of the class
        # it is used to access variables that belong to the class
        # it has to be the first parameter of any function in the class
        class Person:
          def __init__(mysillyobject, name, age):
            mysillyobject.name = name
            mysillyobject.age = age
        
          def myfunc(abc): 
            print("Hello my name is " + abc.name)
        
        p1 = Person("John", 36)
        p1.myfunc() 
        # Hello my name is John
        
        # Modify Object Properties
        p1 = Person("John", 36)
        print(p1.age) 
        # 36
        p1.age = 40
        print(p1.age)
        # 40
        
        # Delete Object Properties
        del p1.age
        print(p1.age)
        # error
        
        # Delete Objects
        del p1
        print(p1)
        # error
        
        # empty class
        class Person:
          pass
        ```
        
    - Inheritance
        - define a class that inherits all the methods and properties from another class
        - **Parent class** : the class being inherited from (base class)
        - **Child class** : the class that inherits from another class (derived class)
        
        ```python
        # Create a Parent Class
        # Any class can be a parent class, the syntax is the same
        
        # Create a class named Person
        # with firstname and lastname properties
        # and a printname method
        class Person:
          def __init__(self, fname, lname):
            self.firstname = fname
            self.lastname = lname
        
          def printname(self):
            print(self.firstname, self.lastname)
        
        # Use the Person class to create an object
        # execute the printname method
        x = Person("John", "Doe")
        x.printname()
        # John Doe
        
        # Create a Child Class
        # create a class that inherits the functionality from another class
        # send the parent class as a parameter when creating the child class
        
        # Create a class named Student
        # which will inherit the properties and methods from the Person class
        class Student(Person):
          pass
        # pass when do not want to add any other properties or methods to the class
        
        # Student class has the same properties and methods as the Person class
        x = Person("Mike", "Olsen")
        x = Student("Mike", "Olsen")
        x.printname()
        # Mike Olsen
        
        # add __init__() function to the child class (instead of pass)
        class Student(Person):
          def __init__(self, fname, lname):
            #add properties etc.
        
        # When add the __init__() function
        # the child class will no longer inherit the parent's __init__() function
        
        # add a call to the parent's __init__() function
        # to keep the inheritance of the parent's __init__() function
        class Student(Person):
          def __init__(self, fname, lname):
            Person.__init__(self, fname, lname)
        
        x = Student("Mike", "Olsen")
        x.printname()
        # Mike Olsen
        
        # successfully added the __init__() and kept the inheritance of the parent class
        # ready to add functionality in __init__()
        
        super() 
        # make the child class inherit all the methods and properties from its parent
        class Student(Person):
          def __init__(self, fname, lname):
            super().__init__(fname, lname)
        
        x = Student("Mike", "Olsen")
        x.printname()
        # Mike Olsen
        # do not have to use the name of the parent element
        # it will automatically inherit the methods and properties from its parent
        
        # Add Properties
        # Add a property called graduationyear to the Student class
        class Student(Person):
          def __init__(self, fname, lname):
            super().__init__(fname, lname)
            self.graduationyear = 2019
        
        x = Student("Mike", "Olsen")
        print(x.graduationyear)
        # 2019
        
        # year 2019 should be a variable
        # passed into the Student class when creating student objects
        class Student(Person):
          def __init__(self, fname, lname, year):
            super().__init__(fname, lname)
            self.graduationyear = year
        
        x = Student("Mike", "Olsen", 2019)
        print(x.graduationyear)
        # 2019
        
        # Add Methods
        # Add a method called welcome to the Student class
        class Student(Person):
          def __init__(self, fname, lname, year):
            super().__init__(fname, lname)
            self.graduationyear = year
        
          def welcome(self):
            print("Welcome", self.firstname, self.lastname, 
        		"to the class of", self.graduationyear)
        
        x = Student("Mike", "Olsen", 2019)
        x.welcome()
        # Welcome Mike Olsen to the class of 2019
        
        # If add a method in the child class
        # with the same name as a function in the parent class
        # the inheritance of the parent method will be overridden
        ```
        
    - Iterators
        - an object that contains a countable number of values
        - an object that can be iterated upon, meaning that can traverse through all the values
        - Technically, iterator is an object which implements the iterator protocol, which consist of the methods `__iter__()` and `__next__()`
        
        ---
        
        - Lists, tuples, dictionaries, and sets are all iterable objects
        - iterable *containers* which can get an iterator from
        
        ```python
        iter() # which is used to get an iterator
        # Return an iterator from a tuple, and print each value
        mytuple = ("apple", "banana", "cherry")
        myit = iter(mytuple)
        print(next(myit)) # apple
        print(next(myit)) # banana
        print(next(myit)) # cherry
        
        # strings are iterable objects, and can return an iterator
        # iterable objects, containing a sequence of characters
        mystr = "banana"
        myit = iter(mystr)
        print(next(myit)) # b
        print(next(myit)) # a
        print(next(myit)) # n
        print(next(myit)) # a 
        print(next(myit)) # n
        print(next(myit)) # a
        
        # for loop actually creates an iterator object 
        # executes the next() method for each loop
        
        # for loop to iterate through an iterable object
        mytuple = ("apple", "banana", "cherry")
        for x in mytuple:
          print(x)
        # apple
        # banana
        # cherry
        
        # Iterate the characters of a string
        mystr = "banana"
        for x in mystr:
          print(x)
        # b
        # a
        # n
        # a
        # n
        # a
        
        # create an object/class as an iterator, implement __iter__() and __next__()
        __init__()
        # which allow to do some initializing when the object is being created
        __iter__()
        # acts similar, do operations (initializing etc.), but always return iterator object itself
        __next__()
        # allows to do operations, and return the next item in the sequence
        
        # Create an iterator that returns numbers
        # starting with 1, and each sequence will increase by one (returning 1,2,3,4,5 etc.)
        class MyNumbers:
          def __iter__(self):
            self.a = 1
            return self
        
          def __next__(self):
            x = self.a
            self.a += 1
            return x
        
        myclass = MyNumbers()
        myiter = iter(myclass)
        print(next(myiter)) # 1
        print(next(myiter)) # 2
        print(next(myiter)) # 3
        print(next(myiter)) # 4 
        print(next(myiter)) # 5
        
        # StopIteration
        # example above would continue forever if had enough next() 
        # or if it was used in a for loop
        StopIteration # prevent the iteration to go on forever
        
        # in __next__(), add a terminating condition to raise an error 
        # if the iteration is done a specified number of times
        class MyNumbers:
          def __iter__(self):
            self.a = 1
            return self
        
          def __next__(self):
            if self.a <= 5:
              x = self.a   # same
              self.a += 1  # same
              return x     # same
            else:
              raise StopIteration
        
        myclass = MyNumbers()
        myiter = iter(myclass)
        
        for x in myiter:
          print(x)
        # 1
        # 2
        # 3
        # 4
        # 5
        ```
        
    

- Import modules
    - Basic
        - Consider a module to be the same as a code library
        - file containing a set of functions that want to include in application
        
        ```python
        # Create a Module
        # just save the code in a file with the file extension .py
        # mymodule.py
        def greeting(name):
          print("Hello, " + name)
        
        # Use a Module
        # Import the module named mymodule, and call the greeting function
        import mymodule
        mymodule.greeting("Jonathan")
        # Hello, Jonathan
        
        # using a function from a module, syntax:
        module_name.function_name
        
        # Variables in Module
        # contain functions, variables of all types (arrays, dictionaries, objects etc)
        # mymodule.py
        person1 = {
          "name": "John",
          "age": 36,
          "country": "Norway"
        }
        
        # Import the module named mymodule, and access the person1 dictionary
        import mymodule
        a = mymodule.person1["age"]
        print(a) 
        # 36
        
        # Built-in Modules
        # Import and use the platform module
        import platform
        x = platform.system()
        print(x)
        # Windows
        
        dir() 
        # list all the function names (or variable names) in a module
        # can be used on all modules, also the ones create yourself
        import platform
        x = dir(platform)
        print(x)
        # ['DEV_NULL', '_UNIXCONFDIR', 'WIN32_CLIENT_RELEASES', 'WIN32_SERVER_RELEASES']
        
        # Import From Module
        # import only parts from a module, by using the from keyword
        # mymodule.py
        def greeting(name):
          print("Hello, " + name)
        person1 = {
          "name": "John",
          "age": 36,
          "country": "Norway"
        }
        
        # Import only the person1 dictionary
        from mymodule import person1
        print(person1["age"])
        # 36
        
        # do not use the module name when referring to elements in the module
        # Example: person1["age"], not mymodule.person1["age"]
        ```
        
    - Dates
        - date in Python is not a data type
        - Format
            
            
            | Directive | Description | Example |
            | --- | --- | --- |
            | %a | Weekday, short version | Wed |
            | %A | Weekday, full version | Wednesday |
            | %w | Weekday as a number 0-6, 0 is Sunday | 3 |
            | %d | Day of month 01-31 | 31 |
            | %b | Month name, short version | Dec |
            | %B | Month name, full version | December |
            | %m | Month as a number 01-12 | 12 |
            | %y | Year, short version, without century | 18 |
            | %Y | Year, full version | 2018 |
            | %H | Hour 00-23 | 17 |
            | %I | Hour 00-12 | 05 |
            | %p | AM/PM | PM |
            | %M | Minute 00-59 | 41 |
            | %S | Second 00-59 | 08 |
            | %f | Microsecond 000000-999999 | 548513 |
            | %z | UTC offset | +0100 |
            | %Z | Timezone | CST |
            | %j | Day number of year 001-366 | 365 |
            | %U | Week number of year, Sunday as the first day of week, 00-53 | 52 |
            | %W | Week number of year, Monday as the first day of week, 00-53 | 52 |
            | %c | Local version of date and time | Mon Dec 31 17:41:00 2018 |
            | %C | Century | 20 |
            | %x | Local version of date | 12/31/18 |
            | %X | Local version of time | 17:41:00 |
            | %% | A % character | % |
            | %G | ISO 8601 year | 2018 |
            | %u | ISO 8601 weekday (1-7) | 1 |
            | %V | ISO 8601 weeknumber (01-53) | 01 |
        
        ```python
        # import module named datetime to work with dates as date objects
        import datetime
        
        # current date
        x = datetime.datetime.now()
        print(x)
        # 2022-09-01 01:52:00.123620
        
        # date contains year, month, day, hour, minute, second, and microsecond
        
        # Return the year and name of weekday
        x = datetime.datetime.now()
        print(x.year)
        print(x.strftime("%A"))
        # 2022
        # Thursday
        
        # Creating Date Objects
        # three parameters of datetime() : year, month, day
        x = datetime.datetime(2020, 5, 17)
        print(x)
        # 2020-05-17 00:00:00
        
        # optional parameters for time and timezone
        # (hour, minute, second, microsecond, tzone)
        # default value of 0, (None for timezone)
        
        strftime()
        # formatting date objects into readable strings
        # takes one parameter, format, to specify the format
        x = datetime.datetime(2018, 6, 1)
        print(x.strftime("%B"))
        # June
        ```
        
    - Math
        
        ```python
        # built-in math functions
        min() ; max()
        x = min(5, 10, 25)
        y = max(5, 10, 25)
        print(x) # 5
        print(y) # 25
        
        x = abs(-7.25)
        print(x) # 7.25
        
        x = pow(4, 3) # 4*4*4
        print(x) # 64
        ```
        
        ```python
        # built-in module called math
        
        import math
        
        x = math.sqrt(64) # square root
        
        math.ceil()
        # Round a number upward to its nearest integer
        x = math.ceil(1.4)
        print(x) # returns 2
        
        math.floor()
        # Round a number downward to its nearest integer
        y = math.floor(1.4)
        print(y) # returns 1
        
        math.pi # constant value of PI
        # 3.141592653589793
        ```
        
        [https://www.w3schools.com/python/module_math.asp](https://www.w3schools.com/python/module_math.asp)
        
    - JSON
        - Syntax for storing and exchanging data
        - Text, written with JavaScript object notation
        
        | Python | JSON |
        | --- | --- |
        | dict | Object |
        | list | Array |
        | tuple | Array |
        | str | String |
        | int | Number |
        | float | Number |
        | True | true |
        | False | false |
        | None | null |
        
        ```python
        import json
        
        # Parse JSON - Convert from JSON to Python
        json.loads()
        
        # Convert from JSON to Python:
        # some JSON:
        x = '{ "name":"John", "age":30, "city":"New York"}'
        # parse x:
        y = json.loads(x)
        # the result is a Python dictionary:
        print(y["age"])
        # 30
        
        json.dumps()
        # Convert from Python to JSON
        # a Python object (dict):
        x = {
          "name": "John",
          "age": 30,
          "city": "New York"}
        # convert into JSON:
        y = json.dumps(x)
        # the result is a JSON string:
        print(y)
        # {"name": "John", "age": 30, "city": "New York"}
        
        # Format the Result
        x = {
          "name": "John",
          "age": 30,
          "married": True,
          "divorced": False,
          "children": ("Ann","Billy"),
          "pets": None,
          "cars": [
            {"model": "BMW 230", "mpg": 27.5},
            {"model": "Ford Edge", "mpg": 24.1}
          ]
        }
        
        # indent parameter to define the numbers of indents
        print(json.dumps(x, indent=4))
        {
            "name": "John",
            "age": 30,
            "married": true,
            "divorced": false,
            "children": [
                "Ann",
                "Billy"
            ],
            "pets": null,
            "cars": [
                {
                    "model": "BMW 230",
                    "mpg": 27.5
                },
                {
                    "model": "Ford Edge",
                    "mpg": 24.1
                }
            ]
        }
        
        # define the separators, default value is (", ", ": ")
        json.dumps(x, indent=4, separators=(". ", " = "))
        {
            "name" = "John".
            "age" = 30.
            "married" = true.
            "divorced" = false.
            "children" = [
                "Ann".
                "Billy"
            ].
            "pets" = null.
            "cars" = [
                {
                    "model" = "BMW 230".
                    "mpg" = 27.5
                }.
                {
                    "model" = "Ford Edge".
                    "mpg" = 24.1
                }
            ]
        }
        
        # order the keys
        json.dumps(x, indent=4, sort_keys=True)
        {
            "age": 30,
            "cars": [
                {
                    "model": "BMW 230",
                    "mpg": 27.5
                },
                {
                    "model": "Ford Edge",
                    "mpg": 24.1
                }
            ],
            "children": [
                "Ann",
                "Billy"
            ],
            "divorced": false,
            "married": true,
            "name": "John",
            "pets": null
        }
        ```
        
    - RegEx
        - Regular Expression, sequence of characters that forms a search pattern
        - check if a string contains the specified search pattern
        
        ---
        
        - Metacharacters
            - characters with a special meaning
            
            | Character | Description | Example |
            | --- | --- | --- |
            | [ ] | A set of characters | "[a-m]" |
            | \ | Signals a special sequence (can also be used to escape special characters) | "\d" |
            | . | Any character (except newline character) | "he..o" |
            | ^ | Starts with | "^hello" |
            | $ | Ends with | "planet$" |
            | * | Zero or more occurrences | "he.*o" |
            | + | One or more occurrences | "he.+o" |
            | ? | Zero or one occurrences | "he.?o" |
            | { } | Exactly the specified number of occurrences | "he.{2}o" |
            | ( ) | Capture and group |  |
            
        - Special sequence
            
            
            | Character | Description | Example |
            | --- | --- | --- |
            | \A | Returns a match if the specified characters are at the beginning of the string | "\AThe" |
            | \b | Returns a match where the specified characters are at the beginning or at the end of a word(the "r" in the beginning is making sure that the string is being treated as a "raw string") | r"\bain" r"ain\b" |
            | \B | Returns a match where the specified characters are present, but NOT at the beginning (or at the end) of a word(the "r" in the beginning is making sure that the string is being treated as a "raw string") | r"\Bain" r"ain\B" |
            | \d | Returns a match where the string contains digits (numbers from 0-9) | "\d" |
            | \D | Returns a match where the string DOES NOT contain digits | "\D" |
            | \s | Returns a match where the string contains a white space character | "\s" |
            | \S | Returns a match where the string DOES NOT contain a white space character | "\S" |
            | \w | Returns a match where the string contains any word characters (characters from a to Z, digits from 0-9, and the underscore _ character) | "\w" |
            | \W | Returns a match where the string DOES NOT contain any word characters | "\W" |
            | \Z | Returns a match if the specified characters are at the end of the string | "Spain\Z" |
        - Sets
            - set of characters inside a pair of square brackets `[]`
            
            | Set | Description |
            | --- | --- |
            | [arn] | Returns a match where one of the specified characters (a, r, or n) is present |
            | [a-n] | Returns a match for any lower case character, alphabetically between a and n |
            | [^arn] | Returns a match for any character EXCEPT a, r, and n |
            | [0123] | Returns a match where any of the specified digits (0, 1, 2, or 3) are present |
            | [0-9] | Returns a match for any digit between 0 and 9 |
            | [0-5][0-9] | Returns a match for any two-digit numbers from 00 and 59 |
            | [a-zA-Z] | Returns a match for any character alphabetically between a and z, lower case OR upper case |
            | [+] | In sets, +, *, ., (), $,{} has no special meaning, so [+] means: return a match for any + character in the string |
        
        | Function | Description |
        | --- | --- |
        | findall | Returns a list containing all matches |
        | search | Returns a Match object if there is a match anywhere in the string |
        | split | Returns a list where the string has been split at each match |
        | sub | Replaces one or many matches with a string |
        
        ```python
        import re
        
        # Search the string: starts with "The" , ends with "Spain"
        txt = "The rain in Spain"
        x = re.search("^The.*Spain$", txt)
        if x:
          print("YES! We have a match!")
        else:
          print("No match")
        # YES! We have a match!
        
        findall() 
        # returns a list containing all matches
        # Print a list of all matches
        # Return a list containing every occurrence of "ai":
        txt = "The rain in Spain"
        x = re.findall("ai", txt)
        print(x)
        # ['ai', 'ai']
        
        txt = "The rain in Spain"
        # Check if "Portugal" is in the string:
        x = re.findall("Portugal", txt)
        print(x) # []
        if (x):
          print("Yes, there is at least one match!")
        else:
          print("No match")
        # No match
        
        search() 
        # searches the string for a match
        # returns a Match object if there is a match
        # more than one match, only the first occurrence will be returned
        
        # Search for the first white-space character in the string
        txt = "The rain in Spain"
        x = re.search("\s", txt)
        print("The first white-space character is located in position:", x.start())
        # The first white-space character is located in position: 3
        
        # If no matches are found, the value None is returned
        txt = "The rain in Spain"
        x = re.search("Portugal", txt)
        print(x) # None
        
        split() 
        # returns a list where the string has been split at each match
        # Split at each white-space character
        txt = "The rain in Spain"
        x = re.split("\s", txt)
        print(x)
        # ['The', 'rain', 'in', 'Spain']
        
        # specifying the maxsplit parameter
        # control the number of occurrences
        # Split the string only at the first occurrence
        txt = "The rain in Spain"
        x = re.split("\s", txt, 1)
        print(x)
        # ['The', 'rain in Spain']
        
        sub()
        # replaces the matches with the text of your choice
        # Replace all white-space characters with the digit "9":
        txt = "The rain in Spain"
        x = re.sub("\s", "9", txt)
        print(x)
        # The9rain9in9Spain
        
        # specifying the count parameter
        # control the number of replacements
        # Replace the first 2 occurrences:
        txt = "The rain in Spain"
        x = re.sub("\s", "9", txt, 2)
        print(x)
        # The9rain9in Spain
        
        # Match Object is an object containing information
        # about the search and the result
        
        # If there is no match, the value None will be returned
        # instead of the Match Object
        
        # search that will return a Match Object
        # search() function returns a Match object:
        txt = "The rain in Spain"
        x = re.search("ai", txt)
        print(x)
        # <_sre.SRE_Match object; span=(5, 7), match='ai'>
        
        .span()
        # returns a tuple containing the start-, and end positions of the match.
        .string
        # returns the string passed into the function
        .group()
        # returns the part of the string where there was a match
        
        # Print the position (start- and end-position) of the first match occurrence
        # regEx looks for any words that starts with an upper case "S":
        
        # Search for an upper case "S" character in the beginning
        # and print its position
        txt = "The rain in Spain"
        x = re.search(r"\bS\w+", txt)
        print(x.span())
        # (12, 17)
        
        # Print the string passed into the function:
        # The string property returns the search string:
        txt = "The rain in Spain"
        x = re.search(r"\bS\w+", txt)
        print(x.string)
        # The rain in Spain
        
        # Print the part of the string where there was a match
        # regEx looks for any words that starts with an upper case "S":
        
        # Search for an upper case "S" character in the beginning 
        # and print the word
        txt = "The rain in Spain"
        x = re.search(r"\bS\w+", txt)
        print(x.group())
        # Spain
        ```
        
    

- Input & Output
    - User Input
        
        ```python
        # Python 3.6
        username = input("Enter username:")
        print("Username is: " + username)
        # Enter username: S
        # Username is: S
        
        # Python 2.7
        username = raw_input("Enter username:")
        print("Username is: " + username)
        # Enter username: S
        # Username is: S
        ```
