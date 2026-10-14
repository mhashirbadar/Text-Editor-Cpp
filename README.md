# Text Editor in C++

A basic line based text editor built for **CS-218 Data Structures and Algorithms** (Complex Engineering Problem, Fall 2026), Department of Computer and Information Systems Engineering, BS Computer Systems Engineering.

The focus of the project is not the user interface but the design of data structures and algorithms that store and manipulate text efficiently. All core structures are implemented from scratch rather than taken from the standard library containers.

## Features

- **File operations:** new document, open existing file, save, save as, exit
- **Display:** show the whole document, line by line, with line and character counts
- **Insert and delete:** insert text at a position, delete a character, word or range, insert a new line, delete a line or range of lines
- **Search:** find a word or sequence of characters and report every match location
- **Replace:** replace one occurrence or all occurrences
- **Undo:** stack-based undo for insertion, deletion and replacement
- **Error handling:** invalid input (empty search string, missing file, empty document, out-of-range positions) is handled without crashing

## Data structures

| Purpose | Structure |
| --- | --- |
| Document | Doubly linked list of lines |
| Text of each line | Custom dynamic character array (`MyString`) |
| Undo history | Custom stack of `Command` records |
| Search results | Dynamic array of (line, column) pairs |

Undo stores an inverse-able record of each edit (type, position, affected text) instead of a snapshot of the whole document. The full justification and time/space complexity analysis are in the project report.

## Project structure

```
.
├── src/
│   ├── MyString.h / MyString.cpp    # dynamic char array
│   ├── LineList.h / LineList.cpp    # doubly linked list of lines
│   ├── Stack.h / Stack.cpp          # undo stack
│   ├── Command.h                    # undo record
│   ├── Editor.h / Editor.cpp        # document operations
│   ├── FileIO.cpp                   # load and save
│   └── main.cpp                     # command loop
├── tests/                           # test cases and sample files
├── report/                          # project report
└── README.md
```

## Build and run

Requires a C++11 (or newer) compiler such as `g++`.

```bash
g++ -std=c++11 -Wall -Wextra -g src/*.cpp -o editor
./editor
```

To check for memory errors and leaks while developing:

```bash
g++ -std=c++11 -g -fsanitize=address src/*.cpp -o editor
```

## Usage

Commands will be documented here once the command loop is implemented.

## Complexity summary

Let n = number of lines, L = line length, m = pattern length, k = matches.

| Operation | Time |
| --- | --- |
| Insert line at known position | O(1) |
| Insert or delete line by index | O(n) to locate, O(1) to link or unlink |
| Insert or delete text in a line | O(L) |
| Search (naive) | O(total characters · m) |
| Replace all | O(total characters · m + k·L) |
| Undo (stack pop) | O(1), plus reapplying the operation |

## Progress

- [ ] `MyString`
- [ ] `LineList`
- [ ] Display and statistics
- [ ] File operations
- [ ] Insert and delete
- [ ] Search
- [ ] Replace
- [ ] Undo stack
- [ ] Error handling
- [ ] Testing
- [ ] Project report

## Limitations

To be completed after implementation (for example: naive search algorithm, line-based editing without a cursor, bounded undo depth).

## Author

Hashir CS-124 Abdul Rehman CS-137
CS-218 Data Structures and Algorithms, SE Batch 2025
