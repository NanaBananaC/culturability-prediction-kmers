# Predicting Marine Bacterial Culturability Using Discriminative k-mers
A computational framework for predicting the culturability of marine bacterial genomes by identifying discriminative genomic signatures (k-mers).

---

## Overview

Most marine bacteria are considered *unculturable*, meaning they cannot be grown in lab conditions. This significantly limits our ability to study their biological functions and potential applications.

In this project, we propose an **algorithmic approach to predict bacterial culturability** based on genomic sequence patterns.

We identify **characteristic k-mers** that:
- Appear frequently in *culturable* bacteria
- Appear less frequently in *unculturable* bacteria

This enables a data-driven way to estimate whether a new bacterial genome is likely to be culturable.

---

## Problem Formulation

We define:

- **A**: Set of culturable bacterial genomes  
- **B**: Set of unculturable bacterial genomes  
- **S**: Selected set of k-mers  

### Objective
`score(A, B, S, d) = coverage(S, A, d) - coverage(S, B, d)`

Where:
- `coverage(S, A, d)` = fraction of sequences in A matched by k-mers in S
- `d` = mismatch tolerance

The goal is to find a set of k-mers that strongly distinguishes A from B.

---

## Methods

### 1. Brute Force (Baseline)
- Enumerates all possible k-mer subsets
- Guarantees optimal solution
- ❌ Computationally infeasible (exponential complexity)

---

### 2. Greedy Algorithm
- Iteratively selects k-mers with highest marginal gain
- Fast and scalable
- ❌ May get stuck in local optimum

---

### 3. Monte Carlo Algorithm
- Randomly samples k-mers across multiple trials
- Explores larger search space
- ❌ High computational cost

---

### 4. Modified Greedy (Proposed)
- Combines greedy selection with randomness
- Avoids local optima while maintaining efficiency
- Best balance between performance and runtime

---

## Dataset
Link: https://drive.google.com/file/d/1HImE6Yudv7mPZf5HYgdu1ZE4pYMGEgFJ/view?usp=drive_link
- **Culturable (Set A)**  
  - 16S rRNA sequences from marine bacterial culture collections  

- **Unculturable (Set B)**  
  - 16S rRNA sequences labeled as *uncultured marine bacterium* from NCBI  

Future extension:
- Full genome datasets (not used due to computational constraints)

---

## Results

### Key Findings

- Modified Greedy consistently outperforms:
  - Higher scores
  - Reasonable runtime

- Greedy:
  - Fast but lower accuracy

- Monte Carlo:
  - Better exploration but slow

### Example

| Algorithm         | Runtime | Score |
|------------------|--------|------|
| Greedy           | Fast   | ~0.53 |
| Monte Carlo      | Slow   | ~0.57 |
| **Modified Greedy** | Moderate | **~0.81** |

---

## Insights

- Identified k-mers:
  - Cluster at similar positions across culturable genomes
  - Suggest presence of conserved genomic features

- These k-mers can act as:
  - **biomarkers for culturability**
  - guiding signals for microbial cultivation

---

## Applications

- Predict culturability of unknown bacteria  
- Guide lab cultivation strategies  
- Accelerate microbial discovery  
- Enable large-scale metagenomic analysis  

---

## Complexity

| Method              | Complexity |
|--------------------|----------|
| Brute Force        | Exponential ❌ |
| Greedy             | Efficient |
| Monte Carlo        | High (depends on trials) |
| Modified Greedy    | Efficient + exploratory |

---

## Future Work

- Extend to full genome datasets  
- Improve feature interpretability  
- Integrate biological priors  
- Deploy as a prediction tool for new sequences  

---

## Conclusion

We developed a **modified greedy algorithm** that efficiently identifies k-mer signatures predictive of bacterial culturability.

This approach:
- Scales to real genomic datasets  
- Provides biologically meaningful insights  
- Bridges computational methods with microbiology  

---

## Authors

- Juo-Hsuan Chang  
- Zachary Brown  
- Juheng Wu  

UC San Diego — BENG 280B (2025/03)

