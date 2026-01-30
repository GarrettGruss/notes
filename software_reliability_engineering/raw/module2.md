# Software Reliability and Safety
## CS 8317 – Spring 2026

**Module 2: Tree Based Reliability Models & Integrated SRE/Hazard Analysis**

---

## Agenda

**Deliverables**
- Assignment 1 due today
- Assignment 2 due next week

**Topics**
- Environment and needs
- Background: Existing approaches
- TBRMs: Tree-based reliability Models
- Integrated SRE using TBRMs & others

---

## Overview

**Reliability:** Problem/failure-free operations

**Time domain:** for a specific period.
- Reliability growth models.

**Input domain:** for a specific input set.
- Repeated sampling models.

**A new integrated approach: TBRMs**
- Tree-based reliability models (TBRMs)
- Both input/time domain information.
- Data driven/sensitive partitions.
- Risk focusing and remedial actions.

**Details:** SRE2 j7tbrm.pdf (Tian 1995), SRE2_3_b1sreAIC.pdf (Tian 1998) with more background

---

## Product Environment

**Large (medium-reliable) products:**
- Commercial: Compilers, software tools and computing environments.
- Telecommunication products too.
- Size: Up to millions of LOC.
- Widely distributed/large user population.
- No precise operational profile.
- Process: roughly waterfall.

**Overall testing:**
- Long testing period (2 ∼ 18 months).
- Different testing sub-phases.
- System testing focuses on reliability.
- Test-until-it-breaks commonly used.
- Staffing level variations.
- Code base stability

---

## Testing Environment

**Scenario-based testing.**
- Shifting focus: learning/dependency.

**Functionality-based scenario classes:**
- Randomized workload
- Progression: complexity & intensity increases
- Defect fixing and related runs
- Division among testers.

**Specific reliability analysis issues:**
- Scenario-based ∼ random testing
- Due to parallelism and interleaving

**Defect fixing effect:**
- No long-term dependency
- Short-term dependency will need grouping. Discussed later
- Uneven faults; TBRMs

---

## Needs and Constraints

**Need assessment and analysis:**
- Track test effort, progress and defect.
- Reliability assessment and prediction.
- Effective defect detection and removal.
- Process and quality improvement.

**Environmental constraints:**
- Minimize cost & schedule risks.
- Data availability and affordability.
- Process refinement.
- Maximize data utilization.

---

## Overall Solution

**Combine SRGMs and IDRMs into TBRMs.**

**Analysis and control:**
- SRGMs
- TBRMs: tree-based reliability models.
- Progress monitoring & exit criteria.

**Problem identification and correction:**
- Use of input domain information
- IDRMs (input domain reliability models)
- Identify high risk areas
- Automatic partitioning via TBRMs.
- Remedial actions for improvement.

---

## Solution: Coverage & Scope

**Product coverage:**
- Commercial products from IBM.
- Improvement over original process.

**Evolutionary approach:**
- Individual techniques.
- Integration and refinement.

**Scope of Engagement:**
- Data definition and collection.
- Data visualization and analysis.
- Test progress tracking.
- Reliability tracking with SRGMs.
- Reliability improvement with TBRMs.

---

## Data: UBST & Data

**Data and tracking:**
- Integration with schedule information.
- Normalization effect.
- Summary reports and visualization.
- Consistency checking automation.
- Customer usage information gathering
- Operational profile construction.

**Coverage and input-domain analysis:**
- Functionality/function/static/dynamic.
- Different levels of coverage for different testing phases.
- Focused coverage through TBRM.

---

## Software Reliability Growth Model

- Shape can either take a concave or S-shape
- Use cumulative defects over time

**Measuring test time:**
- Calendar time, example months
- Number of test runs
- Execution time, example CPU time, transactions etc.

*[Figure: Software Reliability Growth Model curve]*

---

## Experience: SRGMs

**Time measurements:** Fig.2 (Tian 1998) - Product E

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Calendar time models useless.
- Products A, B, and C: Fig.3 (Tian 1998)

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Calendar time Fig. 3 (Abuta-Tian 2018)
- SRE4_j36oedSRE.pdf

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Execution time models costly & sensitive.
- Product B Fig.6b (Tian 1998)

**Models:**
- Geo – Moranda's geometric de-eutrophication model
- Musa – Musa's basic execution time model
- Musa-Okumoto – logarithmic Poisson execution time model

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Runs suitable for some products.
- Product B: Fig.6a (Tian 1998)

**Model:**
- LV – Littlewood-Varrel Bayesian model

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Runs suitable for some products.
- Product D: Fig.8a (Tian 1998)

**Model:**
- S: Yamada-Ohba-Osaki S-shaped non-homogeneous Poisson process (NHPP) model

*[Figure]*

---

## Experience: SRGMs

**Non-Homogenous Poison Process (NHPP) models**
- Concave – Goel-Okumoto
- S-Shape – Yamada
- Musa-Okumoto
- Another variation on NHPP logarithmic execution

Fig. 12 (Abuta-Tian 2018)

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Runs suitable some products.
- Product D: Fig.8b (Tian 1998)
- Failure intensity data (rate data)

**Model:**
- GO: Goel-Okumoto NHPP model

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Failure intensity – Fig. 7 (Abuta-Tian 2018)

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Transactions for other products.
- Product E: Fig.9 (Tian 1998)

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Time measurement comparison
- Product E: Fig.5 (Tian 1998)

*[Figure]*

---

## Experience: SRGMs

**Model applicability and effectiveness:**
- Context sensitive modeling for sub-groups or sub-phases ⇒ TBRMs.
- Product B: Fig.7 (Tian 1998)

**Details:**
- Groups 1, 3, and 4: Failure interval data
- Groups 1 and 3: Execution time-based failure

*[Figure]*

---

## Operational Reliability Assessment

**System's reliability snapshot during operation**
- Failure rate stability/operational stability

**Use Input Domain Reliability Model (IDRM)**
- Nelson model (Nelson, 1978)

**Estimate's reliability (R) for different time segments as:**
- ƒ – number of failures
- λ – failure rate
- n – number of runs

**Stable period**
- Individual rate falls 15% with the stable period s to N (Abuta-Tian 2018)

*[Figure]*

---

## Operational Reliability Assessment

**Model applicability and effectiveness:**
- Fig. 8 (Abuta-Tian 2018)

*[Figure]*

---

## Other: Trend Test

**Analyze reliability of a system, using defects**
- Uniquely counted defects
- Set at an interval (Month)

**Use Laplace trend test, where Laplace factor:**

**Negative** - decreasing failure intensity
- Implies reliability growth
- Most defects have been found

**Positive** - increased failure intensity
- Implies reliability decay
- Trend not established for region between

---

## Other: Trend Test

**Model applicability and effectiveness:**
- Gives a better view of defect distribution
- Demonstrated Reliability growth
- Fig. 5 (Abuta-Tian 2018)

*[Figure]*

---

## Experience: SRGM Conclusions

**Modeling result interpretation:**

**Accuracy of models:**
- Assessment, model goodness-of-fit.
- Prediction: training & testing sets
- Product purity at exit.
- Bounded estimations: multiple models.
- Convergence of modeling results.

**Evolving to usage-based data/model:**

**Assurance of homogeneity:**
- Homogeneous – constant fault detection rate per fault
- If 'yes', run-based data/model;
- If 'no', transaction measurement.
- Suitable for input domain analysis.
- Also, as cross validation for TBRMs.

---

## Assessing Existing Approaches

**Time domain reliability analysis:**
- Customer perspective.
- Overall assessment and prediction.
- Ability to track reliability change.
- Problem: how to improve reliability?

**Input domain reliability analysis:**
- Explicit operational profile.
- Better input state definition.
- Hard to handle change/evolution.
- Problem: realistic reliability assessment and handling numerous data sets/partitions?

---

## An Integrated Approach

**Combine strengths of the two.**

**Using TBRM for individual modeling:**
- Input state: categorical information.
- Each run as a data point.
- Time cutoff for partitions too.
- Data sensitive partitioning
- Nelson models for subsets.

**Integrated reliability analyses:**
- TBRM: partitioned subset reliability.
- Use both input and timing information.
- Monitoring changes in trees.
- Enhanced exit criteria.
- SRGM: overall reliability near exit.
- Integrate into the testing process.

---

## TBM: Technique for Integration

---

## TBRM Simple Example

**1 categorical predictor and 1 response:**
- Binary grouping for partitioning
- Example: Fig 10 (Tian 1998)

*[Figure]*

---

## TBRM Simple Example

**1 numerical predictor and 1 response:**
- Binary operator (≥) for partitioning
- Run numbering (rsn)
- Example: Fig 15 (Tian 1998)

*[Figure]*

---

## TBRM Simple Example

**1 categorical predictor and 1 response:**
- Interpretation as piecewise linear model
- Example continued: Fig 14 (Tian 1998)

*[Figure]*

---

## TBRM Example

**The n mixed predictors and 1 response:**
- Full TBRM
- Example: Fig 11 (Tian 1998)

*[Figure]*

---

## TBRM in Integrated Analysis

**Tree-based reliability models (TBRMs) using all information:**
- Input domain partitioning information.
- Testing results.
- Timing information.
- Each run as a data point.

**Model construction:**

**Response:** Result indicator.
- 1 for success, 0 for failure.
- Nelson model for subsets.
- Mapping to failure rate or mean-time-between-failures (MTBF)

**Predictor:** Timing and input states.
- Data sensitive partitioning.
- Key factors affecting reliability.
- Homogeneity of product reliability.

---

## Using Integrated Analysis

**Interpretation of trees:**
- Predicted response: success rate.
- Nelson reliability estimate.
- Time predictor: reliability change.
- State predictor: risk identification.

**Monitoring reliability change:**
- Change in predicted response.
- Through tree structural change.

**Risk identification and remedies:**
- Identify high risk input state.
- Additional analysis.
- Enhanced test cases.
- Remedies for components.

---

## TBRMs in Integrated Analysis

**Treatment of product bundles:**
- TBRM for individual products.
- Dynamic change with respect to process needs.
- SRGM (& TBRM) for bundle near exit.

**Risk identification:**
- High risk input sub-domains.
- Additional analysis for the identified.
- Guide for remedial actions.

**Results interpretation:**
- Progression of trees & tree types.
- Usage as exit criteria.

---

## TBRMs at Different Times

**Fig 12a (Tian 1998): an early TBRM.**
- High-risk areas identified by input
- Early actions to improve reliability
- Test scenario SC and SN (Scenario Number)

*[Figure]*

---

## TBRMs at Different Times

**Fig 12b (Tian 1998): whole testing phase**
- High-risk areas ≈ early runs
- Uniformly reliable implies ready for release

*[Figure]*

---

## Cross Validation

**Consistency with macro models:**
- Effects on cost, schedule, quality.

**Validate with reliability growth models:**
- Trend of reliability growth.
- Stability of failure arrivals.
- Estimated reliability.
- Product purity level at exit.

**Process changes & improvements:**
- Failure detection and fault removal.
- Long term effect on development.
- Ultimate test: In-field problems.

---

## TBRM Result Comparison

---

## TBRM Result Comparison

**Fig 22.6 (p.384): TBRMs used in D**
- Better reliability growth in D
- Compare to A, B, and C (no TBRMs)

*[Figure]*

---

## Integrated Approach: Implementation

**Modified testing process:** Fig 18 (Tian 1998)
- Additional link for data analysis.
- Process change and remedial actions.

*[Figure]*

---

## Integrated Approach: Implementation

**Tool support:** Fig 20 (Tian 1998)
- Different types of tools
- I/O and interconnection

*[Figure]*

---

## Integrated Approach: Implementation

**Activities and Responsibilities:**
- Evolutionary, stepwise refinement.
- Collaboration: project & quality orgs.
- Experience factory prototype (Basili).

**Implementation:**
- Passive tracking and active guidance.
- Periodic and event-triggered.
- Software tool support

---

## Implementation Support

**Types of tool support:**

**Data capturing**
- Mostly existing logging tools
- Modified to capture new data

**Analysis and modeling**
- SMERFS modeling tool
- S-PLUS and related programs

**Presentation/visualization and feedback**
- S-PLUS and Tree-Browser

**Implementation of tool support:**
- Existing (IBM + others) tools: cost go down
- New tools and utility programs

**Tool integration**
- Loosely coupled suite of tools
- Connectors/utility programs
- Common depository: S-PLUS

---

## Application Summary

**Tracking and input-domain analysis:**
- Effectiveness of visualization.
- Problems with input-domain assessment.

**Time-domain analysis refinement:**
- Data normalization by runs/transactions best.
- Context sensitive modeling promising.

**Integrated approach using TBRM:**
- Guidance as well as assessment.
- Risk focusing implies reliability improvement.
- Progression of trees.
- Usage as exit criteria.
- Cross validation.

---

## Future Directions

**Implementation and deployment:**
- Data: automated data capturing.
- OP: evolutionary approach.
- Integration: analysis and improvement.
- Use in different industrial environments.

**Exploration and improvement:**
- Customize time/transaction measurement.
- Early indicators/predictive modeling.
- Customer environment/OP refinement.
- Integrate to life-cycle quality models.
- Management and cost modeling.
- Refinement of modeling techniques.
- Continued research at SMU and collaboration with our industrial partners.

---

## Hazard Analysis (HA) Agenda

- Hazard Analyses and Techniques
- Fault Tree Analysis (FTA)
- Event Tree Analysis (ETA)
- Other HA Techniques

---

## Safety Techniques

**Hazard and risk identification:**
- Accident scenarios: actual/hypothetical
- Starting points for safety
- Focus: operations and operational environment

**Hazard analysis and assessment:**
- Fault trees: (static) logical conditions
- Event trees: dynamic sequences
- Other analyses/assessment techniques

**Hazard and risk resolution**
- Hazard elimination
- Hazard reduction
- Hazard control
- Damage control

---

## Safety Techniques in Process

**Starting points for safety (initiation)**
- Accident actual/hypothetical
- Hazard and risk identification

**Hazard analysis (pre-process?)**
- Input: above plus expertise
- Output: driver for Hazard Resolution (below)

**Hazard and risk resolution**
- Negate
- Tolerate(passive)/control(active)
- Damage control (post accident)

**In-process:**
- Cascading activities
- Hazard Resolution and/plus Hazard Analysis

---

## Hazard Analysis: Types/Levels/Scope

**Sub-system hazard analyses (SSHA)**
- Hazard within individual sub-system
- Component/sub-system in isolation

**System hazard analyses (SHA)**
- Focus: interface and interaction
- Sub system/environment/human effect on system
- Throughout development process
- Focus on early phases to provide info. for other activities (hazard resolution and safety verification)

**SHA/SSHA in software process**
- Throughout development process
- Focus on early phases to provide information for other activities
- Hazard resolution and safety verification

---

## Hazard Analyses: Techniques

**Primary techniques for SHA/SSHA:**
- Fault-tree analyses (FTA)
- Event-tree analyses (ETA)
- SQE Ch.16.4 and Safeware Ch.14.

**Other techniques:**
- Design reviews & checklists
- Hazard indices
- Risk trees
- Cause-consequence analysis (CCA)
- Hazard & operability analysis (HAZOP)
- Failure modes and effect analysis (FMEA)
- FMECA (FMEA + Criticality), etc.

Above: "Safeware" Ch.14.
Specific to software: "Safeware" Ch.15.
System Theoretic Accident Mode (STAMP) (Model 4)

---

## Hazard Analysis: FTA

**Fault tree idea:**
- Top event (accident)
- Intermediate events/conditions
- Basic or primary events/conditions
- Logical connections
- Form a tree structure

**Elements of a fault tree:**
- Nodes: conditions and sub-conditions
- Terminal vs. no terminal
- Logical relations among sub-conditions
- AND, OR, NOT
- Other types/extensions possible

---

## Hazard Analysis: FTA Example

*[Figure: Example FTA for an automobile accident (Fig. 16.3, p.276)]*

---

## Hazard Analysis: ETA

**Event Tree Analysis (ETA): Why?**
- FTA: focus on static analysis
- Logical conditions (static)

**Dynamic aspect of accidents**
- Timing and temporal relations
- Real-time control systems

**Search space/strategy concerns:**

**Contrast ETA with FTA:**
- FTA: backward search
- ETA: forward search
- May yield different path/info.
- ETA provide additional info.

---

## Hazard Analysis: ETA Example

*[Figure: Example ETA for an automobile accident (Fig 16.4, p.277)]*

Compare/contrast with FTA a few slides back.

---

## Hazard Analysis: SFTA

**SFTA: Software FTA**
- Same concept applied to software
- Actual implementation (white-box)

**Language elements (high-level):**
- Assignment and function calls
- Branching statement, loops, etc.

**It can also be used for specification/architecture**
- Black-box control flow diagram
- Equivalent language representation

**SFTA construction:**
- Templates/examples for diff. statements
- Safeware 18.2.2 (pp.497-507)
- Additional work needed, especially for system design/architecture new work of STPA by Leveson

---

## Cause-Consequence Analysis

**Construct the Cause Tree**
- Work backwards from the critical event
- Identifying primary, secondary, and root causes
- Assign probabilities to basic events

**Develop the Consequence Tree**
- Move forward from the critical event
- Identify safety functions and barriers
- Determine possible outcomes

Ref: Jeremiah Genest - CCA

*[Figure]*

---

## Hazard Analysis: ETA & CCA

**ETA alone:** trace of accident. May desire explanation also (from FTA)

**Cause-consequence diagram (CCA):**
- Combine ETA with FTA
- Explaining decisions in ETA

**Using ETA and CCA:**
- Partial vs. total ETA
- Focus on main consequences

Details: "Safeware" 14.5-14.6 (pp.327-pp.335)

---

## Hazard Analyses: FMEA & FMECA

**Failure modes and effect analysis (FMEA)**
- Reverse of FTA
- Some similarity to OP
- Focus on logical conditions
- Typically include environmental variables, operational scenarios, etc.

**FMEA relation to other Hazard Analysis techniques**
- Similar to ETA, but not focusing on time nor sequence

**FMECA (FMEA + Criticality), etc.**
- Root in traditional (hardware) reliability engineering
- Less so because of the dynamic/variable nature of software executions