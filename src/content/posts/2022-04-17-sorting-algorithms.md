---
template: blog-post
title: Sorting Algorithms
slug: algorithms-sort
date: 2022-04-17 14:16
description: Sorting Algorithms
---
**Merge Sort**

Description: Divide and Conquer Algorithm 

Time Complexity: 

* Best: O(n * log(n))
* Worse: O(n * log(n))

Space Complexity:

* Best: O(n)
* Worse: O(n)

Pseudocode for Merge Sort:

* Split

  * Function will take in an array
  * If the array contains more than 1 element
  * Split array into two arrays from the middle value
  * Recursively continue calling the same function providing the left and right side of the array (will continue splitting)
* Merge them together

  * Let i, j, k be variables to keep track of left, right, original passed in array respectively
  * Create a while loop that will compare left and right arrays

    * If left is greater than right (array will decrement, largest first, smallest last. Inverse it by checking if left is smaller than right)

      * Have original array at index k equal to left at index i
      * Increment i (also k)
    * Else

      * Have original array at index k equal to right at index j
      * Increment j (also k)
  * Create a while loop for left

    * While i is less than the length of the left array
    * Continue to move items to the original array from the left array 
    * Increment i and k  
  * Create a while loop for right

    * While j is less than the length of the right array
    * Continue to move items to the original array from the right array
    * Increment j and k



```
def merge_sort(self, array):
        if (len(array) > 1):
            mid = len(array)//2
            left = array[:mid]
            right = array[mid:]
            
            self.merge_sort(left)
            self.merge_sort(right)

            i = j = k = 0
            
            while i < len(left) and j < len(right):
                if (left[i] < right[j]):
                    array[k] = left[i] 
                    i += 1 
                else: 
                    array[k] = right[j]
                    j += 1
                k += 1
            
            while i < len(left):
                array[k] = left[i]
                i += 1
                k += 1
            
            while j < len(right):
                array[k] = right[j]
                j += 1
                k += 1
            
            return array
```