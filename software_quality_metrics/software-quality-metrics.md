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
