# Module 1 Study Notes: Software Reliability & Safety Engineering

---

## Key Definitions

**Reliability**: Probability of failure-free operation for a specific time period or input conditions under a specific environment.

**Safety**: The property of being accident-free with regards to human health for embedded/hybrid software systems.

**Dependability**: "The trustworthiness of a computing system which allows reliance to be justifiably placed on the services it delivers" (IFIP WG10.4). Includes: reliability, availability, safety, security.

**Accident/Mishap**: Unplanned series of events leading to unacceptable loss (death, injury, property damage).

**Hazard**: A set of conditions that can lead to accidents under certain environmental conditions.

**Risk**: Function of three elements:
1. Likelihood of a hazard
2. Likelihood a hazard leads to an accident
3. Worst possible loss due to accident

---

## Defect Terminology (Causal Chain)

- **Error** → **Fault** → **Failure**
  - **Error**: Missing/incorrect human action
  - **Fault**: Internal defect in the system (cause of failures)
  - **Failure**: External behavioral deviation from expected behavior

---

## Reliability vs. Safety vs. Security

| Attribute | Defect Impact | Causes/Focus |
|-----------|---------------|--------------|
| **Reliability** | All failures | All causes |
| **Safety** | Accidents only (severe consequences) | All causes, especially external/interface; hazard is pre-condition |
| **Security** | Intentional/malicious attacks | Intentional/malicious causes only |

---

## Quality Standards

**ISO 9126** characteristics: Functionality, Reliability, Usability, Efficiency, Maintainability, Portability

**ISO 25010** additions:
- Product quality: Adds compatibility and security
- Quality in use: Effectiveness, efficiency, satisfaction, freedom from risk, context coverage
- Safety = "freedom from risk"

---

## Quality Assurance Techniques

1. **Defect Prevention**: Error source elimination, error blocking
2. **Defect Removal**: Inspection, testing
3. **Defect Tolerance**: Fault tolerance → failure reduction, damage minimization

---

## Software Reliability Engineering (SRE)

**Core Activities**:
- Failure measurement and data collection
- Reliability assessment and prediction
- Decision making and management
- Reliability improvement

**Two Main Approaches**:

| Approach | Description | Models |
|----------|-------------|--------|
| **Time Domain** | Failure arrival process, statistical modeling | Software Reliability Growth Models (SRGMs) |
| **Input Domain** | Repeated random sampling | Input Domain Reliability Models (IDRMs), Fault seeding models |

**TBRMs (Tree-Based Reliability Models)**: Combine time and input domain information; provide risk identification and guide remedial actions.

---

## Software Safety Engineering (SSE)

**Focus**: Accidents and their pre-conditions (hazards), not all failures

**Key Analysis Techniques**:
- **FTA (Fault Tree Analysis)**: Static logical conditions. Describes how failures in the system cascade into/cause more failures.
- **ETA (Event Tree Analysis)**: Start with a failure, and backpropogate the workflow/events that causes the failure.
- **FMEA (Failure Mode and Effects Analysis)**

**Hazard Resolution Strategies**:
1. **Eliminate**: Remove hazard sources
2. **Reduce**: Create barriers, minimize failure probability
3. **Control**: Isolation, containment, fail-safe design
4. **Damage reduction**: Post-accident mitigation

---

## Software Safety Program (SSP) Lifecycle

**Major Activities**:
1. Hazard identification and analysis
2. Hazard resolution (design for safety)
3. Safety verification
4. Change analysis and operational feedback

**SSP by Development Phase**:
- **Concept phase**: Initial risk assessment, preliminary hazard list
- **Requirements**: SRS satisfies safety constraints, formal language
- **High-Level Design**: Identify safety-critical items via FTA/ETA, isolation/encapsulation
- **Low-Level Design**: Preserve safety invariants, dynamic properties
- **Code**: Combination of testing/inspection/formal verification
- **Maintenance**: Change effect analysis

---

## Key Software Myths (False Beliefs)

- Software is lower cost than other devices
- Software is easy to change
- Computers provide greater reliability
- Higher software reliability = higher safety
- Testing/formal verification eliminates all defects
- Reusing software increases safety
- Computers always reduce risk vs. mechanical systems

---

## Risk Factors in Modern Systems

- New technology → new hazards
- Increasing complexity
- Interdependency → increased exposure
- Increasing energy amounts
- Increased automation
- Increasing centralization and scale
- Faster pace of technological change

---

## Fault Tolerance

**N-Version Programming (NVP)**: Multiple independently developed versions of the same program run concurrently.
- High cost technique
- Used primarily in SSE for hazard reduction/control

---

## Testing Connection to SRE

- **UBST (Usage-Based Statistical Testing)**: Based on Operation Profile
- **Nelson model**: Input Domain Reliability Model
- **Fault seeding (bebugging)**: Intentionally inject artificial faults to measure test coverage

--

## Software Reliability Growth Model (SRGM)

The SRGM plots defect or failure count over time as an index. Minor, Major, and Critical failures can be given a different weight, and the combined failure score is modeled over time.

--

## Orthagonal Defect Classification (ODC)

ODC is a methodology to classify defects so they can be aggregated and defect trends identified.

### Opener Section

When you find a defect, the following attributes can be classified

- **Activity**: This is the actual activity performed at the time of defect discovery. For example, during function test phase, an engineer might decide to do a code inspection. The phase would be function test but the activity is code inspection.
- **Trigger**: The environment or condition that had to exist for the defect to surface. What is needed to reproduce the defect? During Review and Inspection activities, choose the selection which best describes what you were thinking about when you discovered the defect. For other defects, match the description with the environment or condition which was the catalyst for the failure.
- **Impact**: For in-process defects, select the impact which you judge the defect would have had upon the customer if it had escaped to the field. For field reported defects, select the impact the failure had on the customer.

### Closer Section

when you know how the defect was fixed, the following attributes can be classified.

- **Target**: Represents the high level identity of the entity that was fixed.
Defect Type: Represents the nature of the actual correction that was made.
- **Qualifier** (applies to the Defect Type): Captures the element of either a nonexistent or wrong or irrelevant implementation.
- **Source**: Identifies the origin of the Target ( i.e. Design/Code, ID, etc.) which had the defect.
- **Age**: Identifies the history of the Target ( i.e. Design/Code, ID, etc.) which had the defect.

### Example ODC Classification Tables
Source: [IBM](https://s3.us.cloud-object-storage.appdomain.cloud/res-files/70-ODC-5-2.pdf)

**Opener Section** (when defect is opened):

| Activity | Trigger | Impact |
|----------|---------|--------|
| Design Rev | Design Conformance | Reliability |
| Code Inspection | Logic/Flow | Performance |
| Unit Test | Compatibility | Security |
| Function Test | Test Coverage/Variation | Usability |
| System Test | Workload/Stress | Capability |
| | Configuration | Serviceability |

**Closer Section** (when defect is fixed):

| Target | Defect Type | Qualifier | Age | Source |
|--------|-------------|-----------|-----|--------|
| Design/Code | Assignment/Initialization | Missing | Base | In-House |
| | Checking | Incorrect | New | Library |
| | Algorithm/Method | Extraneous | Rewritten | Outsourced |
| | Function/Class/Object | | ReFixed | Ported |
| | Timing/Serialization | | | |
| | Interface | | | |


---

## Availability

- **MTTF**: Mean time to failure (Operational Time / Number of Failures)
    * Track timestamps when system starts operation
    * Record when each failure occurs
    * Calculate time between start and each failure
    * Average these intervals
- **MTTR**: Mean time to recovery (Total Downtime / Number of Failures)
    * Record timestamp when failure detected
    * Record timestamp when system restored to operation
    * Calculate duration of each outage
    * Average these recovery times

Availability = MTTF / (MTTF + MTTR)

---

## Quick Reference: Acronyms

| Acronym | Meaning |
|---------|---------|
| SRE | Software Reliability Engineering |
| SSE | Software Safety Engineering |
| SRGM | Software Reliability Growth Model |
| IDRM | Input Domain Reliability Model |
| TBRM | Tree-Based Reliability Model |
| FTA | Fault Tree Analysis |
| ETA | Event Tree Analysis |
| FMEA | Failure Mode and Effects Analysis |
| SSP | Software Safety Program |
| NVP | N-Version Programming |
| UBST | Usage-Based Statistical Testing |
| OP | Operation Profile |
| HLD | High-Level Design |
| LLD | Low-Level Design |