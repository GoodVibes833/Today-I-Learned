## Brute Force



### # What is Brute Force ?

```
- Try all cases
- very inefficiency
- easy to code
- start point to think other algorithms
```



### # case1 : sum

```
# find sum of 0 to 100
	0+1 = 1
	1+2 = 3
	3+4 = 7
		...
	4950+100 = 5050 
	
# if its number is huge?  : inefficiency!
```



### # case2 : password 

```
# if a password is 5 digit with numbers ?
 -> 0~9(10ea) 
 -> 10^5 cases
 
# if a password is 5 digit with numbers and alphabet ?
 -> 0~9(10), a~z(26)
 -> 36^5 cases
 -> safer


# Brute force attack(hacking case): by trying all cases
 1. needed prevent system like if when typying wrong PW 5times, it make users to stop log in 5 minutes
 		-> hacking time increased
 2. include Special Characters within password

```





O(N)