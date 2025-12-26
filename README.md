# Course 3: Typed Passages

*The Simply Typed Lambda Calculus through Brennis Mund's Typing Discipline*

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/buildLittleWorlds/types-typed-passages/blob/main/notebooks/01-the-omega-crisis.ipynb)

> "He gave passages their boundaries" — Brennis Mund's epitaph

## Course Overview

This course teaches the **simply typed lambda calculus** through the story of Brennis Mund (780-862), son of Kelleth Mund, who solved the Omega problem that haunted his father's late career.

Where Course 1 (Pure Passage Calculus) introduced lambda calculus and Course 2 (Combinatorial Reduction) explored variable-free alternatives, this course addresses the dark side of untyped computation: **non-termination**. The expression Omega `((λx.x x)(λx.x x))` reduces forever. Brennis's solution was to add **types** — boundaries that constrain what passages can accept, preventing the self-application pattern that creates Omega.

## Prerequisites

- Course 1: Pure Passage Calculus (lambda calculus fundamentals)
- Course 2: Combinatorial Reduction (helpful but not required)

## Learning Objectives

By the end of this course, you will be able to:

1. Explain why untyped lambda calculus admits non-terminating expressions
2. Define base types and arrow types
3. Apply the typing judgment Γ ⊢ M : τ
4. Use the three typing rules (VAR, ABS, APP)
5. Prove that specific expressions are untypable (Omega, Y combinator)
6. State the Type Safety theorem (Progress + Preservation)
7. Explain the Strong Normalization theorem and its implications
8. Discuss the tradeoff between safety and expressiveness

## Tutorials

| # | Title | Topic | Technical Content |
|---|-------|-------|------------------|
| 01 | The Omega Crisis | Why types are needed | Non-termination, Omega, Triple Omega |
| 02 | Types as Boundaries | Base and arrow types | nat, bool, τ₁→τ₂ |
| 03 | The Typing Rules | How to assign types | VAR, ABS, APP rules |
| 04 | Type Safety | Well-typed programs don't go wrong | Progress + Preservation |
| 05 | Strong Normalization | Every typed term terminates | The normalization theorem |
| 06 | The Expressiveness Tradeoff | What types prevent | Y combinator untypability |
| 07 | The Typed Passage Discipline | Brennis's final synthesis | Putting it all together |

## The Scholar: Brennis Mund

**Brennis Mund** (780-862) was Kelleth Mund's son. He joined the Classification Integrity Committee in 780 and dedicated his career to solving the Omega problem.

Key milestones:
- **802**: Proposes the typing discipline
- **810**: Formalizes typing judgment and rules
- **812**: Proves Omega is untypable
- **830**: Proves strong normalization
- **835**: Proves Y combinator is untypable
- **850**: Publishes "The Typed Passage Discipline"

## Technical Concepts

### The Omega Problem

Omega is the expression `((λx.x x)(λx.x x))`. It reduces to itself:
```
(λx.x x)(λx.x x) → (λx.x x)(λx.x x) → ...
```
This is non-termination — the computation never produces a value.

### Types as Boundaries

Brennis's insight: Omega requires self-application `(x x)`. For this to work, `x` must have type `τ` such that `τ = τ→σ`. No finite type satisfies this!

**Base types**: `nat`, `bool`
**Arrow types**: `τ₁ → τ₂` (passages from τ₁ to τ₂)

### The Typing Judgment

`Γ ⊢ M : τ` means "in context Γ, expression M has type τ"

Three rules:
- **VAR**: If `(x:τ) ∈ Γ`, then `Γ ⊢ x : τ`
- **ABS**: If `Γ, x:τ₁ ⊢ M : τ₂`, then `Γ ⊢ (λx.M) : τ₁→τ₂`
- **APP**: If `Γ ⊢ M : τ₁→τ₂` and `Γ ⊢ N : τ₁`, then `Γ ⊢ (M N) : τ₂`

### Key Theorems

1. **Preservation**: If `Γ ⊢ M : τ` and `M → M'`, then `Γ ⊢ M' : τ`
2. **Progress**: If `Γ ⊢ M : τ`, then either M is a value or M can reduce
3. **Strong Normalization**: Every well-typed term terminates

## Datasets

This course uses datasets derived from the Living Ledger:

| Dataset | Description |
|---------|-------------|
| `typed_passage_expressions.csv` | Typed and untyped expressions |
| `typing_derivations.csv` | Step-by-step type derivations |
| `normalization_traces.csv` | Reduction sequences for typed terms |
| `type_system_comparison.csv` | Simply typed vs. untyped |

## Living Ledger Integration

This course contributes **25 canonical events** to the Living Ledger, spanning Brennis Mund's career from 795-863.

Key events:
- EV-800-001: Reduction engine halt (the crisis)
- EV-802-002: Typing discipline proposed
- EV-830-001: Strong normalization proved
- EV-862-005: Brennis Mund dies

## How to Use This Course

Each notebook can be run in Google Colab. Click the badge at the top of each notebook to launch:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

## Connection to Other Courses

- **Course 1** (Pure Passage Calculus): Introduces the untyped calculus that creates the Omega problem
- **Course 2** (Combinatorial Reduction): Shows that combinators have the same issue (MM = Ω)
- **Course 4** (Continuous Domains): Will address how to recover recursion with fixed-point semantics
- **Course 5** (Dependent Classifications): Will extend types to carry proofs

## Repository

This course is part of the [densworld-courses](https://github.com/buildLittleWorlds) project.

---

*Types & Computation Series*
*buildLittleWorlds*
