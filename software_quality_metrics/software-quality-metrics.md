# Software Quality Metrics

## Metrics: Internal vs. External

**Basic Assumption**: Lower complexity = cheaper to build, easier to maintain, more reliable

**Internal Metrics**: Depend on programs only. Available earlier, finer granularity, controllable.
- Examples: Size (LOC, Function Points), Complexity (Cyclomatic, Data, Control), Structure (Coupling, Cohesion)

**External Metrics**: Depend on external factors. "-ilities". Customer/user perspective, measured late, harder to control.
- Examples: Reliability, Usability, Security, Time, Effort, Cost, Productivity, Customer satisfaction

**Relationship**: Correlated but not uniquely determined
- External metrics = dependent variables (targets)
- Internal metrics = independent variables (predictors, leading indicators)
- Process: Discover appropriate measures → Establish predictive relations → Use and validate

**GQA Framework**: External (Time, Effort, Quality, Productivity), Internal (Size, Complexity). Related via models (e.g., Putnam).

## Metrics and Models

### Measurement Frameworks

**GQM (Goal-Question-Metric)**: Define study goals, questions, and metrics for answers.

**QIP (Quality Improvement Paradigm)**: Quantify changes and impacts to software baseline.

**Experience Factory**: Organizational learning and continuous improvement.

**Measurement Theory**: Formalization - R: relation, f(x): functional mapping, aRb <-> f(a) > f(b)

**Evaluation Criteria**: Properly defined? Properly used? Useful results? Helps select metrics, propose new ones, identify context.

**Empirical Evaluation**: Statistical analysis → Formal models (Tian-Zelkowitz, Koru-Tian)

**Putnam/Myers 5 Core Metrics**: External (Time, Effort, Quality, Productivity), Internal (Size). Key: Relationship between metrics.

### Metrics Usage Workflow

1. Use GQM to select metrics (external for goals, internal for control)
2. Measurement activities (tools, data tracking)
3. Analysis/modeling (Tian SQE Ch.19, risk models Ch.21)
4. Use results (assessment, prediction, control)
5. Experience Factory for future improvement

**Key Components of SE**: Methods/Processes, Formal Foundations, Experimentation

## External Quality Metrics

**Quality "-ilities"**: Reliability, Availability, Usability, Security, Maintainability, Scalability, Extensibility, Portability, Safety

### Reliability & Availability

**Reliability**: Probability of failure-free operation. Requires defect measurement and analysis (Tian/SQE Ch.20, 22).

**Availability**: `MTTF / (MTTF + MTTR)`
- Measurement issues: downtime vs repair, partial operation, severity, time units
- Management: Software rejuvenation (restart, cleanup, failover)

### Performance

**Metrics**: Response/turnaround time, throughput, resource utilization (memory, CPU)
**Variations**: Total, average, variance, worst-case, real-time considerations
**Activities**: Task modeling, benchmarks

### Usability

**Classical Metrics**: Learning time, task performance, error/success rate, retention, satisfaction
**Modern**: Manual vs automated (intended vs actual usage), success rate, #steps, task time
**KLM (Keystroke Level Model)**: Keystrokes required to finish task without errors

### Security, Maintainability, Safety

**Security**: Many sub-attributes, specialized techniques, field data
**Maintainability**: Effort on task, related to portability/flexibility/testability
**Safety**: Focus on assurance (direct measurement impractical)

### Defect Capture

Establish system boundaries to identify defects. Capture: requirement/feature, configuration (revision, system), inputs, state, severity.

## Other External Metrics

### Customer Satisfaction
Surveys (Kan Ch.14): Ordinal scale, percentages, logistic analysis. Field data.

### Effort & Cost
**Effort** (Laird Ch.6): Man-Month. "Mythical Man-Month" (Brooks). Estimation > measurement.
**Cost** (Laird Ch.12): Factors (salary, overhead, risk, capital), cost-benefit analysis.
Both use size as input, similar techniques (Tian SQE Ch.19).

### Schedule & Productivity
**Schedule**: Time-based project delivery metrics
**Productivity**: Output per effort unit (LOC/month, FP/month)

## Internal Size Metrics

**Measurement Levels**: Lexical (tokens, LOC, variables), Syntactic (statement count), Semantic (DU pairs, naming)

### LOC & Function Point

**LOC**: Total/code/comment/blank lines

**Function Point**: Count inputs, inquiries, outputs, master files. Language-independent, black-box view, available earlier. Uses weights (Laird table 4.3).

### Gearing Factors & Reuse

**Gearing Factors** (Laird tables 4.1, 4.2): LOC ratio between languages (e.g., 38 LOC Access = 91 LOC Cobol). Compare productivity, estimate porting.

**NASA Reuse Classification**: Verbatim, Slightly modified (<25%), Extensively modified (≥25%), New
**Counting practices**: 25% count each use, 20% once, 5% never, 50% never count

**Cone of Uncertainty**: Size estimation improves during development

**NASA Metrics Maintenance**: 25% maintain, 20% baseline only, 5% don't track, 50% never maintain

## Internal Complexity Metrics

Complexity = general term for all internal metrics. Categories: Size, Information, Volume, Algorithmic, Non-code-based.

### Theory: Dimensions & Levels

**3 Orthogonal Dimensions**: Presentation (physical layout), Control (instructions/structures/dependencies), Data (items/structures/dependencies). Creates 3-D space, proximity = similarity.

**3 Measurement Levels**:
- **Lexical**: Token-based (LOC, GOTOs, decisions, branches, variables)
- **Syntactic**: Syntax-based (statements, concatenation, nesting)
- **Semantic**: Semantics-based (DU pairs, dependencies, sensitization)

Similar to ABCs (Attribute-Based Credentials): flexibility, zero-knowledge property.

### Control Complexity

**McCabe's Cyclomatic**: `v = e - n + 2p` or `v = c + 1`
- Higher (>10) = difficult/error-prone code
- Indicates test cases needed
- Poor effort correlation

**Knot Count**: Crossing control structures (break, goto). Target ≤0. High = unstructured.

### Data Complexity

**Levels**: Lexical (variable counts), Syntactic (scoping, visible sets), Semantic (DU pairs, data flow)

(TODO): Create table: metrics domain × Lexical/Syntactic/Semantic

### Interface & Information Flow

**Interface**: Lexical counting (name, type, frequency, I/O statements/parameters). Used in Function Point.

**IFM**: `(fan-in × fan-out)²`. Flow into/out of procedure, includes global data structures.

### Volume & Halstead

**Halstead**: Tokens as operators/operands
- Primitive: n₁ (distinct operators), n₂ (distinct operands), N₁ (total operators), N₂ (total operands)
- Volume: `V = (N₁ + N₂) log₂(n₁ + n₂)`
- Effort: `E = V² / V*`

**HAC (Bai/Zelkowitz)**: Similar to Halstead but accounts for control flow and data structures.

### Object Oriented (CK Metrics)

**WMC**: Weighted methods per class (complexity)
**DIT**: Depth of inheritance tree (high DIT preferred)
**NOC**: Number of children (goal: high DIT, low NOC)
**CBO**: Coupling between classes
**RFC**: Response for class (local + called methods)
**LCOM**: Lack of cohesion (dissimilarity). Identifies design flaws, promotes encapsulation.

## Other Internal Metrics

### Interface/Usability Metrics

Map to ABCs:
1. **Anthropomorphic**: User traits/intention (KLM - expert task completion time)
2. **Behavioral**: Expected interactions, user perception
3. **Cognitive**: Task-based
4. **Social**: Communication/coordination in distributed systems

### Presentation Complexity

**Levels**: Lexical (comments, blanks), Syntactic (indentation, formatting rules), Semantic (naming, aliasing)

### Hybrid & Other Metrics

**Hybrid**: Combine dimensions (Function Point, IFM, Halstead)
**PCA**: Principal Component Analysis - factor analysis, reduces dimensionality
**Multiple approaches**: Profiler, ensemble models, integrated analysis

**Algorithmic**: Graph coloring (Chaitin-Briggs), minimal representation (sums/products), computational linkage

### Non Code-based

**Function Point-like**: Applied to specs, designs

**Card & Glass Design**: Structural (fan-out, interconnections), Data (interfaces, size), System (combined architectural complexity)

## Advanced Topics

Results analysis, hypothesis testing, Koru-Tian usage, ESE bigger picture, integrated approach. Applications: traditional (commercial, telecom) vs new (net-centric, SOA, cloud).

# Module 4: Formal Models for Metrics Evaluation

## Goal of Controlled Software Development

**Develop an engineering discipline**:
- Measure and evaluate the working product
- Construct scientific model for software measurement
- Techniques from other disciplines + new techniques if necessary

**Basic Questions**:
- What to measure: Goal and environment
- How to measure it: Metrics and tools
- Selection and validation

## Overview: Solution Strategy

**Need scientific model of program complexity**:
- Develop theory of program complexity (organize empirical knowledge)
- Develop technique for measure evaluation and selection
- Extrapolate measurement activities to new applications
- Validate model using data from NASA Software Engineering Laboratory (SEL)

**Theory is systematic extension** of earlier studies by:
- R.E. Prather (1984): Axiomatic Theory of Software Complexity Measure
- N.E. Fenton & R.W. Whitty (1986): Axiomatic approach through Program Decomposition
- E.J. Weyuker (1988): Evaluating software complexity measures

---

## Prather: Axiomatic Software Complexity (1984)

[Article Link](https://academic.oup.com/comjnl/article-abstract/27/4/340/331819?redirectedFrom=fulltext)

**Structured programs built from statements**:
- **Sequence**: `begin S₁;S₂;…;Sₙ end`
- **Selection**: `If P then S₁ else S₂`
- **Repetition**: `While P do S`

Where Sᵢ (S, T respectively) are structure processes, P is arbitrary predicate.

### Prather's Three Axioms

**Axiom**: Statement or proposition regarded as established, accepted, or self-evidently true.

Suppose `m` is a function from the class of structured programs. Proper measure of program complexity if it satisfies:

**Axiom 1 (Sequence)**: `m(S₁;S₂;…;Sₙ) ≥ Σᵢ m(Sᵢ)`
- Complexity of sequence ≥ sum of component complexities

**Axiom 2 (Selection)**: `2m(S₁) + m(S₂) ≥ m(if P then S₁ else S₂) > m(S₁) + m(S₂)`
- Selection complexity bounded by component complexities

**Axiom 3 (Repetition)**: `2m(S₁) ≥ m(while P do S) > m(S)`
- Repetition complexity bounded by loop body complexity

### Observations
- Earliest attempt on axiomatic model
- Some intuition captured (example interactions)
- **Limitations**: Limited scope, questionable justification for some axioms

---

## Fenton & Whitty: Hierarchical Complexity (1986)

**Flowgraph notation**: `F = (G, a, z)`
- G: directed multigraph with distinguished nodes a, z
- If F has n procedure nodes x₁,...,xₙ and F₁,...,Fₙ are arbitrary flowgraphs
- Unique nested flowgraph: `F(F₁ on x₁,...,Fₙ on xₙ)`

**Sequence of flowgraphs**: `seq(F₁,...,Fₙ)`

**Complexity m of uniquely sequential flowgraph**:

**Definition of g functions**:
- `gₙ = Σⁿᵢ₌₁ m(Fᵢ)` for each n (summation)
- `gₙ = max(m(F₁),...,m(Fₙ))` for each n (maximum)

**Definition of h function**:
- `h(m(F), m(F₁),...,m(Fₙ)) = m(F) · max(m(F₁),...,m(Fₙ))`

### Fenton's Hierarchical Complexity Axioms
- `m(seq(F₁,...,Fₙ)) = gₙ(m(F₁),...,m(Fₙ))`
- `m(F(F₁ on xᵢ,...,Fₙ on xₙ)) = h(m(F), m(F₁),...,m(Fₙ))`

### Observations
- General framework (could be too general?)
- Contrast with Prather's work
- Relation to later work (add specifics, measurement theory-based)

---

## Weyuker: Nine Properties (1988)

**Notation**: P, Q, R denote program bodies
- `IF PRED THEN P ELSE Q END`
- `WHILE PRED DO P ENDWHILE`
- `P;Q` - composition of programs P and Q

**Halstead Volume reference**: `V = (N₁ + N₂) log₂(n₁ + n₂)`
- n₁: distinct operators, n₂: distinct operands
- N₁: total operators, N₂: total operands

### The 9 Properties

**Property 1 (Non-coarseness)**: `(∃P,Q)(V(P) ≠ V(Q))`
- Measure should not rank all programs as equally complex

**Property 2 (Granularity)**: `{P, V(P) = c}` is finite
- Where c is non-negative number
- Strengthens Property 1 - measure not too "coarse"
- All programs should not be divided into just a few complexity classes

**Property 3 (Non-uniqueness)**: `∃P,Q (P ≠ Q ∧ V(P) = V(Q))`
- Complexity of distinct programs P and Q can be similar
- Each complexity satisfies this property

**Property 4 (Design details matter)**: `∃P,Q (P ≡ Q ∧ V(P) ≠ V(Q))`
- For two programs computing same function
- Implementation details determine complexity

**Properties 1-4**: Deal mostly with measures, not directly with syntax/semantics

**Property 5 (Monotonicity)**: `∀P,Q (V(P) ≤ V(P;Q) ∧ V(Q) ≤ V(P;Q))`
- Composition complexity ≥ component complexity

**Property 6 (Non-equivalence of interaction)**: `∃P,Q,R (V(P) = V(Q) ∧ V(P;R) ≠ V(Q;R))`
- R may not interact with P, while R interacts with Q (or vice versa)
- Complexity of P;R might differ from Q;R

**Property 7 (Permutation sensitivity)**: `∃P,Q (P = perm(Q) ∧ V(P) ≠ V(Q))`
- Responsive to order of statements
- Q formed by permuting order of statements of P
- Example: Second assignment of X, Y has no influence on first loop in P
- But second assignment in Q may affect outer values

**Property 8 (Renaming independence)**: `∀P ∀x,y (V(P) = V(P[x/y]))`
- P is renaming of Q
- Complexity of P and Q are equal

**Property 9 (Interaction increases complexity)**: `∃P,Q (V(P) + V(Q) < V(P;Q))`
- Complexity of concatenated programs greater than sum of their complexity
- Reflects interaction between concatenated subprograms

### About Weyuker's Properties
- More systematic treatment
- Inspired/led to many follow-up works:
  - **Positive**: Refinement
  - **Negative**: Counter examples
  - **Other**: Development & alternatives

**Important follow-up works**:
- Measurement theory based (Zuse)
- Cherniavsky and Smith
- Tian and Zelkowitz
- Briand and Basili
- Others

---

## Tian-Zelkowitz Framework (1995)

**Publication**: J. Tian and M. V. Zelkowitz, "Complexity measure evaluation and selection," IEEE Transactions on Software Engineering, vol. 21, no. 8, pp. 641-650, Aug. 1995.

### Tian-Zelkowitz as Follow-up to Weyuker
- Merit of Weyuker's properties
- Some universally satisfied → Basis for universal axioms
- Some for certain types of metrics → Classification?
- A theory based on the above
- An evaluation/selection process

### Framework Components

**1. Axioms**: Define program complexity and state common properties

**2. Dimensionality Analysis**: Basis for metrics classification
- **Aspects/Dimensions**: Presentation, Control, Data
- **Levels**: Lexical, Syntactic, Semantic

**3. Classification Scheme**: Define mutually exclusive, collectively exhaustive classes

---

## Tian-Zelkowitz: The Five Axioms

### Defining Complexity

**Definition**:
- `R` - Complexity binary relation ranking on programs
- With P and Q programs:
  - `R(P,Q)` - Ranking of P being no more complex than Q
  - `C(P,Q) iff R(P,Q) ∨ R(Q,P)` - Programs are comparable

**Comments**:
- Internal to the programs
- Related empirical to external properties
- Very broad definition (needs further qualification and quantification)

### Axiom A1: Functional Comparability

`∀P,Q (P ≡ Q ⇒ C(P,Q))`

**Functionally equivalent programs are comparable**
- `R(P,Q)` - Ranking of P being no more complex than Q
- `C(P,Q) iff R(P,Q) ∨ R(Q,P)`

### Axiom A2: Composite Comparability

`∀P,Q (IN(P,Q) ⇒ C(P,Q))`

**Composite program comparable with its components**
- `IN(P,Q)`: P is a subprogram of Q
  - `AST(P)` is a subtree of `AST(Q)`
  - AST(P): graphical representation of program P
  - AST(Q): graphical representation of program Q

**Comments**:
- Hard problem due to undecidability
- R is self-reflexive
- R is not transitive

### Axiom A3: Monotonicity

`∃k ∈ N (∀P,Q (IN(P,Q) ∧ dist(P,Q) > k) ⇒ R(P,Q))`

**Sufficiently large programs will not be ranked lower in complexity**
- Constant k limiting non-monotonicity of two programs
- `IN(P,Q)`: P is a subprogram of Q
  - `AST(P)` is a subtree of `AST(Q)`
- Where `dist(P,Q)`: number of edges (nodes + 1) between root AST(P) and root of AST(Q)

**Comments**:
- General trend must be followed
- Local deviations allowed

### Axiom A4: Measurability

**Definition**: A complexity measure V is a quantification of complexity ranking R
- V maps programs into real numbers: `V: U ⇒ ℜ`
- ℜ: Set of real numbers
- U: Universe of programs

`∀P,Q (R(P,Q) ⇒ V(P) ≤ V(Q))`

**A measure must agree with the ranking it is approximating**

**Non-Axiom** (commonly assumed by other models):
- `∀P,Q (V(P) ≤ V(Q) ⇒ R(P,Q))`
- Doesn't hold due to:
  - Incomparable cases
  - Non-transitive cases

### Axiom A5: Distribution/Diversity

**Requirement**: Measure values must not cluster around one single dominating point

**Formal notation**:
`∀k ∈ ℜ ∃δ > 0 (|U - {P : V(P) ∈ (k-δ, k+δ)}| = |U|)`

**Alternative form (A5')**:
`∀k ∈ ℜ ∃δ > 0 (prob(P : V(P) ∈ (k-δ, k+δ)) < 1)`

Where:
- δ: region size of function V (δ-region)
- k: constant limiting non-monotonicity
- prob(P): Probability of a given program P

**Rationale**:
- No δ-region around any point V can totally dominate a measure
- A single dominating cluster is disallowed
- Fails to achieve goal of providing comparison for programs

---

## Tian-Zelkowitz: Dimensionality Analysis

### Three Complexity Dimensions (3-D Space)

**1. Presentation**:
- Physical presentation for readers
- Has no effect on functionality

**2. Control**:
- Instructions, control structures
- Control dependencies

**3. Data**:
- Data items, data structures
- Data dependencies

**Commentary**:
- Control and Data give abstract view
- Orthogonal dimensions
- Creates 3-D dimension space
- **27 possible distances** between points in 3-D space
- Space proximity ≈ measure similarity

**Dividing Control and Data dimensions**:
- Count
- Structure
- Dependency

### Three Measurement Levels

**1. Lexical**:
- Token-based measure computation
- Examples: LOC, GOTOs, decisions, branches, variable counts

**2. Syntactic**:
- Directly syntax-based measure computation
- Examples: Statements, concatenation, nesting

**3. Semantic**:
- Semantic analysis needed for measure computation
- Examples: DU pairs, dependencies, sensitization

---

## Tian-Zelkowitz: Classification Schemes

### Vertical Classification

**Classification based on computational models used**:

**1. Abstract vs Non-abstract**:
- Question: Depend only on syntax trees of programs?
- Yes → **Abstract**
- No → **Non-abstract**

**2. Functional vs Non-functional**:
- Question: Invariant (never changes) to renaming?
- Yes → **Functional**
- No → **Non-functional**

### Hierarchical Classification

**Classification based on complexity relations of component-composite programs**:

**1. Context-free vs Interactional**:
- Question: Sensitivity to context?
- Yes → **Interactional**
- No → **Context-free**

**2. Primitive vs Non-primitive**:
- Question: Dependency on building element only, not organization?
- Yes → **Primitive**
- No → **Non-primitive**

**3. Overall vs Non-overall**:
- Question: Capture both interface and internal?
- Yes → **Overall**
- No → **Non-overall**

### Classification Notation Examples

**Common Metrics**:
- **scan**: Scan size (token-based metric)
- **stmt**: Statement count
- **ss**: Software Science (Halstead metrics)
- **cyc**: McCabe's cyclomatic complexity
- **knot**: Knot count
- **du**: Definition-use pair (DU pair)
- **hac**: Hierarchical Abstract Computer
- **ac**: Adamov-Richter compound metric
- **fp**: Function point
- **lc**: Line of code

---

## Application and Validation

### Application Domain

**Risk Identification for projects in NASA/SEL**:
- **Pilot experiment**: Apply scientific model to select complexity measures
- **Data collection**: Run multiple applications and collect results
- **Analysis**: Analyze resulting data-points to validate scientific model

### Risk Identification

**Risk in software decisions**:
- Multiple alternatives
- Uncertainty about future development
- Large investment
- Significant consequences

**Classification Tree Analysis (CTA)** (Selby & Porter):
- **Risk**: Likelihood of high cost or effort
- **High cost**: Highest quartile (80:20 rule)
  - 20% of a software system responsible for 80% of errors
- **Basis**: Historical data
- **Methodology**: Classification trees

### CTA Prediction Example

Predictions made based on:
- Classification tree
- Sample module measurement data

### CTA Cost & Performance

**Cost factors**:
- **Tree generation**: Measure pool size S
- **Tree usage**: Tree-complexity/node-count

**Performance Measures**:
- **Coverage**: Predictions made
- **Accuracy**: Correct predictions
- **Completeness**: Correct predictions of actual high-cost modules
- **Consistency**: Correct high-cost predictions

**Compare predicted vs actual data**:
- `Coverage = P / (P + N)`
- `Accuracy = (M₁₁ + M₂₂) / P`
- `Completeness = M₁₁ / A⁺`
- `Consistency = M₁₁ / P⁺`

---

## Validation: NASA/SEL Environment

### Problems and Environment

**Goal**: Extrapolate pilot study result to validate Tian-Zelkowitz model

**Embedded Environment (NASA/SEL)**:
- **16 ground support projects**
- **SLOC**: 3K to 112K of Fortran code
- **Staffing**: 4-23 persons
  - Required between 5 and 140 person-months
  - Over 5-25 months
- **Modules**: 83-531 per project, about 4700+ total
- **Measures**: 74 collected

**Direct Environment (Classification Tree Analysis)**:
- Training set size: 1
- Testing on immediate next project
- 10 data points from 16 raw data
- 5 data points from isolated data

### Validation Results

**Comparing with original CTA**, measure selection using Tian-Zelkowitz model is **effective**:

**Cost**:
- Measure pool size: Reduced dramatically
- Classification tree complexity: Reduced dramatically

**Performance**:
- **Coverage**: Remained virtually the same
- **Completeness**: Remained virtually the same
- **Accuracy**: Improved
- **Consistency**: Improved

**Comparing with random guessing**:
- CTA based on either measure selection method made great improvement
- Well worth the cost

**Multiple data-points indicate validity** of Tian-Zelkowitz model

### Validation Baselines

**Baseline 1: Original CTA** (actual results)

**Baseline 2: Optimal Random Guessing**:
- Coverage = 100%
- Accuracy = 62.5%
- Completeness = 25%
- Consistency = 25%

**Other random guessing**:
- Consistency ≡ 25%
- Max(accuracy) = 75% (with 0% completeness)
- Max(completeness) = 100% (with 25% accuracy)

---

## Conclusion on Tian-Zelkowitz Framework

**The model provides scientific model of program complexity**:
- To understand and improve software process

**The theory of program complexity**:
- Embodies empirical research
- Extends formal models in this area

**The technique of measure evaluation**:
- Demonstrates usability of their theory in solving software engineering problems

**The model appears valid and effective** as demonstrated by multiple applications

---

## Follow-up Work to Tian-Zelkowitz

**Briand-Basili property-based metrics**: Further refinement of property-based approaches

**Goal Question Metrics (GQM)**: Integration with property/axiom frameworks

**Metrics validation work (Schneidewind)**: Empirical validation techniques

**Other theoretical work**: Continued development of formal foundations