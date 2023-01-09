
# Breaking the Ice with Graphs

## An Introduction to Graph Theory in Programming Part-1

![](https://miro.medium.com/max/1050/0*3ZTHLDLFWv-8_fPF)

Photo by  [Chris Ried](https://unsplash.com/@cdr6934?utm_source=medium&utm_medium=referral)  on  [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

Algorithms and Data Structures can be a scary place for anyone new to Computer Science and Competitive Coding. Graphs are often considered to be one of the scarier data structures out there.

But graphs are super fun once you get a hang of them.😃

Let’s get started.

# What is a Graph Data Structure?

A graph is a tool in mathematics that is used to depict the relationship between entities.

![](https://miro.medium.com/max/563/1*MrxLGnH_6FlBYbuFu4eEqg.png)

A simple directed graph

The circles are called vertices and represent some entities. These could be anything ranging from stations in a rail network to members of a family.

The lines are called edges and represent some relation.

There are 2 types of graphs — directed graphs and undirected graphs. The one shown above is directed, which means that the edges go in 1 direction. So I can go from 1 to 2 but not 2 to 1. Getting rid of the arrows would make it an undirected graph which would mean all edges are 2-way.

Graphs are extremely useful wherever we have to solve problems involving objects related to each other. In the real world computer networks, social networks, cities connected by highways can all be analyzed as graph problems. The applications are endless — from calculating the similarity between 2 twitter users or calculating the optimal path a delivery truck must take to city planning and water supply management.

**Basic Terms:**

-   Walk: Any sequence of edges joining a sequence of vertices. Suppose you go from node 1 to 2 to 4 — it would constitute a walk 1->2,2->4.
-   Trail: A walk in which all edges are distinct. So, you do not travel a given edge more than once.
-   Cycle: A non-empty trail starting and ending at the same vertex.

# Representing a Graph in a Computer

There are 2 popular ways to represent a graph in code:

1.  Adjacency matrix

2. Adjacency List

## Adjacency Matrix

Suppose a graph has n vertices. We can represent the connections between them by using an n x n matrix.

Follow these steps:

1.  Initialize an n x n matrix with 0s( if the vertices are numbered from 1 it would be convenient to use a (n+1)x(n+1) matrix ignoring the 0th row and column).
2.  If there is an edge from vertex u to v set matrix[u][v]=1. Do this for each edge.

Your adjacency matrix is ready✨.

Thus every connection is represented by a 1 at the appropriate position.

![](https://miro.medium.com/max/624/1*56IYne8lDqDb86Y9aEHf_Q.png)

Adjacency Matrix for the Graph shown above.

## Adjacency List

An Adjacency list is a list of lists.

You have a main list with n sub-lists corresponding to the n vertices.

The ‘ith’ sub-list contains vertices that vertex ‘i’ is connected to.

For Example, if there edges from vertex 1 to 2,3 and 4, then the first sub-list will contain 2,3 and 4.

![](https://miro.medium.com/max/588/1*wAjLqWaia7oma_ste-UwNw.png)

Adjacency List for the Graph shown above.

In C++ this structure can easily be implemented by using 2-d vectors.

## Matrix Vs List:

(|V| stands for number of vertices and |E| stands for number of edges.)

A matrix has certain advantages:

-   We can check if an edge exists between 2 vertices u and v by checking mat[u][v] ie. in O(1) time. But in an adjacency list, you would have to traverse the whole sub-list of u and hence the worst case could take O(|V|) time if u is connected to every other vertex(Adjacency lists can be implemented in other ways to eliminate this problem).
-   Removing or inserting an edge can be done in constant time by changing one value again O(1) while an adjacency list could take O(|V|).

A List has the following advantage:

-   It takes much less space as compared to a matrix as long as every vertex is not connected to every other vertex O(|V|+|E|). But a matrix always takes O(|V|²) space, which is often not suitable for competitive coding problems.

Now let's get to the good stuff!

# Graph Traversals

There are 2 classic approaches to traversing a graph both of which take time complexity of O(|V|+|E|).

1.  Depth First Search
2.  Breadth First Search

## Depth First Search

Depth First Search popularly known as DFS, in essence, means you follow a path till the very end before trying out another, hence depth-first. It is generally done recursively or using a stack.

The pseudo-code:

//n is number of vertices  
visited[n]={0};  
dfs(source){  
    dfs[source]=1;  
    for(vertex u adjacent to source){  
        if(!visited[v]){  
           dfs(u);  
         }  
     }  
}

In simple words, you maintain an array to remember the vertices visited so far. Initially, it would be filled with 0 or false. On visiting a vertex u you would make arr[ u]=1 or true. Then you visit an unvisited vertex adjacent to your current vertex and set that vertex as visited and then visit its neighbour and so on ‘recursively’ until the vertex you are in has no unvisited neighbours.

Once this stage is reached you return to the previous recursive call, and visit the next unvisited neighbour and so on.

In the above graph, you would visit vertices in the following order: 1 2 4 3

## Breadth First Search

Breadth First Search popularly known as BFS, in essence, means you visit all unvisited neighbours of the current vertex first and then do the same for the next vertex. It is generally done using a queue.

The pseudo-code:

//n is number of vertices  
visited[n]={0};  
bfs(source){  
    visited[source]=1;  
    Queue q;  
    q.push(source);  
    while(!q.empty()){  
        cur=q.pop();  
        for(vertex u adjacent to source){  
           if(!visited[u]){  
              visited[u]=1;  
              q.push(u);  
           }  
         }  
     }  
}

In the above graph, you would visit vertices in the following order: 1 2 3 4

## Some Basic Applications:

1.  In an unweighted graph, BFS would give the shortest path from source to any given node.
2.  DFS can be used to easily detect cycles.

Whether you’re a competitive programmer, a CS student, a network administrator or planner, graphs are an indispensable tool worth using.

You’ve now got a taste of graphs and understand the concepts that will enable you to dive deeper into the world of graphs.

To get to the next stage of your exploration of graphs follow this link  [https://medium.com/the-acm-manipal-blog/navigating-through-graphs-5105964aced7](https://medium.com/the-acm-manipal-blog/navigating-through-graphs-5105964aced7)
