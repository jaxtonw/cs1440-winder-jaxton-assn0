# CS 1440 Assignment 0: Demo Project - Instructions

*   [How to Do This Assignment](#how-to-do-this-assignment)
*   [What We Look for When Grading](#what-we-look-for-when-grading)
*   [Program Requirements](#program-requirements)


## Previous Semester Assignment Statistics

Statistic                        | Value
--------------------------------:|:---------------
Average Hours Spent              | 2.56
% students thought this was Easy | 52.14%
... Medium                       | 43.57%
... Hard                         | 2.86%
... Too Hard/Did not complete    | 1.43%


## How to Do This Assignment

Follow the shell tutorial's instructions closely.

This repository includes a Python program that's not fully functional yet, along with its documentation. It showcases DuckieCorp's coding and documentation standards. Your task is to resolve a bug in the program and complete its documentation. The bug's solution is disclosed as you progress through lesson `7-workflow.sh` in the Shell Tutor. Remember, attempting to fix the bug without following the tutorial means you're not doing it correctly!


## What We Look for When Grading

**Total points: 50**

*   Completion of tutorial (50 points)
    *   This repository is pushed to your own account on GitLab
    *   The certificate and command logs are present in this repository


## Program Requirements

### Terminal Function Plotter

`src/plotter.py` is a Python program that plots mathematical functions such as `y = sin(x)` and `y = cos(x)`, using the terminal as a grid to display X,Y coordinate pairs with spaces ` ` or asterisks `*`. This concept is discussed by Jon Bentley in his book "Programming Pearls", page 28, under "Data Structures Programs", as an alternative to storing output in an array.

The program demonstrates an efficient way to represent a sine wave by printing each "pixel" as it's computed. This is different from the usual approach of using a 2D array of `*`s and spaces or a 1D array for encoding (X, Y) coordinates.

This technique saves memory by not creating any arrays at the cost of more CPU time as it recalculates the function's value for each pixel, even if a `*` isn't printed. Essentially, the terminal is used as a 2D array, representing the function's value at each point in the viewport.

You can decide if this is a good use of the computer's resources ;-)


## User Interface

*   The user is expected to input a single character, then press `Enter`
    *   Both upper- and lower-case input is accepted
    *   The menu is repeated when an invalid option is chosen
        *   A brief error message is shown which echoes the user's input
        *   This is to help the user understand their mistake and reduce their frustration
    *   The program immediately quits when `q` or `Q` is entered
*   When a valid input is given that function is plotted on the screen
    *   The name of the function is printed
    *   A vertical line is printed along the left margin
    *   A horizontal line is printed along the bottom margin
    *   The points where the function has values are denoted with **bold yellow** asterisks `*`
    *   For all other points a space ` ` is printed
    *   The size of the plot is **80 columns** wide by **14 lines tall**
*   The **domain** and **range** of each plot must be chosen such that the functions do not raise errors
    *    For example, the square root function `math.sqrt()` crashes with a `ValueError` when it is given a negative number as input
    *   Care must be taken by the programmer to choose a valid **domain** for each function so that crashes are avoided
*   After the plot is drawn, the user is returned to the menu
*   If the user presses `Ctrl-C` to forcibly terminate the program, Python will exit with an exception
    *   This is the only acceptable way for this program to crash


### Running the Terminal Function Plotter

When the user runs `src/plotter.py` they are *prompted* for one of a set of functions to plot.  The menu looks like this:
 
```
$ python src/plotter.py
Terminal Function Plotter
-------------------------
a) sin(x)
b) cos(x)
c) tan(x)
d) x^2
e) x^3
f) abs(x)
g) floor(x)
h) sqrt(x)
i) log10(x)
j) exp(x)
q) Quit

>
```

*Note that `$` denotes the command shell prompt and `>` represents the prompt in `src/plotter.py`.*


### Output examples

#### Invalid Input

When the user provides an invalid option, a brief message is printed before the menu is redisplayed.

```
> 8
Unrecognized option '8'

> seven
Unrecognized option 'seven'

> exit
Unrecognized option 'exit'
```


#### Killing the program with `Ctrl-C`

As described above, the program may crash when the user enters `Ctrl-C`.  The exact output may vary, but will be similar to:

```
> ^CTraceback (most recent call last):
  File "/home/fadein/school/cs1440-falor-erik-assn0/src/plotter.py", line 50, in <module>
    o = input(menu).lower().rstrip()
KeyboardInterrupt
```

Whatever the user's Python system outputs in this situation is acceptable.


#### Function Plots
Below are samples of what each function's plot should look like.  Your program's output must match these samples *exactly* (with the understanding that the asterisks `*` will be printed in **bold yellow**).

##### sin(x)

```
y = sin(x)
|
|
| ****                                              ****
|*    ****                                      ****    ****
|         **                                  **            **
|           **                              **                **
|             **                          **                    **
|               *                        *                        *
|                **                    **                          **
|                  **                **                              **
|                    **            **                                  **
|                      ****    ****                                      ****    *
|                          ****                                              ****
|
|
+---------------------------------------------------------------------------------
```


##### cos(x)

```
y = cos(x)
|
|
|                                      *****
|                                   ***     ***
|                                ***           ***
|                               *                 *
|**                           **                   **                           **
|  **                       **                       **                       **
|    *                    **                           **                    *
|     **                **                               **                **
|       ***           **                                   **           ***
|          ***     ***                                       ***     ***
|             *****                                             *****
|
|
+---------------------------------------------------------------------------------
```


##### tan(x)

```
y = tan(x)
|                                                   *                             
|                                                                            *    
|*                                                                                
|                         *                        *                        *     
|                        *                        *                        *      
|                      **                       **                       **       
|                  ****                     ****                     ****         
|             *****                    *****                    *****             
|         ****                     ****                     ****                  
|       **                       **                       **                      
|      *                        *                        *                        
|     *                        *                        *                         
|                                                                                *
|    *                                                                            
|                             *                                                   
+---------------------------------------------------------------------------------
```


##### x^2

```
y = x^2
|               *                                                 *               
|                *                                               *                
|                 *                                             *                 
|                  *                                           *                  
|                   *                                         *                   
|                    *                                       *                    
|                     *                                     *                     
|                      *                                   *                      
|                       **                               **                       
|                         *                             *                         
|                          **                         **                          
|                            **                     **                            
|                              **                 **                              
|                                ****         ****                                
|                                    *********                                    
+---------------------------------------------------------------------------------
```

##### x^3

```
y = x^3
|                                                                                 
|                                                    *                            
|                                                   *                             
|                                                                                 
|                                                  *                              
|                                                **                               
|                                              **                                 
|                                   ***********                                   
|                                 **                                              
|                               **                                                
|                              *                                                  
|                                                                                 
|                             *                                                   
|                            *                                                    
|                                                                                 
+---------------------------------------------------------------------------------
```

##### abs(x)

```
y = abs(x)
|**                                                                             **
|  ***                                                                       ***  
|     ***                                                                 ***     
|        ***                                                           ***        
|           ****                                                   ****           
|               ***                                             ***               
|                  ***                                       ***                  
|                     ***                                 ***                     
|                        ***                           ***                        
|                           ***                     ***                           
|                              ****             ****                              
|                                  ***       ***                                  
|                                     *** ***                                     
|                                        *                                        
|                                                                                 
+---------------------------------------------------------------------------------
```


##### floor(x)

```
y = floor(x)
|                                                                                *
|                                                                        ******** 
|                                                                                 
|                                                                ********         
|                                                        ********                 
|                                                                                 
|                                                ********                         
|                                        ********                                 
|                                ********                                         
|                                                                                 
|                        ********                                                 
|                ********                                                         
|                                                                                 
|        ********                                                                 
|********                                                                         
+---------------------------------------------------------------------------------
```


##### sqrt(x)

```
y = sqrt(x)
|                                                                           ******
|                                                                ***********      
|                                                      **********                 
|                                              ********                           
|                                     *********                                   
|                              *******                                            
|                       *******                                                   
|                  *****                                                          
|             *****                                                               
|         ****                                                                    
|     ****                                                                        
|   **                                                                            
| **                                                                              
|                                                                                 
|*                                                                                
+---------------------------------------------------------------------------------
```


##### log10(x)

```
y = log10(x)
|                                             ************************************
|               ******************************                                    
|     **********                                                                  
|  ***                                                                            
| *                                                                               
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
|                                                                                 
+---------------------------------------------------------------------------------
```

##### exp(x)

```
y = exp(x)
|                                                                                *
|                                                                               * 
|                                                                              *  
|                                                                            **   
|                                                                           *     
|                                                                         **      
|                                                                       **        
|                                                                     **          
|                                                                  ***            
|                                                               ***               
|                                                           ****                  
|                                                      *****                      
|                                              ********                           
|                              ****************                                   
|******************************                                                   
+---------------------------------------------------------------------------------
```
