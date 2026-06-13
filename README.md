# Algorithms for Massive Data - Market-Basket Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/leilacielok/market_basket_analysis/blob/main/project.ipynb)

This notebook implements and compares three frequent itemset mining algorithms on the IMDB Top 1000 dataset:

- **Apriori**: baseline candidate-generation algorithm;
- **PCY**: hash-based optimization of Apriori for frequent pairs;
- **SON**: partition-based algorithm that mines local chunks and validates candidates globally.

Each movie is represented as a basket containing its main actors (`Star1`, `Star2`, `Star3`, `Star4`), representing items. The goal is to find frequent singletons, pairs and triples of actors.

# Main Findings

The three algorithms return the same frequent itemsets, but their execution times differ.

- **Apriori** is the fastest on this dataset because the baskets are very small.
- **PCY** does not provide a significant advantage here, because each basket contains only up to four actors, so the number of candidate pairs is already limited.
- **SON** is useful as a partition-based algorithm for large or distributed datasets, but on this small dataset it introduces additional overhead due to local mining and global candidate recounting.
