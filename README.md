# Fortran associative array (A.K.A. hash table or dictionary)
* Implemented with treap, a clever randomized binary search tree

## Purpose
* An associative array for fortran, which enables insertion, deletion, and search for O(log n) cost
    * Roughly corresponds to `std::set` and `std::map` of C++ standard template library (STL)
* Other operations allowed
    * Obtain minimum/maximum item: O(log n); not implemented yet
    * Merge/split: O(1); not implemented yet
    * Obtain size of an array: O(1)

## Usage
See `main.f90` and `Makefile` for sample usage

## Todo
* Better key handling (insertion already exist, search not found, etc.)
* Second argument (i.e., value of the dictionary)
    * Currently it is just implemented as a multiset rather than a dictionary
* Ordered derived type as a key
    * https://software.intel.com/en-us/forums/intel-fortran-compiler-for-linux-and-mac-os-x/topic/595015

## References
* Treap https://en.wikipedia.org/wiki/Treap
* Treap https://www.slideshare.net/iwiwi/2-12188757

