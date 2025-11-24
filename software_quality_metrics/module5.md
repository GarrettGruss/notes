# Module 5: New Models and ESE

## Overview: Empirical Research in Software Engineering (ESE)

**Key Reference:**
Kitchenham et al., "Preliminary guidelines for empirical research in software engineering," IEEE Transactions on Software Engineering, vol. 28, no. 8, pp. 721-734, Aug. 2002

### Why ESE Guidelines?
- Increasing ESE research activities
- Maturing of Software Engineering and ESE
- Practical concerns for multiple stakeholders:
  - Readers/students
  - Researchers and meta-analysts
  - Reviewers and editors
  - Publication venues (journals, conferences)

## ESE Guideline Foundations

### Internal Basis
- Research and reviewer experience in ESE
- Author and reviewer perspectives
- Computer Science and Software Engineering work

### External Basis
- Scientific method from mature disciplines
- Physical sciences (Physics, Chemistry, Biology)
- Medical field guidelines
- External expert collaboration

## ESE Guideline Topic Areas

### 1. Experimental Context
- **Organization**: Steps and specifications
- **Notation**: TAx (Topic Area "x")
- **Elements**:
  - Background
  - Research hypothesis
- **Study Types**: Observational or formal experiments

### 2. Experimental Design
- **Elements**:
  - Population definition
  - Sampling technique and rationale
- **Statistical Validity**:
  - Simplicity
  - Define experimental unit
- **Reducing Bias**:
  - Define treatment/intervention
  - Use appropriate blinding levels

### 3. Conduct Experiment
- Domain-specific execution
- **Data Collection**:
  - Define common guidelines and measurements
  - Accurate and complete data collection
  - Response rate and representativeness (for surveys)
  - Ensure unbiased data for analysis

### 4. Analysis
- Guidelines independent of analysis type
- **Best Practices**:
  - Avoid data torture/fishing
  - Use blind analysis
- **Analysis Types**:
  - Classical (domain-centric/specification-centered)
  - Bayesian (probability statements with new data)
  - Frequency analysis
  - Pre-post relations analysis

### 5. Presentation of Results
- **Understandable** to others
- **Guidelines**:
  - Describe statistical procedures
  - Provide sufficient details
  - Include raw data when possible (for independent verification)
  - Appropriate use of graphics
  - Ensure readers understand results and context

### 6. Interpretation of Results
- Avoid misinterpretation
- Distinguish between:
  - **Inferential statistics**: Predictions from sample to generalization
  - **Predictive models**: Probability of outcome based on predictor variables
- Statistical significance ` practical importance
- Specify study limitations and follow-up possibilities

---

## Data Collection

### Data Sources & Procedures
- Data source identification
- Collection procedures
- **Tools**: Computing and extracting

### IBM Orthogonal Defect Classification (ODC) Data
- Complexity metrics
- Defect data
- Activity tracking

### Data Extraction Examples
**Web Measurement:**
- Karami & Tian (2018): "Maintaining accurate web usage models using updates from activity diagrams"
- Karami & Tian (2018): "Improving Web Application Reliability and Testing Using Accurate Usage Models"

### Data Mining
- Unstructured/big data sources
- Extensive processing required
- **AutoODC** (SMU): Huang et al. (2015) - Automated Generation of Orthogonal Defect Classifications

---

## Validation and Hypothesis Testing

### Hypothesis Definitions
- **Hypothesis**: Assumption made for argument's sake
- **Simple hypothesis**: One value (� = 115)
- **Composite hypothesis**: Range of values (� ` 115)
- **Null Hypothesis (H�)**: Status quo
- **Alternative Hypothesis (H�)**: Believed to be true

### Hypothesis Testing Process
- Choose between competing hypotheses about population parameter
- Uses sample knowledge
- Rigorous statistical validity

---

## Case Study: Koru-Tian Hypothesis Testing

**Reference:** Koru & Tian (2005), "Comparing High-Change Modules and Modules with the Highest Measurement Values in Two Large Scale Open-Source Products," IEEE Trans. on Software Engineering

### Products Analyzed
1. **Mozilla**:
   - 800K LOC
   - 3,154 data points
   - 51 measures

2. **OpenOffice**:
   - 2,700K LOC
   - 15,226 data points
   - 46 measures

### Mann-Whitney U Test
- Merges two samples S� and S� (n� and n� points)
- Sorts to obtain ranking sequence
- Calculates test statistic U
- Obtains z (standard score)

**Significance Levels:**
- � = 1%: z_critical = 2.58
- � = 5%: z_critical = 1.96

**Formal Hypotheses:**
- **H�**: S� and S� drawn from same population
- **H�**: S� change count distribution shifted left/right of S�
- **Decision Rule**: Accept H� if z d z_critical; otherwise reject H� and accept H�

### Metrics Tested

#### Top Change Metrics
Modules ranked by percentile change count

**Size Measures:**
- **TOPLOC**: Top line of code
- **TOPNAL**: Top number of local attributes

**Coupling Measures:**
- **TOPACMIC**: Top ancestor coupling, class method interaction, import coupling
- **TOPCBO**: Top coupling between objects

**Cohesion Measures:**
- **TOPICH**: Information flow-based cohesion
- **TOPLCOM1**: Lack of cohesion in methods

**Inheritance Measures:**
- **TOPAIF**: Top ancestor coupling, inverse friends
- **TOPCLD**: Top class to leaf depth

### Results

#### Mozilla Test Results
- First value: 5.32
- TopChange vs TOPLOC: Top 2% modules compared
- All null hypotheses rejected at both � = 1% and 5%

#### OpenOffice Test Results
- First value: 13.01
- TopChange vs TOPLOC: Top 2% modules compared
- All null hypotheses rejected at both � = 1% and 5%

### HC vs HM Relationship Types

**Type A (H�)**: HC and HM identical (rightmost cluster has highest average change count)

**Type B (H�)**: HC and HM different
- **Type B1**: HC immediately preceded HM
- **Type B2**: Another segment exists between HC and HM

### Key Findings
- **High-defect vs high-complexity**: Statistically different; complexity ranking of high-defect was 60-80%
- **HM vs HC modules**: Majority of high-change modules different from highest measurement modules (inconclusive hypothesis test; high-change metrics ranked ~80th percentile)

---

## Other Hypothesis Test Examples

**Reliability Assessment:**
Y. Tian et al. (2017), "Reliability Assessment and Prediction with Testing Efficiency Growth for Open Source Software"

- Experience factory approach
- Capitalization and reuse of lifecycle experience
- Results compared using hypothesis testing

---

## Tailored Metrics

**Example:**
Karami & Tian (2018), "Improving Web Application Reliability and Testing Using Accurate Usage Models"

**Impact of Accurate Markov Operational Profile (OP):**
- Test coverage and efficiency (waste reduction)
- Reliability improvement
