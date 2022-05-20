# HackerRank_Python_Write a function

## Problem

## Solution
* What I learned : The calendar builtin module has a function isleap() that returns True if the year is leap, otherwise it returns False

      import calendar
      def is_leap(year):
        return calendar.isleap(year)
        
![image](https://user-images.githubusercontent.com/99947811/169516256-eb2c081b-8c77-4db6-a9be-c151cfee16ae.png)


### Other Solution(1)
    
    def is_leap(year):
        if year % 4 == 0 and (year % 400 == 0 or year % 100 != 0):
            return True
        else:
            return False
    year = int(input())
    print(is_leap(year))

    '''

### Other Solution(2)

    def is_leap(year):
        if year % 4 ==0:
            if year % 100 !=0:
                return True
        elif year % 400 ==0:
            return True
        else :
            return False
    year = int(input())
    print(is_leap(year))
    
    
    
![image](https://user-images.githubusercontent.com/99947811/169520214-ffb60a24-4676-4a9d-bee9-0df9c183469d.png)

