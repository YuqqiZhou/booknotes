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

Filtering methods 
|paper|detail|
|---|---|
|GraphQL|local pruning and global refinement<br>local pruning is not fixed with RDF model<br> global refinement,"k度匹配性",prune v' if (v')'s neighbours not match v's neigbours|
|**CFL**|compressed path index : 'neighbour generating','neighbour filtering'|
|dp-iso|candidate space. But use *LDF* as generate rule, so it is not well|

Recommendation
1. **Fillter Methods**  Use the candidate vertex computation method of GraphQL as default. If the preprocessing time often dominates the query time, then switch to the method of CFL or DP-iso. 
2. **ordering methods** Adopt the ordering methods of GraphQL and RI on dense and sparse data graphs respectively.
3. Use CECI/DP-iso-style auxiliary data structures to maintain edges between candidates, and adopt the set intersection
based local candidates computation. If the data graphs are very dense, then use QFilter as the set intersection method. 
4. Enable the failing sets pruning on large queries, but disable it on small ones. By integrating the recommended techniques in each category into Algorithm 1, we can obtain
an optimized method that outperforms the state-of-the-art algorithms such as DP-iso.