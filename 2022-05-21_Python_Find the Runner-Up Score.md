#HackerRank_Python_Find the Runner-Up Score

## Problem
![image](https://user-images.githubusercontent.com/99947811/169661267-e733b13a-59f5-4a0d-bbe3-9d5f652d27a1.png)
Link(https://www.hackerrank.com/challenges/find-second-maximum-number-in-a-list/problem?isFullScreen=true&h_r=next-challenge&h_v=zen)

## Solution

    if __name__ == '__main__':
        n = int(input())
        arr = list(map(int, input().split()))
        arr.sort()
        print(arr[arr.index(max(arr))-1])

        # sorting asc : sort() 
        # index of max element : max(arr)
        # 2nd max element : arr.index(max(arr))-1
        # to get index number, make the 'arr' into 'list()'
        
![image](https://user-images.githubusercontent.com/99947811/169661253-f35bed55-010b-4112-b249-8a55fa5cc53d.png)
