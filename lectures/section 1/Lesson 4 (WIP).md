# Assignment Review
Welcome back! The last lesson ended with with an assignment that would test your knowledge of `if` statements and conditionals. If you haven't attempted it yet, go do that! For everyone else, here's how I would do the simple, non-extra-credit version.

## Version 1
```python
budget = int(input("Welcome to the zoo! What's your budget? "))  
  
# For rich people  
if budget > 10000:  
    choice = input("Dang, you're loaded! Do you want an elephant or a tiger? ")  
    if choice == "elephant":  
        print("Here's your elephant! Thanks for visiting the zoo!")  
    elif choice == "tiger":  
        print("Here's your tiger! Thanks for visiting the zoo!")  
# For poor people  
else:  
    choice = input("You can buy a llama or a goat with that amount. ")  
    if choice == "llama":  
        print("Here's your llama! Thanks for visiting the zoo!")  
    elif choice == "goat":  
        print("Here's your goat! Thanks for visiting the zoo!")
```

First, we get our budget from the user. We wrap the `int()` function around the `input()` function, since the `input()` function returns a string. That's probably a bit confusing to you, but don't worry, today's lesson is all about functions.

Next we use an `if` statement with the condition `budget > 10000`. If that condition evaluates to `True`, we enter the body of the statement. If it doesn't, we skip to `else` and execute that code instead.

Within the bodies of both the `if` and `else`, we're getting the user's input for their choice of animal. Here, since we want it to be a string, we don't have to convert it to another type, like we had to do before with `int()`. 

Then there's an `if`/`elif` pair that are using the equality operator (`==`) to test if the `choice` variable matches one of the acceptable choices. If it does, we complete sale. If none of the `elif` conditions are met, nothing happens. Since we haven't provided an `else` statement, the flow of execution then leaves the `if`/`else` construct, and since there's nothing after that, the program terminates. 

## Version 2 (Extra Credit)

```python
# For rich people  
if budget > 10000:  
    choice = input("Dang, you're loaded! Do you want an elephant or a tiger? ")  
    if choice == "elephant" or choice == "tiger":  
        print(f"Here's your {choice}! Thanks for visiting the zoo!")  
    else:  
        print("We don't have that animal in stock.")  
# For poor people  
elif budget > 0:  
    choice = input("You can buy a llama or a goat with that amount. ")  
    if choice == "goat" or choice == "llama":  
        print(f"Here's your {choice}! Thanks for visiting the zoo!")  
    else:  
        print("We don't have that animal in stock.")  
# For negative budgets  
elif budget < 0:  
    print("What kinda shenanigans are you trying to pull? Get outta here!")  
# For freeloaders  
elif budget == 0:  
    print("Here, kid, have some peanuts. Now scram.")
```

Things start to get a bit messy here, with the added conditions. In the future, you'll learn ways to make a problem like this more straightforward, but this is the best we can do for now.

I've changed the `else` to an `elif` and now it specifially checks for the condition `budget > 0`. I did this mainly to keep those two similar blocks of code next to each other. They represent the most common, or expected, program flow. The two added conditions -- that budget is zero or negative -- are what we call *edge cases*. We don't expect them to happen often, but we want to account for them when they do.

The big change here is the distilation of the two `elif`s that check the animal name. Before, I used an `elif` to handle each one. Now both conditions are in the same `if` statement, separated by the word `or`. `or` is an operator that returns `True` if either of the expresions on its left and right evaluate to `True`.

Within the body of this new `if`, I'm using an f-string, which I briefly covered in Lesson 2. The F stands for "format", and they're one of a few ways to format strings. They key details here are the `f` that's outside the opening quotation marks, and the use of of curly brackets (`{}`) to hold the variable name. 

This change is an example of *refactoring*. Refactoring is when we change the way the code is written, without changing what it actually does. Usually when we refactor, it's to make it easier to read the code and add onto it in the future. With this example, I can now add new animals easily, and update the text for all purchases from one location.

## Version 3 -- Stop It From Crashing
This assignment does have one glaring usibility flaw: if you type in something that's not a number for your budget, it crashes! That's not a very good user experience, and the user isn't given feedback on what they did wrong (unless they're able to intepret the python error message they'll be looking at).

To keep this from happening, first we pin down where the error is coming from. In this case, it's `int()`. If we give that function a string that doesn't represent a number,  it raises an error. To keep this from happening, we can first get the input, then before attempting the conversion, check to see if the string is nothing but numbers. I've ommited the rest of the code in the example for clarity.

```python
budget = input("Welcome to the zoo! What's your budget? ")  
if budget.isdigit():  
    budget = int(budget)  
else:  
    print("That's not a number, ya goober!")
```

`budget.isdigit()` is a *method* on string objects, and it returns `True` if the string contains nothing but digits. Every string has this method -- try it out in [the REPL](https://www.pythonanywhere.com/try-ipython/).

```python
In [1]: "2231".isdigit()
Out[1]: True

In [2]: "abdf".isdigit()
Out[2]: False

In [3]: "5326abdf".isdigit()
Out[3]: False
```

We'll be learning about methods today, but for now let's get back to this supposedly non-crashing animal-purchasing application.

I say "supposedly," because if you were to make that change and run it, you'd see:
```
Welcome to the zoo! What's your budget? one dollar
That's not a number, ya goober!
Traceback (most recent call last):
  File "/home/critter/programming/white_sands/assignment1.py", line 52, in <module>
    if budget > 10000:
TypeError: '>' not supported between instances of 'str' and 'int'
```

The `one dollar` at the end of the first line is what I typed. We see that it gives us the message we wanted, but then it crashes, because there's nothing stoping the program from continuing on to that `budget > 10000` condition. As the error message tells us: `'>' not supported between instances of 'str' and 'int'`.  (`str` is the actual type name for strings, and is what you'll see in error message.)

One way of fixing this is to use the `type()` function mentioned in the previous lesson.

```python
budget = input("Welcome to the zoo! What's your budget? ")  
if budget.isdigit():  
    budget = int(budget)  
else:  
    print("That's not a number, ya goober!")

if type(budget) == int:
	<rest of the code goes here>
```

Try it out, and make sure you're indenting your code correctly!

# Objects
What's an object? In real life, we use the word object to describe almost anything -- a water bottle, a table, a car. Things we can see and touch and manipulate. In Python, all forms of data are objects. An integer is an object, as is a string or a floating-point number like `23.8`.

In real life, objects have properties. A water bottle can be full or empty or somewhere in-between. A table has a length, width, and height. A car has a lot of obvious properties, like make, model and year, but also the number of passengers or amount of gas in the tank.

These objects also can have actions that can be taken on them. This is where the metaphor starts breaking down, because we don't normally think of things like this, but bear with me. A water bottle can be drank from. A desk can be sat at. And a car can be ridden in and driven. 

Likewise, objects in Python have properties and actions that can be taken on them. For example, strings store their length. Strings also can be lowercased by calling the method `.lower()`. For example, `"TEST".lower()` returns the string `test`. Similarly, there's an `.upper()` method, the `.isdigit()` method we saw before, and a bunch of others.

Functions are objects, too! Take print, for example. In the REPL try running `print(print.__doc__)` (that's two underscores on either side). What gets returned? Documentation! This is the exact

Explain the assignment
nested if/elif
string comparison
type() in the comparison

More operators 
integer division
modulo

and/or

chainable operators
https://docs.python.org/2/reference/expressions.html#operator-precedence

f-strings

some string methods

floats

talk about documentation 