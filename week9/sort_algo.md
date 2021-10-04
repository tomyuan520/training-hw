- 1 冒泡排序
```python
def bubbleSort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

```

- 2选择排序
```python
def selectionSort(arr):
    n = len(arr)
    for i in range(n):
        min_index = i
    for j in range(i + 1, n):
        if arr[min_index] > arr[j]:
            min_index = j
            arr[i], arr[min_index] = arr[min_index], arr[i]

```

- 3插入排序
```python
def insertionSort(arr):
    n = len(arr)
    for i in range(1, n):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
            arr[j + 1] = key

```

- 4希尔排序
```python

def shellSort(arr):
    n = len(arr)
    gap = int(n / 2)
    while gap > 0:
        for i in range(gap, n):
            tmp = arr[i]
            j = i
        while j >= gap and arr[j - gap] > tmp:
            arr[j] = arr[j - gap]
            j -= gap
            arr[j] = tmp
            gap = int(gap / 2)

```

- 5归并排序
```python

def merge(left, right):
    ret = []
    i, j = 0, 0
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            ret.append(left[i])
            i += 1
        else:
            ret.append(right[j])
            j += 1
    ret += left[i:]
    ret += right[j:]
return ret

def mergeSort(arr):
    n = len(arr)
    if n <= 1:
        return arr
    mid = int(n / 2)
    left = mergeSort(arr[: mid])
    right = mergeSort(arr[mid:])
return merge(left, right)

```