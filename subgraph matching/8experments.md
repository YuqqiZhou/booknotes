### In-Memory Subgraph Matching: An In-depth Study

Experimental results for QuickSI,
GraphQL, CFL, CECI, DP-iso, RI and VF2++. All are *in-memory* algorithms.
#### four aspects

- method of filtering candidate vertices in the data graph
- method of ordering query vertices; 
- method of enumerating
partial results
- other optimization techniques

#### motheds types
|Community|Model|Methodology|Description|
|:-:|:-:|:-:|:-:|
|Databse|exploration-based <br>搜索|Backtracking Search|recursively extends intermediate results by mapping query vertices to data vertices along an order of query vertices|
|Databse|Multi-way Join<br>表连接|Pair-wise Join <br> Worst-Case Optimal Join||
|AI/Bioinformatics|state space representation <br>状态空间搜索|Backtracking Search|each state represents an intermediate result. The feasible state in the state space is a match|
|AI|constraint programming <br>限制条件检验|Backtracking Search|vertices and edges in q correspond to variables and constraints respectively. The domain of the variables is the data ertices. This approach can evaluate subgraph matching by finding assignments to variables that satisfy the constraints.<br>先凑点集，然后验证是否符合限制条件|

#### Frameworks

|Name|Description|
|:-:|:-:|
|direct-enumeration|directly explores G to enumerate all results|
|indexing-enumeration|build index upon graph G|
|preprocessing-enumeration|1.candidate vertex set for each query vertex <br> 2.build auxiliary data structures for edeges <br>3.generate matching order<br>4.enumeratre all the results|
1.
2.
3.