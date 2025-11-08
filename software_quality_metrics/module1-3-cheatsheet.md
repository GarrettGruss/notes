# Modules 1-3 Cheatsheet: Software Quality Metrics

## Core Concept: Internal vs External Metrics

**Basic Assumption**: Lower complexity = cheaper to build, easier to maintain, more reliable

| Type | Definition | Examples | Characteristics |
|------|------------|----------|-----------------|
| **Internal** | Depend on programs only | Size (LOC, FP), Complexity (Cyclomatic), Structure (Coupling, Cohesion) | Available early, fine granularity, controllable |
| **External** | Depend on external factors | Reliability, Usability, Security, Time, Effort, Cost, Productivity | "-ilities", customer perspective, measured late, hard to control |

**Relationship**:
- External = **dependent variables** (targets)
- Internal = **independent variables** (predictors, leading indicators)
- **NOT uniquely determined** (correlated but not 1:1)

**Process**: Discover measures → Establish predictive relations → Use and validate

---

## Key Frameworks

| Framework | Purpose | Key Idea |
|-----------|---------|----------|
| **GQM** (Goal-Question-Metric) | Define study goals | Goals → Questions → Metrics for answers |
| **QIP** (Quality Improvement Paradigm) | Quantify changes | Impacts to software baseline |
| **Experience Factory** | Organizational learning | Continuous improvement |
| **Putnam/Myers 5 Core** | External + Internal | Time, Effort, Quality, Productivity (ext) + Size (int) |
| **Measurement Theory** | Formalization | `aRb ⟺ f(a) > f(b)` |

---

## Metrics Usage Workflow (5 Steps)

1. **Select**: Use GQM (external for goals, internal for control)
2. **Measure**: Tools, data tracking
3. **Analyze**: Modeling (Tian SQE Ch.19, risk models Ch.21)
4. **Use**: Assessment, prediction, control
5. **Improve**: Experience Factory for future

**Key SE Components**: Methods/Processes, Formal Foundations, Experimentation

---

## External Quality Metrics

### Quality "-ilities"

Reliability | Availability | Usability | Security | Maintainability | Scalability | Extensibility | Portability | Safety

### Reliability & Availability

| Metric | Formula/Description | Notes |
|--------|---------------------|-------|
| **Reliability** | Probability of failure-free operation | Requires defect measurement/analysis |
| **Availability** | `MTTF / (MTTF + MTTR)` | Downtime vs repair, severity, time units |
| **Management** | Software rejuvenation | Restart, cleanup, failover |

**MTTF**: Mean Time To Failure | **MTTR**: Mean Time To Repair

### Performance

**Metrics**: Response/turnaround time, throughput, resource utilization (memory, CPU)
**Variations**: Total, average, variance, worst-case, real-time
**Activities**: Task modeling, benchmarks

### Usability

| Approach | Metrics |
|----------|---------|
| **Classical** | Learning time, task performance, error/success rate, retention, satisfaction |
| **Modern** | Manual vs automated, intended vs actual usage, success rate, #steps, task time |
| **KLM** (Keystroke Level Model) | Keystrokes required to finish task without errors |

### Security, Maintainability, Safety

| Metric | Description |
|--------|-------------|
| **Security** | Many sub-attributes, specialized techniques, field data |
| **Maintainability** | Effort on task, related to portability/flexibility/testability |
| **Safety** | Focus on assurance (direct measurement impractical) |

### Defect Capture

**Capture**: requirement/feature, configuration (revision, system), inputs, state, severity
**Process**: Establish system boundaries to identify defects

---

## Other External Metrics

### Customer Satisfaction
- **Method**: Surveys (Kan Ch.14)
- **Data**: Ordinal scale, percentages, logistic analysis, field data

### Effort & Cost

| Metric | Description | Notes |
|--------|-------------|-------|
| **Effort** | Man-Month | "Mythical Man-Month" (Brooks), Estimation > measurement |
| **Cost** | Salary, overhead, risk, capital | Cost-benefit analysis |

Both use **size as input**, similar techniques (Tian SQE Ch.19)

### Schedule & Productivity

- **Schedule**: Time-based project delivery metrics
- **Productivity**: Output per effort unit (LOC/month, FP/month)

---

## Internal Size Metrics

### Measurement Levels

| Level | Description | Examples |
|-------|-------------|----------|
| **Lexical** | Token-based | Tokens, LOC, variables |
| **Syntactic** | Syntax-based | Statement count |
| **Semantic** | Meaning-based | DU pairs, naming |

### LOC vs Function Point

| Metric | Description | Characteristics |
|--------|-------------|-----------------|
| **LOC** | Lines of Code | Total/code/comment/blank lines |
| **Function Point (FP)** | Count inputs, inquiries, outputs, master files | Language-independent, black-box, available earlier, uses weights |

### Gearing Factors & Reuse

**Gearing Factors**: LOC ratio between languages
- Example: 38 LOC Access = 91 LOC Cobol
- Uses: Compare productivity, estimate porting

**NASA Reuse Classification**:
- Verbatim
- Slightly modified (<25%)
- Extensively modified (≥25%)
- New

**Counting Practices**:
- 25% count each use
- 20% count once
- 5% never count
- 50% never count

**Cone of Uncertainty**: Size estimation improves during development

**NASA Metrics Maintenance**:
- 25% maintain
- 20% baseline only
- 5% don't track
- 50% never maintain

---

## Internal Complexity Metrics

**Complexity**: General term for all internal metrics

**Categories**: Size, Information, Volume, Algorithmic, Non-code-based

### 3 Orthogonal Dimensions

| Dimension | Description | Aspects |
|-----------|-------------|---------|
| **Presentation** | Physical layout | Comments, blanks, indentation, formatting, naming |
| **Control** | Instructions/structures | GOTOs, decisions, branches, statements, nesting |
| **Data** | Data items/structures | Variables, scoping, visible sets, DU pairs, data flow |

**Creates 3-D space**: Proximity = similarity

### 3 Measurement Levels (Detailed)

| Level | Presentation | Control | Data |
|-------|--------------|---------|------|
| **Lexical** | Comments, blanks | LOC, GOTOs, decisions, branches | Variable counts |
| **Syntactic** | Indentation, formatting rules | Statements, concatenation, nesting | Scoping, visible sets |
| **Semantic** | Naming, aliasing | Dependencies, sensitization | DU pairs, data flow |

---

## Control Complexity Metrics

### McCabe's Cyclomatic Complexity ⭐

**Formulas**:
- `v = e - n + 2p` (edges - nodes + 2×components)
- `v = c + 1` (decisions + 1)

**Interpretation**:
- `v > 10`: Difficult/error-prone code
- Indicates test cases needed
- **Limitation**: Poor effort correlation

### Knot Count

**Definition**: Crossing control structures (break, goto)
- **Target**: ≤ 0
- **High value**: Unstructured code

---

## Data Complexity Metrics

| Level | Metrics |
|-------|---------|
| **Lexical** | Variable counts |
| **Syntactic** | Scoping, visible sets |
| **Semantic** | DU pairs, data flow |

---

## Interface & Information Flow

### Interface Metrics

**Lexical counting**: Name, type, frequency, I/O statements/parameters
**Used in**: Function Point

### Information Flow Metric (IFM)

**Formula**: `IFM = (fan-in × fan-out)²`
- **fan-in**: Flow into procedure
- **fan-out**: Flow out of procedure
- Includes global data structures

---

## Volume & Halstead (Software Science)

### Halstead Metrics

**Primitives**:
- `n₁`: Distinct operators
- `n₂`: Distinct operands
- `N₁`: Total operators
- `N₂`: Total operands

**Derived**:
- **Volume**: `V = (N₁ + N₂) log₂(n₁ + n₂)`
- **Effort**: `E = V² / V*`

### HAC (Bai/Zelkowitz)

Similar to Halstead but **accounts for control flow and data structures**

---

## Object-Oriented Metrics (CK Metrics)

| Metric | Name | Description | Goal |
|--------|------|-------------|------|
| **WMC** | Weighted Methods per Class | Complexity | Lower |
| **DIT** | Depth of Inheritance Tree | Inheritance depth | **Higher** ✓ |
| **NOC** | Number of Children | Child classes | Lower |
| **CBO** | Coupling Between Classes | Coupling | Lower |
| **RFC** | Response For Class | Local + called methods | Lower |
| **LCOM** | Lack of Cohesion | Dissimilarity | Lower |

**Design Goal**: High DIT, Low NOC
**LCOM Use**: Identifies design flaws, promotes encapsulation

---

## Interface/Usability Metrics (ABC Framework)

| Type | Description | Example |
|------|-------------|---------|
| **Anthropomorphic** | User traits/intention | KLM (expert task completion time) |
| **Behavioral** | Expected interactions | User perception |
| **Cognitive** | Task-based | Cognitive load |
| **Social** | Communication/coordination | Distributed systems |

---

## Hybrid & Other Metrics

### Hybrid Metrics

**Combine dimensions**: Function Point, IFM, Halstead

### Analysis Techniques

- **PCA** (Principal Component Analysis): Factor analysis, reduces dimensionality
- **Multiple approaches**: Profiler, ensemble models, integrated analysis

### Algorithmic Metrics

- Graph coloring (Chaitin-Briggs)
- Minimal representation (sums/products)
- Computational linkage

### Non Code-based Metrics

**Function Point-like**: Applied to specs, designs

**Card & Glass Design**:
- **Structural**: Fan-out, interconnections
- **Data**: Interfaces, size
- **System**: Combined architectural complexity

---

## Quick Reference: Key Formulas

| Metric | Formula |
|--------|---------|
| **Availability** | `MTTF / (MTTF + MTTR)` |
| **Cyclomatic** | `v = e - n + 2p` or `v = c + 1` |
| **IFM** | `(fan-in × fan-out)²` |
| **Halstead Volume** | `V = (N₁ + N₂) log₂(n₁ + n₂)` |
| **Halstead Effort** | `E = V² / V*` |
| **Productivity** | `LOC/month` or `FP/month` |

---

## Quick Reference: Metric Categories

### By Timing
- **Early**: Internal (LOC, FP, Cyclomatic)
- **Late**: External (Reliability, Customer Satisfaction)

### By Control
- **Controllable**: Internal (design choices)
- **Hard to control**: External (user behavior, environment)

### By Granularity
- **Fine**: Internal (per function, per class)
- **Coarse**: External (per system, per project)

### By Perspective
- **Developer**: Internal (code complexity)
- **Customer**: External (quality "-ilities")

---

## Common Thresholds & Rules of Thumb

| Metric | Threshold | Meaning |
|--------|-----------|---------|
| **Cyclomatic** | > 10 | Difficult/error-prone |
| **Knot Count** | ≤ 0 | Target (structured code) |
| **DIT** | Higher | Preferred (reuse) |
| **NOC** | Lower | Preferred (maintainability) |
| **80:20 Rule** | 20% code → 80% errors | Risk identification |

---

## Study Tips

### Must Memorize
- Internal vs External definitions & examples
- Cyclomatic formulas (both)
- Halstead primitives (n₁, n₂, N₁, N₂)
- CK metrics names & goals
- 3 Dimensions: Presentation, Control, Data
- 3 Levels: Lexical, Syntactic, Semantic
- Availability formula

### Must Understand
- Why internal ≠ external (correlated, not determined)
- When to use LOC vs FP (language-dependent vs independent)
- Cyclomatic > 10 interpretation (testing, risk)
- High DIT is good, Low NOC is good (why?)
- IFM captures information flow (fan-in × fan-out)²

### Must Compare
- LOC vs Function Point (dependent vs independent)
- Internal vs External (early vs late, controllable vs not)
- Halstead vs HAC (basic vs enhanced)
- Cyclomatic vs Knot (decisions vs crossing)
- WMC vs RFC (methods complexity vs response set)

### Workflow to Remember
GQM select → Measure → Analyze → Use → Experience Factory improve

### Frameworks to Remember
- **GQM**: Goals → Questions → Metrics
- **Putnam/Myers**: 4 external + 1 internal (Size)
- **CK Metrics**: WMC, DIT, NOC, CBO, RFC, LCOM

---

## Common Acronyms

| Acronym | Full Name |
|---------|-----------|
| **LOC** | Lines of Code |
| **FP** | Function Point |
| **GQM** | Goal-Question-Metric |
| **QIP** | Quality Improvement Paradigm |
| **MTTF** | Mean Time To Failure |
| **MTTR** | Mean Time To Repair |
| **KLM** | Keystroke Level Model |
| **IFM** | Information Flow Metric |
| **HAC** | Hierarchical Abstract Computer |
| **DU** | Definition-Use (pairs) |
| **WMC** | Weighted Methods per Class |
| **DIT** | Depth of Inheritance Tree |
| **NOC** | Number of Children |
| **CBO** | Coupling Between Objects |
| **RFC** | Response For Class |
| **LCOM** | Lack of Cohesion of Methods |
| **PCA** | Principal Component Analysis |

---

## Key References

- **Tian SQE Ch.19**: Measurements and models
- **Tian SQE Ch.20, 22**: Defect measurement and analysis
- **Tian SQE Ch.21**: Risk models
- **Kan Ch.14**: Customer satisfaction surveys
- **Laird Ch.6**: Effort (Man-Month)
- **Laird Ch.12**: Cost factors
- **Laird tables 4.1, 4.2**: Gearing factors
- **Laird table 4.3**: Function Point weights
- **Brooks**: "Mythical Man-Month"

---

## Advanced Topics Preview

- Results analysis
- Hypothesis testing
- Koru-Tian usage
- ESE (Empirical Software Engineering) bigger picture
- Integrated approach
- Applications: Traditional (commercial, telecom) vs New (net-centric, SOA, cloud)
