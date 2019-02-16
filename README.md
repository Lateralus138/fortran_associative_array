# Fortran associative array [![Build Status](https://travis-ci.org/ysdtkm/fortran_associative_array.svg?branch=master)](https://travis-ci.org/ysdtkm/fortran_associative_array)
This provides an associative array, known as "hash table" or "dictionary" data types, which is lacking in Fortran. This scalable implementation utilizes treap (randomized binary search tree) data structure.

## Specifications
* An associative array for fortran, which enables fast insertion, deletion, and search
    * Roughly corresponds to `std::map` (C++) or `dict` (Python)
    * Operations already implemented
    
      |Operation                  |Cost     |Note                                          |
      |----                       |----     |----                                          |
      |Insertion/assignment       |O(log n) |`insert_or_assign` subroutine                 |
      |Deletion                   |O(log n) |`remove` subroutine                           |
      |Existence/lookup           |O(log n) |`exists` and `get_val` functions              |
      |Max/min/k-th element       |O(log n) |`get_kth_key` function                        |
      |Count                      |O(1)     |`get_size` function                           |
      |Clear                      |O(n)     |Implicitly called as a destructor             |

    * Other operations allowed by the data structure (not implemented)
    
      |Operation                  |Cost                     |Note                                          |
      |----                       |----                     |----                                          |
      |Merge/split                |O(log n)                 |Destructive                                   |
      |(lower\|upper)\_bound      |O(log n)                 |                                              |
      |Range search               |O(log n + elements found)|                                              |
      |Deep copy                  |O(n)                     |Preorder DFS                                  |
      |Conversion to sorted array |O(n)                     |`show` subroutine is similar                  |

## Usage
* See `sample.f90` for sample usage
* Edit `dtypes.h` for using for another data types
    * For string key (arbitrary length), `keytype1` should be `character(:),allocatable` and `keytype2` should be `character(*)`
    * For other key types, `keytype1` and `keytype2` are the same

## References
* Treap https://en.wikipedia.org/wiki/Treap
* Treap https://www.slideshare.net/iwiwi/2-12188757

