import numpy as np
import random 
import pandas as pd

def create_random_distance_matrix(n):
# Creating a random symmetric distance matrix that follows the triangle inequality

    matrix = np.zeros((n, n), dtype=int)

    for i in range(n):
        for j in range(i + 1, n):
            matrix[i, j] = random.randint(50, 100)

    for i in range(n):
        for j in range(i + 1, n):
            for k in range(j + 1, n):
                matrix[j, k] = random.randint(50, 100)
                while matrix[i, j] + matrix[j, k] < matrix[i, k]:
                    matrix[i, k] = random.randint(50, 100)

    matrix = matrix + matrix.T
        
    return matrix