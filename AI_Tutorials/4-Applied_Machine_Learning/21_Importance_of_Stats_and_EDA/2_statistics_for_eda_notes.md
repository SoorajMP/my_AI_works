# Statistics for EDA
> Why stats matters for Exploratory Data Analysis — builds on the significance/importance of EDA.

## Overview (What / Why / How)
- **What**: statistics = science of analysis & interpretation of data. Toolkit of concepts to describe variable behavior.
- **Why**: raw data (long lists of numbers) is meaningless at a glance → stats compresses it into interpretable signals (center, spread, relationships).
- **How**: applied differently depending on how many variables you're looking at — univariate (1 var), bivariate (2 vars), and beyond (sampling → population).

## Problem Statement
- EDA needs a way to describe data, not just stare at it.
- Staring at a raw list of numbers → no insight.
- Need answers to:
  - Where is the data centered?
  - What's the range/spread?
  - What's the average?
- Stats gives the tools to answer these without manually scanning every value.

---

## 1. Univariate Analysis
- Definition: understanding **one variable** and its distribution.
- Core tool: **central tendency** measures.
  - Mean
  - Median
  - Mode
- Example: raw list of numbers → unreadable as-is → central tendency + range give quick understanding of "what this variable holds."

```mermaid
flowchart LR
    A[Raw list of numbers] --> B{Apply central tendency}
    B --> C[Mean]
    B --> D[Median]
    B --> E[Mode]
    C --> F[Compact understanding of variable]
    D --> F
    E --> F

    classDef input fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef process fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef output fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A input
    class B process
    class C,D,E process
    class F output
```

---

## 2. Bivariate Analysis
- Definition: relationship between **two variables**.
- Core question: do the variables depend on each other?

### Key concepts
- **Correlation / Covariance** → define how two variables move together (numeric-numeric).
- **Similarity tests** (z-test, chi-square test) → quantify whether two samples/groups are significantly similar or different.
- **t-test** → used in business experiments to check if results are statistically significant (not just random chance).

### Intuition example
- Two variables given, e.g. a numeric variable split by **gender** (male / female).
- Split data into subgroups (categories) → compare subgroups.
- Question asked: are these subgroups significantly different, or just random variation?
- Reframe: does gender have an effect on this variable?

```mermaid
flowchart TD
    A[Two variables] --> B[Split into categories]
    B --> C[Group 1: Male]
    B --> D[Group 2: Female]
    C --> E{Compare groups}
    D --> E
    E --> F[Significantly different?]
    E --> G[Just random chance?]

    classDef inputNode fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef groupNode fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef decisionNode fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A inputNode
    class B inputNode
    class C,D groupNode
    class E,F,G decisionNode
```

### Statistical tests — purpose map

```mermaid
flowchart LR
    subgraph tests[Bivariate / Group Comparison Tests]
        Z[z-test]
        CHI[chi-square test]
        T[t-test]
    end
    Z --> Q1[Are two samples significantly similar/different?]
    CHI --> Q1
    T --> Q2[Was a business experiment result significant, or by chance?]

    style tests fill:#f0f0f0,stroke:#888888,color:#000000
    classDef testNode fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef purposeNode fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class Z,CHI,T testNode
    class Q1,Q2 purposeNode
```

---

## 3. Sampling → Population (Estimation)
- Statistics lets you approximate **true parameters of the entire dataset (population)** using **small samples**.
- Layman analogy: imagining/drawing the full big picture from small sample pieces.
- Deeper, more intuitive treatment still to come — not detailed here yet.

```mermaid
flowchart LR
    A[Small sample groups] --> B[Statistical estimation] --> C[Approximate true population parameters]

    classDef n1 fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef n2 fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef n3 fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A n1
    class B n2
    class C n3
```

---

## Overall Structure / Taxonomy

```mermaid
mindmap
  root((Statistics for EDA))
    Univariate
      Mean
      Median
      Mode
    Bivariate
      Correlation
      Covariance
      Similarity tests
        z-test
        chi-square test
      t-test
        business experiments
    Sampling & Estimation
      Small samples
      Approximate population parameters
```

---

## Key Takeaway
- Statistics = the interpretation layer on top of raw data during EDA.
- Univariate → describe **one** variable (center, spread) via mean/median/mode.
- Bivariate → describe **relationship between two** variables via correlation/covariance + significance tests (z, chi-square, t-test).
- Sampling/estimation → generalize from small samples to the full population.
- This is a conceptual overview; each term (correlation, z-test, chi-square, t-test, sampling) warrants a dedicated deep-dive on its own.

## Quick Reference

```mermaid
flowchart TD
    S[Statistics] --> U[Univariate: 1 variable]
    S --> B[Bivariate: 2 variables]
    S --> P[Sampling: sample → population]

    U --> U1[mean / median / mode]
    B --> B1[correlation / covariance]
    B --> B2[z-test, chi-square: similarity of groups]
    B --> B3[t-test: experiment significance]
    P --> P1[estimate true parameters from samples]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class S root
    class U,B,P branch
    class U1,B1,B2,B3,P1 leaf
```

- Not yet covered in detail (flagged for later): correlation/covariance mechanics, z-test, chi-square test, t-test, sampling theory.
