# HackerRank_Python_Write a function

## Problem
    Link(https://www.hackerrank.com/challenges/write-a-function/problem)
    An extra day is added to the calendar almost every four years as February 29, and the day is called a leap day. It corrects the calendar for the fact that our planet takes approximately 365.25 days to orbit the sun. A leap year contains a leap day.

    In the Gregorian calendar, three conditions are used to identify leap years:

    The year can be evenly divided by 4, is a leap year, unless:
    The year can be evenly divided by 100, it is NOT a leap year, unless:
    The year is also evenly divisible by 400. Then it is a leap year.
    This means that in the Gregorian calendar, the years 2000 and 2400 are leap years, while 1800, 1900, 2100, 2200, 2300 and 2500 are NOT leap years.

    Task
    Given a year, determine whether it is a leap year. If it is a leap year, return the Boolean True, otherwise return False.
    Note that the code stub provided reads from STDIN and passes arguments to the is_leap function. It is only necessary to complete the is_leap function.
    
    
 
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
reference (https://www.hackerrank.com/challenges/write-a-function/forum)


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

