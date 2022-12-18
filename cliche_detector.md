
Here's the scenario: you're an English teacher, and you know that your students are, by and large, unimaginative. But you want to have hard data, so you decide to go back through your years of accumulated student papers and count the frequency of clichés. But that's a lot of work to do manually, so you're going to write a program to do that for you. 

The first thing is to write down your goals. What, exactly, do you want to accomplish? In this case, let's say that you want to be able to have a folder full of essays (that could be in multiple formats, like Word, plain text, or PDF), and you'll have a list of clichés. When you run this program, the program will output statistics like the number of papers that used clichés, the average amount of clichés used, and a frequency count of the clichés. 

It's natural to be confronted by a complex project and feel overwhelmed. There are so many things to do, where do you even start? The key to managing the complexity is to break the problem down into smaller components, and work on these individually. It's pure folly to tackle a problem like this head-on.

Breaking our requirements down, we can see a few main elements. 

* finding and counting the clichés in a given piece of text
* calculating and displaying statistics based on those findings 
* reading files from a folder
* reading different file formats like Word and PDF

And within each of those items, we can break it down further. That first item, finding and counting the clichés in a given piece of text, contains the following distinct sub-problems:

* how to tell if a word or phrase is within a larger body of text
* how to search for each cliché from the list of clichés 
* how to keep track of the count


The best place to start is at the beginning, so let's dive in!

# How to run this code

For a text editor, try [online-python.com](https://www.online-python.com/). For an interactive console, try out the [IPython console](https://www.pythonanywhere.com/try-ipython/).

# Finding a substring in a string

If you remember from our previous lessons, a string is the data type that holds text. For our program, our clichés will be strings, and are essays will be strings. For the sake of brevity, the following examples will use strings that are shorter than an essay. The code, however, will remain the same no matter whether the data is a single sentence or a 200-page dissertation.

To tell if a shorter string is part of a longer one, we use the `in` keyword.

```python
"is" in "this is a test" # true
"dog" in "this is a test" # false
"IS" in "this is a test" # false -- case matters!
```

In order to do case-*insensitive* matching, we need to convert the string into lowercase. Obviously, we're hard-coding the strings in these examples, but pretend that they're coming from somewhere outside our control.

```python
"is" in "ThiS IS a TeSt".lower() # true
```

These lines of code all return a `True` or `False` value. If you run this in the console, you'll see those values; if you run this in a script, you'll see nothing, because you'll only see output from a script if you print it, like:

```python
print("is" in "ThiS IS a TeSt".lower()) # outputs the word "True"
```

Step 1 is complete -- we know how to tell if a substring is present in a string! Hooray!

Now for step 2 -- we have a list of strings (clichés, in the future) and we want to know how many of them are present in a string. 

```python
words = ["snow", "the", "video", "bunny", "under"]

sentence = "The snow in the mountains was melting and Bunny had been dead for several weeks before we came to understand the gravity of our situation.".lower()

for word in words:
	if word in sentence:
		print(f"{word} was present")
	else:
		print(f"{word} was not present")
```

Here's a quick refresher on some things in this program:

* lists are containers that hold multiple elements, like strings. We declare lists with square brackets, and put the elements inside, separated by commas.
* a `for` loop iterates over a list, and does all the stuff inside the loop once per element from the list, and assigns that element to the specified variable. In this case, on the first iteration of the loop, the variable `word` will be "snow". On the second, "video". On the third, "mountain", etc. 
* `if` statements will run the code that's inside them (that is, indented) if the specified condition is true. The condition in this case is `word in sentence`. If the condition is false, the code inside the `else` will be executed instead.

If you run this code, you may notice that it says that "under" is present in the sentence. But that word isn't actually there -- what gives? Well, Python doesn't know about what a word is, let alone a sentence. All Python knows is strings, and strings are sequences of characters. All `in` is doing is checking for the specified sequence of characters, and it found "under" in "understand". There are ways we can fix that, but let's leave that for later.

For now, let's try to get a count of how many times these words were used. Python makes that easy -- instead of using `in`, we can use the `count` method of strings.

```python
for word in words:
	count = sentence.count(word)
	print(f"{word} occurred {count} times")
```

This will output:

```
snow occurred 1 times
the occurred 3 times
video occurred 0 times
bunny occurred 1 times
under occurred 1 times
```

If the pluralization of "times" when the count is 1 bothers you, it can be addressed like so:

```python
for word in words:
	count = sentence.count(word)
	s = "" if count == 1 else "s" 
	print(f"{word} occurred {count} time{s}")
```

But back to the important things: instead of printing the count immediately, we want to save it for later use. For this, we need a dictionary, which is how we associate one piece of data with another. A real-world dictionary maps a word to its definition; for example "cat" is mapped to "cute animals, better than dogs", and "dog" is mapped to "disgusting animals that eat poop". (This dictionary was written by a cat.)

In programming terminology, the word like "cat" is the *key*, and the definition is the *value*. In our program, the keys will be words, and the values will be the count of those words. That would look like:

```python
counts = {}  
for word in words:  
    counts[word] = sentence.count(word)  
  
most_frequent_word, most_frequent_count = max(counts.items(), key=lambda item: item[1])  
print(f"Most used word was '{most_frequent_word}', with {most_frequent_count} uses.")
```

This is a great example of how some things that sounds simple ("find the maximum value in a dictionary, and print the key and value") are deceptively complex. Let's take this line apart:

```python
most_frequent_word, most_frequent_count = max(counts.items(), key=lambda item: item[1])  
```
The equals sign always means assignment. In this case, we're assigning to two variables at once. This works whenever the thing to the right of the equals sign is a sequence. For example, 

```python
a, b = [10, 40] # a=10 and b=40
a, b = (10, 40) # just like above, but using a tuple instead of a list
a, b = ("funny number", 69) # the items in the sequence don't have to be the same type
a, b = "AB" # any iterable works -- a="A" and b="B"
```

`max()` is a function that either takes two arguments, like `max(69, 420)` or an iterable, like a list. Here, we're passing in `counts.items()`, which gives us an iterable that contains all the key/value pairs as tuples. So in our case, the first element is `("snow", 1)`, the second is `("the", 3)` and so on. If all we did was pass this argument to `max()`, it would return `("video", 0)`, because it would be comparing based on the first item in the tuple, and "v" occurs later in the alphabet than any of the other words.

We want to find the maximum count, so we have to specify a `key` argument, that controls what data the `max()` function actually considers. This argument needs to be a function that accepts a single argument. Before comparing the elements of the given iterable, `max()` first runs the elements through this function.

A `lambda` is a miniature, inline function that we use for this sort of throw-away task. It doesn't have to be a lambda, though -- this also works:

```python
def get_second_element(item):
	return item[1]

most_frequent_word, most_frequent_count = max(counts.items(), key=get_second_item)  
```

But if we never intend on using it for anything else, that full-fledged function definition is just a waste of space. In comparing the two, note that with lambdas, the syntax is: `lambda <argument>: <return value>`. The `return` keyword is not required -- whatever expression that you put there will be automatically returned.

Let's take a look at the questions we set out to answer:

* how to tell if a word or phrase is within a larger body of text (done!)
* how to search for each cliché from the list of clichés (done!)
* how to keep track of the count (done!)

All done! Well, almost... there's an implied requirement, one that will be true for all areas of this project: we want to make this code *modular*.  We want to use it as a componenet in a larger program, and not have to make any changes, like changing the names of variables. To do this, we can just make it a function:

```python
def frequency(substrings, string):  
    counts = {}  
    for substring in substrings:  
        counts[substring] = string.count(substring)  
  
    return counts
```

Note how we've removed the printing and the finding of the max, because each function should only do one job. This function returns the substring frequencies, and that's it. Elsewhere,(perhaps in a separate file entirely) we could have this:

```python
words = ["snow", "the", "video", "bunny", "under"]

sentence = "The snow in the mountains was melting and Bunny had been dead for several weeks before we came to understand the gravity of our situation.".lower()

counts = frequency(words, sentence)
most_frequent_word, most_frequent_count = max(counts.items(), key=lambda item: item[1])  
print(f"Most used word was '{most_frequent_word}', with {most_frequent_count} uses.")
```

From now on, when we're working on the other challenges this project provides, we don't have to think about frequency calculations at all. We've successfully compartmentalized that code, freeing us up to think about bigger things, like how it will fit in with our other components. And if we ever want to improve how we're finding the frequencies (for example, to stop it from finding "under" in "understand"), we can return to this function and focus entirely on this one small task. 

A large part of successful software engineering is managing complexity, and modularization is key.

We can now cross off the first item from our to-do list:

* ~~finding and counting the clichés in a given piece of text~~
* calculating and displaying statistics based on those findings 
* reading files from a folder
* reading different file formats like Word and PDF

Next up: you decide!
