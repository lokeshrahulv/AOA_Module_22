# EX 4A DYNAMIC PROGRAMMING - 1
## DATE:
## AIM:
To find longest common subsequence using Dynamic Programming.



## Algorithm
1. Create a table c where each cell stores the LCS length for parts of u and v.
2. Fill the table from the end of both strings towards the start.
3. If characters match, add 1 to the LCS length; else take the maximum of two possible moves.
4. Start from the beginning and move through c to reconstruct one LCS.
5. Print the matching characters along the path.  

## Program:

```
/*
Program to implement the longest common subsequence using Dynamic Programming

.
Developed by:  LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
def lcs(u, v):
    """Return c where c[i][j] contains length of LCS of u[i:] and v[j:]."""
    c = [[-1]*(len(v) + 1) for _ in range(len(u) + 1)]
    for i in range(len(u) + 1):
        c[i][len(v)] = 0
    for j in range(len(v)):
        c[len(u)][j] = 0
 
    for i in range(len(u) - 1, -1, -1):
        for j in range(len(v) - 1, -1, -1):
            if u[i] == v[j]:
                c[i][j] = 1 + c[i + 1][j + 1]
            else:
                c[i][j] = max(c[i + 1][j], c[i][j + 1])
    return c
 
def print_lcs(u, v, c):
    """Print one LCS of u and v using table c."""
    i = j = 0
    while not (i == len(u) or j == len(v)):
        if u[i] == v[j]:
            print(u[i], end='')
            i += 1
            j += 1
        elif c[i][j + 1] > c[i + 1][j]:
            j += 1
        else:
            i += 1
 
u = input()
v = input()
c = lcs(u, v)
print_lcs(u, v, c)

```

## Output:
![image](https://github.com/user-attachments/assets/d39aedf0-f3b6-4e2e-9760-6239e787ceb8)




## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
