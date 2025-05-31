<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>DFS Traversal - Exp No 2</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 30px;
      line-height: 1.6;
    }
    h1, h3 {
      color: #2e6da4;
    }
    h1 {
      font-size: 26px;
    }
    h3 {
      font-size: 20px;
    }
    p, ol, ul {
      font-size: 16px;
    }
    code {
      background: #f4f4f4;
      padding: 2px 6px;
      border-radius: 4px;
    }
    pre {
      background: #f4f4f4;
      padding: 12px;
      border-radius: 6px;
      overflow-x: auto;
    }
    hr {
      border: 1px solid #ddd;
    }
    strong {
      color: #333;
    }
  </style>
</head>
<body>

<h1>Exp No 2: Implement Depth First Search Traversal of a Graph</h1>
<h3>Name: SANJUSHRI A</h3>
<h3>Register Number: 212223040187</h3>

<h3>Aim:</h3>
<p>To implement Depth First Search Traversal of a Graph using Python 3.</p>

<h3>Theory:</h3>
<p><strong>Depth First Traversal</strong> (or DFS) for a graph is similar to Depth First Traversal of a tree. Unlike trees, graphs may contain cycles (a node may be visited twice), so a boolean <code>visited</code> array is used to avoid processing a node more than once.</p>

<p>A graph can have more than one DFS traversal. Depth-first search starts at the root (or any arbitrary node) and explores as far as possible along each branch before backtracking.</p>

<p><strong>Steps:</strong></p>
<ol>
  <li>Initially, stack and visited arrays are empty.</li>
  <li>Visit the starting node (e.g., node 0) and put its adjacent unvisited nodes into the stack.</li>
  <li>Visit the node on top of the stack, mark it as visited, and push its unvisited neighbors into the stack.</li>
  <li>Continue until all nodes are visited and the stack is empty.</li>
</ol>

<h3>Illustration:</h3>
<ul>
  <li><strong>Step 1:</strong> Stack and visited arrays are empty.</li>
  <li><strong>Step 2:</strong> Visit node 0 → Stack: [1, 2, 3]</li>
  <li><strong>Step 3:</strong> Visit node 1 → Stack: [2, 3, neighbors of 1]</li>
  <li><strong>Step 4:</strong> Visit node 2 → Stack: [3, 4, neighbors of 2]</li>
  <li><strong>Step 5:</strong> Visit node 4</li>
  <li><strong>Step 6:</strong> Visit node 3</li>
</ul>

<h3>Algorithm:</h3>
<ol>
  <li>Construct a Graph with Nodes and Edges</li>
  <li>DFS uses Stack and Recursion</li>
  <li>Insert a START node to the STACK</li>
  <li>Explore successors or neighbors if unvisited</li>
  <li>If not visited, add to STACK; else, continue backtracking</li>
</ol>

<hr>

<h3>Program:</h3>
<pre><code>from collections import defaultdict

# Depth First Search using Stack and Recursion
def dfs(graph, start, visited, path):
    path.append(start)
    visited[start] = True
    for neighbour in graph[start]:
        if not visited[neighbour]:
            dfs(graph, neighbour, visited, path)
    return path

# Input the number of nodes and edges
graph = defaultdict(list)
n, e = map(int, input().split())

# Build the graph
for _ in range(e):
    u, v = input().split()
    graph[u].append(v)
    graph[v].append(u)  # undirected graph

# DFS traversal
start = 'A'
visited = defaultdict(bool)
path = []
traversed_path = dfs(graph, start, visited, path)
print(traversed_path)
</code></pre>

<h3>Sample Input:</h3>
<pre><code>8 9
A B
A C
B E
C D
B D
C G
D F
G F
F H
</code></pre>

<h3>Sample Output:</h3>
<pre><code>['A', 'B', 'E', 'D', 'C', 'G', 'F', 'H']</code></pre>

<hr>

<h3>Sample Input:</h3>
<pre><code>5 5
0 1
0 2
0 3
2 3
2 4
</code></pre>

<h3>Sample Output:</h3>
<pre><code>['0', '1', '2', '3', '4']</code></pre>

<hr>

<h3>Result:</h3>
<p>Thus, a graph was constructed and Depth First Search was implemented successfully.</p>

</body>
</html>
