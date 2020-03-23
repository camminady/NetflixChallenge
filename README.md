# Netflix Challenge


## Preprocessing the raw data

1) Download the raw data from this [archive](https://archive.org/download/nf_prize_dataset.tar) and place the extracted files in this folder.

2) Execute all cells in the `InitialPreProcessing.ipynb`. This might take up to 20 minutes.

## Postprocessed data

Since the data is sparse, we store it that way. Think of the matrix `S` with entries `S[i,j] = r`, interpreted as movie `i` was ranked by user `j` with `r` stars. 
Additionally to `r`, we also store `y`, `m`, and `d` which represent the year, month, and day on which the rating was given.

In step 2), several `.npy` files are being created. They store (in numpy format) the following data:

| File name  | Description | Data type | Array length |
| ------------- | ------------- |  ------------- | 
| `I.npy`   | Movie index| `np.uint16` | 100480507|
| `J.npy`   | User index | `np.uint32` | 100480507|
| `V.npy`   | Rating    | `np.uint8` | 100480507|
| `Y.npy`   | Year of rating | `np.uint16` | 100480507|
| `M.npy`   | Month of rating | `np.uint8` |100480507|
| `D.npy`   | Day of rating | `np.uint8` | 100480507|
| `R.npy`   | Release year of movie | `np.uint16`| 17770|
| `T.npy`   | Title of movie | `str` | 17770|

There are 100480507 total ratings for 17770 movies.

