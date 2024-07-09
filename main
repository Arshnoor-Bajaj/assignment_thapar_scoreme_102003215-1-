def longest_path(graph: list) -> int:
    topo_order = topological_sort(graph)
    return calculate_longest_path(graph, topo_order)

def topological_sort(graph):
    n = len(graph)
    in_degree = [0] * n
    for u in range(n):
        for v, _ in graph[u]:
            in_degree[v] += 1

    queue = [u for u in range(n) if in_degree[u] == 0]
    
    topo_order = []
    while queue:
        u = queue.pop(0)
        topo_order.append(u)
        for v, _ in graph[u]:
            in_degree[v] -= 1
            if in_degree[v] == 0:
                queue.append(v)
    
    return topo_order

def calculate_longest_path(graph, topo_order):
    n = len(graph)
    dist = [-float('inf')] * n
    # Initialize the distance of all nodes with no incoming edges to 0
    for u in topo_order:
        if dist[u] == -float('inf'):
            dist[u] = 0
        for v, weight in graph[u]:
            if dist[v] < dist[u] + weight:
                dist[v] = dist[u] + weight
    
    return max(dist)
