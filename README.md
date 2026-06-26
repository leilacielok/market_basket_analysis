# Algorithms for Massive Data - Market-Basket Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/leilacielok/market_basket_analysis/blob/main/project.ipynb)

This project implements and compares three frequent itemset mining algorithms on a movie-cast dataset derived from the IMDb Top 1000 dataset.

Each movie is modelled as a basket, while the actors appearing in the columns `Star1`, `Star2`, `Star3`, and `Star4` are treated as items. The objective is to identify frequent singletons, pairs, and triples of actors, interpreting them as recurring collaboration patterns within the dataset.

## Implemented Algorithms

- **Apriori**: baseline level-wise frequent itemset mining algorithm based on candidate generation and pruning.
- **PCY**: hash-based optimization of Apriori designed to reduce the number of candidate pairs through bucket counting and bitmap filtering.
- **SON**: partition-based algorithm that mines candidates locally on data chunks and validates them globally through a second counting phase.

Each movie is represented as a basket containing its main actors (`Star1`, `Star2`, `Star3`, `Star4`), representing items. The goal is to find frequent singletons, pairs and triples of actors.

# Main Findings

The three algorithms return the same frequent itemsets, confirming the correctness of the implementations. However, their execution profiles differ.

- **Apriori** performs best on this dataset because the baskets are very small and fit easily in memory.
- **PCY** introduces limited benefits in this setting, since each basket contains at most four actors and the number of possible candidate pairs is already constrained.
- **SON** is conceptually well suited to large-scale or distributed data, but on this compact dataset it introduces additional overhead due to local candidate generation and global recounting.

Overall, the results show that algorithmic advantages depend strongly on dataset size, basket length, and workload complexity.
