# FCMDS: Finding Close Minimal D-separators in DAGs

[![Python Version](https://img.shields.io/badge/python-3.7%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Code for paper: Counting Minimal D-separators in DAGs with Its Applications in Consistency Testing

## 📖 Introduction

We introduce a novel algorithm for enumerating all minimal d-separators between two given variables in a Directed Acyclic Graph (DAG). Unlike existing approaches that typically rely on graph moralization, our method operates directly on the original DAG. The algorithm is built upon a newly established necessary and sufficient condition for minimality. We prove that its time complexity is $\mathcal{O}(n^3 R_{ab})$, where $n$ is the number of nodes and $R_{ab}$ denotes the total number of minimal d-separators between vertices $a$ and $b$. 

To demonstrate its practical utility, we apply the proposed **Finding Close Minimal D-separators (FCMDS)** algorithm to generate sparse basis sets for DAG consistency testing. Empirical results show that, across various graph densities, FCMDS significantly reduces the number of conditioning variables compared to traditional parent-set methods, with a reduction exceeding **80%** in sparse graphs. This makes the algorithm well-suited for causal inference and constraint-based structure learning in large-scale graphical models.

## ✨ Key Features
- **Direct DAG Operation:** Operates without the need for graph moralization.
- **High Efficiency:** Polynomial time complexity $\mathcal{O}(n^3)$ per minimal d-separator.
- **Sparse Basis Generation:** Substantially reduces the number of conditioning variables (>80% reduction for sparse graphs), outperforming traditional parental basis methods.

## ⚙️ Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/jstfp/Counting-Minimal-D-separators-in-DAGs.git
   cd Counting-Minimal-D-separators-in-DAGs
   ```
2. Install the required dependencies. The code relies on standard Python scientific libraries:
   ```bash
   pip install networkx matplotlib
   ```
## 🚀 Quick Start & Reproducing Experiments
All core algorithms (like FCMS) and the code for generating comparison plots (Parental vs. Sparse basis) are entirely contained within the Jupyter Notebook.
To use the algorithm or reproduce the empirical results, please open and run the provided notebook:
1. Launch Jupyter Notebook in your terminal:
   ```bash
   jupyter notebook main.ipynb
   ```
2. Inside the notebook, you will find the definition of the FCMS(g, u, v) function. An internal example looks like this:
   import networkx as nx
   ```python
   # 1. Create a simple Directed Acyclic Graph (DAG)
   G = nx.DiGraph()
   G.add_edges_from([('0', '1'), ('1', '2'), ('0', '3'), ('3', '2')])

   # 2. Find the minimal d-separator between node '0' and node '2'
   source_node = '0'
   target_node = '2'

   # 3.Calling the algorithm defined in the previous cells
   separator = FCMS(G, source_node, target_node)
   print(f"Minimal d-separator between {source_node} and {target_node}: {separator}")
   ```
3. By running the cells towards the end of the notebook, you will execute run_experiment_and_plot(), which outputs two visual charts:
Sum of conditioning set sizes: Comparing sparse vs. parental methods across different node sizes \(n\) and expected neighbor densities \(l\).
% Reduction in conditioning set size: Demonstrating the benefit (often >80%) of using the sparse basis over the parental basis.
## 📂 Repository Structure
main.ipynb: The main interactive notebook containing the core algorithm FCMS, helper functions for DAG connectivity, random DAG generators, experiment evaluations, and matplotlib visualizations.

