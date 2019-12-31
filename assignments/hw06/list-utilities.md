---
layout: homework
title: "List Utilities"
---

<style>
img {
    border: 1px solid #000;
}

.warning {
    background-color: yellow;
    color: #aa1122;
    font-weight: bold;
}

.hidden {
    display: none;
}

.hintButton {
    color: #7788ff;
    cursor: pointer;
}
</style>

<script>
document.addEventListener('DOMContentLoaded', hideHints);

function hideHints(evt) {
    document.querySelectorAll('.hint').forEach((ele, i) => {
        const div = document.createElement('div');
        div.id = 'hint' + i + 'Button';
        ele.id = 'hint' + i;
        ele.classList.add('hidden');
        div.addEventListener('click', onClick);
        div.textContent = 'Show Hint';
        div.className = 'hintButton';
        ele.parentNode.insertBefore(div, ele);
    });

}

function onClick(evt) {
    const hintId = this.id.replace('Button', '');
    const hint = document.getElementById(hintId);
    hint.classList.toggle('hidden');
    this.textContent = this.textConent === 'Show Hint' ? 'Hide Hint' : 'Show Hint';
}
</script>

# Functions and Lists - Due Tuesday, October 29th at 11pm


```
          __________________________________
    ()==(                                   (@==()
         '__________________________________'|
           |                                 |
           |    persuasive pudding           |
           |    misauthorization flab        |
           |    acceptable queue             |
           |                                 |
           |             ~ a haiku written   |
           |               by my computer    |
         __)_________________________________|
    ()==(                                   (@==()
         '----------------------------------'
```
## Overview 

* __Part 1__ `listutils.py` - a few short exercises to practice working with functions and lists
    * do this part first!
    * in the next part, you'll be able to use this file as a module and potentially reuse some of the code that you've already written
* __Part 2__ choose 2 of the 3 to do... if you do the third, it will count as extra credit towards your __homework__ grade
    1. `syllabic_poetry.py`: generate a haiku, tanka, randomly generated syllabic poem or user specified syllabic poem based on a hardcoded list of words
    2. `mydate.py` and `birthday.py`: run a simulation to approximate the probability of two people having the same birthday (the birthday paradox)
	3. `drawing.py`: create 3 functions for drawing shapes with turtle


## Part 1 - listutils.py

In this part, you'll be writing a few short functions that work with lists. Some of these functions already have built-in counterparts in Python, but we'll implement our own to practice loops, accumulators, and working with lists. Consequently: 

1. some of the instructions will specify functions, methods, and operators that you will not be allowed to use
2. additionally, the instructions will also specify the parameters and return values of each function you'll be writing.

Once you're done with this file, you can use it as a module! This means that you may be able to reuse some the functions that you create here in the next part(s).

1. __Download__ [listutils.py](listutils.py) by right-clicking and choosing `Save As`
2. Then write the following functions...

<hr>

#### get_duplicates(lst)

__Parameters__:

* `lst` - a list that will be searched for duplicate values

__Return Value__:

* a new list containing the elements that occur more than once in the original list

__Description__:

`get_duplicates` will return an entirely new list consisting of the elements in the original list passed in, `lst`, that occur more than once (that are repeated / duplicated). Each of these elements should appear only once in the newly returned list. For example, if the original list were `['cat', 'cat', 'cat', 'cat', 'dog', 'bat', 'ant', 'ant']`, then the resulting list would be `['cat', 'ant']` because `cat` and `ant` occur more than once.

<div class="hint" markdown="block">
1. Because we're returning a new list...
2. Start off with creating a new list and using it as an accumulator
3. Loop over the incoming list (the argument passed in)
4. Find a way to determine if each element occurs more than once
    * you can use a list method to do this
    * if you do this manually, you may have to nest a loop within another loop
5. Make sure to only include each repeated element only once in the new list
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>duplicates = get_duplicates([1, 2, 3, 1, 4, 2])
print(duplicates) # --> [1, 2] because both 1 and 2 have duplicates
</code></pre>

<hr>

#### has_duplicates(lst)

__Parameters__:

* `lst` - a list that will be searched for duplicate values

__Return Value__:

* `True` if the `lst` passed in has duplicate values, `False` otherwise

__Description__:

`has_duplicates` will return a boolean value, `True` or `False`, depending on whether or not the list passed in as an argument has at least one element that occurs more than once

<div class="hint" markdown="block">
1. An easy way to implement this is to call the previous function, `get_duplicates`
2. ... and you can use the results to determine what boolean value to send back
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>result1 = has_duplicates([1, 2, 3, 1, 4]))
print(result1) # --> True
result2 = has_duplicates([1, 2, 3, 4, 5]))
print(result2) # --> False
</code></pre>

<hr>


#### join_elements_with(glue, lst):

__Parameters__:

* `glue` - a string that will be placed between each element in the `lst` passed in
* `lst` - a list of elements that will be joined together to form a new string

__Return Value__:

* a string composed of all elements from `lst` connected by `glue`

__Description__:

`join_elements` takes a list and turns it into a string! It does this by creating a string that is composed of all of the elements in the original `lst` passed in as an argument and placing the string, `glue`, between each element. For example, if `lst` were `['Alice', 'Bob', 'Carol']`, and the `glue` were `---`, then the resulting string would be `Alice---Bob---Carol`.

__Note that there is built-in string method, called join, that already does this__. ⚠️ Do not use the built-in `join` method to write yours.

It may be helpful to find out if you're looking at the last element in the list. One way to do this, with the concepts that we already know, is to use a simple count to keep track of which element the loop is on. Another alternative is to use a `for` loop with a `range` where the range generates every possible index in the list, rather than looping over the list itself. Lastly, for those looking for a challenge, try to find out how to use the `enumerate` built-in function!

<div class="hint" markdown="block">
1. start with an empty string as an accumulator
2. it may be a good idea to have a counter as well to determine which element you're on
3. don't add the glue string if you're on the last element
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>result = join_elements_with('X', ['cat', 'dog', 'bat'])
print(result) # --> catXdogXbat
</code></pre>

<hr>

#### fill(size, fill_value=0)

__Parameters__:

* `size` - an `int` specifying the number of elements in the new list
* `fill_value` - a value of any type to fill the list with
	* the default value should be 0
	* assume that value will be some immutable type, like an `int`, `float` or `str`
	* (you don't have to worry about repeating nested lists, for example)

__Return Value__:

* a new `list` with length `size` elements, each with value, `fill_value` 

__Description__:

Create a new list filled with `fill_value`, `size` number of times

<div class="hint" markdown="block">
Create a new list and either:

1. use this list as an accumulator 
2. create the list with an initial value and repeat it

</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>
lst1 = fill(5)        # [0, 0, 0, 0, 0]
lst2 = fill(3, 'hi')  # ['hi', 'hi', 'hi']
</code></pre>

<hr>

#### random_choose(lst):

__Parameters__:

* `lst` - a list of elements to randomly choose a value from

__Return Value__:

* one of the elements from the original list

__Description__:

`random_choose` returns a random element from the list, `lst`, passed in as an argument. You can use the `random` module's `randint` function to do this.

__Note that the random module actually already has a function that does this, called choose__. ⚠️ Do not use `random.choose` in your implementation (though, again, `random.randint` is ok).

<div class="hint" markdown="block">
1. Given a list of n elements, what are the possible indexes (what is the min and max)?
2. Once you know the possible indexes, you can use `randint` to generate a number that falls within these indexes
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>weekdays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri']
weekday = random_choose(weekdays)

# should print out a single weekday from list of weekdays
print(weekday) 
</code></pre>

<hr>

#### random_fill(min_val, max_val, list_length)

__Parameters__:

* `min_val` - the minimum value for each randomly generated integer in new list
* `max_val` - the maximum value for each randomly generated integer in new list
* `list_length` - the number of elements in the newly generated list

__Return Value__:

* a `list` that consists of randomly generated integers

__Description__:

`random_fill` will create a new list with `list_length` elements in it. Each element will be a randomly generated integer between `min_val` and `max_val` inclusive. 

<div class="hint" markdown="block">
1. Because we're creating a new list, start off with a new empty list
2. A `for` loop will allow you to repeat code a specific number of times
3. On each iteration of your loop, generate a random integer that falls between `min_val` and `max_val` inclusive
4. Add this new integer to your list
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>new_list = random_fill(1, 10, 4)

# should print out a list with 4 elements... 
# each w/ number from 1 - 10
print(new_list) 
</code></pre>

<hr>

#### stringify_elements(lst)

__Parameters__:

* `lst` - a list that has elements that will be converted to strings

__Return Value__:

* a `list` that consists of strings

__Description__:

`stringify_elements` will create a new list composed only of string versions of the elements in the original list. For example, the list `[1, 2, 3]` would result in `['1', '2', '3']` being returned


<div class="hint" markdown="block">
1. Because we're creating a new list, start off with a new empty list
2. This will be your accumulator... 
3. Append a random number to your list on each iteration of the loop
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>result = stringify_elements([1, 2, 3])
print(result) # --> should print out ['1', '2', '3'] (all elements are strings!)
</code></pre>


<hr>


#### mean(lst)

__Parameters__:

* `lst` - a `list` of values (you can assume values will all be numeric, so no validation required)

__Return Value__:

* a `float`

__Description__:

Returns the average of all numbers in list. ⚠️ __Do not use `sum` in your implementation__

__Example Usage__:

<pre><code data-trim contenteditable>print(mean([1, 2, 3, 4, 5])) # 3
</code></pre>


<hr>


## Part 2 - Option #1 - syllabic_poetry.py

For part 2, you can __choose two out of three options__ to do, with the third as extra credit

1. generate syllabic poetry (this option) OR...
2. verify the "birthday" paradox using a simulation 
3. make some drawing functions with turtle

For this option, #1, you'll be writing a program that generates [syllabic poetry](https://en.wikipedia.org/wiki/Syllabic_verse) based on a provided list of words which will be provided to you as an _actual_ Python list of lists in the code to download. Your program will generate one of the following based on input from the user:

1. [haiku](https://en.wikipedia.org/wiki/Haiku)
2. [tanka](https://en.wikipedia.org/wiki/Tanka)
3. a 5 line syllabic poem with a random number of syllables per line
4. a poem whose lines and syllables per line are supplied by the user

Your program will ensure that the poetry generated adheres to the number of syllables required by the poem specified (for example, in a haiku, there would be 17 syllables in 3 lines: 5, 7 and 5. However, content will not be taken into consideration.

__The words provided will be in a format of a list of lists__. The outer list will contain seven sub lists of words. Each inner list represents a collection of words with a specific number of syllables. The number of syllables is based on the position of the inner list. The 1st list (at index 0) will have words that have 1 syllable, the 2nd list (and index 1) will have words that have 2 syllables, etc.

Here's a short example, with ellipsis representing additional elements (there are more than 2 words in each sub list, and there are 7 sub lists:

<pre><code data-trim contenteditable> # 1 syllable words     2 syllable words
[['age', 'roof', ...], ['stunner', 'sucrose', ...],  ...]
</code></pre>

Assuming that the variable that contains this list of lists is called `available_words`, to retrieve a list of 2 syllables words, use `available_words[1]`. To retrieve the word `stunner`, use `available_words[1][0]` __Feel free to modify this list of lists to suit the kind of content you'd like your poetry generator to create!__

To write this program: 

1. __Download__ [syllabic_poetry.py](syllabic_poetry.py) by right-clicking and choosing `Save As`
2. Write the following functions to help with your program
    * `generate_word`
    * `generate_line`
    * `generate_lines`
    * __feel free to `import` your `listutils` module from part 1 if you think any of those functions will be useful__
    * you can write more functions if you want!
3. write an interactive program that asks the user to specify what kind of syllabic poetry to create

<hr>

#### generate_word(syllables_in_word)

__Parameters__:

* `syllables_in_word` - the number of syllables in the word to be generated

__Return Value__:

* a `string` - a randomly chosen word composed of the number of syllables specified by `syllables_in_word`... return `None` if the number of syllables given is not between 1 and 7 inclusive

__Description__:

`generate_word` is a function that is partially implemented. It contains a local variable that holds a list of lists. Each inner list is a list of strings. The position of the inner list in the containing list determines the number of syllables in each word that it has. The list of lists is partially shown below:


<pre><code data-trim contenteditable># a local variable, available_words, within the generate_word 
# function will have the following list of lists
# 1 syllable words      2 syllable words          
[['age', 'roof', ...], ['stunner', 'sucrose', ...], ...]
</code></pre>

Again, this list is already present in the file that you download. However, you can __modify this word list to shape the content of the poetry your program generates__. To complete the implementation, you will use the integer passed in as an argument, `syllables_in_word`, to randomly choose an element from `available` words. This randomly chosen word should be returned by the function.

Assume that the argument passed in is a number. However, if the number of syllables given is less than one or more than seven, do not return anything (or return `None`).


<div class="hint" markdown="block">
1. First, check if the number passed in is valid
2. If it is... then find the correct sublist by using that number
3. Finally, to retrieve a random element from the list, you can use one of the functions that you created in part 1!
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>word = generate_word(3)
another_word = generate_word(1)

# the following prints out a three syllable word
# ... and a one syllable word (randomly chosen from
# a set of words)
print(word, another_word) # --> prints out randomly and word

# this will return None because the number of syllables is less than 1
yet_another_word = generate_word(0) # --> None!
</code></pre>

<hr>

#### generate_line(syllables_in_line)

__Parameters__:

* `syllables_in_line` - the total number of syllables in the line of poetry to generate

__Return Value__:

* a `string` that represents a series of words whose total number of syllables is equal to `syllables_in_line`

__Description__:

`generate_line` will create a string that contains a series of words whose total number of syllables is equal to the integer passed in, `syllables_in_line`. Each word in the series is randomly generated, and the number of syllables of each word is random as well, as long as it fits within the total number of syllables.

For example, if the number 5 is passed in, this function will generate a string as a sequence of words with the total number of syllables equal to 5. This means that the combination of words may vary. Here are some potential combinations of words that all add up to 5 syllables:

* team bureau slime rare (1 + 2 + 1 + 1)
* immoveable age (4 + 1)
* wearability (5)



<div class="hint" markdown="block">
One possible algorithm for doing this is:

<pre><code data-trim contenteditable>while line_syllables < syllables_required:
  max_syllables_word = 7:
  if syllables_required - cur_syllables< 7:
    max_syllables_word = syllables_required - cur_syllables
  generate word whose max syllables fits criteria above
  add word to line
  update current syllable count
</code></pre>

1. remember to set up accumulators for current syllable count and your line
2. use a while loop as shown above
3. update your accumulators within the body of the while loop
4. use your previously created `generate_word` function

</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>line = generate_line(5):
print(line) # --> immoveable age (or some other random series of words!)
</code></pre>

<hr>

#### generate_lines(all_lines)

__Parameters__:

* `all_lines` - a `list` of numbers representing the number of syllables in each line; a 5 element list would mean that there are 5 lines in the poem... and each element in that list would represent the number of syllables for that specific line

__Return Value__:

* a new `list` that contains a line of words per element, with each line adhering to the number of syllables specified by the `list`, `all_lines`, passed in

__Description__:

`generate_lines` will create a `list` of lines of poetry based on the `list` of syllables per line passed in. The poem will be generated by choosing the words randomly, but still adhering the number of syllables specified per line. For example, if the `list` passed in is [5, 7, 5], then a poem with 3 lines, with the first line having 5 syllables, the 2nd line having 7 syllables and the last line, having 5 syllables, would be created.

The poem that is generated will be a `list` of lines. There should be the same number of lines as the number of elements in the `list` passed in.

<div class="hint" markdown="block">
1. use your `generate_line` implementation above
2. call it using each element in the `all_lines` list passed in
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable># the following should return a list of lines of a
# randomly generated poem...
# for example, it may return (as a single list,
# and formatted with new lines for readability):
# [  
#    'persuasive pudding', 
#    'misauthorization flab', 
#     'acceptable queue'
# ]
syllables_per_line = [5, 7, 5]
generate_lines(syllables_per_line)
</code></pre>

<hr>

#### Ask the User to Generate a Poem!

Using all of the functions that you defined above, create a program that asks the user what kind of poem they would like to generate:

<pre><code data-trim contenteditable>I would like to write some poetry for you. Would you like a...
  * (h)aiku
  * (t)anka
  * (r)andom 5 line poem, or do you want to
  * (s)pecify lines and syllables for each line?
</code></pre>

__Once the user chooses the kind of poem to generate, the program will print out__:

1. An abbreviated version of the number of syllables per line, separated by dashes
    * for example `5-7-5` is a three line poem with 5 syllables, 7, and finally 5 again on the last line
    * the output should look like `Here is your poem (5-7-5):`
2. The poem itself

__The poem that the program generates will be based on the input from the user__:

1. If the user types in `h` or `t`, generate a haiku and a tanka poem respectively. 
    * A Haiku has a 5-7-5 pattern of syllables per line (5 syllables for the first line, 7 for the second, 5 again for the last). 
        * Here's an example of what a haiku may look like
            <pre><code data-trim contenteditable>Here is your poem (5-7-5):
=====
flab lien trimming bowls
collapsibility big
second clearheaded
</code></pre>
    * Tanka has 5-7-5-7-7 pattern. 
        * And... an example of tanka
            <pre><code data-trim contenteditable>clearheaded chopper begone imprint their
hipper nonrevolution henchman fig
sprightliest trimming chit
cheekily
queue forbiddingness queue ate
</code></pre>
2. If the user chooses `r`, then generate a 5 line poem with a random number of syllables per line (though, cap the syllables per line to a reasonable amount)
    * Here's an example of a randomly generated 5 line poem:
        <pre><code data-trim contenteditable>Here is your poem (5-7-5-7-7):
=====
brail cathartic team
electrometallurgist
seditious rune rone
unruinable crouton
acceptable brown brown stir
</code></pre>
3. Finally, if the user chooses `s`, then they will be allowed to specify the number of lines and syllables for each line by asking more questions:
    1. ask for the number of syllables for the line, and __include the line number__ in the question
        <pre><code data-trim contenteditable>How many syllables for lines 1?
</code></pre>
    2. then... __print out the current number of lines__ and ask if they'd like to continue, 
        <pre><code data-trim contenteditable>There are currently 1 lines. Add another line (y/n)?
</code></pre>
    3. if the answer is `y`, then go back to 1 to ask for the number of syllables in the next line
    4. a full example interaction is below (note that the line number and current number of lines are specified)
        <pre><code data-trim contenteditable>How many syllables for line 1?
>3
There are currently 1 lines. Add another line (y/n)?
>y
How many syllables for lines 2?
>3
There are currently 2 lines. Add another line (y/n)?
>y
How many syllables for lines 3?
>12
There are currently 3 lines. Add another line (y/n)?
>n
</code></pre>
        * the line number is specified
        * the current line count is displayed
    5. An example of the poem that this generates may look like:
        <pre><code data-trim contenteditable>box nought depth
prevention
vapourizing profitably stunner rode miss
</code></pre>
4. If the user does not type valid option, print out `ERROR` and your favorite poem about making a mistake
    <pre><code data-trim contenteditable>A crash reduces
Your expensive computer
To a simple stone.
</code></pre>
    (From [Netlingo haiku poetry error messages](http://www.netlingo.com/word/haiku-poetry-error-messages.php))

<hr>

## Part 2 - Option #2 - mydate.py and birthday.py

For part 2, you can __choose from one of two options__ or __do both__:

1. generate syllabic poetry OR...
2. verify the "birthday" paradox using a simulation (this option!)
3. `drawing.py`: create 3 functions for drawing shapes with turtle

Apparently, in a set of 23 randomly chosen people, there's a _pretty good chance_ that two of those people will have the same birthday! Yes, it's _actually_ true, and it's called the [Birthday Problem or the Birthday Paradox](https://en.wikipedia.org/wiki/Birthday_problem). [betterexplained.com](https://betterexplained.com/articles/understanding-the-birthday-paradox/) has a good write-up on why, but we'll use a computer simulation to approximate this probability. We'll create tools to randomly generate dates, and then we'll see if any month and day combinations match.

You'll be doing this in two parts:

1. write a bunch of functions to help with creating dates
2. create an interactive program that allows you to run the simulation multiple times 

1. __Download__ [mydate.py](mydate.py) and [birthday.py](birthday.py) by right-clicking and choosing `Save As`
2. Write the following functions in `mydate.py` to help implement your program:
    * `is_valid_month_num(n)`
    * `month_num_to_string(month_num)`
    * `date_to_string(date_list)`
    * `dates_to_strings(date_list)`
    * `remove_years(date_list)`
    * `is_leap_year(year)`
    * `get_num_days_in_month`
    * `generate_date(start_year, end_year)`
    * you can use your `mylist.py` as a module if any of those functions are helpful
    * you can write more functions if you want!
3. Using your previously implemented `mydate.py` as a module, import it and use it to help write `birthday.py`
    * In `birthday.py`, you'll write a simulation by generating random birthdays
    * The simulation will be an interactive program that asks the user how many trials to run... as well as other parameters for generating birthdays for a group of people
    * The percentage of times that at least one duplicate occurs should be printed out at the end

#### is_valid_month_num(n)

__Parameters__:

* `n` - an integer representing a month, with 1 being January and 12 being December

__Return Value__:

* a `boolean` - `True` if number passed in is between 1 and 12 inclusive, `False` otherwise

__Description__:

`is_valid_month_num` will take a month in numeric format and return a boolean value based on whether that number is a valid month (1 through 12, inclusive)

__Example Usage__:

<pre><code data-trim contenteditable>result1 = is_valid_month_num(3) 
print(result1) # True
result2 = is_valid_month_num(37) 
print(result2) # False
</code></pre>

<hr>
    
#### month_num_to_string(month_num)

__Parameters__:

* `month_num` - an integer representing a month, with 1 being January and 12 being December

__Return Value__:

* a `string` - the month name corresponding to the number passed in, `None` if the number passed in is invalid

__Description__:

`month_num_to_string` will take a month in numeric format and return a string representing the month's name (given a valid month number). If the month number passed in is not valid, `None` is returned (either implicitly by not returning anything or by explicitly returning `None`). 

<div class="hint" markdown="block">A simple way to implement this would be to create a list of month names within your function and send back the appropriate one based on position.
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>result1 = month_num_to_string(1) 
print(result1) # 'January'
result2 = month_num_to_string(10) 
print(result2) # 'October'
result3 = month_num_to_string(234) 
print(result3) # None
</code></pre>

<hr>

#### date_to_string(date_list)

__Parameters__:

* `date_list` - a three-element `list` containing integers representing a year, month and day; for example, `[2012, 3, 14]` represents March 14th, 2012

__Return Value__:

* a `string` - the string version of the date passed in as the original `list`; the format of the string returned is month_name day_number, year: March 14th, 2012


__Description__:

`date_to_string` assumes that it will be passed a `list` containing valid numbers for year, month and day (you will not have to check the numbers passed in). Given `[YEAR_NUMBER, MONTH_NUMBER, DAY_NUMBER]`, this function will construct a string in the format of `MONTH_NAME DAY_NUMBER, YEAR_NUMBER` where `MONTH_NAME` is determined by using one of the previous function with `MONTH_NUMBER`. 

For example, `[1979, 10, 7]` should give back `'October 7, 1979'`.

<div class="hint" markdown="block">
1. Again, use one of the previously implemented functions for this
2. No looping is required!
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>date_to_string([1979, 10, 7]) 
# returns the string: October 7, 1979
</code></pre>

<hr>

#### dates_to_strings(list_of_date_lists)

__Parameters__:

* `list_of_date_lists` - a `list` containing dates, with each date being a sub list of composed of three elements (as described in `date_to_string`)

__Return Value__:

* a `list` - a `list` of string versions of each sub list (date) from the original list passed in

__Description__:

`dates_to_strings` converts a list of lists to a list of strings. Each inner list in the list of lists is a date in the format of a three-element list (as explained in the previous function). The result is a list of strings, with each string representing one of the original dates in the list passed in. For example, `[[1979, 10, 7], [2000, 02, 20]]` should give back `['October 7, 1979', 'February 20, 2000']`.

__Example Usage__:

<pre><code data-trim contenteditable>res = dates_to_strings([[1979, 10, 7], [2000, 02, 20]]) 
print(res) # ['October 7, 1979', 'February 20, 2000']
</code></pre>

<hr>

#### remove_years(list_of_date_lists)

__Parameters__:

* `list_of_date_lists` - a `list` containing dates, with each date being a sub list composed of three elements (as described in date_to_string)

__Return Value__:

* a `list` - a new `list` with 2-element sub lists representing a month and a day (year is removed)

__Description__:

`remove_years` creates a new `list` with the year element removed for every sub list in a list of date lists. This essentially converts a list of three-element lists to a list of two-element lists.

__Example Usage__:

<pre><code data-trim contenteditable>res = remove_years([[1979, 10, 7], [2000, 02, 20]]) 
print(res) # [[10, 7], [2, 20]]
</code></pre>

<hr>

#### is_leap_year(year)

__Parameters__:

* `year` - an `int` specifying the year to check

__Return Value__:

* a `boolean` - `True` if the year, `year`, is a leap year, `False` otherwise

__Description__:

Determines whether a year is a leap year or not using [this algorithm from microsoft](https://support.microsoft.com/en-us/help/214019/method-to-determine-whether-a-year-is-a-leap-year). Returns `True` or `False` accordingly.

<div class="hint" markdown="block">
1. a lot of nested if statements may be helpful
2. after getting it to work with nested if statements, you can rewrite it more easily so that it contains no nesting!
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>for year in [1988, 1992, 1996, 1600, 2000, 2400]:
    print(is_leap_year(year)) # True for each one!

for year in [1700, 1800, 1900, 2100, 2200, 2300, 2500, 2600]:
    print(is_leap_year(year)) # False for each one!
</code></pre>

<hr>

#### get_num_days_in_month(month_num, year)

__Parameters__:

* `month_num` - an `int` specifying the month number
* `year` - an `int` specifying the year to check

__Return Value__:

* an `int` - the number of days for the month represented by `month_num` at year, `year` or `None` if the `month_num` passed in is not valid

__Description__:

Determines the number of days in a month given a month (in the format of a number from 1 through 12), as `month_num` and a year as `year`. Leap years should be taken into account (February may have 28 or 29 days). You can map months with their days by storing number of days in a list. The position of the number of days in the list will help determine what month it's in. If the month number passed in is not between 1 and 12, inclusive, then give back `None` (this could be done implicitly by no having a `return` or by explicitly returning `None`).

<div class="hint" markdown="block">
1. A list that just stores days for every month may help
    * the number at index 0, or the first element, will store the number of days for January
    * the number at index 11, or the last element, will store the number of days for December
    * `[31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]`
    * note that February has 28 by default, but that could change depending on whether or not it's a leap year
2. Using `month_num` to generate the appropriate index, pull out the correct number of days
3. Watch out for February and invalid month numbers, though!
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>get_num_days_in_month(2, 1988) # 29
get_num_days_in_month(2, 1900) # 28
get_num_days_in_month(11, 1900) # 30
get_num_days_in_month(12, 1900) # 31
get_num_days_in_month(1, 1900) # 31
get_num_days_in_month(30, 1999) # None
</code></pre>

<hr>

#### generate_date(start_year, end_year)

__Parameters__:

* `start_year` - an `int` specifying the minimum year that the randomly generated date may have
* `end_year` - an `int` specifying the maximum year that the randomly generated date may have

__Return Value__:

* a `list` - a new `list` consisting of 3 `int`s: a year, month number, and a day

__Description__:

`generate_date` creates a date with random, month, day and year using other functions from this module. The date generated must have a year that falls within `start_year` and `end_year`. It must also generate a valid month number (1 through 12)... and lastly a valid number of days (including a valid number of days for February during leap years).

<div class="hint" markdown="block">
</div><br>

__Example Usage__:

<pre><code data-trim contenteditable>date = generate_date(2015, 2017) 
print(date) # a random 3 element list, like: [2017, 9, 5]
</code></pre>

<hr>


#### Interactive Program (`birthday.py`)

Once you've finished your functions, write an interactive program that simulates creating a group of people, each with a random birthday. To do this:


1. __Download__ [birthday.py](birthday.py) if you haven't done so already
2. `import` your `mydate` module (also `import` `listutils` if you find any of those functions useful)
3. First, ask how many times the simulation should be run
    <pre><code data-trim contenteditable>How many times should I run the simulation?
</code></pre>
4. Then, ask wow many birthdays should be generated 
    <pre><code data-trim contenteditable>How many birthdays should I generate per trial?
</code></pre>
5. Once you have the user input...
6. __repeat the following based on the number of trials specified by the user__:
    1. generate the number of birthdays specified (you can use and start and end year to create these dates)
    2. remove the years from the dates
    3. find the dates that occur more than once
    4. print out the following:
        * the trial number
        * the number of dates that occur more than once
        * and a comma separated list of the duplicate dates, in parentheses
    5. here's some example output:
        <pre><code data-trim contenteditable>Trial #1: 2 dates occur more than once! (August 2, April 24)
Trial #2: 1 date occurs more than once! (September 16)
How many times should I run the simulation?
Trial #3: No dates are the same.
.
.
.
</code></pre>
7. After running all of the trials specified...
    * calculate the probability that there will be duplicates by...
    * taking the count of trials where at least one date occurred more than once
    * ...and dividing that by the number of trials specified
    * output the resulting number as a percentage with the following information:
        * the total number of trials
        * the total number of trials that had a birthday that occurred more than once
        * the probability of a duplicate
        * the number of birthdays generated for every trial
    * for example:
        <pre><code data-trim contenteditable>Results:
=====
Out of 7 trials, 4 had dates that were repeated
We can conclude that you have a 57.14% chance of sharing a birthday with someone if you are in a group of 23 people
</code></pre>
8. An example of a full run of the program is below:
<pre><code data-trim contenteditable>How many times should I run the simulation?
>7
How many birthdays should I generate per trial?
>23
Trial #1: 2 dates occur more than once! (August 2, April 24)
Trial #2: 1 date occurs more than once! (September 16)
Trial #3: No dates are the same.
Trial #4: 2 dates occur more than once! (February 4, July 21)
Trial #5: No dates are the same.
Trial #6: 1 date occurs more than once! (September 14)
Trial #7: No dates are the same.

Results:
=====
Out of 7 trials, 4 had dates that were repeated
We can conclude that you have a 57.14% chance of sharing a birthday with someone if you are in a group of 23 people
</code></pre>




## Part 2 - Option #3 - drawing.py 


`def line(t, coord1, coord2)`

* t is a turtle object passed in
* coord1 and coord2 are 2-element lists that represent x, y coordinates
* draws a line from coord1 to cord2

`def poly(t, *coords)`

* t is a turtle object passed in
* *\coords is any number of x, y coordinates... each as a 2-element list
* draws a polygon based on coords (will close off polygon by drawing a line from last coord to first)

`def rectangle(t, coord, width, height, color)`

* t is a turtle object passed in
* coord is upper left corner of rectangle
* assume width and height are ints
* color is the color to fill with
* (use t.color('red'), t.begin_fill(), and t.end_fill())

Example code:

```
import turtle
t = turtle.Turtle()
wn = turtle.Screen()
rectangle(t, [0, 0], 100, 200, 'green')
t.color('blue')
poly(t, [100, 100], [50, 50], [-50, 50])
poly(t, [-100, 100], [-100, 50], [-200, 50], [-200, 100], [-150, 0])
#poly(t, [0, 0], 100, 200)
wn.mainloop()

```
