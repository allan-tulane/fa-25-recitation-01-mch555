# CMPS 2200  Recitation 01

**Name (Team Member 1):**_________________________  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**
Worse-case input key for linear search is at the end of the list because the algorithm has the check every element before returning: len(mylist)

worse-case input key for binary search is when the key is not in the list or if it is the last one checking while having: log₂(len(mylist)) + 1
 


- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**TODO: your answer goes here**
for linear search, the best case scenario would be the first element in the list, because the algorithm just has to do 1 comparison: mylist[0]

for binary search, the best case scenario for the key would be exactly in the middle of the list, because the algorithm would only do one comparison: mylist[len(mylist)//2]

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**

Users/hunte/Downloads/fa-25-recitation-01-mch555-main/fa-25-recitation-01-mch555-main/main.py
|        n |   linear |   binary |
|----------|----------|----------|
|       10 |    0.003 |    0.004 |
|      100 |    0.005 |    0.002 |
|     1000 |    0.051 |    0.003 |
|    10000 |    0.510 |    0.003 |
|   100000 |    5.817 |    0.010 |
|  1000000 |   79.605 |    0.014 |
| 10000000 |  744.559 |    0.019 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**TODO: your answer goes here**
Yes, they match the empirical results from the timing data. This is because for linear search, the results shows linear growth, where the runtime increased from .003 seconds at n=10 to 744.559 seconds at n=10,000,000. For binary search the runtime icreases slowly as the input size grew. The timing data confirms this because at n=1,000 the runtime was .003 seconds and only .019 seconds at n=10,000,000

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **TODO: your answer goes here**

  Linear search checks each element one by one, taking O(n) time for each search. The total time for searching k times is:  O(k*n)

  + For binary search? **TODO: your answer goes here**

  Binary search needs the list to be sorted, and sorting take O(n^2) times. Each binary search takes O(logn) time therefore searching k times takes: O(n^2)+k*O(logn)

  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **TODO: your answer goes here**

  if you search few times, then linear search is better because sorting costs too much, but if you search many times, then binary search is must faster. So if you search more than n times, it is better to sort and then use binary search (k>=O(n))
 
      
