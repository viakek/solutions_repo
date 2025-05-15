# Problem 1

# Equivalent Resistance Using Graph Theory

### Motivation

The **equivalent resistance** between two terminals (START and END) in an electrical network is a central concept in circuit analysis. While basic configurations can be handled with simple series and parallel rules, **complex circuits** with many junctions and loops require a more robust approach.

Using **graph theory**, we model the circuit as a graph where:
- **Nodes** represent junctions,
- **Edges** represent resistors,
- **Weights** on edges represent resistance values.

This transforms circuit simplification into a graph-reduction problem. The process can be fully automated and is essential for tasks like circuit simulation, network optimization, and computer-aided design.

---

## 1. Graph-Based Circuit Simplification

### Step-by-Step Approach

Given a weighted undirected graph:

- START and END are the terminals.
- Each edge $e_{ij}$ has a resistance $R_{ij}$.
- The goal is to compute a single equivalent resistance $R_{\text{eq}}$ between START and END.

We apply the following reduction rules iteratively:

---

### 1.1 Series Reduction

If a node (not START or END) has exactly two neighbors and connects only to them, its resistors are in **series**.

Replace this subgraph:

A -- R₁ -- B -- R₂ -- C


with:

A -- R₁₂ -- C


Where:

$$
R_{\text{eq}} = R_1 + R_2
$$

---

### 1.2 Parallel Reduction

If multiple resistors connect the same two nodes, they are in **parallel**.

Replace this:

A -- R₁ -- B
A -- R₂ -- B


with:

A -- R_{\text{eq}} -- B


Where:

$$
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2}
$$

---

### 1.3 Iteration

Repeat series and parallel simplification until only one resistor remains between START and END:

$$
R_{\text{total}} = R_{\text{eq}}
$$

---

## 2. Python Algorithm

This Python implementation uses `networkx` to represent the circuit as a graph.

```python
import networkx as nx

def equivalent_resistance(graph: nx.MultiGraph, start, end):
    G = graph.copy()

    def combine_series():
        changed = False
        for node in list(G.nodes):
            if node in (start, end):
                continue
            neighbors = list(G.neighbors(node))
            if len(neighbors) == 2:
                u, v = neighbors
                # Assume only one edge each for series detection
                data1 = list(G.get_edge_data(u, node).values())[0]
                data2 = list(G.get_edge_data(node, v).values())[0]
                R1 = data1['resistance']
                R2 = data2['resistance']
                R_eq = R1 + R2
                G.add_edge(u, v, resistance=R_eq)
                G.remove_node(node)
                changed = True
        return changed

    def combine_parallel():
        changed = False
        edge_list = list(G.edges(keys=True, data=True))
        seen = set()
        for u, v, k, d in edge_list:
            pair = tuple(sorted((u, v)))
            if pair in seen:
                continue
            all_edges = list(G.get_edge_data(u, v).values())
            if len(all_edges) > 1:
                resistances = [e['resistance'] for e in all_edges]
                R_eq = 1 / sum(1 / R for R in resistances)
                G.remove_edges_from([(u, v, key) for key in list(G.get_edge_data(u, v).keys())])
                G.add_edge(u, v, resistance=R_eq)
                changed = True
            seen.add(pair)
        return changed

    while True:
        if not (combine_series() or combine_parallel()):
            break

    if G.has_edge(start, end):
        return list(G.get_edge_data(start, end).values())[0]['resistance']
    else:
        raise Exception("No path between START and END")

# Example test
if __name__ == "__main__":
    G = nx.MultiGraph()
    G.add_edge("START", "A", resistance=2)
    G.add_edge("A", "B", resistance=3)
    G.add_edge("B", "END", resistance=4)
    G.add_edge("A", "END", resistance=6)  # Parallel path

    result = equivalent_resistance(G, "START", "END")
    print(f"Equivalent resistance: {result:.2f} ohms")
```

## 3. Example Analysis

Given the test circuit:

- START → A: $R = 2\,\Omega$
- A → B: $R = 3\,\Omega$ 
- B → END: $R = 4\,\Omega$  
- A → END: $R = 6\,\Omega$  

### Step-by-step:

1. Combine A–B and B–END (series):  
   $R_{\text{AB-END}} = 3 + 4 = 7\,\Omega$

2. A has two paths to END:  
   - One path is: $7\,\Omega$  
   - Other path is: $6\,\Omega$

3. Combine those in parallel:

   $$
   \frac{1}{R_{\text{eq}}} = \frac{1}{6} + \frac{1}{7} = \frac{13}{42}
   \Rightarrow R_{\text{eq}} \approx 3.23\,\Omega
   $$

4. Finally, add START–A:

   $$
   R_{\text{total}} = 2 + 3.23 = 5.23\,\Omega
   $$

---

## 4. Conclusion

We showed how to:

- Use graph theory to model electrical circuits.
- Detect and simplify series and parallel connections.
- Automate the process using Python and `networkx`.

This method scales well to arbitrarily complex networks and is highly applicable to modern engineering workflows such as simulation, layout, and optimization of electrical systems.
