# AOA_Module_22
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
# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..



## Algorithm
1. Create a table lookup to store lengths of matching characters.
2. Compare each character of X with each character of Y.
3. If characters match, update the lookup value and track the maximum length and ending position.
4. After filling the table, the longest common substring is found at the tracked position.
5. Extract and print the substring from X using the recorded indices.  

## Program:
```
/*
Program to implement the longest common substring problem

.
Developed by:  LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
def LCS(X, Y, m, n):
    maxLength = 0
    endingIndex = m
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
    return X[endingIndex - maxLength: endingIndex]

X = input()
Y = input()
m = len(X)
n = len(Y)
print('The longest common substring is', LCS(X, Y, m, n))
```

## Output:
![image](https://github.com/user-attachments/assets/69731d23-7375-4146-9b23-51e606c7cd61)




## Result:
Thus the program was executed successfully for finding the longest common substring .

# EX 4C DYNAMIC PROGRAMMING – 3
## DATE:
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.

## Algorithm
1. Take the input string and reverse it.
2. Compare both strings using dynamic programming to find matching characters.
3. If characters match, increase the length by 1 and move diagonally.
4. If not matching, move in the direction where maximum length is found (left or up).
5. Final answer is the length of the longest palindromic subsequence.

 

## Program:
```
/*
Program to implement to find the length of the longest palindromic subsequence in it

.
Developed by:  LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
dp = [[-1 for i in range(1001)]for j in range(1001)]
def lps(s1, s2, n1, n2):   
    if (n1 == 0 or n2 == 0):       
        return 0    
    if (dp[n1][n2] != -1):      
        return dp[n1][n2]    
    if (s1[n1 - 1] == s2[n2 - 1]):       
        dp[n1][n2] = 1 + lps(s1, s2, n1 - 1, n2 - 1)       
        return dp[n1][n2]    
    else:      
        dp[n1][n2] = max(lps(s1, s2, n1 - 1, n2), lps(s1, s2, n1, n2 - 1))      
        return dp[n1][n2]
seq = input()
n = len(seq)
s2 = seq
s2 = s2[::-1]
print(f"The length of the LPS is",lps(s2, seq, n, n))
```

## Output:
![image](https://github.com/user-attachments/assets/5d353642-4b3f-4f0a-b6a8-ff3ae628ff71)




## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.

# EX 4D DYNAMIC PROGRAMMING – 4
## DATE:
## AIM:
To find the minimum number of operations to convert str1 to str2 using Naive recursive method.





## Algorithm
1. If one string is empty, return the length of the other string.
2. If the last characters of both strings match, the cost is 0; else, cost is 1.
3. Recursively calculate three options: insert, delete, or replace a character.
4. Take the minimum of the three operations plus the current cost.
5. Final result is the minimum number of edits needed to convert one string into another.  

## Program:
```
/*
Program to implement to find the minimum number of operations to convert str1 to str2 using Naive recursive method

.
Developed by:  LOKESH RAHUL V V
Register Number: 212222100024
*/
```
```
def LD(s, t):
    
    if s == "":
        return len(t)
    if t == "":
        return len(s)
    if s[-1] == t[-1]:
        cost = 0
    else:
        cost = 1
    res = min([LD(s[:-1], t)+1, LD(s, t[:-1])+1, LD(s[:-1], t[:-1]) + cost])
    return res
str1=input()
str2=input()
print('Edit Distance',LD(str1,str2))
```

## Output:
![image](https://github.com/user-attachments/assets/adc74bd7-29a4-4694-9e5e-7101e258dc5e)




## Result:
Thus the program was executed successfully for finding edit distance between two strings.
