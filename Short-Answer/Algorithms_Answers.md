# Analysis of Algorithms

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```
a)  a = 0        
    while (a < n * n * n):   # O(n^3) 
         a = a + n * n       # O(1) +  O(-n^2)
```                 
##  ANSWER:  O(n) =  O(n^3) - o(n^2) 
##           not O(n^3) because a(interval) is increased by n^2 which decreases the number of iterrations by n^2  as n increases  )

```
b)  sum = 0                   
    for i in range(n):    # O(n) 
      i += 1
      for j in range(i + 1, n): # O(n) 
        j += 1
        for k in range(j + 1, n):  # O(n)
          k += 1
          for l in range(k + 1, 10 + k): # O(n)
            l += 1
            sum += 1            
```
##  ANSWER: O(n^4)  

```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)
```
##  ANSWER: O(n)  recursion, iteration is based on # bunnies


## Exercise II
Suppose that you have an _n_-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor _f_ or higher, and doesn't get broken if dropped off a floor less than floor _f_. Devise a strategy to determine the value of _f_ such that the number of dropped eggs is minimized.
Write out your proposed algorithm in plain English or pseudocode and give the runtime complexity of your solution.

Solution 1: Start from the BOTTOM story counting UP until you reach the floor where the egg breaks.
                  BAD: Will waste eggs if _f_ is HIGH floor

Solution 2: Start from the TOP story counting DOWN until you reach the floor where the egg breaks.
                  BAD: Will waste eggs if _f_ is LOW floor

Solution 3: Run two loops, Start from the TOP story counting DOWN until you reach the floor where the egg breaks.
                       and Start from the BOTTOM story counting UP until you reach the floor where the egg breaks. 
                  BAD: Will waste eggs if _f_ is in the MIDDLE floor

Solution 4: Mimic a binary search( with recursion) 

             1. Set floor-range_top = top_floor

             1. Set floor-range_bottom = bottom_floor

             2. Calculate midpoint( floor-range_top -  floor-range_bottom // 2) of floor_range & Drop the egg from there

                If egg breaks

                    # disregard top half

                    set floor_range_top = midpoint

                    set floor_range_bottom = bottom_floor

                    repeat 2  until egg doesn't break then return midpoint + 1

                else if egg doesn't break

                    # disregard bottom half of _n_ 

                    set floor_range_top = top_floor

                    set floor_range_bottom = midpoint

                    repeat 2  until egg breaks   return midpoint
                    


Time Complexity:  O(logn)  As in a binary search, the list keeps getting cut in half
