# EXPERIMENT 2 NUMERICAL PYTHON NUMPY-PA2_ECE2112_MALLARI,LJN
**Submitted by Lance Joseph N. Mallari**

**2ECE-A    Date: 09/08/2026**

This is repository contains all the necessary code for PA2 along with the breakdown for each line of code
### I. Intended Learning Outcomes
At the end of this laboratory activity, the student should be able to:
1. create and reshape NumPy arrays using appropriate NumPy functions;
2. perform vectorized numerical operations on an ndarray;
3. compute array statistics and use Boolean conditions to select elements; and
4. save computed NumPy arrays as .npy files.

### II. Instructions
Write Python code in a Jupyter Notebook to solve each problem. Import NumPy as np. Place each
problem in a separate, clearly labeled section of the notebook.

• Use NumPy array operations. Do not use Python loops or list comprehensions to perform the
  required numerical calculations or filtering.
  
• Do not hard-code a computed result. Construct every result from the array specified in the problem.

• Use the exact variable and output filenames stated below.

• Display the requested checks in the notebook before saving each result.

• Do not use libraries other than NumPy.

### III. PROGRAMMING PROBLEMS


**A. REPRODUCIBLE NORMALIZATION PROBLEM**
Create a reproducible random 5 × 5 integer ndarray named X. Use the following two statements before
performing any calculation:

```
np.random.seed(2112)

X = np.random.randint(10, 101, size=(5, 5))
```

Normalize the complete array using:

```
Z = X − ¯x / σ
```

where ¯x is the mean of all 25 elements and σ is their population standard deviation as returned by
NumPy’s default std() call. Store the normalized array in X normalized.
Required checks: Display X, X normalized, its mean, and its standard deviation. Up to floating-
point rounding, the normalized mean must be 0 and the normalized standard deviation must be 1.
Save the normalized array as:

```
X_normalized.npy
```

### PART A CODE:
```
Import numpy as np
```
```
np.random.seed(2112)

X = np.random.randint(10, 101, size=(5, 5))

x_mid = X.mean()
sigma = X.std()

X_normalized = (X - x_mid) / sigma

print("Array X:\n", X)
print("\nNormalized Array (X_normalized):\n", X_normalized)
print("\nMean of X_normalized:", X_normalized.mean())
print("Standard Deviation of X_normalized:", X_normalized.std())

np.save("X_normalized.npy", X_normalized)
```
### OUTPUT A:

```
Array X:
 [[48 11 15 67 21]
 [11 41 13 66 24]
 [71 79 53 67 70]
 [77 35 91 19 96]
 [35 54 37 41 17]]

Normalized Array (X_normalized):
 [[ 0.06340841 -1.36714726 -1.2124926   0.79801809 -0.98051059]
 [-1.36714726 -0.20723725 -1.28981993  0.75935442 -0.86451959]
 [ 0.95267275  1.26198209  0.25672675  0.79801809  0.91400909]
 [ 1.18465476 -0.43921926  1.72594609 -1.05783793  1.91926443]
 [-0.43921926  0.29539042 -0.36189192 -0.20723725 -1.13516526]]

Mean of X_normalized: 0.0
Standard Deviation of X_normalized: 0.9999999999999999
```

**Detailed Explanation of Each function in A**
* `np.random.seed(2112)`: Sets a fixed seed for NumPy's pseudo-random number generator so that the generated numbers remain identical every time the script runs.
* `X = np.random.randint(10, 101, size=(5, 5))`: Creates a 5x5 matrix **X** containing random integers between 10 and 100 (inclusive).
* `x_mid = X.mean()`
`sigma = X.std()`: Calculates the mean (**x_mid**) and population standard deviation (**sigma**) across all 25 elements in matrix **X**.
* `X_normalized = (X - x_mid) / sigma`: Computes the z-score normalization for each element in the matrix.
> Where **X** is each matrix entry, **x_mid** is the mean of all 25 entries, and **sigma** is the standard deviation.


* `print("Array X:\n", X)`: Displays the original 5x5 array **X** in the console output.
* `print("\nNormalized Array (X_normalized):\n", X_normalized)`: Displays the normalized version of matrix **X**.
* `print("\nMean of X_normalized:", X_normalized.mean())`: Displays the mean of the normalized array (which evaluates to approximately 0).
* `print("Standard Deviation of X_normalized:", X_normalized.std())`: Displays the standard deviation of the normalized array (which evaluates to approximately 1).
* `np.save("X_normalized.npy", X_normalized)`: Exports and saves the normalized array as a binary `.npy` file named `X_normalized.npy`.


### B. CUBES DIVISIBLE BY 4 PROBLEM
Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a
10 × 10 ndarray named C. Thus, C begins with 1^3 and ends with 100^3
Use a Boolean condition on C to obtain every cubed value divisible by 4. Store the selected values in
div by 4. Preserve NumPy’s normal row-major selection order.
Required checks: Display the shape of C, the array div by 4, and the number of selected elements.
A correct solution has 50 selected elements; the first is 8 and the last is 1,000,000.

Save the selected array as:
`div_by_4.npy`



### PART B CODE:
```
C = (np.arange(1, 101) ** 3).reshape(10, 10)

div_by_4 = C[C % 4 == 0]

print("Shape of C:", C.shape)
print("\nArray of cubed values divisible by 4 (div_by_4):\n", div_by_4)
print("\nNumber of selected elements:", div_by_4.size)
print("First element:", div_by_4[0])
print("Last element:", div_by_4[-1])

np.save ("div_by_4.npy", div_by_4)
```
### OUTPUT B:
```
Shape of C: (10, 10)

Array of cubed values divisible by 4 (div_by_4):
 [      8      64     216     512    1000    1728    2744    4096    5832
    8000   10648   13824   17576   21952   27000   32768   39304   46656
   54872   64000   74088   85184   97336  110592  125000  140608  157464
  175616  195112  216000  238328  262144  287496  314432  343000  373248
  405224  438976  474552  512000  551368  592704  636056  681472  729000
  778688  830584  884736  941192 1000000]

Number of selected elements: 50
First element: 8
Last element: 1000000
```
**Detailed Explanation of Each function in B:**
The following functions and methods in this code are:

* `C = (np.arange(1, 101) ** 3).reshape(10, 10)`: Generates numbers from 1 to 100, cubes each value, and reshapes the array into a $10 \times 10$ matrix **C**.
* `div_by_4 = C[C % 4 == 0]`: Filters array **C** using boolean indexing to extract only the elements divisible by 4.
> Where `C % 4 == 0` evaluates to `True` for any entry that leaves a remainder of 0 when divided by 4.

* `print("Shape of C:", C.shape)`: Prints the dimensions/shape of matrix **C** (which outputs `(10, 10)`).
* `print("\nArray of cubed values divisible by 4 (div_by_4):\n", div_by_4)`: Displays the 1D array containing all filtered cubed values divisible by 4.
* `print("\nNumber of selected elements:", div_by_4.size)`: Displays the total count of elements matching the condition in the `div_by_4` array.
* `print("First element:", div_by_4[0])`: Displays the first element (index 0) of the `div_by_4` array.
* `print("Last element:", div_by_4[-1])`: Displays the final element (index -1) of the `div_by_4` array.
* `np.save ("div_by_4.npy", div_by_4)`: Exports and saves the `div_by_4` array as a binary `.npy` file named `div_by_4.npy`.



### C. ABOVE-MEAN SQUARES PROBLEM
Create a 6 × 6 ndarray named S containing the squares of the first 36 positive integers in increasing
row-major order. Compute the mean of all elements of S and store it in S mean. Then use Boolean
filtering to select only the elements strictly greater than S mean. Store these values in above mean.
Required checks: Display S, S mean, above mean, and the number of selected elements. A correct
solution has 15 selected elements; the first is 484 and the last is 1296.

Save the selected array as:
`above_mean.npy`


### PART C CODE:
```
S = (np.arange(1, 37) ** 2).reshape(6, 6)

S_mean = S.mean()

above_mean = S[S > S_mean]

print("Array S:\n", S)
print("\nMean of S (S_mean):", S_mean)
print("\nElements strictly greater than S_mean (above_mean):\n", above_mean)
print("\nNumber of selected elements:", above_mean.size)
print("First element:", above_mean[0])
print("Last element:", above_mean[-1])

np.save("above_mean.npy", above_mean)
```

### OUTPUT C:
```
Array S:
 [[   1    4    9   16   25   36]
 [  49   64   81  100  121  144]
 [ 169  196  225  256  289  324]
 [ 361  400  441  484  529  576]
 [ 625  676  729  784  841  900]
 [ 961 1024 1089 1156 1225 1296]]

Mean of S (S_mean): 450.1666666666667

Elements strictly greater than S_mean (above_mean):
 [ 484  529  576  625  676  729  784  841  900  961 1024 1089 1156 1225
 1296]

Number of selected elements: 15
First element: 484
Last element: 1296
```

**Detailed Explanation of Each function in C:**
* `S = (np.arange(1, 37) ** 2).reshape(6, 6)`: Generates numbers from 1 to 36, squares each value, and reshapes the array into a 6x6 matrix **S**.
* `S_mean = S.mean()`: Calculates the mean across all 36 elements in matrix **S** and assigns it to **S_mean**.
* `above_mean = S[S > S_mean]`: Filters array **S** using boolean indexing to extract only the elements strictly greater than **S_mean**.
> Where `S > S_mean` evaluates to `True` for any entry whose value exceeds the calculated mean.

* `print("Array S:\n", S)`: Displays the original 6x6 array **S** in the console output.
* `print("\nMean of S (S_mean):", S_mean)`: Displays the calculated mean of matrix **S**.
* `print("\nElements strictly greater than S_mean (above_mean):\n", above_mean)`: Displays the 1D array containing all elements that are greater than **S_mean**.
* `print("\nNumber of selected elements:", above_mean.size)`: Displays the total count of elements stored in the `above_mean` array.
* `print("First element:", above_mean[0])`: Displays the first element (index 0) of the `above_mean` array.
* `print("Last element:", above_mean[-1])`: Displays the final element (index -1) of the `above_mean` array.
* `np.save("above_mean.npy", above_mean)`: Exports and saves the `above_mean` array as a binary `.npy` file named `above_mean.npy`.

---
### **END OF NOTEBOOK**
