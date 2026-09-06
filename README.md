#### 1) **Reproducible Normalization Problem** - Generates a 10x10 array of cubed numbers from 1 to 100 and extracts elements divisible by 4.

```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

x = np.mean(X)

a = np.std(X)

X_normalized = (X-x)/a

print("Mean:", round(X_normalized.mean()))
np.save("X_normalized", X_normalized)
```

##### Step-by-step procedure
- `np.random.seed(2112)` → Sets random seed to ensure reproducibility of number generation
- `X = np.random.randint(10, 101, size=(5, 5))` → Generates a 5x5 array of random integers ranging from 10 to 100
- `x = np.mean(X)` → Computes the mean of all elements in array X
- `a = np.std(X)` → Calculates the standard deviation of the elements in array X
- `X_normalized = (X-x)/a` → Standardizes the array by subtracting the mean and dividing by the standard deviation
- `print("Mean:", round(X_normalized.mean()))` → Rounds the mean of the normalized array and displays it
- `np.save("X_normalized", X_normalized)` → Saves the normalized NumPy array as .npy file

#### Outcome
```python
X
array([[48, 11, 15, 67, 21],
       [11, 41, 13, 66, 24],
       [71, 79, 53, 67, 70],
       [77, 35, 91, 19, 96],
       [35, 54, 37, 41, 17]], dtype=int32)

x
np.float64(46.36)

X_normalized
array([[ 0.06340841, -1.36714726, -1.2124926 ,  0.79801809, -0.98051059],
       [-1.36714726, -0.20723725, -1.28981993,  0.75935442, -0.86451959],
       [ 0.95267275,  1.26198209,  0.25672675,  0.79801809,  0.91400909],
       [ 1.18465476, -0.43921926,  1.72594609, -1.05783793,  1.91926443],
       [-0.43921926,  0.29539042, -0.36189192, -0.20723725, -1.13516526]])

print("Mean:", round(X_normalized.std()))
Mean: 0

print("Standard Deviation:", round(X_normalized.std()))
Standard Deviation: 1
```

#### 2) **Cubes Divisible by 4 Problem** - Generates a 10x10 array of cubed numbers from 1 to 100, extracts the elements divisible by 4, and saves the result to a file.

```python

C = (np.linspace(1,100,100) ** 3).reshape(10,10)

C.shape

div_by_4 = C[C % 4 == 0]

div_by_4.shape

np.save("div_by_4", div_by_4)

```

## Step-by-step procedure
- `C = (np.linspace(1,100,100) ** 3).reshape(10,10)` → Generates 100 evenly spaced cubes numbers from 1 to 100 and reshapes the resulting array into a 10x10 matrix
- `C.shape` → Returns the dimensions of array C
- `div_by_4 = C[C % 4 == 0]` → Filters the array by using boolean indexing to extract elements that are only divisible by 4
- `div_by_4.shape` → Returns the dimensions of the array div_by_4
- `np.save("div_by_4", div_by_4)` → Saves the filtered NumPy array as .npy file

#### Outcome
```python

C
array([[1.00000e+00, 8.00000e+00, 2.70000e+01, 6.40000e+01, 1.25000e+02,
        2.16000e+02, 3.43000e+02, 5.12000e+02, 7.29000e+02, 1.00000e+03],
       [1.33100e+03, 1.72800e+03, 2.19700e+03, 2.74400e+03, 3.37500e+03,
        4.09600e+03, 4.91300e+03, 5.83200e+03, 6.85900e+03, 8.00000e+03],
       [9.26100e+03, 1.06480e+04, 1.21670e+04, 1.38240e+04, 1.56250e+04,
        1.75760e+04, 1.96830e+04, 2.19520e+04, 2.43890e+04, 2.70000e+04],
       [2.97910e+04, 3.27680e+04, 3.59370e+04, 3.93040e+04, 4.28750e+04,
        4.66560e+04, 5.06530e+04, 5.48720e+04, 5.93190e+04, 6.40000e+04],
       [6.89210e+04, 7.40880e+04, 7.95070e+04, 8.51840e+04, 9.11250e+04,
        9.73360e+04, 1.03823e+05, 1.10592e+05, 1.17649e+05, 1.25000e+05],
       [1.32651e+05, 1.40608e+05, 1.48877e+05, 1.57464e+05, 1.66375e+05,
        1.75616e+05, 1.85193e+05, 1.95112e+05, 2.05379e+05, 2.16000e+05],
       [2.26981e+05, 2.38328e+05, 2.50047e+05, 2.62144e+05, 2.74625e+05,
        2.87496e+05, 3.00763e+05, 3.14432e+05, 3.28509e+05, 3.43000e+05],
       [3.57911e+05, 3.73248e+05, 3.89017e+05, 4.05224e+05, 4.21875e+05,
        4.38976e+05, 4.56533e+05, 4.74552e+05, 4.93039e+05, 5.12000e+05],
       [5.31441e+05, 5.51368e+05, 5.71787e+05, 5.92704e+05, 6.14125e+05,
        6.36056e+05, 6.58503e+05, 6.81472e+05, 7.04969e+05, 7.29000e+05],
       [7.53571e+05, 7.78688e+05, 8.04357e+05, 8.30584e+05, 8.57375e+05,
        8.84736e+05, 9.12673e+05, 9.41192e+05, 9.70299e+05, 1.00000e+06]])

C.shape
(10, 10)

div_by_4
array([8.00000e+00, 6.40000e+01, 2.16000e+02, 5.12000e+02, 1.00000e+03,
       1.72800e+03, 2.74400e+03, 4.09600e+03, 5.83200e+03, 8.00000e+03,
       1.06480e+04, 1.38240e+04, 1.75760e+04, 2.19520e+04, 2.70000e+04,
       3.27680e+04, 3.93040e+04, 4.66560e+04, 5.48720e+04, 6.40000e+04,
       7.40880e+04, 8.51840e+04, 9.73360e+04, 1.10592e+05, 1.25000e+05,
       1.40608e+05, 1.57464e+05, 1.75616e+05, 1.95112e+05, 2.16000e+05,
       2.38328e+05, 2.62144e+05, 2.87496e+05, 3.14432e+05, 3.43000e+05,
       3.73248e+05, 4.05224e+05, 4.38976e+05, 4.74552e+05, 5.12000e+05,
       5.51368e+05, 5.92704e+05, 6.36056e+05, 6.81472e+05, 7.29000e+05,
       7.78688e+05, 8.30584e+05, 8.84736e+05, 9.41192e+05, 1.00000e+06])

div_by_4.shape
(50,)

```

#### 3) **Above-Mean Squares Problem** - Generates a 6x6 array of squared numbers from 1 to 36, extracts the elements greater than the mean, and saves the result to a file.

```python

S = (np.linspace(1,36,36) ** 2).reshape(6,6)

S_mean = np.mean(S)

above_mean = S[S > S_mean]

above_mean.shape

np.save("above_mean", above_mean)
```

## Step-by-step procedure
- `S = (np.linspace(1,36,36) ** 2).reshape(6,6)` → Generates 36 evenly spaced squared numbers from 1 to 36 and reshapes the resulting array into a 6x6 matrix
- `S_mean = np.mean(S)` → Computes the mean value of all elements in array S
- `above_mean = S[S > S_mean]` → Filters the array using boolean indexing to only extract elements that is greater than the mean
- `above_mean.shape` → Returns the dimensions of the filtered array above_mean
- `np.save("above_mean", above_mean)` → Saves the filtered NumPy array as .npy file

#### Outcome
```python

S
array([[1.000e+00, 4.000e+00, 9.000e+00, 1.600e+01, 2.500e+01, 3.600e+01],
       [4.900e+01, 6.400e+01, 8.100e+01, 1.000e+02, 1.210e+02, 1.440e+02],
       [1.690e+02, 1.960e+02, 2.250e+02, 2.560e+02, 2.890e+02, 3.240e+02],
       [3.610e+02, 4.000e+02, 4.410e+02, 4.840e+02, 5.290e+02, 5.760e+02],
       [6.250e+02, 6.760e+02, 7.290e+02, 7.840e+02, 8.410e+02, 9.000e+02],
       [9.610e+02, 1.024e+03, 1.089e+03, 1.156e+03, 1.225e+03, 1.296e+03]])

S_mean
np.float64(450.1666666666667)

above_mean
array([ 484.,  529.,  576.,  625.,  676.,  729.,  784.,  841.,  900.,
        961., 1024., 1089., 1156., 1225., 1296.])

above_mean.shape
(15,)

```
