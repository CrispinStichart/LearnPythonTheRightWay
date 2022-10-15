# Wait, Where's the Diving Board?
In the end, coding comes down to typing code into a text editor and having the computer run it. There's a lot of complexity hidden in that simple sentence. For example, what's a text editor? You may think you know, but you *probably* don't. 

However, I don't want to bog this class down with a bunch of technical explanations right from the get-go, and burden you with downloading a bunch of software, so we're going to use an online editor. Go to [online-python.com](https://www.online-python.com/), and... that it's, you're ready to code!

Specifically, you're ready to code in Python. Python is a programming language that, if you're reading this document in the first place, you may have heard of. Python is used in most introductory programming courses, due to its ease of use and almost human-like grammar. But make no mistake, Python isn't a toy language -- amongst many other things, it's the language most often used for data science and machine learning tasks, two very hot job markets right now. 

# online-python.com -- A Quick Overview
When the page loads, you'll see two text areas. The bigger one on top is where you'll type your code. By default, it starts you off with a simple program that adds two numbers together. (If this is not the case for you, see the next section.) The smaller text area underneath is where output from your program will , and this is also where you'll type any input your program requests.

The green "Run" button, underneath the main code editor, is what you click to run your program. Go ahead and click it now, to run this example program. You should see the words "Enter 1st number:" and then a blinking line underneath them. So type a number, any number, and hit enter. Then you'll be prompted for another number. Obey the command of your robotic overlord. After hitting enter to submit the number, you will then see a bit of text showing the calculation you just performed and the result. 

## Troubleshooting
Hopefully, you were able to run the program without issue. If you do experience issue, try two things:
1. reload the page and try again
2. make sure you're typing a whole number only, like `5` or `192`. Don't add spaces, don't use a decimal point like `3.14`, and don't spell out a number like `fourty-two`

If you're still having trouble, ask a friend for help! Even if your friend isn't a programmer, two heads are better than one.

## Future-Proofing This Document.
As of October 2022, the online-python website starts you off with the program I described above. Since this may change, here's the program in its entirety:

```python

# Online Python - IDE, Editor, Compiler, Interpreter

def sum(a, b):
    return (a + b)

a = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))

print(f'Sum of {a} and {b} is {sum(a, b)}')
```

If the example program is different, or if online-python is inaccessible, copy this into your editor. For this first lesson, this is the code we'll be playing around with. 

# Poking It With a Stick to See What Happens
Traditionally, a CS101 University course will start you on your programming journey with an hour-long lecture about various fundamentals. Not here, not in my classroom. You're going to start by poking this program with a stick. Metaphorically. 

Take a look at this program, what do you see? I know you don't know how to code yet, but I'm sure you can spot some obvious things. For example, you can see the text `"Enter 1st number: "`, which was the first thing you saw when you ran the program. Poke it! What can you change it to? Can you change it to `Enter 1st awesome number: `? Can you put any text you want in there? Do you even need it at all? 

These are all great questions, and they're all questions you can answer by... poking at it! You're going to get some error messages, but don't be scared. There is literally nothing you can do that will harm your computer, yourself, your credit score, or your loved ones. If you get an error, do the following:

1. Read the error message. It will probably be mostly gibberish to you but try to pull out relevant information. Does it tell you something about where the problem happened? Did it tell you something that looked like the name of the error?
2. Undo your change -- `Ctrl+Z` on most computers, `Cmd+Z` on Macs. If worse comes to worst, just reload the page, or copy and paste the code I provided above. Nothing is permanent.

## Things to Try
Before reading this section, keep poking at the code. Try to make educated guesses as to why things work or don't work. Try to spot similarities between different parts of the code. Try adding things. And don't rush! When I've gone through this exercise in person with students, we usually spend an hour just messing around, and mostly what I say during this is "try it".

And only once you start to run out of things to do, and you feel like you're not learning anything... try some of these things!


### Change The Text
You may have noticed two things about the parts of the code that appear as text on your screen when you run the program. 

First, the text is green. This is called *syntax highlighting*. It has no effect on the code itself; rather, it's a feature any decent text editor will provide that makes it much easier to read and understand code.

Second, they're surrounded by quotation marks. Well, that's what we programmers call them. You may be more familiar with them as apostrophes. But we call those `'` *single quotes*, and we call `"` *double quotes.*

Beware the curly quotes: if you copy and paste code from the web or a Word document, the quotations might look like this: `“ ”`. Note how they're curved in an aesthetically pleasing manner. They may look nicer, but they cannot be used as substitutes for "programmer quotations". Don't take my word for it, try it out!

What can you put inside the quotation marks before they stop working? Can you put emojis? Can you put more quotations? Can you put line breaks?

### Delete that Weird Little `f`
Take a gander at line 10:

```python
print(f'Sum of {a} and {b} is {sum(a, b)}')
```

And now compare it to lines 7 and 8:

```python
a = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))
```

You'll notice that although the text in green was outputted to your screen, line 10 has a little more going on. In particular, there are some things in curly braces, and there's that `f` *outside* the opening quotation mark. 

That `f` looks dumb, delete it. Now run your program again and see the result. 

### Change the Order of `input()`
You may have noticed that the two lines that prompt you for input look very similar:

```python
a = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))
```
If you've played around with changing the text that's displayed for the prompt, you may have noticed that it bears no relation to how the rest of the code works. But does the order of lines matter? Can you have `b =` before `a =`?

### Change the Name of Variables
`a` and `b` are examples of what we call *variables*. If you hated math in school, this might trigger some flashbacks:

```
12 = x + 4

Find the value of x
```

But it's the same concept. `a` and `b` are variables that hold a value -- in this case, we don't know the exact thing they're holding, all we know is that it's a number that the user typed in.

But `a` and `b` are such *boring* names... can we spice it up a bit? Can we rename `a` to something like... `Crispin`? I don't know why, I just really like that name. So you make the change, and your code looks like this:

```python
def sum(a, b):
    return (a + b)

Crispin = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))

print(f'Sum of {a} and {b} is {sum(a, b)}')
```

And you're wondering, hey, do I have to change `a` where it appears everywhere else? Well, find out by pressing the run button. You'll get output like this:

```
Enter 1st number: 
1
Enter 2nd number: 
2
Traceback (most recent call last):
  File "main.py", line 10, in <module>
    print(f'Sum of {a} and {b} is {sum(a, b)}')
NameError: name 'a' is not defined


** Process exited - Return Code: 1 **
Press Enter to exit terminal
```

Note that the program didn't crash until *after* I entered my input. This shows us that Python doesn't always "read ahead" to detect errors in our program.

The error message itself tells us two important things:
1. The line number where the error happened (and it also shows us the entire line, just so there's no confusion)
2. The name of the error (in this case, `NameError`) and a short description (`name 'a' is not defined`)

In your programming career, you'll see far more error messages than you will successful outputs with no errors. Don't be scared of them! Just read the description, look at the line, and try to figure it out. 

In this case, it's pretty clear -- we changed the name of a variable from `a` to `Crispin`, and then we tried to use `a`, and Python said (in a Canadian accent) "`a`?" 

So let's change `a` to `Crispin` on that line, so it now looks like:

```python
print(f'Sum of {Crispin} and {b} is {sum(Crispin, b)}')
```

Run it, and you find that everything works! "But wait," (you say) "we didn't change the other two uses of `a`!" And you're right. We'll get to that. 

### Change the Name of the `sum` Thing 
You've changed a variable name, but what about that `sum`... thing? It's a pretty descriptive name right now (after all, it *does* sum two numbers) but what if we want to make it less descriptive and more *avant-garde*? Hm... how about changing `sum` to `avant-garde`? Does that work? No? What about `avant_garde`? Do you have to update it anywhere else?

### Change the *Other* `a` and `b` 
So that ~~`sum`~~ `avant_garde` thing we have looks like this:

```Python
def sum(a, b):
    return (a + b)
```

We saw earlier that these `a` and `b`s didn't relate to the other `a` and `b`s in the program. Do they operate on the same rules? Can we rename them? What if we change the math -- subtract instead of add?

### Add a `c`
Try something big: prompt the user for a third number, and calculate `a + b + c`. I know you don't know how any of this really works, and that's okay. Just activate the pattern-matching part of your brain, do some copy and pasting, and try to make it work. Take it slow and make one change at a time, and carefully read the error message.

# The Part of the Lesson Where I Actually Give You Answers
Congratulations! You survived your first brush with computer programming! But you still have many unanswered questions, and I'm going to answer *some* of them. If these explanations seem incomplete or too rushed for your tastes, don't worry -- in subsequent chapters of this course, we'll be slowing down and looking at one concept at a time. This overview is just here to whet your appetite and make sure that you don't have any major misunderstandings about what you've seen so far. 

---------------

We'll step through the original program, line by line. Here's what we're starting with:

```python

# Online Python - IDE, Editor, Compiler, Interpreter

def sum(a, b):
    return (a + b)

a = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))

print(f'Sum of {a} and {b} is {sum(a, b)}')
```

## Line 3
```python
# Online Python - IDE, Editor, Compiler, Interpreter
```

You might not have even given this any thought, but this is part of the code. It's what we call a *comment*. Everything on a line after a pound sign (`#`) is ignored by the computer. 

We use comments to explain how code works and why we wrote it the way we did. In any project larger than a handful of lines, you can consider comments *mandatory*. Even if you're just writing a program for yourself, I can guarantee you that if you write a line of code that's not 100% self-explanatory and leave no comment, then within a week you'll be staring at that line and thinking: *what the heck does that do?* 

## Lines 4-5
```python
def sum(a, b):
    return (a + b)
```

This is what we call a `function`. If you have some math or formal logic background, you might recognize the concept. For the rest of you, here's a quick explanation to tide us over until the full lesson. 

Functions are reusable pieces of code. Functions are also like [Mad Libs](https://en.wikipedia.org/wiki/Mad_Libs) stories, because they let us fill in the blanks -- we can tell the same basic story, but the small details are different each time. 

`def` is a keyword that tells Python that we're about to define a function. `sum` is the name we chose for this function. We can pick almost anything for the name. The main restrictions are: no spaces, no punctuation, no dashes, no special characters other than the underscore (`_`), and most depressing of all, no emoji. 

Following the name is the list of parameters, or arguments (I'll use the terms interchangeably). These are inside parenthesis. Even if the function has no parameters, it still requires parenthesis. 

The parameters in this case are `a` and `b`. Again, these are names that we pick, with the only restriction being the same naming rules mentioned for functions. Think of these as the empty spaces in Mad Libs where you'll pencil in your wacky adjectives and nouns. When this function is actually used, that's when we actually specify what, exactly, `a` and `b` are. 

But for the duration of the function definition, we just know that they're *something* that will be present, and we can still write our "story" around them, without knowing their exact values.

Oh, and then there's a colon (`:`). You'll always see a colon before any code that's indented. 

Line 5 is what we call *body* of the function. It's a pretty small body; it should really hit the gym more often. Notice the indent. It's four spaces here, but the number of spaces is arbitrary. Any amount will work, so long as you're consistent. But if you don't use four spaces, people will look at you funny. Four spaces is Just How We Do Things Around Here.

The `return` keyword is how the function communicates its results back to the section of code that used it. In this case, we're returning the result of an addition operation, but all the standard math operations are available to us:
* add: `+`
* subtract: `-`
* divide: `/`
* multiply: `*`
* power: `**`
	* (instead of 4³ we would write `4**3`)

Multiple operators can be used on one line, like `10 - 24 + 69 * 420 / 777`. Order of operations matterherehere here, and [PEMDAS](https://www.cuemath.com/numbers/pemdas/) is observed.

Although we only have one line in this function, there's no limit -- we could have a million lines if we wanted.

## Lines 7-8
```python
a = int(input('Enter 1st number: '))
b = int(input('Enter 2nd number: '))
```

There's actually quite a bit happening on these lines! Let's look at the first line specifically, since the second differs only in unimportant details.

`a =` tells python to assign the value of whatever is on the right side the equals sign to the variable `a`. After this line, we can use `a` anywhere we would use a value directly. 

`int()` is a function that converts something that is not a whole number, to a whole number. Or as we call them, an *integer*. For example, a decimal number can be converted like so: `int(4.2)` results in the integer `4`. `int()` can also convert strings to integers -- wait hold on, what's a string? Good question! We'll come back to `int()`, and move on to:

`input()` is a function that will pause the program and allow the user to type in something. When the user hits their enter key, `input()` returns that string. Wait, we *still* don't know what a string is! Okay, moving on:

`'Enter 1st number: '` is a string. For strings that are *hardcoded* (as we say) into a program, you'll recognize them by their quotation marks. Double or single quotation marks, doesn't matter -- it's a string. Literal text (as opposed to code) is called a string for [historical reasons](https://stackoverflow.com/questions/880195/the-history-behind-the-definition-of-a-string), but basically because it's a *string* (or sequence) of characters. "Characters" are what we call the individual letters, numbers, symbols, etc.

This naturally brings us to the concept of data types. Any sort of data we manipulate in code is of some type or another. It might be an integer, or a decimal number, or a boolean True/False value, or something more complicated like a collection of things. Or even something complex and really abstract, like a bank account.

Types matter, because some operations make no sense on some types. For example, can you add integers together? Sure! Can you add an integer and a decimal? Sure, that still makes sense! Can you add a string to another string?

...no seriously, can you? Try it out!

It doesn't do the same thing as adding numbers, but it still makes sense. But what about subtracting a string from a string, or adding a string to a number? 

You know what I'm going to say here, but I'll say it anyway: try it!

This doesn't work because, well, it doesn't make sense, and Python strives to be sensible by default.

Okay, now let's back up a step. We're looking at the string  `'Enter 1st number: '`, and now we kind of know what a string is, but why is it in the parenthesis of the `input()` function? Well you see, `input()` takes an optional argument (remember those?) that represents the prompt that is displayed to the user before the user enters their input. This prompt doesn't change anything about how `input()` works or what happens to the text the user enters.

Let's back up another step, and look at the context:

```python
int(input('Enter 1st number: '))
```

How Python interprets this code, is that it first sees `int(` and thinks, "okay, now I'm going to read the parameters for `int()`".  Then it sees `input()` and says, "aw, shucks, here we go again" because it knows that it can't execute the `int()` function until it's executed the `input()` function. It's like a box inside a box. 

So Python reads the arguments for `input()` (in this case, the string `'Enter 1st number: '`) sees the closing parenthesis, and executes `input()`. `input()` does a lot of magic (explaining how `input()` actually works is *not* 101 material), and displays the prompt to the user. The user types something, and hits enter.

Let's pretend the user typed `4`. Now the input function returns that value, but not as an integer, because it doesn't know anything about numbers. All it knows is that the user gave it text of some kind -- could be a number, maybe not. So what `input()` returns in this case is the *string* `"4"`. 

Now at this point in the program's execution, to Python, the code now looks something like this:

```python
int("4")
```

Python has completely *evaluated* the `input()` function, and can now get on with the business of executing `int()` with the argument `"4"`. When `int()` receives a string as its argument, what it does is go down the string, character by character, verifying that all the characters present represent numbers. If they are, it returns the number that those characters represented. In this case, it returns `4`.

So now, to Python, the whole of line 7 looks like this:

```python
a = 4
```

Since the expression on the right has been completely evaluated, now Python can make a note in its little black book of variables, that the name `a` refers to the value `4`.

Line 8 is an identical process; only the details differ.

## Line 10
```python
print(f'Sum of {a} and {b} is {sum(a, b)}')
```

`print()` is a function that displays output. The name comes from the era before monitors were invented, and room-sized computers would literally print their output onto paper. 

The argument we're passing to print is what's called an "f-string", where the F stands for "format". It's the simplest (but not the only) way to format text in different ways, and combine hard-coded string literals with the value of variables. 

An f-string works the same as a string, except that wherever you see curly braces (`{}`), Python first evaluate the code inside, then converts the result to a string and puts that value in where the curly braces used to be. Oftentimes the only thing in a set of curly braces is a single variable, but there can be almost any kind of code in there.

The third set of curly braces is where we use (or in programming terminology, we *call*) the `sum()` function we defined before. We pass in our `a` and `b` variables as parameters. `a` and `b` both have definite values at this point -- they're the integers the user gave us.

If the user typed in `6` and `3`, when Python is evaluating this line and reaches that final set of curly braces, the line looks like this (to Python):

```python
print(f'Sum of 6 and 3 is {sum(6, 3)}')
```

Now it calls the function, and the function does what we told it to do, which is to add the two arguments together and return the result. That result is dropped into the f-string where `{sum(6, 3)}` was, the completed string is sent to `print()`, and `print()` sends the text to our monitor.

# Where To Go From Here
Do **NOT** continue on to Lesson 3! This was some hardcore learning you just did, and your brain is fried! You may think you want more, but what you really need is to take some time off and come back later. Maybe even tomorrow!

I will allow you back into my classroom only when you are rested and refreshed. I mean it!