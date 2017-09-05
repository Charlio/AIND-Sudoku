# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: The naked twins problem states that when there are two boxes containing the same two digits in a unit, then they are called naked twins and since these two boxes must contain 
the two digits, all other boxes in the unit cannot contain the two digits. Thus we can eliminate all appearances of the two digits in all other boxes of the unit. This technique
is implemented in the naked_twins funciton for all the units. Moreover, in order to use the constraint propagation to solve it, i.e. reduce the possibilities in each iteration for 
future searches, I plugged naked_twins() in the while loop in reduce_puzzle function, both after eliminate() and after only_choice(). So each time after we call eliminate() or 
only_choice(), we call naked_twins() to further reduce the puzzle, so that it introduces new constraints for other parts of the board that can help us further reduce the number of 
possibilities. This addition of the naked_twins() can both help us solve the sudoku faster, and solve much harder sudokus.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: The diagonal sudoku problem states that besides the regular requirements, we also impose that the two nine-box diagonals also consist of the nine different digits. This new requirement
add one more constraint to the sudoku problem. In order to use constraint propagation, I add the two diagonal units into our unitlist and unit dict, so that in every call of eliminate(), 
only_choice() and naked_twins(), we also reduce the puzzle in the diagonal units in every iteration. This addition of a new local constraint further reduces the search space as it 
introduces new constraints for other parts of the board that can help us further reduce the number of possibilities. 

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

