
| Method                       | Description                                           | Example Input                      | Example Output                  |
|------------------------------|-------------------------------------------------------|------------------------------------|---------------------------------|
| `np.array()`                 | Create an array from a list or tuple                   | `[1, 2, 3]`                        | `array([1, 2, 3])`              |
| `np.zeros()`                 | Create an array filled with zeros                      | `(2, 3)`                           | `array([[0., 0., 0.], [0., 0., 0.]])` |
| `np.ones()`                  | Create an array filled with ones                       | `(3, 3)`                           | `array([[1., 1., 1.], [1., 1., 1.], [1., 1., 1.]])` |
| `np.empty()`                 | Create an empty array                                  | `(2, 2)`                           | `array([[0., 0.], [0., 0.]])`    |
| `np.arange()`                | Create an array with evenly spaced values              | `(0, 10, 2)`                       | `array([0, 2, 4, 6, 8])`         |
| `np.linspace()`              | Create an array with evenly spaced values over a range | `(0, 1, 5)`                        | `array([0. , 0.25, 0.5 , 0.75, 1. ])` |
| `np.random.rand()`           | Create an array of random values                       | `(3, 3)`                           | Randomly generated array         |
| `ndarray.shape`              | Get the dimensions of an array                         | `array([[1, 2, 3], [4, 5, 6]])`    | `(2, 3)`                        |
| `ndarray.reshape()`          | Reshape an array                                      | `(2, 3)`                           | Reshaped array                   |
| `ndarray.ndim`               | Get the number of array dimensions                     | `array([[1, 2, 3], [4, 5, 6]])`    | `2`                             |
| `ndarray.size`               | Get the total number of elements in an array           | `array([[1, 2, 3], [4, 5, 6]])`    | `6`                             |
| `ndarray.flatten()`          | Flatten a multi-dimensional array                      | `array([[1, 2], [3, 4]])`          | `array([1, 2, 3, 4])`           |
| `np.concatenate()`           | Combine multiple arrays together                       | `((arr1, arr2), axis=0)`           | Concatenated array               |
| `np.split()`                 | Split an array into sub-arrays                         | `(arr, 2)`                         | List of sub-arrays               |
| `np.transpose()`             | Change the rows into columns and columns into rows     | `array([[1, 2], [3, 4]])`          | Transposed array                 |
| `np.add()`                   | Add two arrays element by element                      | `(arr1, arr2)`                     | Element-wise sum                 |
| `np.subtract()`              | Subtract elements of one array from another            | `(arr1, arr2)`                     | Element-wise subtraction         |
| `np.multiply()`              | Multiply two arrays element by element                 | `(arr1, arr2)`                     | Element-wise multiplication      |


| `np.divide()`                | Divide elements of one array by another                | `(arr1, arr2)`                     | Element-wise division            |
| `ndarray[start:end:step]`    | Extract a portion of the array with a step size        | `arr[1:5:2]`                       | Extracted sub-array              |
| `ndarray[condition]`         | Use a condition to select specific elements            | `arr[arr > 5]`                     | Filtered array                   |
| `ndarray[:, col_index]`      | Access a specific column in a multi-dimensional array  | `arr[:, 2]`                        | Column array                     |
| `np.meshgrid()`              | Create coordinate matrices from coordinate vectors     | `x = [1, 2, 3], y = [4, 5]`        | `X`, `Y` coordinate matrices     |
| `np.stack()`                 | Stack arrays along a new axis                          | `(arr1, arr2)`                     | Stacked array                    |

Remember, these examples are simplified to make them easier to understand for a 6th grader. You can explore more about each method and their functionalities as you continue to learn and gain programming skills!
