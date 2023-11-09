import tkinter as tk
from tkinter import messagebox

# The possible positions in the grid
POSSIBLE_POSITIONS = [2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048]

# Function to add a new tile in a random empty cell
def add_new_tile():
    global grid
    empty_cells = []
    for i in range(4):
        for j in range(4):
            if grid[i][j] == 0:
                empty_cells.append((i, j))

    if len(empty_cells) > 0:
        random_cell = empty_cells[randint(0, len(empty_cells) - 1)]
        grid[random_cell[0]][random_cell[1]] = choice(POSSIBLE_POSITIONS)
        update_grid_display()

# Function to check for valid moves in all four directions
def valid_moves():
    for i in range(4):
        for j in range(4):
            if grid[i][j] != 0:
                for k in range(4):
                    if i != k and grid[i][j] == grid[k][j]:
                        return True
                    if j != k and grid[i][j] == grid[i][k]:
                        return True

    return False

# Function to merge the tiles in all four directions
def merge_tiles():
    global grid
    moved = False
    for i in range(4):
        for j in range(4):
            if grid[i][j] != 0:
                for k in range(4):
                    if i != k and grid[i][j] == grid[k][j]:
                        grid[i][j] *= 
