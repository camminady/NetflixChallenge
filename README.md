# Netflix Challenge

## TLDR: Downloading the final data
The `*.npy` files (which are described in this README below) can be downloaded [here](https://nextcloud.scc.kit.edu/s/kqD4r65irGBLYNK).


## Postprocessed data description

Since the data is sparse, we store it that way. Think of the matrix `S` with entries `S[i,j] = v`, interpreted as movie `i` was ranked by user `j` with `v` stars. 
Additionally to `v`, we also store `y`, `m`, and `d` which represent the year, month, and day on which the rating was given.

In step 2), several `.npy` files are being created. They store (in numpy format) the following data:

| File name     | Description           | Data type     | Array length |
| ------------- | -------------         | ------------- | -------------|
| `I.npy`       | Movie index           | `np.uint16`   | 100480507    |
| `J.npy`       | User index            | `np.uint32`   | 100480507    |
| `V.npy`       | Rating                | `np.uint8`    | 100480507    |
| `Y.npy`       | Year of rating        | `np.uint16`   | 100480507    |
| `M.npy`       | Month of rating       | `np.uint8`    | 100480507    |
| `D.npy`       | Day of rating         | `np.uint8`    | 100480507    |
| `R.npy`       | Release year of movie | `np.uint16`   | 17770        |
| `T.npy`       | Title of movie        | `str`         | 17770        |

There are 100480507 total ratings for 17770 movies and 2649429 users.

## Reading the data 

With Python, the data can be read using numpy as `X = numpy.load('x.npy',allow_pickle=True)`. This is also possible in Julia using [NPZ](https://github.com/fhs/NPZ.jl) and would look like this:

```

julia> using NPZ;

julia> I = npzread("I.npy");


julia> J = npzread("J.npy");

julia> V = npzread("V.npy");

julia> using SparseArrays

julia> A = sparse(I,J,V);

julia> varinfo()
  name                    size summary                                   
  –––––––––––––––– ––––––––––– ––––––––––––––––––––––––––––––––––––––––––
  A                882.645 MiB 17770×2649429 SparseMatrixCSC{UInt8,Int64}
  Base                         Module                                    
  Core                         Module                                    
  I                191.651 MiB 100480507-element Array{UInt16,1}         
  InteractiveUtils 162.212 KiB Module                                    
  J                383.303 MiB 100480507-element Array{UInt32,1}         
  Main                         Module                                    
  V                 95.826 MiB 100480507-element Array{UInt8,1}          
```

## Preprocessing the raw data

To reproduce the data, follow this description.
1) Download the raw data from this [archive](https://archive.org/download/nf_prize_dataset.tar) and place the extracted files in this folder.

2) Execute all cells in the `InitialPreProcessing.ipynb`. This might take up to 20 minutes.

