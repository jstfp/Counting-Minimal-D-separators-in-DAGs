# Counting-Minimal-D-separators-in-DAGs
Code for paper:Counting Minimal D-separators in DAGs with Its Applications in Consistency Testing
# FCMDS: Finding Close Minimal D-separators in DAGs

[![Python Version](https://img.shields.io/badge/python-3.7%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

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
Install the required dependencies. The code relies on standard Python scientific libraries:
pip install networkx matplotlib
## 🚀 Quick Start
The core algorithm is implemented in the FCMS(g, u, v) function. Here is a simple example of how to use it to find the minimal d-separator between two nodes in a given DAG:
import networkx as nx
from <YOUR_SCRIPT_NAME> import FCMS 

# 1. Create a simple Directed Acyclic Graph (DAG)
G = nx.DiGraph()
G.add_edges_from([('0', '1'), ('1', '2'), ('0', '3'), ('3', '2')])

# 2. Find the minimal d-separator between node '0' and node '2'
source_node = '0'
target_node = '2'

separator = FCMS(G, source_node, target_node)

print(f"Minimal d-separator between {source_node} and {target_node}: {separator}")
## 📊 Reproducing Experiments (Model Checking)
To reproduce the empirical results and generate the comparison plots (Parental vs. Sparse basis) mentioned in the paper, simply run the main script:
python <YOUR_SCRIPT_NAME>.py
This will run the run_experiment_and_plot() function, which evaluates the sum_conditioning_sizes_on_graph over multiple random DAGs and displays the following plots:
Sum of conditioning set sizes: Comparing sparse vs. parental methods across different node sizes \(n\) and expected neighbor densities \(l\).
% Reduction in conditioning set size: Demonstrating the benefit (often >80%) of using the sparse basis over the parental basis.
## 📂 Repository Structure
<YOUR_SCRIPT_NAME>.py: Contains the core algorithm FCMS, helper functions for DAG connectivity, and random DAG generators (generate_connected_dag, generate_random_dag). Also contains the code for experiment evaluation and matplotlib visualization.
