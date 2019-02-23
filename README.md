# Fortran associative array [![Build Status](https://travis-ci.org/ysdtkm/fortran_associative_array.svg?branch=master)](https://travis-ci.org/ysdtkm/fortran_associative_array)
A scalable associative array (known as **hash table** or **dictionary**) for Fortran

## Specifications
* Internal data structure is treap (randomized binary search tree)
* Roughly corresponds to `std::map` (C++) or `dict` (Python)
    * A **key** can be `characters` (either fixed or arbitrary length), an `integer`, or a `real`
    * A **value** can be any fortran intrinsic data type (with fixed length or kind). A *copy* of the value is stored in the `dict` object
    * Does not affect Fortran's intrinsic random state
* Implemented operations

  |Operation                  |Cost     |Implementation                                                    |
  |----                       |----     |----                                                              |
  |Insertion/assignment       |O(log n) |Subroutine `insert_or_assign(dict, key, val)`                     |
  |Deletion                   |O(log n) |Subroutine `remove(dict, key)`<br>(Error if not exist)            |
  |Existence of a key         |O(log n) |Logical function `exists(dict, key)`                              |
  |Reference                  |O(log n) |Valuetype function `get_val(dict, key)`<br>(Error if not exist)   |
  |Get max/min/k-th key       |O(log n) |Keytype function `get_kth_key(dict, k)`<br>(Error if out of bounds; 1-based)|
  |Count                      |O(1)     |Integer function `get_size(dict)`                                           |
  |Retrieve sorted array      |O(n)     |Subroutine `get_keys_vals(dict, keys, vals, n)`<br>(Not for arbitrary length keys)|
  |Clear                      |O(n)     |Implicitly called as a destructor                                           |

* Other operations allowed by the data structure (not implemented)

  |Operation                  |Cost                     |Note                                          |
  |----                       |----                     |----                                          |
  |Merge/split                |O(log n)                 |Destructive                                   |
  |lower_bound/upper_bound    |O(log n)                 |                                              |
  |Range search               |O(log n + elements found)|                                              |
  |Deep copy                  |O(n)                     |Preorder DFS                                  |

* Speed comparison with `gfortran`/`g++`, without compiler optimization

  <img src="test/speedtest/visual/out.png" width="50%">

## Usage
* See `sample.f90` for sample usage
* Edit `dtypes.h` if using another data types
    * For string key (arbitrary length), `keytype1` should be `character(:),allocatable` and `keytype2` should be `character(*)`
    * For other key types, `keytype1` and `keytype2` are the same

## References
* Treap https://en.wikipedia.org/wiki/Treap
* Treap https://www.slideshare.net/iwiwi/2-12188757

