# HackerRank_Python_List comprehensions

## Problem
Link(https://www.hackerrank.com/challenges/list-comprehensions/problem?isFullScreen=true)
![image](https://user-images.githubusercontent.com/99947811/169660101-2c9588dd-0cff-4585-b533-d47f18dd1696.png)


## Solution

* for문 대신 List comprehension으로 코드작성
#### [expression for. condition]

    x = int(input())
    y = int(input())
    z = int(input())
    n = int(input())
    result = [ [i,j,k] for i in range(x+1) for j in range(y+1) for k in range(z+1) if i+j+k!=n ]
    print(result)
                 
![image](https://user-images.githubusercontent.com/99947811/169660037-2e8fa860-d1f9-404e-8ee1-66561cd248e9.png)



** for문으로 펼친 ver.

    x = int(input())
    y = int(input())
    z = int(input())
    n = int(input())

    result = []

    for i in range(x+1):  #범위 : 0,1,..., x-1,x
        for j in range(y+1):
            for k in range(z+1):
                if i+j+k!=n:
                    result.append([i,j,k])
    print(result)
    
![image](https://user-images.githubusercontent.com/99947811/169659773-15c0038d-e6f7-4537-a5db-7490588271a9.png)

