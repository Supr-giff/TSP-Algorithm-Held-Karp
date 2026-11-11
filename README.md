# Held–Karp Algorithm for TSP

## Introduction

The **Traveling Salesperson Problem (TSP)** aims to find the shortest route that visits every city once and returns to the starting city.

**Held–Karp** solves TSP using **Dynamic Programming (DP)** and two techniques:
- **Bitmasking:** Tracks visited cities using binary numbers.
- **Memoization:** Saves calculated costs to avoid repeating work.

## Pseudocode

**Input:** A 4×4 distance matrix (C0, C1, C2, C3).

```text
1. Create empty memo and best_path tables.

2. Define TSP(current_city, visited):

   IF all cities are visited:
       RETURN distance back to C0

   IF state exists in memo:
       RETURN saved cost

   minimum_cost = infinity

   FOR each unvisited city:
       Update visited bitmask
       cost = distance to next city + TSP(next_city, updated_bitmask)

       IF cost < minimum_cost:
           minimum_cost = cost
           Save next_city in best_path

   Save minimum_cost in memo
   RETURN minimum_cost

3. Start TSP from C0 with bitmask 0001.

4. Reconstruct the route using best_path:
   Start route at C0
   Follow saved next cities until all cities are visited
   Add C0 at the end

5. RETURN minimum distance and optimal route
```

## Complexity

- **Time:** \(O(n^2 \times 2^n)\)
- **Space:** \(O(n \times 2^n)\)

Here, **n** is the number of cities.
