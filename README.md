# Python-project-2048-Game

import random
def start_game():
    mat = []
    for i in range(4):
        mat.append([0]*4)
    return mat


def move_up(grid):
    size = len(grid)
    for j in range(size):
        for i in range(1, size):
            if grid[i][j] != 0:
                k = i
                while k > 0 and grid[k-1][j] == 0:
                    grid[k-1][j] = grid[k][j]
                    grid[k][j] = 0
                    k -= 1
                if k > 0 and grid[k-1][j] == grid[k][j]:
                    grid[k-1][j] *= 2
                    grid[k][j] = 0
    return grid
    pass

def move_down(grid):
    size = len(grid)
    for j in range(size):
        for i in range(size-2, -1, -1):
            if grid[i][j] != 0:
                k = i
                while k < size-1 and grid[k+1][j] == 0:
                    grid[k+1][j] = grid[k][j]
                    grid[k][j] = 0
                    k += 1
                if k < size-1 and grid[k+1][j] == grid[k][j]:
                    grid[k+1][j] *= 2
                    grid[k][j] = 0
    return grid
    pass

def move_right(grid):
    size = len(grid)
    for i in range(size):
        for j in range(size-2, -1, -1):
            if grid[i][j] != 0:
                k = j
                while k < size-1 and grid[i][k+1] == 0:
                    grid[i][k+1] = grid[i][k]
                    grid[i][k] = 0
                    k += 1
                if k < size-1 and grid[i][k+1] == grid[i][k]:
                    grid[i][k+1] *= 2
                    grid[i][k] = 0
    return grid
    pass

def move_left(grid):
    size = len(grid)
    for i in range(size):
        for j in range(1, size):
            if grid[i][j] != 0:
                k = j
                while k > 0 and grid[i][k-1] == 0:
                    grid[i][k-1] = grid[i][k]
                    grid[i][k] = 0
                    k -= 1
                if k > 0 and grid[i][k-1] == grid[i][k]:
                    grid[i][k-1] *= 2
                    grid[i][k] = 0
    return grid
    pass


mat = start_game()
mat[1][3] = 2
mat[2][2] = 2
mat[3][0] = 4
mat[3][1] = 8
mat[2][1] = 4
inputs = [int(ele) for ele in input().split()]
for ele in inputs:
    if ele == 1:
        mat = move_up(mat)
    elif ele == 2:
        mat = move_down(mat)
    elif ele == 3:
        mat = move_left(mat)
    else:
        mat = move_right(mat)
    print(mat)
