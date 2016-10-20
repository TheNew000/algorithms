#Danny's Sorting Algorithms!

For a deeper explanation of my custom sorts please check out my [algorithm page!](http://www.dannyarango.com/algorithms "My Algorithm Page")  Otherwise, I'm including a brief explanation and the actual code for my sorting algorithms.

###Danny's BubbleSort:

Here I take the concept of a bubble sort but ascend the list with the highest value and then descend the list with the lowest value.  I'm able to half the initial amount of times we go over "n" right off the bat!.

```Python
def danny_bub2(list):
    for i in range((len(list))//2):
        for j in range(i, (len(list) - 1) - i): 
            if list[j] > list[j + 1]: 
                list[j], list[j + 1] = list[j + 1], list[j]      
        for k in range((len(list) - 2) - i, i, -1): 
            if list[k] < list[k - 1]: 
                list[k], list[k - 1] = list[k - 1], list[k]
    print list
```

###Danny's Select Sort:

I applied the same ascending descending/halving the initial "n" concept to the select sort.

```Python
def danny_shortsort_select(list):
    maxPos = 0
    for num in range((len(list) - 1)//2):
        for loc in range(num + 1, len(list) - num):
            if list[loc] > list[maxPos]:
                maxPos = loc
        list[loc], list[maxPos]=list[maxPos], list[loc]
        minPos = loc - 1
        for loc2 in range(loc - 2, num - 1, -1):
            if list[loc2] < list[minPos]:
                minPos = loc2
        list[loc2], list[minPos]=list[minPos], list[loc2]
        maxPos = loc2 + 1
    return list
```


###Danny's Select Sort (For mostly organized lists):

This sort contains a check to see if the highest or lowest value is already in the last or first index and instead of doing nothing it will put the value it's holding into the index next to that highest value and then drop it's index value by two instead of one on that pass.  Not tremendously useful for chaotic lists but it could quickly eliminate indexes for lists that are mostly organized to begin with!

```Python
def danny_select(list):
    maxPos = 0
    beg = 0
    end = len(list)
    for num in range((len(list) - 1)//2):
        for loc in range(beg + 1, end - num):
            if list[loc] > list[maxPos]:
                if loc != end - num - 1:
                    maxPos = loc
                elif loc == end - num - 1:
                    loc -= 1
                    end -= 1
        list[loc], list[maxPos]=list[maxPos], list[loc]
        minPos = loc - 1
        for loc2 in range(end - 2, num - 1, -1):
            if list[loc2] < list[minPos]:
                if loc2 != beg:
                    minPos = loc2
                elif loc2 == beg:
                    beg += 1
                    loc2 += 1
        list[loc2], list[minPos]=list[minPos], list[loc2]
        maxPos = loc2 + 1
        if maxPos == minPos:
            return list
    return list
```
