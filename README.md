# 2048 AI
## Introduction
This project is an AI that plays the popular number game 2048 by implementing a minimax algorithm. It uses `selenium webdriver` to interact with a web app version of the game. For those unfamiliar with 2048, it is a sliding tile puzzle game in which the goal is to swipe and merge tiles of the same value to form powers of 2 until the 2048 tile is obtained. The original version of the game can be played [here](https://play2048.co/ "2048").

## File Organization
**Board.py**: A class that maintains the state of the game by storing it as a 4x4 matrix. It includes a variety of methods that can simulate a move on the board and also check if a move in a certain direction is possible. The `heuristic()` function provides a metric for quantitatively describing how "favorable" a given configuration of tiles is.

**Driver.py**: A class that interacts with a web app version of the game by sending key inputs to the page.

**minimax.py**: A file that contains the functions that implement a vanilla minimax algorithm. 

**matrix_functions.py**: A file that contains four basic matrix manipulation functions to help simulate a move.

**loop.py**: The driver code that, when executed, opens a session of the game in a new Chrome window and solves the board live. It also prints the sequence of moves taken to the terminal.

## Minimax Algorithm Discussion
A minimax approach is appropriate here because 2048 can be viewed as an adversarial game in which the player is trying to maximize their score and obtain the highest possible tile while the game is trying to prevent them from doing so by randomly placing 2 or 4 tiles on the board after every move. This provides a basic sketch for the algorithm: the player is trying to maximize the heuristic evaluation of the board (discussed below) while the computer plays "optimally" and tries to minimize that evaluation. In the context of the minimax algorithm, the player's children states can be found by simulating the moves UP, DOWN, LEFT, and RIGHT if possible. The opponent or game's children can be found by placing a 2 or 4 tile in one of the empty cells of the board. Since the number of children nodes can grow very large, the search depth is intially set to 5. Alpha-beta pruning can be used to improve the efficiency of the search if there are time or space requirements.

## Heuristic Function
One common strategy for playing 2048 is to accumulate all high-valued tiles near a corner of the board. The heuristic function utilized here essentially makes the AI conform to this style of play.

## How To Run
Download all files in the repository and execute `loop.py` by running `python loop.py`.  If needed, install webdriver-manager by running `pip install webdriver-manager`.
