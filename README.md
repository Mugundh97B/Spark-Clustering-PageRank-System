# Spark Clustering, Inverted Index & PageRank System

This repository contains the implementation of three core large-scale data processing algorithms using **PySpark**:

-  Clustering (k-center, k-means++, Coreset)
-  Inverted Index & Search Engine (TF-IDF)
-  PageRank on Graph Data

---

##  Project Overview

This project is part of **Machine Learning for Big Data (MLBD)** coursework and demonstrates how distributed computing (Spark) can be used to solve real-world data processing problems efficiently.

---

##  Key Concepts Implemented

###  Part 1: Clustering

- **k-center (Farthest First Traversal)**
- **k-means++ Initialization**
- **Coreset Approach (kcenter → kmeans++)**

 Dataset:
- UCI SpamBase Dataset
- 4601 data points × 58 features

Results:

| Method | Objective Value |
|--------|---------------|
| kcenter | ~206,587 |
| kmeans++ | ~77,727  |
| Coreset (k1=10) | ~156,735 |
| Coreset (k1=20) | ~140,166 |

Insights:
- k-means++ gives best clustering quality
- Coreset improves efficiency but slightly reduces accuracy
- Increasing coreset size improves performance

---

###  Part 2: Inverted Index & Search Engine

- Built a complete **search engine backend**
- Implemented:
  - Stop word removal
  - Token normalization
  - Position indexing
  - Query processing

Features:
- `queryFindPagesWhichContainWord`
- `queryFindPositionsOfWordInAPage`

---

### TF-IDF Demonstration

- Demonstrated relevance scoring

Observation:
- Word **"stack"** appears in all documents  
- IDF = log(N/N) = 0  
- TF-IDF = 0  

Common words are not useful for ranking

---

###  Part 3: PageRank (Spark)

- Implemented iterative PageRank using Spark RDDs
- Used damping factor β = 0.8
- Ran for 40 iterations

Small Graph Result:
Top score ≈ 0.0357 (Expected ≈ 0.036)


Whole Graph Result:

**Top 5 Nodes:**
| Rank | Node | Score |
|------|------|------|
| 1 | 263 | 0.002020 |
| 2 | 537 | 0.001943 |
| 3 | 965 | 0.001925 |
| 4 | 243 | 0.001852 |
| 5 | 285 | 0.001827 |

**Bottom 5 Nodes:**
| Rank | Node | Score |
|------|------|------|
| 1 | 558 | 0.000328 |
| 2 | 93 | 0.000351 |
| 3 | 62 | 0.000353 |
| 4 | 424 | 0.000354 |
| 5 | 408 | 0.000387 |

 Validation:
PageRank sum ≈ 1.0

---

### Convergence Analysis

- Rapid convergence within ~5 iterations
- Stable thereafter
- 40 iterations sufficient

---

## Tech Stack

- Python 
- PySpark
- NumPy
- Matplotlib

---

## Repository Structure


├── datasets/

├── notebook.ipynb

└── README.md


---

## Assumptions

- Squared Euclidean distance used for clustering
- Node IDs are not assumed sequential in PageRank
- No dangling nodes in graph
- Stop words are excluded but counted for positions
- Edge duplicates are removed

---

## observation

- k-means++ provides best clustering performance
- Coreset balances efficiency vs accuracy
- Inverted index enables fast search queries
- TF-IDF reduces importance of common words
- PageRank effectively ranks nodes in large graphs
- Spark enables scalable distributed computation

---

