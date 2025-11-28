# BalancedList – Unrolled Linked List with Optimized Operations

This project implements three linear data structures in C++:

- `ArrayList` – dynamic array with automatic resize
- `SinglyLinkedList` – singly linked list with a tail pointer
- `BalancedList` – an **unrolled linked list** that stores multiple items per node and is optimized to achieve near *O(log n)* behavior for key operations

The project was built as part of **ICS 46: Data Structure Implementation** at UC Irvine.

---

## Features

- **ArrayList**
  - Dynamic resizing with `expand()` and `shrink()`
  - `add(index, item)` and `remove(index)` that shift elements appropriately

- **SinglyLinkedList**
  - Tail pointer for efficient `addLast()` / `removeLast()`
  - Index-based `get`, `add`, and `remove` with full pointer maintenance

- **BalancedList**
  - Unrolled linked list: each node contains an `ArrayList` of fixed capacity (e.g., 10 elements)
  - Splits nodes when full and redistributes elements
  - Supports:
    - `get(index)`
    - `add(item)` at the front
    - `add(index, item)` at arbitrary positions
    - `remove()` from front
    - `remove(index)` from arbitrary positions
  - Designed to keep operations efficient even for large lists by balancing work across nodes

---

## Project Structure

```text
ArrayLinkedList/
├── build/               # Out-of-source build directory (ignored in Git)
├── gtest/               # GoogleTest files for unit testing
├── include/
│   ├── ArrayList.hpp
│   ├── ArrayList.tpp
│   ├── SinglyLinkedList.hpp
│   ├── SinglyLinkedList.tpp
│   └── BalancedList.tpp
├── src/
│   └── main.cpp         # Demo / timing harness
├── CMakeLists.txt
└── test_lab.cpp         # Unit tests

----

Build Instructions:
# From the repo root
mkdir -p build
cd build

cmake ..
make

After a successful build, binaries will be located in build/bin.

Running:
From inside build/bin

# Run the main program with timing / demo
./ArrayLinkedList

# Run unit tests
./ArrayLinkedListTests


Implementation Notes

BalancedList is implemented as a single linear chain of nodes (no extra trees or skip lists).
Each node wraps an ArrayList:
When a node becomes full, it is split:
A new node is created
Some elements are moved into the new node
Pointers are updated and the new element is inserted
The design goal is to balance the work of:
Index-based access
Insertions at arbitrary positions
Deletes at arbitrary positions


