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

$$A -- R_{\text{eq}} -- B$$


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

```python
import networkx as nx
import matplotlib.pyplot as plt
from IPython.display import display, Image
import io

# Global step counter
step_counter = 0

# Initialize graph
G = nx.DiGraph()
edges = [
    ('B+', 'R2'), ('R2', 'R3'), ('R3', 'R4'), ('B+', 'R1'), ('R1', 'R4'),
    ('R4', 'R5'), ('R5', 'B-')
]
G.add_edges_from(edges)

def draw_graph(G, highlight_nodes=[], title="Step"):
    global step_counter
    print(f"Drawing graph: {title}")
    pos = nx.spring_layout(G, seed=42)
    fig, ax = plt.subplots(figsize=(8, 6))
    node_colors = ['red' if node in highlight_nodes else 'lightgray' for node in G.nodes()]
    nx.draw(G, pos, with_labels=True, arrows=True, node_color=node_colors, node_size=1000, ax=ax)
    plt.title(title)

    buf = io.BytesIO()
    plt.savefig(buf, format='png')
    buf.seek(0)
    display(Image(data=buf.read()))
    plt.close()
    step_counter += 1

# Step 1: Draw initial
draw_graph(G, title="Initial Circuit")

# === Step 2: Series Merge R2 + R3 -> R23 ===
G.add_edge('R23', 'R4')
G.remove_edge('R2', 'R3')
G.remove_edge('R3', 'R4')
G = nx.relabel_nodes(G, {'R2': 'R23'})
G.remove_node('R3')
draw_graph(G, highlight_nodes=['R23'], title="Series Merge: R2 + R3 → R23")

# === Step 3: Series Merge R4 + R5 -> R45 ===
G.add_edge('R45', 'B-')
G.remove_edge('R4', 'R5')
G.remove_edge('R5', 'B-')
G = nx.relabel_nodes(G, {'R4': 'R45'})
G.remove_node('R5')
draw_graph(G, highlight_nodes=['R45'], title="Series Merge: R4 + R5 → R45")

# === Step 4: Connect R1 and R23 directly to R45 if not already ===
# (This ensures all 3 are feeding into same node)
G.add_edge('R1', 'R45')
G.add_edge('R23', 'R45')

# === Step 5: Merge R1, R23, R45 (Parallel) → R12345 ===
# All three go from B+ to B-, now merge into single R12345
G.add_edge('R12345', 'B-')
G.remove_edge('R1', 'R45')
G.remove_edge('R23', 'R45')
G.remove_edge('R45', 'B-')
G = nx.relabel_nodes(G, {'R1': 'R12345'})
G.remove_node('R23')
G.remove_node('R45')
draw_graph(G, highlight_nodes=['R12345'], title="Parallel Merge: R1 || R23 || R45 → R12345")

# Final
draw_graph(G, title="Final Simplified Circuit")
```

![alt text](Untitled-7.png)
![alt text](Untitled-8.png)
![alt text](Untitled-9.png)
![alt text](Untitled-10.png)
![alt text](Untitled-11.png)

## 2. Python Algorithm

## Step 1: Original Circuit (with parallel and series resistors)

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
