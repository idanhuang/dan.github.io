# Majority Vote Algorithm

The Boyer-Moore majority vote algorithm is to find the majority element in an array using linear time and constant space. The majority element should appear more than n/2 times in an anrray of size n.

## Algorithm
```
Initialize majority element and coutner = 0
For each element x in the array:
  if counter = 0
    majority = x and counter++;
  else if x == majority
    counter++;
  else
    counter--;
return majority;
```





### References
1. https://en.wikipedia.org/wiki/Boyer%E2%80%93Moore_majority_vote_algorithm
