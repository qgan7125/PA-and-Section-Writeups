# Section7-SudokuSearch-Writeup 

## Introduction 
The goal of today's section is to develop a deeper understanding of recursive
backtracking. We will be doing this by examining and coding an recursive backtracking search
for amore complicated problem, solving a Sudoku puzzle. 

Recall the recursive backtracking template: 

```
 void enumerate( problem params,current decision point, collection of decisions) {
            
            if all decisions have been made
                process this point in search space
                return
 
            for all possible local decisions at current decision point
                make local decision
                recursively call enumerate to make decision
	}
```

In order to apply recursive backtracking to a more complex problem, we will utilize
helper methods. The idea is to use helper methods to decompose the problem 
in a way that maintains the recursive backtracking template and keeps code clarity high. 

Also, it is helpful to have a general understanding of Sudoku. Sudoku is a logic
puzzle that is typically a 9x9 grid. This grid consists of nine 3x3 sub grids. 
Each row, column and sub grid should each contain only one instance of 1-9. 
Typically Sudoku puzzles have many squares pre-filled out so that there is only 
one solution possible. When solved by hand, logical elimination is used to fill 
the squares, however, an recursive backtracking can use brute force to find the answer. 

## Warm Up 

```
	2 4 6 | 7 A 8 | 3 1  
	3     |   9   |     2
	  9   |     4 | 6   8 
	_ _ _ | _ _ _ | _ _ _ 
	4 D 9 | 1 2 3 |      
	C 6   |     B | 8
	1   7 |     6 |     4
	_ _ _ | _ _ _ | _ _ _ 
	6 7   |     5 | 9     
	  1 3 | 9     |     7
	      | 3 4 7 |
```

## Setup

Go to the course webpage, click resources, and then click on the Section 7 URL. It will be 
the URL to the public start repository in the CS210 repository. Since you are going to clone 
the main repository, you will not be able to push to GitHub. At the end of section, you will 
need to upload your .java file to Gradescope for the output to be graded. 

Then do the following:

Click on the green "Clone or download" button on the right of the web page and copy the provided URL.

Import your Section 7 repository into Eclipse.

open Eclipse
File —> Import —> Git —> Projects from Git, Next, Clone URI, Next, paste in repository URL from github
Next, Select the master branch, Next, make the local destination /home/username/eclipse-workspace/Section7-SudokuSearch-yourgithubid.
Next, Import existing Eclipse projects, Next, Finish.
Now you are ready to start coding.

## The Assignment
Overview : Implement pieces of an recursive backtracking algorithm to complete the code to 
find a solution to a Sudoku puzzle. Upload to gradescope to check for correctness and
answer the conceptual questions to show your SL. 

### Part One - Decomposition 
After importing the section, your section leader will walk the class through the 
decomposition chosen for the problem. They will discuss how to check if all decisions 
have been made, where the decision point is being found and how pruning and 
backtracking is applicable to this solution. 

### Part Two - Implementation 
Complete the five functions with TODOs in them: inRow, inColumn, process, 
findUnassignedLoc and noConflicts. Additionally, fill in enumerate to match the 
recursive backtracking template as closely as possible. 

### Conceptual Questions 

Q1 

```
How is the decision point found? Where is it used in the problem and how is this different from 
the recursive backtracking template?
```

Q2

```
What function completes the pruning? 
```
