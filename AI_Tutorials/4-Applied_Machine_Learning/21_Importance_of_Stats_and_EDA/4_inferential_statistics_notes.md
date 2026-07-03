# Inferential Statistics
> The second branch of statistics — using a sample to approximate and validate claims about the whole population.

## Overview (What / Why / How)
- **What**: approximating a population estimate using a sample, and analyzing what approximation errors can occur while doing so.
- **Why**: measuring/observing an entire population directly is often impractical (too large, too slow, too expensive) — a well-chosen sample gives a usable estimate instead.
- **How**: take a small sample → compute a representative statistic from it → generalize/extrapolate that statistic to the full population → validate the generalization by repeating and checking consistency.

## Problem Statement
- Directly measuring or testing an entire population is often infeasible.
- Need a principled way to:
  - Estimate population-level quantities from limited samples.
  - Judge whether an observed effect (in a sample) is real or just chance.
- This is distinct from descriptive statistics, which only summarizes the data already at hand — inferential statistics reasons beyond it.

---

## Core Idea: Population vs Sample

```mermaid
flowchart LR
    A[Population: complete data] --> B[Draw a sample]
    B --> C[Compute statistic from sample]
    C --> D[Generalize to population]
    D --> E[Approximation + possible error]

    classDef popNode fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef sampleNode fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef resultNode fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A popNode
    class B,C sampleNode
    class D,E resultNode
```

---

## Worked Example 1: Tile Pavement Area
- Task: find total area of tile pavement in a courtyard, using only a coin as a measuring tool.
- Approach (not measuring every tile individually):
  1. Measure dimensions of one tile using the coin.
  2. Recognize tiles slightly differ in size → repeat the measurement across a few tiles.
  3. Calculate the **average** tile dimension from those repeated measurements.
  4. Compute area of a single (average) tile from the average dimension.
  5. Count total number of tiles in the courtyard.
  6. Total area ≈ (area of one average tile) × (total tile count).

### Mapping to inferential statistics concepts
- Courtyard = **population** (complete data).
- Few randomly measured tiles = **sample** from the population.
- Average tile dimension (from sample) = statistic used to approximate the population.
- Total estimated area = population-level approximation built from a small sample.

```mermaid
flowchart TD
    A[Courtyard = population] --> B[Few tiles measured = sample]
    B --> C[Average tile dimension]
    C --> D[Area of one average tile]
    D --> E[× total tile count]
    E --> F[Estimated total pavement area]

    classDef pop fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef samp fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef est fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A pop
    class B samp
    class C,D,E est
    class F est
```

---

## Worked Example 2: Groomed Puppies Experiment
- Business idea: trimming/grooming pups' hair might make them more presentable → sell faster / at higher prices.
- Constraint: grooming every pup is costly, with no guarantee it works.

### Experiment design (small sample first)
- Groom only **5 pups**, reintroduce to store, observe results.
- Observation: groomed pups sold faster and at higher prices than regular pups.
- Risk: this result could just be luck / chance, not a real effect.

### Validating the hypothesis (repetition)
- Repeat the grooming experiment several more times.
- Consistent result across repeats → groomed pups significantly outperform regular pups in sales/profit.
- Conclusion: switch completely to grooming all puppies.

```mermaid
flowchart TD
    A[Idea: grooming increases sales] --> B[Small sample: groom 5 pups]
    B --> C[Observed: faster sales, higher prices]
    C --> D{Real effect or just luck?}
    D --> E[Repeat experiment multiple times]
    E --> F[Consistent result across repeats]
    F --> G[Statistically significant improvement]
    G --> H[Decision: fully switch to groomed puppies]

    classDef idea fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef sample fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef decision fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A idea
    class B,C sample
    class D,E,F,G decision
    class H decision
```

### Why this is inferential statistics
- The 5-pup (and repeated) experiments = **samples**.
- "Groomed pups bring more profit" = a **hypothesis** being tested.
- Repetition addresses the "is this just chance?" question — core concern of inferential statistics.
- Validating hypotheses in a statistically significant way (not just from one lucky trial) is the essence of this branch.
- Other hypotheses of the same shape: e.g. "do weekends bring significantly more sales?" — same inferential logic, different variable.

---

## Overall Structure / Taxonomy

```mermaid
mindmap
  root((Inferential Statistics))
    Core task
      Approximate population from sample
      Quantify approximation error
    Tile pavement example
      Population = courtyard
      Sample = few tiles
      Statistic = average tile dimension
      Result = estimated total area
    Groomed puppies example
      Hypothesis = grooming increases profit
      Sample = small batch of groomed pups
      Repetition = check against chance
      Result = statistically significant decision
    Role in EDA
      Validates hypotheses from hypothesis-generation step
```

---

## Key Takeaway
- Inferential statistics = reasoning from a **sample** to conclusions about the **whole population**, plus accounting for the error in that approximation.
- Two-step pattern in both examples:
  1. Estimate something from a small sample (average tile size / grooomed-pup sales lift).
  2. Repeat / validate to distinguish a real effect from random chance.
- Ties directly into EDA workflow: hypotheses generated during EDA get validated using inferential statistics (checking if effects are statistically significant, not just coincidence).
- Contrasts with descriptive statistics: descriptive summarizes what's already known; inferential extrapolates and tests beyond the observed data.

## Quick Reference

```mermaid
flowchart TD
    IS[Inferential Statistics] --> P1[Goal: approximate population from sample]
    IS --> P2[Goal: test hypotheses for statistical significance]
    IS --> P3[Key risk: mistaking chance for a real effect]

    P1 --> X1["e.g. avg tile size × tile count = pavement area"]
    P2 --> X2["e.g. groomed pups → higher profit, validated by repetition"]
    P3 --> X3["Mitigation: repeat sampling/experiments before concluding"]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class IS root
    class P1,P2,P3 branch
    class X1,X2,X3 leaf
```

- Descriptive statistics + inferential statistics together form the statistical toolkit used throughout EDA.
- Inferential statistics specifically powers the hypothesis-validation step of EDA — confirming whether patterns found are statistically significant, not just noise.
- Next practical step after these concepts: applying them while looking at real data in a Python environment.
