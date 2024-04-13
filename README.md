In the university’s advanced programming lab, you have been tasked with a project that
simulates managing a large dataset that changes over time. Initially, you considered using
standard arrays to handle the fluctuating data - however, you quickly realized that arrays
have fixed sizes, which would make it challenging to accommodate changes in the dataset as
elements are added or removed. Now, most programming languages provide built-in data
structures that allow dynamic resizing. However, they often do not reveal the internal
workings that make this possible. Hence, you are now tasked with:
● Creating a DynamicArray class that manages an array of integers. The class should
include the following methods:
i. void add(int element): Adds an element to the end of the array, resizing as
needed.
ii. bool removeAt(int index): Removes the element at the specified index,
maintaining the order of other elements. Returns true if the operation is
successful, false if the index is out of bounds.
iii. int get(int index) const: Returns the element at the given index or throws an
out-of-bounds exception.
iv. int size() const: Returns the current number of elements in the array.
v. int search(int element): Recursively searches for an element and returns its
index, or -1 if not found.
vi. void sort(): Implements a recursive sorting algorithm to order the array
elements.
