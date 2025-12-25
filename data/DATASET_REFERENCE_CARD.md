# Dataset Reference Card: Typed Passages

## Course Information

**Course:** Types & Computation 03 - Typed Passages
**Scholar:** Brennis Mund (780-862)
**Technical Content:** Simply typed lambda calculus

## Datasets Used

### Primary Datasets

| Dataset | Rows | Source | Description |
|---------|------|--------|-------------|
| `typed_passage_expressions.csv` | ~100 | Living Ledger | Typed and untyped expressions with type annotations |
| `typing_derivations.csv` | ~50 | Living Ledger | Step-by-step type derivations |
| `normalization_traces.csv` | ~30 | Living Ledger | Reduction sequences for typed terms |
| `type_system_comparison.csv` | ~20 | Living Ledger | Typed vs. untyped expressiveness comparison |

### Loading Datasets

```python
import pandas as pd

BASE_URL = "https://raw.githubusercontent.com/buildLittleWorlds/densworld-datasets/main/data/"

# Load typed expressions
expressions_df = pd.read_csv(BASE_URL + "typed_passage_expressions.csv")

# Load typing derivations
derivations_df = pd.read_csv(BASE_URL + "typing_derivations.csv")
```

## Schema Definitions

### typed_passage_expressions.csv

| Column | Type | Description |
|--------|------|-------------|
| `expression_id` | string | Unique identifier |
| `expression` | string | The lambda expression |
| `type` | string | Type annotation (or "untypable") |
| `typable` | boolean | Whether the expression can be typed |
| `terminates` | boolean | Whether reduction terminates |
| `normal_form` | string | Normal form if terminating |
| `reduction_steps` | integer | Number of steps to normal form |
| `discoverer` | string | Who discovered/documented this |
| `discovery_event` | string | Living Ledger event ID |
| `notes` | string | Additional context |

### typing_derivations.csv

| Column | Type | Description |
|--------|------|-------------|
| `derivation_id` | string | Unique identifier |
| `expression` | string | The expression being typed |
| `context` | string | The typing context Γ |
| `step_number` | integer | Step in the derivation |
| `rule_applied` | string | VAR, ABS, or APP |
| `subexpression` | string | Subexpression being typed |
| `type_assigned` | string | Type assigned in this step |
| `event_id` | string | Source Living Ledger event |

### normalization_traces.csv

| Column | Type | Description |
|--------|------|-------------|
| `trace_id` | string | Unique identifier |
| `expression` | string | Starting expression |
| `type` | string | Type of expression |
| `step_number` | integer | Reduction step number |
| `current_term` | string | Term at this step |
| `redex` | string | Redex being reduced |
| `is_value` | boolean | Whether term is a value |

## Living Ledger Integration

### Seeded Events (25)

This course seeded the following canonical events:

| Event ID | Type | Date | Description |
|----------|------|------|-------------|
| EV-795-001 | investigation_launched | 795-03-01 | Non-termination study |
| EV-798-003 | archive_accession | 798-08-01 | Kelleth's papers accessioned |
| EV-800-001 | anomaly_observed | 800-06-15 | Reduction engine halt |
| EV-802-002 | theory_proposed | 802-09-01 | Typing discipline proposed |
| EV-805-001 | theory_proposed | 805-02-15 | Base types |
| EV-805-002 | theory_proposed | 805-08-01 | Arrow types |
| EV-807-001 | manuscript_written | 807-04-01 | "On the Necessity of Boundaries" |
| EV-810-001 | discovery | 810-03-15 | Typing judgment |
| EV-810-002 | discovery | 810-07-01 | Typing rules |
| EV-812-004 | discovery | 812-02-01 | Omega untypability |
| EV-815-001 | theory_contested | 815-05-01 | Expressiveness objection |
| EV-815-004 | debate_published | 815-09-15 | "Safety or Expressiveness" |
| EV-818-001 | manuscript_written | 818-06-01 | "The Typing Rules" |
| EV-825-003 | discovery | 825-02-01 | Preservation theorem |
| EV-825-004 | discovery | 825-08-15 | Progress theorem |
| EV-830-001 | discovery | 830-04-01 | Strong normalization |
| EV-832-001 | manuscript_written | 832-01-01 | "On Termination and Types" |
| EV-835-002 | discovery | 835-06-01 | Y combinator untypability |
| EV-838-007 | theory_proposed | 838-03-01 | Primitive recursion |
| EV-842-020 | discovery | 842-09-01 | Church encoding typing |
| EV-845-022 | personnel_change | 845-01-01 | Brennis promoted |
| EV-850-039 | manuscript_written | 850-08-01 | "The Typed Passage Discipline" |
| EV-858-006 | personnel_change | 858-12-31 | Brennis retires |
| EV-862-005 | death | 862-03-15 | Brennis dies |
| EV-863-001 | archive_accession | 863-06-01 | Brennis's papers accessioned |

### Related Events (from Other Courses)

| Event ID | Type | Description | Course |
|----------|------|-------------|--------|
| EV-752-002 | discovery | Omega discovery | types-01 |
| EV-755-001 | anomaly_observed | Triple Omega divergence | types-01 |
| EV-780-001 | personnel_change | Brennis appointed | types-01 |
| EV-790-001 | discovery | Y in SKI notation | types-02 |
| EV-812-003 | death | Jorell Vance dies | types-02 |

### Encyclopedia Entries

| Entity | Type | Entry Location |
|--------|------|----------------|
| Brennis Mund | Person | `_planning/encyclopedia/consolidated/people.md` |
| Kelleth Mund | Person | `_planning/encyclopedia/consolidated/people.md` |
| Torren Gast | Person | `_planning/encyclopedia/consolidated/people.md` |
| Capital Archives | Place | `_planning/encyclopedia/consolidated/places.md` |

## Query Examples

```python
# Get all Brennis Mund events
!cd _source/living-ledger && python3 tools/ledger.py query --actor brennis_mund --format summary

# Get all typing-related discoveries
!cd _source/living-ledger && python3 tools/ledger.py query --type discovery --date-start 800-01-01 --date-end 850-12-31 --format json
```

## Technical Concepts Covered

| Tutorial | Concept | Dataset Columns Used |
|----------|---------|---------------------|
| 01 | Non-termination | `terminates`, `reduction_steps` |
| 02 | Base/arrow types | `type`, `typable` |
| 03 | Typing rules | `rule_applied`, `type_assigned` |
| 04 | Type safety | `terminates`, `normal_form` |
| 05 | Normalization | `step_number`, `current_term` |
| 06 | Expressiveness | `typable`, `expression` |
| 07 | Synthesis | All columns |

---

*Generated: 2025-12-25*
*Course: types-series/03-typed-passages*
