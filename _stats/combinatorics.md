---
layout: maths
name: Combinatorics
category: Tools
---

<ins>Permutations</ins>

A permutation (also called *arrangement*) is the number of sequences we can make in selecting elements from a set. 

Conditions:

- selected elements are ordered

- no element occurs more than once

- it is not necessary to select all elements from the set

$$P^n_k = n(n-1)(n-2)...(n-k+1) = \frac{n!}{(n-k)!} \text{ where } k \leq n$$

Example: we have 4 numbered balls. If we select 2 of them, how many different ordered sequences can we do?

<ins>Combinations</ins>

Combinations are similar to permutations except that order doesn't matter. We thus adjust the above formula in removing the number of possible permutations in the selected sequence:

$$C^n_k = \begin{pmatrix}n \\ k\end{pmatrix} = \frac{P^n_k}{P^k_k} = \frac{\frac{n!}{(n-k)!}}{\frac{k!}{0!}} = \frac{n!}{(n-k)!k!} \text{ where } k \leq n$$

Example (Time's up): we have 15 names. If I select 5 names, what is the total number of possible combinations? (Answer: 3003!!)