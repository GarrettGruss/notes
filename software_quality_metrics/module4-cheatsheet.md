# Module 4 Cheatsheet: Formal Models for Metrics Evaluation

## Quick Overview

**Goal**: Develop scientific model for software complexity measurement

**Three Main Approaches**:
1. **Prather (1984)**: 3 axioms for structured programs
2. **Weyuker (1988)**: 9 properties for complexity measures
3. **Tian-Zelkowitz (1995)**: 5 axioms + classification framework

---

## Prather's 3 Axioms (1984)

**Programs**: Sequence | Selection | Repetition

| Axiom | Formula | Meaning |
|-------|---------|---------|
| **A1: Sequence** | `m(S₁;S₂;...;Sₙ) ≥ Σᵢ m(Sᵢ)` | Sequence ≥ sum of parts |
| **A2: Selection** | `2m(S₁)+m(S₂) ≥ m(if P then S₁ else S₂) > m(S₁)+m(S₂)` | Selection bounded by components |
| **A3: Repetition** | `2m(S₁) ≥ m(while P do S) > m(S)` | Loop bounded by body |

**Limitations**: Limited scope, questionable justifications

---

## Fenton & Whitty (1986)

**Flowgraph-based**: `F = (G, a, z)` (graph with entry/exit nodes)

**g functions**:
- Summation: `gₙ = Σⁿᵢ₌₁ m(Fᵢ)`
- Maximum: `gₙ = max(m(F₁),...,m(Fₙ))`

**h function**: `h(m(F), m(F₁),...,m(Fₙ)) = m(F) · max(m(F₁),...,m(Fₙ))`

---

## Weyuker's 9 Properties (1988)

### Quick Reference Table

| # | Name | Formula | Key Idea |
|---|------|---------|----------|
| **P1** | Non-coarseness | `∃P,Q: V(P) ≠ V(Q)` | Not all programs equally complex |
| **P2** | Granularity | `{P: V(P) = c}` is finite | Finite clusters (not too coarse) |
| **P3** | Non-uniqueness | `∃P,Q: P≠Q ∧ V(P)=V(Q)` | Different programs can have same complexity |
| **P4** | Design details | `∃P,Q: P≡Q ∧ V(P)≠V(Q)` | Same function, different complexity |
| **P5** | Monotonicity | `∀P,Q: V(P) ≤ V(P;Q) ∧ V(Q) ≤ V(P;Q)` | Composition ≥ components |
| **P6** | Interaction | `∃P,Q,R: V(P)=V(Q) ∧ V(P;R)≠V(Q;R)` | Context matters (R interacts differently) |
| **P7** | Permutation | `∃P,Q: P=perm(Q) ∧ V(P)≠V(Q)` | Order matters |
| **P8** | Renaming | `∀P ∀x,y: V(P) = V(P[x/y])` | Names don't matter |
| **P9** | Interaction++ | `∃P,Q: V(P)+V(Q) < V(P;Q)` | Interaction increases complexity |

### Grouping

**Properties 1-4**: Measure characteristics (not syntax/semantics)
**Properties 5-9**: Program composition and interaction

---

## Tian-Zelkowitz Framework (1995) ⭐

### The 5 Axioms

**Core Notation**:
- `R(P,Q)`: P is no more complex than Q (ranking)
- `C(P,Q)`: P and Q are comparable
- `IN(P,Q)`: P is subprogram of Q
- `V(P)`: Complexity measure value
- `dist(P,Q)`: Distance in AST (edges between roots)

| Axiom | Formula | Meaning |
|-------|---------|---------|
| **A1: Functional Comparability** | `∀P,Q (P≡Q ⇒ C(P,Q))` | Same functionality → comparable |
| **A2: Composite Comparability** | `∀P,Q (IN(P,Q) ⇒ C(P,Q))` | Composite comparable to components |
| **A3: Monotonicity** | `∃k ∈ N (∀P,Q (IN(P,Q) ∧ dist(P,Q)>k) ⇒ R(P,Q))` | Sufficiently large programs not ranked lower |
| **A4: Measurability** | `∀P,Q (R(P,Q) ⇒ V(P)≤V(Q))` | Measure agrees with ranking |
| **A5: Distribution** | `∀k ∈ ℜ ∃δ>0 (prob(P: V(P)∈(k-δ,k+δ)) < 1)` | No single cluster dominates |

**Key**: A3 allows local deviations, A5 prevents all programs clustering around one value

---

## Tian-Zelkowitz: Dimensionality (3×3 = 9 base categories)

### 3 Dimensions (Orthogonal)

| Dimension | Description |
|-----------|-------------|
| **Presentation** | Physical layout (formatting, comments) - no functional effect |
| **Control** | Instructions, control structures, control dependencies |
| **Data** | Data items, data structures, data dependencies |

### 3 Measurement Levels

| Level | Description | Examples |
|-------|-------------|----------|
| **Lexical** | Token-based | LOC, GOTOs, variable counts |
| **Syntactic** | Syntax-based | Statement structure, nesting |
| **Semantic** | Semantic analysis | DU pairs, data flow, dependencies |

**Total**: 3 dimensions × 3 levels = **9 base categories** (can be further subdivided → 27 classes)

---

## Tian-Zelkowitz: Classification Schemes

### Vertical Classification

| Question | Yes → | No → |
|----------|-------|------|
| Depend only on syntax trees? | **Abstract** | **Non-abstract** |
| Invariant to renaming? | **Functional** | **Non-functional** |

### Hierarchical Classification

| Question | Yes → | No → |
|----------|-------|------|
| Sensitive to context? | **Interactional** | **Context-free** |
| Depends only on elements, not organization? | **Primitive** | **Non-primitive** |
| Captures both interface and internal? | **Overall** | **Non-overall** |

---

## Common Metric Notations

| Notation | Metric |
|----------|--------|
| **scan** | Scan size (token-based) |
| **stmt** | Statement count |
| **ss** | Software Science (Halstead) |
| **cyc** | McCabe's cyclomatic complexity |
| **knot** | Knot count |
| **du** | Definition-use pairs |
| **hac** | Hierarchical Abstract Computer |
| **ac** | Adamov-Richter compound metric |
| **fp** | Function point |
| **lc** | Line of code |

---

## Validation: NASA/SEL Study

**Environment**:
- 16 ground support projects
- 3K-112K SLOC (Fortran)
- 4700+ modules total
- 74 measures collected

**Application**: Classification Tree Analysis (CTA) for risk identification

### Performance Metrics Formulas

| Metric | Formula | Meaning |
|--------|---------|---------|
| **Coverage** | `P / (P + N)` | % of predictions made |
| **Accuracy** | `(M₁₁ + M₂₂) / P` | % correct predictions |
| **Completeness** | `M₁₁ / A⁺` | % actual high-cost found |
| **Consistency** | `M₁₁ / P⁺` | % predicted high-cost correct |

### Results vs Baselines

| Baseline | Coverage | Accuracy | Completeness | Consistency |
|----------|----------|----------|--------------|-------------|
| **Random** | 100% | 62.5% | 25% | 25% |
| **Original CTA** | High | Good | Good | Good |
| **T-Z Model** | Same ✓ | **Better ✓** | Same ✓ | **Better ✓** |

**Cost**: Measure pool size & tree complexity **dramatically reduced** ✓

---

## Comparison: Three Approaches

| Aspect | Prather | Weyuker | Tian-Zelkowitz |
|--------|---------|---------|----------------|
| **Year** | 1984 | 1988 | 1995 |
| **Focus** | Structured programs | Measure properties | Complete framework |
| **Count** | 3 axioms | 9 properties | 5 axioms |
| **Scope** | Limited | Systematic | Comprehensive |
| **Classification** | No | No | **Yes** (dimensional + vertical + hierarchical) |
| **Validation** | No | No | **Yes** (NASA/SEL) |
| **Strength** | First attempt | Inspired follow-ups | Practical + validated |
| **Weakness** | Questionable justifications | No classification | More complex |

---

## Key Takeaways

1. **Axioms define validity**: Not all metrics are equally valid
2. **Weyuker inspired T-Z**: Built on properties, added classification
3. **T-Z is comprehensive**: Axioms + Dimensions + Classification + Validation
4. **A5 (Distribution) critical**: Prevents useless clustering
5. **3D space (27 classes)**: Presentation × Control × Data × Lexical/Syntactic/Semantic
6. **Validation matters**: NASA/SEL proved effectiveness (reduced cost, improved accuracy)
7. **Classification helps selection**: Match metric type to measurement goal

---

## Quick Study Tips

**Memorize**:
- Weyuker's 9 property names (especially P6-interaction, P7-permutation, P8-renaming)
- T-Z 5 axiom names (A5 = Distribution/Diversity)
- 3 dimensions: Presentation, Control, Data
- 3 levels: Lexical, Syntactic, Semantic

**Understand**:
- Why A3 allows local deviations (small changes OK, trend matters)
- Why A5 prevents clustering (useless if all programs = "5")
- How classification helps metric selection
- NASA/SEL validation results (same coverage/completeness, better accuracy/consistency, lower cost)

**Compare**:
- Prather → Weyuker → Tian-Zelkowitz (evolution of rigor)
- Cyclomatic complexity violates some Weyuker properties (but still useful!)
- Theory (T-Z axioms) vs Practice (NASA validation)
