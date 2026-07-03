# Descriptive Statistics
> One of the two main branches of statistics — summarizing data as it is, not generalizing beyond it.

## Overview (What / Why / How)
- **What**: descriptive statistics = summarizing a dataset using central tendency, spread, and relationships between variables.
- **Why**: raw transaction-level data (e.g. every single sale) isn't useful to reason about directly — need compact summaries to extract business insight.
- **How**: three complementary forms — tabulated description, graphical description, and discussion of results.

## Problem Statement
- Statistics splits into two main branches:
  - **Descriptive statistics** — summarize the data at hand.
  - **Inferential statistics** — generalize beyond the data at hand (separate topic).
- This note covers descriptive statistics only.

---

## Core Idea: Summarizing Data

```mermaid
flowchart LR
    A[Raw data] --> B[Central tendency]
    A --> C[Spread]
    A --> D[Relation between variables]
    B --> E[Summary / Insight]
    C --> E
    D --> E

    classDef inputNode fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef processNode fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef outputNode fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A inputNode
    class B,C,D processNode
    class E outputNode
```

---

## Worked Example: Pet Shop Sales
- Shopkeeper keeps a ledger of past business → can answer simple business questions using descriptive stats without doing anything predictive.

### Central tendency
- "Out of every 100 pets sold, 35 are dogs" → proportion as a central/typical value.
- "Sold 7.5 fish on average every day" → mean as central value.
  - Doesn't mean exactly 7.5 fish sold daily — some days 10, some days 0.
  - Average smooths daily fluctuation into one representative number.

### Spread
- Day-to-day variation in fish sold (0 some days, 10 other days) = **spread** around the central value (7.5).
- Spread tells you how much individual days deviate from the average — average alone hides this.

### Relationship between variables
- **Negative association**: age of customer ↔ pet sales (as age increases, sales tend to decrease, customer-wise).
- **Positive association**: whether a day is a holiday ↔ sales on that day (holidays → higher sales).
- Sign of association (positive/negative) captured without needing exact correlation values here — just direction of relationship.

```mermaid
flowchart TD
    A[Pet shop ledger] --> B[35 out of 100 pets = dogs]
    A --> C[7.5 fish sold/day on average]
    A --> D[Age vs sales: negative association]
    A --> E[Holiday vs sales: positive association]

    B --> F[Central tendency]
    C --> F
    C --> G[Spread: daily variation 0-10 fish]
    D --> H[Relationship between variables]
    E --> H

    classDef src fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef fact fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef cat fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A src
    class B,C,D,E fact
    class F,G,H cat
```

---

## Forms of Descriptive Statistics
- **Tabulated description** — data organized into tables/summary stats.
- **Graphical description** — visual plots (histograms, bar graphs, pie charts).
- **Discussion of results** — narrative interpretation of what the numbers/plots mean.

### Graphical description — common chart types
- **Histogram** — distribution of a single numeric variable.
- **Bar graph** — comparison across categories.
- **Pie chart** — proportion/percentage breakdown of categories (e.g. percentage of each pet type sold at the shop).
- These chart types are common in industry dashboards and presentations for quick visual summaries.

```mermaid
flowchart LR
    A[Descriptive Statistics] --> B[Tabulated description]
    A --> C[Graphical description]
    A --> D[Discussion of results]

    C --> C1[Histogram]
    C --> C2[Bar graph]
    C --> C3[Pie chart]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A root
    class B,C,D branch
    class C1,C2,C3 leaf
```

---

## Overall Structure / Taxonomy

```mermaid
mindmap
  root((Statistics))
    Descriptive statistics
      Central tendency
        Mean
        Proportion
      Spread
        Day-to-day variation
      Relationships
        Positive association
        Negative association
      Forms
        Tabulated description
        Graphical description
          Histogram
          Bar graph
          Pie chart
        Discussion of results
    Inferential statistics
      Generalize beyond data at hand
```

---

## Key Takeaway
- Descriptive statistics summarizes what's already in the dataset — no generalization beyond it (that's inferential statistics' job).
- Three summarization angles: central tendency (typical value), spread (variation around that value), and relationships (direction of association between variables).
- Three output forms: tables, graphs (histogram/bar/pie), and narrative discussion.
- Average/central value can hide daily variability — always pair central tendency with spread for a complete picture.
- Direction of association (positive/negative) is a simple but useful descriptive insight even before formal correlation is calculated.

## Quick Reference

```mermaid
flowchart TD
    S[Descriptive Statistics] --> T1[Central tendency: typical value]
    S --> T2[Spread: variation around typical value]
    S --> T3[Relationship: direction of association]
    S --> T4[Output forms: table / graph / discussion]

    T1 --> E1["e.g. 35/100 pets = dogs; avg 7.5 fish/day"]
    T2 --> E2["e.g. daily fish sales range 0-10"]
    T3 --> E3["e.g. age↓sales negative; holiday↑sales positive"]
    T4 --> E4["e.g. pie chart of pet-type % sold"]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class S root
    class T1,T2,T3,T4 branch
    class E1,E2,E3,E4 leaf
```

- Next branch to cover: inferential statistics — generalizing from data at hand to broader conclusions.
