# Planarity Testing

## Explanation

This was the final project for Analysis of Algorithms, taken in the Spring of 2010.  The goal was to implement a complex algorithm successfully, which I did.  I plan to attempt implementing this same algorithm at some point in Haskell, which is why the source files are split out into a java folder.

## Assignment Description

### Algorithm

Implement the following algorithm (description taken from di Battista et al.), which tests whether or not a graph is planar.


_Planarity-Testing_
Input: a biconnected graph G with n vertices and a separating cycle C of G.
Output: an indication of whether G is planar.

1. If the graph has more than 3n -6 edges, return "nonplanar."
2. Compute the pieces of G with respect C.
3. For each piece P of G that is not a path,
  1. let P' be that graph obtained by adding P to C
  2. let C' be the cycle of P' obtained from C by replacing the portion of C between two consecutive attachments with a path of P between them
  3.apply the algorithm recursively to graph P' and cycle C'. If P' is nonplanar, return "nonplanar."
4. Compute the interlacement graph I of the pieces.
5. Test whether I is bipartite. If I is not bipartite, return "nonplanar".
6. Return "planar."

### Program Requirements

You must use Java and your code must run natively on the lab Sun machines. Use good programming style.

Your program must be called TestPlanarity and should take a single argument: The name of the input file, which describes in the format given below a single, biconnected graph (you algorithm should only be given biconnected graphs). Your program will read this input file and run a planarity test on the graph it represents. If the graph is planar, your program must output (to standard output) "planar," otherwise it must output "nonplanar." The input file must be formatted as follows.

  * Each line should contain exactly two integers separated by a space.
  * Each line represents an edge.
  * The two numbers on each line represent the vertices that are adjacent to the edge.

Since I will be testing your code on my own test inputs, it is critical that your program can read precisely from the format described above.

### Test Data

Since I will be grading your code on my own (secret, randomly generated) test cases, you need to carefully test your code to make sure that it works. You should leave as much time as possible for this phase. You are free to generate test data anyway you wish, but if you would like to automate the process, the following definitions are useful. The following is a recursive definition of a biconnected graph (not necessary planar or nonplanar). I will use these definitions to randomly generate my test cases.

  * The triangle K_3 is a biconnected graph.
  * Any graph created by removing an edge {u, v} from a bidirected graph and adding a new vertex w and edges {u, w} and {w, v} to it is also biconnected.
  * Any graph created by adding a new vertex w and edges {w, u} and {w, v} to a bidirected graph that contains the vertices u and v is also biconnected.
  * Any graph created by adding a new edge {u, v} to a bidirected graph containing vertices u and v is also bidirected.

Here is a recursive definition of a biconnected, nonplanar graph.

  * K_5 and K(3,3) are biconnected, nonplanar graphs.
  * Any graph created by removing an edge {u, v} from a bidirected, nonplanar graph and adding a new vertex w and edges {u, w} and {w, v} to it is also biconnected and nonplanar.
  * Any graph created by adding a new vertex w and edges {w, u} and {w, v} to a bidirected, nonplanar graph that contains the vertices u and v is also biconnected and nonplanar.
  * Any graph created by adding a new edge {u, v} to a bidirected, nonplanar graph containing vertices u and v is also bidirected and nonplanar.

Here is a recursive definition of a biconnected, planar graph.

  * The triangle K_3 is a biconnected, planar graph.
  * Any graph created by removing an edge {u, v} from a bidirected, planar graph and adding a new vertex w and edges {u, w}, {w, v} to it is also biconnected.
  * Any graph graph created by adding a new vertex w and edges {w, u} and {w, v} to a bidirected graph that contains a face containing the vertices u and v is also biconnected.
  * Any graph created by adding a new edge {u, v} to a bidirected graph that contains a face containing vertices u and v is also bidirected.
