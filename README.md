# BalancedList

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
