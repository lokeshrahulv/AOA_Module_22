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
