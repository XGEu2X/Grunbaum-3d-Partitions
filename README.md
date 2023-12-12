# What is it?

This is an implementation of the algorithms proposed in the article (Article Title). We recommend reading it first.

The implementation is given in a **Jupyter** notebook using **Sagemath**. In the first cell are the definitions of all functions. On the following are some examples of the use including tests with points generated randomly on a square and points generated in the moment curve.

## Usage

### Main example

The use is really simple. You only need to provide the set of points to *find_partition* function and this one returns the first orthogonal equipartition found for that set or an empty list otherwise.

This is an example of usage in which 10,000 randomly generated sets of 8 points each are tested.

```python
#Size of sets to be tested.
num_points=8
#Number of sets to be tested.
N=10000
#Counters.
totalexamples = 0
counterexamples = 0

for totaltries in tqdm(range(N)):
    #Here the set is randomly generated.
    vectors = generate_random_vectors(num_points=num_points, min_coord=-100, max_coord=100)
    try:
        #Tests if the set have an equipartition.
        partition = find_partition(vectors)
        totalexamples += 1
        if len(partition)==0:
            counterexamples += 1
            print_vectors(vectors,as_list=True)
    except Exception as error:
        continue

print("Examples searched in general position:",totalexamples)
print("Counterexamples found:",counterexamples)
print(100.*counterexamples/totalexamples,'%')
```
Notice that in this example the points are randomly generated in a square.

### Util functions

We also implemented some functions to facilitate the usage. There are listed next in a non-formal API.

```python
'''
  Generate a list of random 3D vectors.

  Args:
    num_points (int): Number of random vectors to generate (default is 8).
    min_coord (int): Minimum coordinate value for each axis (default is -10).
    max_coord (int): Maximum coordinate value for each axis (default is 10).

  Returns:
    list: A list of tuples representing random 3D points.
'''
def generate_random_vectors(num_points, min_coord, max_coord)

'''
  Prints a set of points.

  Args:
    vectors (list): Points to be printed.
    as_list (bool):
      True -> Prints the points coordinates with line breaks.
      False -> Prints the indices and then the coordinates.
'''
def print_vectors(vectors,as_list=False)

'''
  Shows the planes of the partition and the indices of the points in one side of each plane.

  Args:
    partition: The partition returned by find_partition function.
'''
def print_partition(partition):

```
