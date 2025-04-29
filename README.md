# Maze Generator and Solver

## Overview

This project, is an interactive maze generator and solver implemented in C programming language. The program utilizes the Prims algorithm to randomly generate mazes and provides users with the option to navigate through and solve them.

## Features

1. Maze Generation: The program uses the Prims algorithm to generate random mazes of varying sizes. The size of the maze is customizable, and the generator marks the start and end points with 'S' and 'E' respectively.

2. Interactive Menu: Users are presented with an interactive menu that allows them to choose from various options, including playing the maze, accessing instructions, and learning more about the project.

3. Maze Solver: After maze generation, users can choose to solve the maze interactively. The program displays the maze, and users can navigate through it using the keys 'W' (up), 'A' (left), 'S' (down), and 'D' (right). The goal is to reach the exit marked with 'E'.

4. Loading Animation: The program includes loading animations to enhance the user experience during maze generation.

## Instructions

To play the maze and explore its features:

1. Run the program.
2. Choose the desired option from the menu.
3. If playing the maze, use the keys 'W', 'A', 'S', and 'D' to navigate, and 'Q' to quit.

## Compilation

The program is written in C and can be compiled using a standard C compiler. If you are using a Windows environment, the Windows API is utilized for certain features.

bash
gcc maze.c -o maze.exe


## Contributors

The Hardcoders team contributed to the development of this project:

- Jenish Thakkar
- Rudra Thakar

## About

This maze generator and solver project were developed as part of an IC project. 
Note : The original repo was moved from 


## Info related to Code and Algoritms used.

We use two 2D arrays (maze and travelled). <br>
The maze array represents the structure of the maze, including walls, passages, and the starting ('S') and ending ('E') points. The outer boundary is initialized with walls ('*'), and all other cells are initialized as a wall or a path based on its position.<br>
The travelled array is used to keep track of which cells have been visited during the maze generation process. It uses the character 't' to represent the not visited cells.<br>
x_coordinate, y_coordinate are used to represent the current coordinates of cursor within the maze.<br>

PRIMS ALGO:<br>
A random number between 0 and 3 is generated. This number is used to determine the direction in which the algorithm will attempt to create the passage.<br>
A while loop contiinues untill all the neighbouring cell of the current cell are not visited. If all the neighbouring cells are visited, the loop breakes.<br>
Each random number represents a direction of motion. <br>
Eg) To move right, we check if the cell which is 2 cells away from the current cell in the right side(let us call it as taget cell) is visited or not. If the target cell is not visited, then a path is created from the cell adjacent to current cell and the target. The path is created by assigning the value of those cell in maze array as ' '.
If the target cell is already visited, we make the cell adjacent  to current cell as wall.<br>
