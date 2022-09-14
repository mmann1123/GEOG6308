<!-- all images are stored in github/GEOG6308 -->
# How to do your ipynb homework

We are going to use `.ipynb` files to do some of your homework, this will allow me to give you prompt feedback on your progress.  The only trick however is that `.ipynb` aren't readable as a text file like `.py` files.  So we will need to use an IDE to open it, there are a number of them available, but I generally suggest using VScode or if you want something less intimidating Thonny.

We have a number of options for doing your homework, online via citrix, in person in the SAL lab, or on your laptop. 

**Recommended**

A) VScode (or Thonny) via citrix 
    - Go to [https://apps.ccas.gwu.edu](https://apps.ccas.gwu.edu/)
    - Click on VScode

B) VScode (or Thonny) in the SAL 
    - See [SAL schedule here](https://calendar.google.com/calendar/u/0/embed?src=email.gwu.edu_c8a8miomq15880o3n5ptm94knc@group.calendar.google.com&ctz=America/New_York)

C) VScode on your laptop [how to install vscode](https://mmann1123.github.io/GEOG6308/vscode_notebook_start.html)

 

**Also Possible**

A) [*Jupyter Notebook on your laptop*](https://mmann1123.github.io/GEOG6308/jupyter_notebook_start.html)

B) [*VScode on your laptop*](https://mmann1123.github.io/GEOG6308/vscode_notebook_start.html)



## Getting Started

1) Change the name of the `.ipynb` file following the directions at the top of the file. This can be done inside the assignment by clicking on the name in the upper left corner. Typically the name will follow this convension: (geo1_emailusername_assignment).

IT IS IMPORTANT YOU CHANGE THE NAME OF YOUR HOMEWORK BEFORE SUBMISSION. PLEASE DO THIS. 

![rename](https://github.com/mmann1123/GEOG6308/blob/main/rename.png?raw=true)

2) Enter your name and any students you collaborated with in the top cell

![name](https://github.com/mmann1123/GEOG6308/blob/main/fill_name.png?raw=tru)

 
3) Fill your answers in the section starting with `# YOUR CODE HERE`

This will require you to *remove* or `#comment out` the following code snippet:

```
raise NotImplementedError()
```

If you leave `raise NotImplementedError()` you might loose points. 

# What's a Function?
Many of these assignments require the use of a `function`. Functions are just a way of assigning a name to a useful peice of code we want to use again and again. For instance `buffer` is a function we use all the time in arcmap.  

In python we could sketch out the buffer function as follows:

```python
def buffer(a_line_or_polygon, distance):

    buffered_object =  a_line_or_polygon.buffer(distance)

    return buffered_object
```

In this case we defined a function that takes an input of a shapefile stored in `a_line_or_polygon`, then we increase the boundary by `distance` and store the new polygon in `buffered_object`.

This just DEFINES the function so that we can use it later. It doesn't EXECUTE it.

To use the function we need to execute it:

```python
a_buffered_shp = buffer(a_line_or_polygon = 'path/to/file/line.shp',
       distance = 100)
```

After we run the function `a_buffered_shp` will hold the buffered output that was `return`ed from the function. 

In our homework we need to define a function and execute it for *almost* all questions. I will however set up the function, give it a name, and tell you what object needs to be returned back to me for grading. 

# General Approach

There will be a series of questions, some of which will be autograded and others that will be manually graded. 

## Questions without using functions

Early on in the semester we won't be using formulas in the questions. Instead I will ask you to create a variable of a certain type with specific values stored inside. In this example I will prompt you to store the square of 1,2,3,4 using a `for` loop, and request the output is stored as a `list`

![no function example](https://github.com/mmann1123/GEOG6308/raw/main/no_function.png?raw=true)

Your answer to the question might look something like this:

![no function answer](https://github.com/mmann1123/GEOG6308/raw/main/no_function_answer.png?raw=true)

You can also confirm the datatype of the variable you created using the function `type()`. Here I confirm that its stored as a `list`:

![confirm its a list](https://github.com/mmann1123/GEOG6308/raw/main/a_list.png?raw=true)

I will then use an autograder to evaluate the contents and type of `alist`. See the sections below for more about the autograder tests. 

Later on in the semester we will use functions to store your answers. PLEASE READ THIS SECTION, the 'correct answer' and 'incorrect' answers will be relevant to all your work. 

## Questions with functions
A question will take the following form. I will provide a specific prompt. 

![assignment](https://github.com/mmann1123/GEOG6308/blob/main/example_question.png?raw=true)

In the example above you need to write code to generate an object called `alist` in your function and return it. I will use your function to generate `alist` and return it to the autograder. 

If I set up, or ask for a function DO NOT DELETE `return alist`, or if you do, add it back.



## Correct Answers
In this example we will write a bit of code that will correctly answers the question.  

![correct](https://github.com/mmann1123/GEOG6308/blob/main/example_correct.png?raw=true)

Note that running the function `squares(10)` provides to desired outcome. 

This answer is validated by the autograder with a series of `assert` tests.  If your answer is 100% correct, you should not throw any error when the assertion tests are run. 

The following assertion tests were completed without throwing any errors. This is what we want!

![assert1](https://github.com/mmann1123/GEOG6308/blob/main/question_assert1.png?raw=true)

## Incorrect Answers

For this question there is another cell with assertion tests that will fail in this case. Here the tests are trying to see if you are handling invalid inputs from the user. For instance setting n=0 or n=-1 should throw an errror. 

![assert2](https://github.com/mmann1123/GEOG6308/blob/main/question_assert2.png?raw=true)

Here the assertion tests are pointing out that we allowed invalid inputs! We should go back to our code and fix it until we are no longer getting errors from this cell of tests. 

# Autograder Tips
The objective is to: 
- Run Cell > Run All, without any errors

How do we do it:
- Create or `return` the object requested in the prompt
- make sure your object is exactly as requested

Tricks:
- You can always add more cells to experiment in, just make sure you put your final answer in the correct place, and *delete* any cells that you don't need in the end. 
- You can always print an object to the screen `print(an_object_name)`, or look at its type `type(an_object_name)`

