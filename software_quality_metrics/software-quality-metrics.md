# software quality metrics

- Size (complexity etc.)
- Time
- Effort
- Reliability (quality etc.)
- Productivity

## module 1: Overall framework

- Goal, Questions, metrics (GQM)
    - What it is, background, and relation to ESE
- Experience Factory (EF)
- Quality improvement paradigm (QIP)
- Other frameworks

## module 1: Mathematical foundation

- Measurement theory
- Types and levels of measurement

## module 2 & 3: External metrics

- Quality: reliability, safety, dependability, usability, etc.
- Cost, time, schedule, activity, environment, etc.
- Areas and contexts: Public-Private Partnership

## module 2 & 3: Internal metrics

- Complexity
- Dimensions and classification of complexity metrics

## module 2 & 3: Defect metrics

- Internal and external view

## module 2 & 3: Relations, classification, usage

## module 4: Empirical evaluation

- Leads to formal model
- Data and statistical analysis
- Other empirical evidence/corroboration
    - evidence to confirm or support finding

## module 4: Formal model

- Historical development
- Tian-Zelkowitz model
- Other recent development ( if we have time)

## module 5: Advance Topics

- Results analysis and hypothesis testing
- Using metrics (Koru-Tian)
- Bigger picture of ESE
- Main ideas, guidelines, applications
- Integrated approach
- Putnam/Myers 5 core metrics
- New applications/development
- Traditional: commercial, telecom, etc.
- New: net-centric, Service-oriented Architecture (SOA), cloud, etc.

# Key components of software engineering

- Methods and Processes
- Formal Foundations (Math/Theory)
- Experimentation (Scientific)

# Capturing Defects / Measurement Framework

The goal of a system is meet specific behavior. System boundaries should be established to identify what constitues a defect. The system boundaries will guide what data should be captured. Defect trends need to be captured to produce actionable insights from a model. Defect should be traceable. At a minimum, you should capture:

- The requirement or feature the defect is related to
- Configuration when the defect occured
    - Revision / release of the code (Tags)
    - System configuration
- Inputs to the system
- System state
- Severity of the defect

## Measurement Framework

**Goal-Question-Metric Paradigm (QGM)**: What is the goal of the study, what are the questions related to the study, what are the metrics for answering questions.

**Quality Improvement Paradigm (QIP)**: Based on goal-question-metric framework.

Whenever a change is made to a software baseline, the changes and impacts should be quantified.

**Experience Factory**:

- 

# Measurement in Emperical Software Engineering (ESE)

**Definition**: Context and measurement theory
**Gathering**: Data collection
**Analysis/Follow up**: Analysis, presentation, interpretation

## Measurement Theory

- Formalization of measurement
    * R: relation
    * f(x): measurement as functional mapping
    * aRb <-> f(a) > f(b)

## Measurement Evaluation

Evaluation criteria:

- Are they properly defined
- Are they properly used
- Do they lead to any useful results

Based on evaluation

- Decide which metrics to select
- Propose new ones
- Under what context should they be used

Evaluation of new metrics

- Identify scope of metric
- Demonstrate use and usefulness
- Identify bias

Empirical evaluation of metrics

- 

## Types of metrics evaluation

# Metrics

## External Measures

- **Quality Metrics:** Reliability, Availability, Usability, Extensibility, security, portability 
- **Non-Quality Metrics:** Customer satisfication, Cost, Effort, Schedule
- **Effort:** Man-Month
- **Cost:** Cost Estimation

## Goal Question Answer (GQA) Metrics

- External: Time, Effort, Quality, Productivity
- Internal: Size

Relate  them using a model, ex: Putnam

## Availability

Track Mean Time To Failure (MTTF) and Mean Time to Repair (MTTR). System availability can be calculated as:

`Availability = MTTF / (MTTF + MMTTR)`

## Code Complexity

Data Items, Data Structures, Data Dependencies

- **Lexical:** Token-based measurement computation: Lines of code (LOC), Control Types, Related Counts, GOTOs, Decisions, Branches, etc.
- **Syntactic:** Semantic Analysis needed for measure computation: Statement Count, Concatenation, Nesting, GOTO
- **Semantic:** Semantic analysis needed for measure computation: Dependency-Use Pair (DU), Control Dependency, Logical/Algebraic sensitization.

## Size Metrics

Cone of uncertainty

![Cone of Uncertainty](https://lh4.googleusercontent.com/8BYWfNyhx-9x_UMAPRR8yWwwvdM5h6WOmwAiOr7kcc7cEdUOsPGhorZjjIX5MQfzSKT7_qrWqLW9lzx3izyQFkhT2YoBTADAiohBprdTuTRySJjao-LozjmOj-sJsameebp32SYkoBwLtaCG-wS73Bg)

### Gearing Factors

How many lines of code are required to write the same method in different languages. Represents relative complexity between languages.

### Size Metrics: Change

Continual Service Improvement (CSI)

-   Improve software quality
-   Reduce dev cost
-   Increase safety and security

Systems to Software Integrity (SSI)

-   Safety, Security, and Maintainability

NASA classification scheme

- 25% of teams maintain active metrics
- 20% of teams baseline metrics, but do not maintain
- 5% do not actively track metrics
- 50% never maintain metrics

### Size Metrics: Function Point

- Count External user inputs, Inquiries, Outputs, Master Files

### Cyclomatic Complexity

Measure of how many unique paths exist

`v = e - n + 2p`
e: edges
n: nodes
p: connected components

`v = c + 1`

### Knot count

Knots indicate branching / crossing of control structures (break, goto). High count indicates lack of structure. Goal is less than 0.

## Data Complexity Metrics
(TODO): Garrett Gruss Create a table for complexity Metrics, rows = metrics domain, columns = Lexical, Syntactic, Semantic

Lexical: Variables

Syntactic: Scoping

Semantic: Data Dependency (DU) pair

### Information Flow Metrics (IFM)

`IFM = (fan-in x fan-out)^2`

Fan-in: Number of local flows into procedure
Fan-out: Number of flows from procedure

## Interface Complexity Metrics

- Usability, UI/UX

Map Lexical/Syntactic/semantic to attribute-based-credentials (ABCs)

- Anthropomorphic: Centered around user's traits/intent
- Keystroke level model (KLM): How many keystrokes are required to finish a task without errors.

## Volume Complexity Metrics

`v = (N1 + N2)log2(n1 + n1)`

- n1: number of distinct operators
- n2: number of distinct operands
- N1: total number of operators
- N2: total number of operands

`E = N2 * v / n1`

- E: Programming effort

## Object Oriented Complexity Metrics

- WMC: Weighted methods per class: complexity.
- DIT: Depth of inheritence tree: Maximum length from the node to the root of the tree.
- NOC: Number of children: number of subclasses: High DIT and low NOC is goal.
- CBO: Coupling between object classes: Number of classes whose methods are used by a class.
- RFK: Response for class: Measure of local methods.
- LCOM: Lack of cohesion on method: measure of dissimilarity of the methods in a class.
    * Promots encapsulation and decreases complexity

## Presentation Complexity Metrics

- Lexical: PResentation Token Metrics, Comments
- Syntactic: Rules used, indentation
- Semantic: Meaning in presentation, aliasing

## Hybrid Metrics

- Interface Complexity
- Halstead's Software Metrics
- Primary Principal Component Analysis (PCA)
- Algorithmic
    * Graph Coloring Chaitin - Briggs Algorithm: Degree < R rule
- Minimal algorithmic representation
    * Representation achieved:
        - sums of products
        - products of sums
    * Objective no term contains unnecessary variables
        - No term is unneccesasary
- Computational Complexity Linkage
    * Example run time to evaluate comparator: Linkage of 2 record files

## Non code-based metrics

- Measuring specs, designs.
- Function point
- Card and Glass design metrics
    * Structural Complexity: fan-out
    * Data Complexity: Interfaces, data size
    * System Complexity: Structural + Data Complexity