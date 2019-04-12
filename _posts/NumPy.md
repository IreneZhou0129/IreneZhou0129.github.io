## Basics 01

1. Create an empty numpy array
```
z = np.zeros((2,3)) // (row, column)
>>>[[0.	0.	0.]
		[0.	0.	0.]]
```

2. Asign value by index
```
z[1,2] = 1
>>>[[0.	0.	0.]
		[0.	0.	1.]]
```

3. function `arange(start, end)` 
```
z = np.arange(1,10)
>>> z
>>> array([1,2,3,4,5,6,7,8,9])

z2 = np.arrange(10)
>>> z2
>>> array([0,1,2,3,4,5,6,7,8,9])
```

4. function `reshape(row, col)`
```
z = np.arange(10).reshape(2,5)
>>> z
>>> [[0,1,2,3,4], [5,6,7,8,9]]
notice: 10 = 2*5
```

5. function `nonzero(listOfNumber)`
```
nonzero_ids = np.nonzero([1,2,3,0,0,4,0])
>>> nonzero_ids
>>> array([0,1,2,5])
```

6. function `eye(num)`
```
z = np.eye(3)
>>> z
>>> [[1.	0.	0.]
		 [0.	1,	0.]
		 [0.	0.	1.]]
```

7. function `diag(listOfNumber, k)`: k = the start position of the first item that in the list of numbers. 
```
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
```
z = np.random.random((2,3))
>>> array([[0.70573305, 0.16557506, 0.53111027],
     		   [0.26959964, 0.79197129, 0.6250762 ]])
```

## Basics 02
