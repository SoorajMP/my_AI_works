# Bank Dataset: Variable Definitions
> First step of EDA on a banking dataset — understanding what each collected variable actually means before analyzing it.

## Overview (What / Why / How / Where)
- **What**: cataloging every variable across the data sources collected for a banking analysis problem, with its definition.
- **Why**: EDA can't start meaningfully until you know what each column represents — skipping this leads to misinterpreting results later.
- **How**: go source by source, variable by variable, noting what each one captures.
- **Where**: three data sources scavenged from the bank — customer data, transactional data, branch data.

## Problem Statement
- First step in EDA = look at what data has been collected and understand the definition of each variable.
- Three distinct sources feed the analysis:
  - Customer data (who the customer is)
  - Transactional data (what the customer does with their account)
  - Branch data (where/how the account is serviced)

---

## 1. Customer Data
- Describes who the customer is (demographic + profile info).

- **Customer ID** — unique identifier assigned to each customer.
- **Vintage** — number of days since the customer has been associated with the bank.
- **Age** — customer's age, in years.
- **Gender** — customer's gender.
- **Number of dependents** — count of dependents the customer has.
- **Occupation** — category such as salaried, self-employed, etc.
- **City** — anonymized city code (raw city identity converted to a code for privacy).

```mermaid
flowchart LR
    A[Customer Data] --> B[Customer ID: unique identifier]
    A --> C[Vintage: days since joining bank]
    A --> D[Age: years]
    A --> E[Gender]
    A --> F[Number of dependents]
    A --> G["Occupation: salaried / self-employed / etc."]
    A --> H[City: anonymized code]

    classDef src fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef var fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class A src
    class B,C,D,E,F,G,H var
```

---

## 2. Transactional Data
- Describes account activity and transaction details per customer.
- Structured around **time windows**: current month, previous month, previous quarter, previous-to-previous quarter.

### Current month variables
- **Current balance** — account balance on the day the data was collected.
- **Current month credit** — total amount credited to the customer in the current month.
- **Current month debit** — total amount withdrawn by the customer in the current month.
- **Current month balance** — average monthly balance for the current month.

### Previous month variables
- Same four variables, but for the previous month:
  - Previous month credit
  - Previous month debit
  - Previous month balance (average monthly balance)
  - (mirrors current month structure — same four transactional aspects, shifted one month back)

### Quarterly variables
- **Average balance, previous quarter** — average balance over the prior 3 months.
- **Average balance, previous-to-previous quarter** — average balance over the 3 months before that (months 4–6 back).
- Note: a quarter = 3 months.

### Net worth category
- **Customer net worth category** — income segment: 1, 2, or 3, denoting net worth group in **descending order** (i.e. 1 = highest group).

```mermaid
flowchart TD
    T[Transactional Data] --> CM[Current Month]
    T --> PM[Previous Month]
    T --> Q[Quarterly]
    T --> NW[Net Worth Category]

    CM --> CM1[Current balance]
    CM --> CM2[Current month credit]
    CM --> CM3[Current month debit]
    CM --> CM4[Current month balance - avg]

    PM --> PM1[Previous month credit]
    PM --> PM2[Previous month debit]
    PM --> PM3[Previous month balance - avg]
    PM --> PM4["(mirrors current month fields)"]

    Q --> Q1[Avg balance: previous quarter]
    Q --> Q2[Avg balance: previous-to-previous quarter]

    NW --> NW1["Segment 1/2/3, descending net worth"]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class T root
    class CM,PM,Q,NW branch
    class CM1,CM2,CM3,CM4,PM1,PM2,PM3,PM4,Q1,Q2,NW1 leaf
```

---

## 3. Branch Data
- Describes where/how the account is administratively tied and last serviced.
- **Branch code** — code identifying the branch where the customer holds their account.
- **Last_transaction** — date of the customer's last transaction (offline or online).

```mermaid
flowchart LR
    B[Branch Data] --> B1[Branch code: account's branch]
    B --> B2["Last_transaction: date, offline or online"]

    classDef src fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef var fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class B src
    class B1,B2 var
```

---

## Overall Structure / Taxonomy

```mermaid
mindmap
  root((Bank Dataset Variables))
    Customer Data
      Customer ID
      Vintage
      Age
      Gender
      Number of dependents
      Occupation
      City - anonymized
    Transactional Data
      Current month
        Current balance
        Current month credit
        Current month debit
        Current month balance avg
      Previous month
        Previous month credit
        Previous month debit
        Previous month balance avg
      Quarterly
        Avg balance previous quarter
        Avg balance previous-to-previous quarter
      Customer net worth category
    Branch Data
      Branch code
      Last_transaction date
```

---

## Key Takeaway
- Three data sources, each answering a different question about the customer: **who** (customer data), **what they do with money** (transactional data), and **where/when they last interacted** (branch data).
- Transactional data has a clear time-layered structure: current month → previous month → previous quarter → previous-to-previous quarter — same underlying metrics (credit/debit/balance) tracked across shifting windows.
- Net worth category (1/2/3) is ordinal and descending — treat as ranked category, not a plain nominal label.
- City is anonymized (privacy) — can't be used for geographic lookup directly, only as a categorical code.
- This variable inventory is a prerequisite step before any statistical or visual EDA — establishes vocabulary and scope before analysis begins.

## Quick Reference

```mermaid
flowchart TD
    D[Bank Dataset] --> S1[Customer Data: 7 vars]
    D --> S2[Transactional Data: 12 vars]
    D --> S3[Branch Data: 2 vars]

    S1 --> D1["ID, Vintage, Age, Gender, Dependents, Occupation, City"]
    S2 --> D2["Current + Previous month: balance/credit/debit x2; Quarter avg x2; Net worth category"]
    S3 --> D3["Branch code, Last_transaction"]

    classDef root fill:#d6e8f7,stroke:#4a90c2,color:#000000
    classDef branch fill:#f7d6d6,stroke:#c24a4a,color:#000000
    classDef leaf fill:#d4f0d4,stroke:#4ac26a,color:#000000
    class D root
    class S1,S2,S3 branch
    class D1,D2,D3 leaf
```

- Next practical step: import and read this dataset in Python for hands-on EDA.
