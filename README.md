# Crypt Arithmetic Puzzle Solver

## Introduction

Crypt arithmetic puzzles pose unique mathematical challenges where letters or symbols represent digits. The solver must find a valid digit for each letter to satisfy a given arithmetic equation. These puzzles adhere to constraints like unique digit representation and non-zero leading digits. Solving such puzzles can involve logical deduction, trial and error, and clever strategies, offering a stimulating exercise in problem-solving and algorithmic thinking.

## Problem Formulation

Crypt arithmetic puzzles can be formulated as search problems, where the state space consists of all possible mappings from letters to digits. A valid state is one where each letter is assigned a unique digit, and the arithmetic operation defined by the puzzle is correctly solved. The initial state has no letters assigned to digits, and the goal state is the assignment where the puzzle equation holds true.

### Objective

Find a mapping from letters to digits that makes the given equation true.

### Constraints

1. Each letter must represent a unique digit.
2. No two letters can represent the same digit.
3. Leading digits of any number in the puzzle cannot be zero.

## Algorithm Descriptions

### Depth-First Search (DFS)

- **Overview**: DFS explores the search space by starting at the root node and exploring as far as possible along each branch before backtracking.
- **Implementation Details**: DFS attempts to assign digits to letters, using backtracking to explore all possible mappings. Solutions are validated with the `is_valid_solution` function.
- **Complexity Analysis**:
  - **Time Complexity**: O(10^n), where n is the number of unique letters.
  - **Space Complexity**: O(n), corresponding to the depth of the recursion.

### A* Search

- **Overview**: A* finds the shortest path to the goal state using a heuristic to estimate the cost from the current state to the goal.
- **Implementation Details**: Utilizes a priority queue and a heuristic function estimating cost based on the absolute difference between partial sums of words and the target value.
- **Complexity Analysis**:
  - **Time Complexity**: Depends on the heuristic's effectiveness but generally O(b^d), where b is the branching factor and d is the depth of the search space.
  - **Space Complexity**: Influenced by the size of the priority queue, which can grow significantly.

## Example: Solving "SEND + MORE = MONEY"

### DFS Steps:

1. Start with an empty mapping and explore digit assignments for each letter.
2. Validate solutions once all letters are assigned.
3. Use backtracking to explore alternative mappings until the solution is found.

### A* Steps:

1. Begin with an initial state and use a heuristic function to guide the search.
2. Assign digits to letters, prioritizing states based on the heuristic value.
3. Validate complete assignments to find the solution.

## Observations and Comparison

- **DFS** is straightforward but may become impractical for larger puzzles due to its exhaustive nature.
- **A* Search** is more efficient than DFS as the heuristic guides the search, potentially reducing the number of states explored. Its efficiency heavily depends on the heuristic's effectiveness.

## Conclusion

A* search, with a well-chosen heuristic, can provide a more efficient solution by intelligently navigating the search space, making it preferable for larger or more complex puzzles. However, the simplicity of DFS may still make it a viable option for simpler puzzles. The choice between DFS and A* involves a trade-off between simplicity and efficiency, with A* generally offering better performance for crypt arithmetic puzzles like "SEND + MORE = MONEY" when the heuristic closely aligns with the problem structure.
