---
template: blog-post
title: Sorting Algorithms
slug: algorithms-sort
date: 2022-04-17 14:16
description: Sorting Algorithms
---
**Heap Sort**

Description: Comparison based sorting, similar to selection sort where we first find the maximum element and place the maximum element at the end

Time Complexity: 

* Best: O(n * log(n))
* Worse: O(n * log(n))

Space Complexity:

* Best: O(1)
* Worse: O(1)

Pseudocode for Heap Sort:

* Create main heap sort function

  * Build the max heap using a for loop with heapify

    * For loop starts from half of the size of the array minus one for the root, decrement until -1 to include 0
  * Extract elements one at a time using a for loop with heapify

    * For loop starts with length of array - 1 and decrement till you reach 0
    * Swap last element with first
    * Call heapify by passing in rooted subtree at index 0
* Create heapify function

  * Heapify takes in an array, n is the size of the heap, a subtree rooted at index i
  * Initialize largest as root
  * Left is 2 * i + 1
  * Right is 2 * i + 2
  * Check if left child of the root exist (see if it is in range of n) and is it greater than the root

    * if it is, set largest equal to the left 
  * Check if right child of the root exist (see if it is in range of n) and is it greater than the root

    * if it is, set largest equal to the right
  * If it changed (largest does not equal i no more)

    * Swap the item with the index at the largest value with the item in the current i value
    * Heapify the root, at index largest

Python Code:

```
def heapSort(self, array: List[int]):
  n = len(array)
  
  for i in range(n // 2 - 1, -1, -1):
    heapify(array, n, i)
  for i in range(n-1, 0, -1):
    array[0], array[i] = array[i], array[0]
    heapify(array, i, 0)

def heapify(array: List[int], n: int, i: int): -> None
  largest = i
  left = 2 * i + 1
  right = 2 * i + 2
  
  if (left < n) and (array[left] > array[largest]):
    largest = left
  
  if (right < n) and (array[right] > array[largest]):
    largest = right
    
  if (largest != i):
    array[i], array[largest] = array[largest], array[i]
    heapify(array, n, largest)
  
```



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

    * If left is less than right (array will increment, smallest first, largest last. Inverse it by checking if left is smaller greater right)

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

Python Code:

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