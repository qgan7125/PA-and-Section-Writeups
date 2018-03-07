# PA6-Garden-Key (Status: Posted Feb 28th at 10:30pm, Clarification on errors March 7 7:30am)
PA6 key and initial writeup draft.

## Learning Objectives

The goal of this assignment is to design a class hierarchy to solve
a problem, implement that hierarchy, use polymorphism, and use
two-dimensional arrays.


What is a class hierarchy you ask? Read about it on [Wikipedia](https://en.wikipedia.org/wiki/Class_hierarchy).
The class diagram you will be submitting will be a simplified version of the UML
class diagrams.  There are many resources on the internet for UML class diagrams.
See all the 2/28/18 class notes for the format expected in this class for PA6.

## Garden Simulation

The problem you will be solving is a garden simulation.  The simulation will read
commands like PLANT, PRINT, GROW, and HARVEST from a file and execute those commands.
The garden that you will be implementing will consist of a number of columns and
rows of plots.  Within each plot there can exist a single plant, which is represented
with a 5x5 grid of cells. Plants are divided up into three different categories:
trees, flowers, and vegetables, all of which have unique characteristics.  
For example, trees grow up, vegetables grow down, and flowers bloom as they grow.

## The Assignment

This is a **two-week assignment**.  The class inheritance diagram will be all that
is due Tuesday March 13th at 11:30 am to both Aropa AND Gradescope.
We make suggestions as to what to implement the first week and then the second week,
but you will be responsible for managing your own time.
The rest of the assignment is due Monday March 19th. 

* Class inheritance diagram: Create this diagram however you would like
  (draw it by hand, use software, etc.).  You need to create a pdf file
  of it and submit it to Aropa AND Gradescope.
    * See (https://gradescope.com/help#help-center-item-student-scanning)
      for some suggestions of how to scan in a document with your phone
      if you plan to produce your pdf by taking a picture of it.
    * You will be building on PA6 for PA8 and PA9.  In PA8 and PA9, you
      will be encouraged to use the model-view-controller pattern.
      Feel free to look that up ahead of time.  You are not required to
      know it until we cover it though.
  * March 1st 7:30am, the Aropa and Gradescope for the PA6 class inheritance
    diagram are ready to accept submissions.
  * During Spring Break the Gradescope submission for the PA6 program will be posted.
 
* Your main program, which must be named PA6Main.java, will need to accept the name
  of an input file on the command line.

* The input file will contain all of the garden initialization settings
  and the commands to simulate.  Here is an example input file.
```
rows: 1
cols: 1

PLANT (0,0) banana
PRINT
GROW 1
print
```
Here is the output for the example:  
```
> PRINT
.....
.....
.....
.....
..b..

> GROW 1

> PRINT
.....
.....
.....
..b..
..b..
```
The output should be printed to standard out.  See PublicTestCases/
for more input and output examples.

* The following are the types of specific plants that could be planted:

```
FLOWERS      TREES      VEGETABLES
-------      -----      ----------
Iris         Oak        Garlic
Lily         Willow     Zucchini
Rose         Banana     Tomato
Daisy        Coconut    Yam
Tulip        Pine       Lettuce
Sunflower
```

* The following are examples of representation arrays for different types of plants.
  For PA6, plants will be represented with ascii characters.  Use the lower
  case version of the first letter of the plant name.  For "Garlic" use 'g',
  for "Daisy" use 'd', etc.
  * Flowers should start in the middle of the 5x5 grid of cells in the
    plot it is planted in.  Each location in a plot is called a cell.
  * Vegetables should start at the top middle.
  * Trees should start at the bottom middle.

```
Rose
.....
..... 
..r..
.....
.....
```
```
Tomato
..t..
..... 
.....
.....
.....
```
```
Coconut
.....
..... 
.....
.....
..c..
```


* Commands that need to be implemented.  See the PublicTestCases/ for more examples.
  There are examples with PLANT, PRINT, and GROW.  Other command input and output
  examples will appear during Spring Break.

  * **The PLANT Command**<br/>
EXAMPLE USE: *PLANT (0,0) rose*<br/>
If the PLANT command is read, it should be followed by plot coordinates and the type of Plant to be planted.
Use this type to plant the correct subclass of plant into the garden at given plot coordinates.
The plot coordinates are given as row and column.  Both rows and columns start at 0.
Rows go down the screen, and columns go across the screen.  Each plot will itself contain 5 cells
(represented as characters).  There is a restriction that the number of cells across should
be less than or equal to 80, therefore the most plot columns allowed is 80/5 or 16.

  * **The PRINT Command**<br/>
EXAMPLE USE: *PRINT*<br/>
If the PRINT command is read, then the entire garden should be printed to standard out.

  * **The GROW Command**<br/>
EXAMPLE USE: *GROW 1*<br/>
If the GROW command is read, then each Plant should grow the specified number of times as seen in the input command.

  * **GROW [num] (x,y)**<br/>
EXAMPLE USE: *GROW 1 (2,3)*<br/>
Grow whichever Plant is located in the garden at position (x,y) num times. If there is nothing at this position
or the position is outside the size of the garden, print, "Can't grow there." and continue.

  * **GROW [num] [type]**<br/>
EXAMPLE USE: *GROW 1 rose*<br/>
Grow only Plants of the specified type num times.

  * **GROW [num] [Plant]**<br/>
EXAMPLE USE: *GROW 1 flower* <br/>
Grow only Plants of the specified class num times.
A plant cannot grow out of its plot.  No error will happen,
but growth should not occur outside the plot boundaries.
Plots also cannot run into each other.

  * **HARVEST**<br/>
Remove all Vegetables from the Garden.

  * **HARVEST (x,y)**<br/>
EXAMPLE USE: *HARVEST (2,3)*<br/>
Harvest Vegetable at location (x,y). If not a Vegetable or outside of Garden, 
print, "Can't harvest there." and continue.

  * **HARVEST [type]**<br/>
EXAMPLE USE: *HARVEST tomato*<br/>
Harvests all Vegetables of the specified type. If there are no Vegetables with that type, do nothing. 

  * **PICK**<br/>
Remove all Flowers from the Garden.

  * **PICK (x,y)**<br/>
EXAMPLE USE: *PICK (2,3)*<br/>
Pick Flower at location (x,y). If not a Flower or outside of Garden, print, "Can't pick there." and continue.

  * **PICK [type]**<br/>
EXAMPLE USE: *PICK rose*<br/>
Pick all Flowers of the specified type. If there are no Flowers with that type, do nothing. 

  * **CUT**<br/>
Remove all Trees from the Garden.

  * **CUT (x,y)**<br/>
EXAMPLE USE: *CUT (2,3)*<br/>
Cut Tree at location (x,y). If not a Tree or outside of Garden, print, "Can't cut there." and continue.

  * **CUT [type]**<br/>
EXAMPLE USE: *CUT PINE*<br/>
Cut all Trees of the specified type. If there are no Trees with that type, do nothing. 
  
* **Unique Class** 

Students will design their own plant type and show an example input and output that illustrates it 
in their README.md file.  This new plant should be different from Vegetable, Flower, and Tree, 
but still be usable alongside them within the garden and work with the commands
PLANT, GROW, and PRINT.

* Error Handling

  * Some of the commands above specify some error handling.
  
  * The garden should never be more than 80 characters across.  If it is print out
  the message "Too many plot columns." and then exit.  Think: How many characters across is
  each plot?
  
  * Other than the above specified errors, the input can be assumed well formed.

## Design Suggestions

We recommend the following:
  * A Garden object with a 2D array or list of plant objects.
  * A Plant class hierarchy of some kind.  The design for this is what will be submitted for
    peer review on Tuesday March 13th at 11:30 am to both Aropa AND Gradescope.
  * A Screen object with a 2D array of characters that each plant can
    print its current representation into.  The Screen object can then print everything
    to standard out. (Hint: what did you do in those drills due before Spring Break?)
    * **hint:** when copying over a Plants representation array place each cell at:
```
     [(Plant's row  * 5) + cell row][(Plant's col * size of plot) + cell col]
```
   into the Screen object's Array.



## Grading Criteria

Half of the PA6 grade will be correctness.  For this assignment, there
will be some private test cases on Gradescope used for grading.

The other half of the PA6 grade will be your decomposition and code clarity.
Twenty of these points will be on your class hierarchy diagram.

Decomposition

* Points will be taken off for copy, pasted, and edited code that
  should have been encapsulated in a method.

* **This program should use fewer than 10 .java files.**
  Each of these files should be (<200 lines).

* Each static method should be less than 30 lines.  This INCLUDES
  comments, but not the method header.  It is easier to read a 
  function if it can all fit on one screen.

* Make things as simple as possible.
  * Only use one Scanner instance.
  * Don't use lambda functions or other features in non-standard ways.
  * Avoid nested loops.
  * Avoid nesting conditionals.
  * Avoid chaining: see the Piazza post for more info


Code Clarity
* YOU should be able to read, understand, and explain your own code
  to someone else a couple days after you wrote it.
  * No magic numbers
  * No methods written to just get the test cases to work

* There needs to be a balance between no comments in the body of the
  methods and a comment for every line in the program.  Either extreme
  will result in points off.

* The file header should include instructions on how someone would
  use this program.  To use the program, one would need to know the
  input file format.

* Use meaningful variable names.  Loop iterators can
  be simple (i for integers, s for strings, n for numbers, etc.).

* The clearest code examples will be anonymously shown in class.

* The most obfuscated code examples will be anonymously shown in class
  with suggestions for improvement.


The coding style in terms of spacing, etc. should be done automatically
every time you save in Eclipse.  As long as you stick with those defaults,
the syntax style should be fine.


## Submission

Write your own code.  We will be using a tool that finds overly similar code.
This Spring 2018 semester in CS 210 we unfortunately have had academic
integrity cases.
I recommend that when talking with others about the assignment, do not write
anything down.

The class hierarchy diagram in pdf format is due Tuesday March 13th at 11:30 am
in Gradescope AND Aropa.

For PA6, you are **REQUIRED** to submit all of your java source files
to Gradescope before Monday March 19th at 11:30 am.
