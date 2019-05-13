---
layout: post
title: numpy
---

1. Create an empty numpy array
```python
z = np.zeros((2,3)) // (row, column)
>>>[[0.	0.	0.], [0.	0.	0.]]
```

2. Asign value by index
```python
z[1,2] = 1
>>>[[0.	0.	0.], [0.	0.	1.]]
```

3. function `arange(start, end)` 
```python
z = np.arange(1,10)
>>> z
>>> array([1,2,3,4,5,6,7,8,9])

z2 = np.arrange(10)
>>> z2
>>> array([0,1,2,3,4,5,6,7,8,9])
```

4. function `reshape(row, col)`
```python
z = np.arange(10).reshape(2,5)
>>> z
>>> [[0,1,2,3,4], [5,6,7,8,9]]
notice: 10 = 2*5
```

5. function `nonzero(listOfNumber)`
```python
nonzero_ids = np.nonzero([1,2,3,0,0,4,0])
>>> nonzero_ids
>>> array([0,1,2,5])
```

6. function `eye(num)`
```python
z = np.eye(3)
>>> z
>>> [[1.	0.	0.]
		 [0.	1,	0.]
		 [0.	0.	1.]]
```

7. function `diag(listOfNumber, k)`: k = the start position of the first item that in the list of numbers. 
```python
listOfNumber = [1,2,3,4]

z = np.diag(listOfNumber, k=0)
>>> array([[1, 0, 0, 0],
    		   [0, 2, 0, 0],
       		 [0, 0, 3, 0],
		       [0, 0, 0, 4]])
		       
z2 = np.diag(listOfNumber, k=1)
>>> array([[0, 1, 0, 0, 0],
    		   [0, 0, 2, 0, 0],
  		     [0, 0, 0, 3, 0],
   		     [0, 0, 0, 0, 4],
       		 [0, 0, 0, 0, 0]])
see, the k increases, the size of matrix increases.
what if k is a negative number...
       		 
z3 = np.diag(listOfNumber, k=-1)
>>> array([[0, 0, 0, 0, 0],
       		[1, 0, 0, 0, 0],
       		[0, 2, 0, 0, 0],
       		[0, 0, 3, 0, 0],
       		[0, 0, 0, 4, 0]])

```

8. function `random.random((row, col))`: each number is a random float in [0.0, 1.0)
```python
z = np.random.random((2,3))
>>> array([[0.70573305, 0.16557506, 0.53111027],
     		   [0.26959964, 0.79197129, 0.6250762 ]])
```

9. Create a 8x8 chessboard

```python
z = np.zeros((8,8), dtype = int)

// [start-row index :: every n element, 
//  start-column index :: every n element] 
// start row at index 1 and column at index 0
z[1::2, ::2] = 1 

z[::2, 1::2] = 1
>>> z
>>>
[[0 1 0 1 0 1 0 1]
 [1 0 1 0 1 0 1 0]
 [0 1 0 1 0 1 0 1]
 [1 0 1 0 1 0 1 0]
 [0 1 0 1 0 1 0 1]
 [1 0 1 0 1 0 1 0]
 [0 1 0 1 0 1 0 1]
 [1 0 1 0 1 0 1 0]]
// z[::2] means every other element
// z[1::2] means every other element, starting at index 1
```

10. min(), max()

```python
z = np.random.random((10,10))
zMin, zMax = z.min(), z.max()

>>> zMin
0.022004881183619873
>>> zMax
0.9985401092319949
```

11. tile(A, repeats)

    ```python
    a = np.array([[0,1],[0,1]])
    >>> a
    array([[0, 1],
           [0, 1]])
    
    z = np.tile(a,(2,4)) // repeat twice in columns, repeat 4 times in rows
    >>> z
    array([[0, 1, 0, 1, 0, 1, 0, 1],
           [0, 1, 0, 1, 0, 1, 0, 1],
           [0, 1, 0, 1, 0, 1, 0, 1],
           [0, 1, 0, 1, 0, 1, 0, 1]])
    ```

12. Normalizing a matrix into range [0,1]

    ```python
    >>> a = np.array([[10,23,15],[66,24,77]])
    >>> a
    array([[10, 23, 15],
           [66, 24, 77]])
    >>> aMax, aMin = a.max(), a.min()
    >>> aMax
    77
    >>> aMin
    10
    >>> a = (a-aMin)/(aMax-aMin) 
    >>> a
    array([[0.        , 0.19402985, 0.07462687],
           [0.8358209 , 0.20895522, 1.        ]])
    
    Visually see the process:
      
    ```

    ![Untitled drawing](/Users/xiaoxinzhou/Downloads/Untitled drawing.png)

13. Add two matrixs 

    ```python
    >>> a = np.zeros((3,3))
    >>> a
    array([[0., 0., 0.],
           [0., 0., 0.],
           [0., 0., 0.]])
           
    >>> c = np.arange(3)
    >>> c
    array([0, 1, 2])
    
    >>> a += c
    >>> a
    array([[0., 1., 2.],
           [0., 1., 2.],
           [0., 1., 2.]])
              
    Notice: two matrixs must in the same shape
    ```

14. linspace(start, stop, num=50, endpoint=True, retstep=False): return evenly spaced numbers over a specified interval.

    ```python
    >>> a = np.linspace(0,5,10, endpoint = True, retstep = False)
    >>> a
    array([0.        , 0.55555556, 1.11111111, 1.66666667, 2.22222222,
           2.77777778, 3.33333333, 3.88888889, 4.44444444, 5.        ])
         
    Notice: if endpoint = False, the stop number will be excluded.
    ```

15. allclose(a, b, rtol=1e-05, atol = 1e-08, equal_nan = False): returns True if two arrays are element-wise equal within a tolerance. 

    ```
    >>> a = np.random.randint(0,2,5)
    >>> a
    array([0, 0, 1, 0, 0])
    >>> b = np.random.randint(0,2,5)
    >>> b
    array([1, 0, 0, 1, 1])
    >>> np.allclose(a, b)
    False
    ```

    
