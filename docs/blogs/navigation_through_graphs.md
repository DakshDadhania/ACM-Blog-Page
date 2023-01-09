
# Navigating Through Graphs

## An Introduction to Graph Theory in Programming Part-2

![](https://miro.medium.com/max/1050/0*fpML6RVeS4-ZwcGA)

Photo by  [Markus Spiske](https://unsplash.com/@markusspiske?utm_source=medium&utm_medium=referral)  on  [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

Now that we know graph representation and traversals, let’s start exploring graphs.

Since graphs can be used to represent connections between cities or supply units and consumers, one major application of graphs is to analyze the best possible routes to go from one point to the other.

# Shortest Path Algorithms

The graphs we have seen so far did not have weights on edges. In other words, we considered each edge to have the same length or cost of traversal.

However, most applications edges have weights or costs associated with them which could represent the length of a highway in a system of cities, the delay of a route in a computer network etc.

Cost can be represented in several ways. We could modify our adjacency list or matrix to store cost.

When we modify the adjacency matrix to store cost, it’s called the cost matrix. In the cost matrix, cost[u][v] would denote the cost to go from u to v.Instead of storing 0 for non-adjacent vertices, we could store a cost of INFINITY and instead of storing a 1 for adjacent vertices, we could store the cost of the edge connecting them. The cost[i][i] would be 0 as there would be no cost to go from vertex i to the same vertex.

Adjacency List could be modified to store pairs of (adjacent vertex, cost) in the sub-lists.

|V| denotes number of vertices and |E| denotes number of edges.

## Floyd Warshall Algorithm

The Floyd Warshall algorithm is an application of dynamic programming in graph theory. It takes the cost matrix as input and gives us the shortest path from every node to every other node. (The graph must not contain negative cycles, because if negative cycles were present we could make the cost arbitrarily small.)

The pseudocode:

floyd_warshall(cost){//number of vertices is n  
  res=costfor k-> 1 to n:for i->1 to n:for j->1 to n:res[i][j]=min(res[i][j],res[i][k]+res[k][j])  
  return res}

We use dynamic programming here — we use a series of |V| matrices to get the final result (we don’t actually store n different matrices but modify the same matrix). In the kth iteration of the outer loop, we compute the shortest path — where the intermediate node is numbered k or less — from every vertex to every other vertex.

So in the 0th iteration, the res matrix has the shortest path between all vertices with intermediate vertices numbered 0 or less (so no intermediate vertices) which is the cost matrix itself.

In the 1st iteration, we would have shortest paths, with intermediate vertices numbered 1 or less and so on. By the end of n iterations, we get the shortest path between all vertices with any set of intermediate vertices allowed and hence this is our result.

**Why does it work?**

Let us say we’re at the kth iteration of the outer loop. We already have the shortest distances with intermediate vertices numbered k-1 or less from the previous iteration.

Now suppose take the case of the shortest path from some vertex i to some vertex j. In the current iteration, we need to find the shortest path from i to j with intermediate vertices less than or equal to k.

Now there are 2 possibilities- the shortest path could include k or not. If it does not include k then the intermediate vertices are numbered k-1 or less and we already computed cost for this in the previous iteration. If it does include k (k appears only once as there are no negative cycle and going through a cycle would not give minimum cost path), the path from i to k can only have intermediate vertices numbers k-1 or less and the path from k to j must have vertices numbered k-1 or less. We have already calculated these distances in the previous iteration and they are available in res[i][k] and res[k][j]. Now taking the best of the 2 cases — including k and not including k — we get our result for the kth iteration.

**When Should You Use the Floyd-Warshall Algorithm:**

**Remember**:- Floyd-Warshall applies to both directed and undirected graphs with both positive and negative edge weight. But there  **shouldn’t be negative length cycles**!

This algorithm has O(|V|³) time complexity.

You can use this algorithm when you have a relatively small number of vertices and many queries.

It is definitely not worth doing if you need to find the shortest path between just 2 vertices.

You cannot use the algorithm in competitive coding questions with number of vertices of the order of 10⁵.

## Dijkstra’s Algorithm:

This is a single-source shortest path algorithm — it gives you the shortest paths from one vertex to all the other vertices.  **This algorithm doesn’t work with negative edge weights.**

Dijkstra's algorithm follows a greedy approach and chooses the least cost path at each step. When you visit a node the current distance to the node from the source is the least and it cannot get smaller than that.

The pseudocode:

djikstra(){Initialize distances to be INF;Make distance[source]=0;set unvisited={all vertices};for i->1 to |V|:current=node with least distance;unvisited.remove(current);for edges from current to each unvisited vertex u:distance[u]=min(distance[u],distance[current]+cost[current][u]);}

**Why does it work?**

The array distances hold the distance or cost from source to all vertices. It is initialized to infinity and then the distance to the source is made 0.

At a given iteration, we choose the vertex say ‘u’ with least distance and this is the final shortest distance for the given vertex. Remember, this distance is the shortest distance considering the previously visited vertices as potential penultimate vertices (the vertex that comes before the last vertex in the shortest path). Now, if there cannot be a shorter path having any other vertex as the penultimate vertex because then we would have to traverse a longer distance to that vertex + distance from that vertex to u (and there are no negative edges).

**There are 2 ways to implement Dijkstra’s Algorithm:**

One of time complexity O(|V|²) and the other of O(|E|log(|V|)).

We can implement it with order O(|V|²) by going through the distance array linearly to find maximum at each iteration.

We can implement it with order O(|E|log(|V|)) by using a priority queue to get the minimum distance path.

In C++ we can effectively use the set of STL to get the minimum and also for updating the distances easily.

**Which implementation should you use:**

If your graph is very dense( most of the vertices are connected to each other) and the edges are of the order of |V|², then the O(|V|²) implementation is preferable as the other one would give O(|V|²log(|V|)).

But if |E| is of the order of |V|, you should go with O(|E|log(|V|)).

**Bonus Tip:**

We’ve talked about single source to all other vertices but finding shortest path from all vertices to a single destination can also be done similarly.

Just invert all edges and do Dijkstra from the destination. The result would be shortest path from all vertices to the destination.✨

**In short,** using Dijkstra is preferable to Floyd-Warshall when you need the distance from only one vertex. However, it cannot handle negative weights.

## Bellman-Ford Algorithm:

Bellman-ford algorithm is also a single source shortest path algorithm like Dijkstra but it can handle negative weights. However, negative length cycles are not allowed for the obvious reason of arbitrarily small distance.

The pseudocode:

bellman-ford(){Initialize distances to be INF;Make distance[source]=0;for i->1 to |V|-1:for each edge from u to v:distance[v]=min(distance[v],distance[u]+cost[u][v])}

At iteration i, we get the smallest length from source to all vertices with maximum of i-1 intermediate vertices in between. So at the end of |V|-1 iterations, we have taken into account all possibilities.

**When should you use it:**

This algorithm has a complexity of O(|V|*|E|).

It overcomes Dijkstra’s shortcoming of no negative weights allowed.

But if only positive weights are present Dijkstra is generally preferable.

If the graph is dense and we have |E| in the order of |V|², then this algorithm gives complexity of O(|V|³) like Floyd-Warshall but doesn’t give as much information.

However, with smaller number of edges and negative weights, this algorithm can be very useful.

**Bonus Tip:**

You can detect negative cycle using the Bellman-Ford algorithm!

Once you do the bellman ford algorithm,for each edge from u to v check if distance[u]+cost[u][v]<distance[v]. If it is true for any edge, then there is a negative cycle present.

The reason is with |V|-1 iterations you get the minimum length path from to all vertices as long as there are no negative cycles. Now if the distance reduces, then it is because of a negative cycle.

That was an introduction to a few popular shortest path algorithms. Hope you found it insightful.
