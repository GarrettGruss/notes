## Reliability Models

## Basic Functions and Definitions

- 𝐹(𝑡): cumulative distribution function(CDF) for failure over time
  * 
- f(𝑡): Probability density function (PDF), f(𝑡) = 𝐹′(𝑡)
- Reliability function 𝑅(𝑡)=1 −𝐹(𝑡)
  * 𝑅(𝑡)=𝑃(𝑇≥𝑡)=𝑃(𝑛𝑜 𝑓𝑎𝑖𝑙𝑢𝑟𝑒 𝑏𝑦 𝑡)
- Hazard function/rate/intensity : 𝓏(𝑡)△𝑡=𝑃{ 𝑡 <𝑇<𝑡+ △𝑡|𝑇>𝑡}
- Mean function m(𝑡) in Non-homogeneous Poisson Process (NHPP)
- Failure rate/intensity,  𝜆(𝑡)= 𝑚′(𝑡)
- Time domain definition: Failure in timespace
  * 𝑅=𝑠/𝑛=(𝑛−𝑓)/𝑛=1−𝑓/𝑛=1−𝑟
  * In this reliability model, s and N (shown as lowercase n in your equation) represent:

s = number of successful operations or non-failed components
n = total number of operations or total number of components

From the equation you've provided:
R = s/n = (n - f)/n = 1 - f/n = 1 - r
Where:

R = reliability (probability of success)
s = number of successes = (n - f)
n = total number of trials/components
f = number of failures
r = failure rate or failure ratio (f/n)

- Mean time between failures (MTBF), Mean time to failure (MTTF), etc.

---

## SRGM Classification

### Data used

**Time-between-failure (TBF) models**
- Random variable: Failure interval

**Failure-count (FC) models**
- Random variable: failure count for given interval
- Most widely used (in this class)

Some models can use both TBF and FC data

### Other classifications possible
- **Time measurement:**
  - Calendar/wall-clock/execution/etc. time
- **F-Distribution**
  - Poisson – fixed rate interval
  - Binomial – two possible outcomes etc.
- Finite vs infinite failures
- Tools: pre-selected models

---

## TBF Models

You are trying to look at failure intervals over time. 

Model characteristics 
Failure intervals as random variable
𝑇_𝒾: random variable for the time between (𝒾−1)^𝑠𝑡 and 𝒾^𝑡h failures 
Distribution/density: 𝐹_𝒾(𝑡) or 𝑓_𝒾(𝑡) 
Directly define 𝓏_𝒾(𝑡)  
Relate 𝓏_𝒾(𝑡) to failures/faults 
Defining TBF models 
Sequence of 𝓏_𝒾(𝑡) over 𝒾
Initial value? 
Physical interpretation possible? 
Rate (or cumulative) data plotting

---

## TBF1: Jelinski-Moranda
One of the earliest model using TBF (time-between-failure) measurement 
Developed in 1972
Failure rate (𝓏_𝒾 𝑜𝑟 𝜆_𝒾): 
Proportional to defects remaining 
Step function: 𝓏_𝒾= 𝜙 ( 𝑁 −(𝒾−1))
𝓏_𝒾 : failure rate for the 𝒾^𝑡h failure 
Two model parameters:
 φ constant for failure exposure
 N constant for total defects 
Plotting 𝓏_𝒾′s and reliability growth 
Relation to later models 
Similar assumptions 
Other failure rate: geometric etc. 
Continuous version: Goel-Okumoto etc.

These models are looking at now to the past, so at this point we already know the total defects in the system. So when you go back to the beginning, it is a long time looking at it. You always consider looking at the final defects, and you want to track how the defects grow to the final cumulative number. YOu will be adjusting the model to best fit your distribution of failures.

Some of these are generic, but others are logarithmic.
---

## TBF2-3: Schick-Wolverton
Variations of Jelinski-Moranda (TBF1) model
Schick-Wolverton linear model (TBF2): 
Proportional to defects remaining and time 
Slope function with renewal 
 𝜆_𝒾= 𝜙 ( 𝑁 −(𝑖 −1))𝑡
Assumptions/parameters like TBF1 
Schick-Wolverton parabolic model (TBF3): 
2^𝑛𝑑 order (parabolic) time renewal 
𝜆_𝒾= 𝜙 ( 𝑁 −(𝒾−1))(𝑎𝑡^2+𝑏𝑡+𝑐)
Assumptions/parameters like TBF2 
Plotting 𝜆_𝒾′s and reliability growth 

They took the jelinski model and they modified it. THe proportion of defects remaining. The paremters are pretty much the same. Depending on your failure distribution, you can fit a parameter in and create a new model. The idea is you want to cosntruct the model. The goal of these models is to construct models that mirror historical recorded defects on a project, so you can reuse these models on future projects to predict the state of their defects.

The goal of these models is to reuse historical trends on future software projects to project defects based on similar software projects.
---

## TBF4: Geometric Models (Moranda)
Just like Jelinski-Moranda (TBF1) 
Failure rate 
Step function but geometric step sizes 
𝜆_𝒾=𝜆_0 𝜙^(𝒾−1)
𝜆_𝒾 : failure rate for the 𝒾^𝑡h failure 
Two model parameters:
– φ: Step reduction/curvature
– 𝜆_0 : Initial failure rate 
Plotting and comparison to TBF1 
Relation to later models 
Close relation to Musa-Okumoto model (logarithmic Poisson) 
Models defect discovery situations 
Hybrid geometric Poisson 
𝜆_𝑖=𝜆_0 𝜙^(𝒾 −1) + 𝑐

---

## TBF5: Imperfect Debugging

Goel-Okumoto 
Failure rate 
Just like Jelinski-Moranda (JM)
Step function 
Allow for imperfect debugging 
𝜆_𝒾= 𝜙 ( 𝑁 −𝓅(𝑖 −1))
𝓅: prob(imperfect debugging) 
Other parameters same 
Parameter re-interpretation as JM 
Relation to later models 
Close relation to Goel-Okumoto NHPP model 
Models defect removal process

This model alows "imperfect debugging". YOu keep adding parameters into the model to simulare imperfect debugging. The original models did not look at the initial failures, and as the models mature we introduce more parameters. This model incorporates the initial failure rate. The step reduction/curvature is how fast you reduce your defects.

---

## TBF6: Littlewood-Verrall (LV)

Bayesian model 
 𝑡_𝒾 : 𝒾^𝑡h inter-failure interval 
Distribution (Probability density function) for 𝑡_𝒾:
𝑓(𝑡_𝒾∣𝜆_𝒾)=𝜆_𝒾ℯ^(−𝜆_𝒾 𝑡_𝒾)
 𝜆_𝒾 : Failure rate parameter 
Distribution (PDF) for 𝜆_𝒾 :
𝑓(𝑡_𝒾|𝛼,𝜓(𝒾))=([𝜓(𝒾)]^𝛼 (𝜆_𝒾)^(𝛼−1) 𝔢^(−𝜓(𝒾)𝜆_𝒾))/⌈(𝛼)┤
𝜓(𝑖) : Increasing function of 𝒾  
𝛼 : Constant 
In SMERFS, LV model with 𝜓(𝑖): 
𝜓(𝑖)= 𝛽_0+𝛽_1𝒾, or 
𝜓(𝑖)= 𝛽_0+𝛽_1𝒾^2
---

## Failure-count (FC) Models

Model characteristics 
Failure count 𝑁_𝒾 random variable 
Time interval: predefined
Equal: Schneidewind model
Different: other models 
Distribution: failure arrival process 
Directly define process parameters 
NHPP most common 
Defining FC models 
Time intervals 
Underlying stochastic processes 
Physical interpretation 
Cumulative (or rate) data plotting

---

## FC1: Goel-Okumoto

Process assumption: NHPP (Non-homogeneous Poisson Process) 
Model definition: 
Probability of 𝑛 failures in [0,𝑡]:
𝑃(𝑁(𝑡)=𝑛)= (𝑚(𝑡)^𝑛)/𝑛!𝑒^(−𝑚(𝑡))
𝑚(𝑡) : Mean function 
𝑚(𝑡)=𝑁(1−𝑒^(−𝑏𝑡))
𝜆(𝑡)=𝑚^′(𝑡): failure rate 
𝜆(𝑡)= 𝑁𝑏𝑒^(−𝑏𝑡)
𝑁: Total estimated failures 
𝑏: Failure exposure as model curvature 
Data: Period failure count (PFC model) 
(N(𝑡) is the random variable)

---

## FC Models: Other NHPP

---

## FC Models: Generalized Poisson

---

## FC Models: Brooks-Motley

---

## FC Models: Musa

---

## FC Models: Musa (Continued)

### Practicality of Musa models
- Software usage; operational profile and execution time
- Predictions (prescriptive) based on process and product characteristics
- Practical issues dealt in Musa book
- Practicality verses theoretical focus

### Applications of Musa models
- AT&T projects: 10-20%
- Best practice at AT&T (Lyu/HSRE Ch.6)
- Adoption in other environments

### Tool and other support
- AT&T's SRE Toolkit
- Training and benchmarking
- Most publicized success stories

---

## Choice of SRGMs

### Issues discussed before
- Goal/environment/experience
- Tool/data availability

### Other model choice issues
- Time measurement and model fit
- Single vs. multiple models
- Composite models possible/meaningful?
- Existing vs. new models
- Assumptions/limitations/applicability

---

## Choice of SRGMs (Continued)

### Time measurement and model fit
- Experience at AT&T (exec. time!)
- IBM experience
- Bad fit implies time appropriate?
- Compare to bad fit implies another model

### Single vs. multiple models
- Best fitted vs. optimistic (fast reliability growth) vs. pessimistic (slow reliability growth)
- Band/range instead of single estimate
- Related: Synthesized/Composite models

### Existing vs. new models
- Simplicity of existing models
- Validation of new models
- Caution against ad-hoc new models

---

## Alternatives to SRGMs

### Reliability: Prob(failure-free operation)
- **Time:** How to measure ⇒ SRGMs
- **Input:** Characterize/classify
- Assumptions: Failure/OP/time/distribution
- Applicability and limitations

### Alternatives to SRGMs
- Input domain/combinatorial
- Fault seeding
- Hybrid models: Cleanroom model
- Coverage-based and predictive
- TBRMs: tree-based reliability models
  - Both time/input information

---

## Nelson's Input Domain Model

Nelson Model: 
Running for a sample of n inputs. 
Randomly selected from set
𝐸={𝐸_𝒾 :𝒾=1,2,…,𝑁}
Sampling probability vector: 
{𝑃_𝒾 :𝒾=1,2,…,𝑁}
{𝑃_𝒾}: Operational profile. 
Number of failures: 𝑓. 
Estimated reliability = success rate
𝑅=(𝑛−𝑓)/𝑛=1−𝑓/𝑛=1−𝑟
𝑟: failure rate. 
Repeated sampling without fixing.

# Nelson's Input Model

Nelson's input model is a **statistical software reliability testing approach** that estimates reliability by sampling test cases according to their operational usage patterns.

## Core Concept

Instead of testing all possible inputs exhaustively or uniformly, you test a **random sample of n inputs** drawn from the operational profile — a probability distribution that reflects how the software will actually be used in practice.

## Key Components

**Operational Profile (π)**: A probability vector where each π_i represents the likelihood that input i will be used in real operation. Inputs used more frequently get higher sampling probabilities.

**Sampling Process**: You randomly select n test inputs according to π, run them through the software, and observe failures.

**Reliability Estimation**: After observing f failures out of n tests, the estimated reliability is simply:
- R̂ = (n - f) / n = success rate

The estimated failure rate θ̂ is the complement: θ̂ = f/n.

## Important Feature

Nelson's model uses **sampling without replacement of fixes** — meaning you continue testing with the faulty software, recording failures as they occur, without stopping to fix bugs between test runs. This provides a snapshot of current reliability under operational conditions.

## Purpose

This model bridges the gap between testing and real-world usage. By weighting tests toward common use cases, it provides a realistic estimate of the reliability users will actually experience, rather than treating all inputs as equally likely.

---

## Other Input Domain Models

Brown-Lipow model: 
Explicit input state distribution. 
Known probability for sub-domains 𝐸_𝒾  

𝑓_𝒾 failures for 𝑛_𝒾 runs from sub-domain 𝐸_𝒾 
𝑅=1−∑_(𝒾=1)^𝑁▒〖(𝑓_𝒾)/(𝑛_𝒾)〗𝑃(𝐸_𝒾)
Ramamoorthy-Bastani: 
Safety critical systems, 𝑅̂=1
Confidence level for 𝑅̂ 
𝓍_𝒾 specific set of inputs 
P(program correct | correct for 𝓍_𝒾’s) 
𝑃=𝑒^(−𝜆𝑉)∏_(𝒾=1)^(𝑛−1)▒〖2/(1+𝑒^(−𝜆 𝓍_𝒾))〗
𝜆 source code complexity 
Recent development by Woit-Parnas


---

## Ho's Input Domain Model

---

## Mills Fault Seeding Model

---

## Cleanroom Reliability Model

---

## Coverage and Coverage-Based Models

### Alternative: coverage analysis
- Defect fixing effect
- Infeasibility of exhaustive testing

### Pure coverage vs. coverage-based models

### Focus on input/internal state coverage
- Function/data/statement coverage
- Path and dependency coverage
- **Assumption:** When coverage increases it implies reliability increases
  - A qualitative relation and not quantified

### Coverage-based modeling
- Analytical: Weyuker etc.
- Empirical: Mathur etc.
- Mixed: Chen/Lyu/Wong

---

## AI/ML-Based Models

### Alternative: AI/ML-Based Models
- AI/ML linkage to modeling techniques
  - Especially to risk identification/analysis
- Existence of mostly massive data
- Mining software repositories

### Characteristics and limitations
- Focus on numbers/quantities instead of functional forms
- Often deal with defects directly instead of reliability
- Possible integration with existing Software Reliability Models?
- TBRM might represent this direction?

---

## General Assumptions and Implications

### Times between failures are independent
- Implies randomized testing
- **Practical scenarios:**
  - Defect fixing effect
  - Structure/progression in testing

### Immediate defect removal
- Duplicate defect counting
- Related but not duplicate?
- Infeasible for in-field defects
- If similar defects are tracked as seperate items, defects can be duplicated. There is a high probability of defect duplications.

### No new fault injected
- Reliability growth assured
- **Practical:** Injection normally less than the removal
- Related: Decreasing failure rate

---

## Assumptions and Implications (Continued)

### Relating failure rate to number of faults
- **Variations to the assumption**
  - Proportionality between the two
  - Functional relation between the two
  - Time dependent relation

### Implications of failure detection and detection sequences

### Operational profile
- Ensures reasonable/meaningful reliability assessments and predictions
- Limits applicability

### Time as a basis for failure rate
- Equivalent time units
- Requires proper time measurement

---

## Assumptions and Applicability

### General considerations
- Assumptions for different model types
- Match them to application environment
- Models necessarily simple
- Impossible perfect match

### Applicability to different processes
- Waterfall generally assumed
- **Testing phases**
  - Used Based Statistical Testing
  - Including Black Box Testing: SRGMs and Input Domain Models
  - White Box Testing: coverage
- Incremental development: Cleanroom
- Spiral model: Iterations
- **Operational phases**
  - Difference in defect removal
  - Data availability

---

## Applicability to Different Phases

A strong usage of the reliability growth model is to manage your customer's expectations.

### Requirement and specification
- Reliability goal from customer expectation
- Feasibility and affordability
- Operational profile construction
- Prepare for random testing

### Design and coding
- Fault detection and removal (QA)
- Musa's prescriptive model
- Other existing models not applicable
- **Alternative models may be needed**
  - Fault and error-based models
  - Constructive information (white box)
  - Predictive models relating to reliability

---

## Applicability to Different Phases (Continued)



### Unit testing
- White-box deterministic testing
- Tester = developer
- Applicable: fault seeding, coverage-based
- Other models not applicable

### Integration and system testing
- Functional/system Verification Testing, regression, integration
- Focus: Customer-oriented operations
- Less emphasis on coverage
- Main phase for SRGMs
- Failure Count models more robust
- Random testing conformance
- Use of other models

---

## Applicability to Different Phases (Further)

### Acceptance testing
- Gate: accept/release or not
- Also plan for product support
- Basis: snapshot(s) or random sampling
- Cleanroom-like model usage
- Input domain model also appropriate

### Operational phase
- Actual operations (post-release)
- Beta or pre-release
- Difference in operational environments
- Data availability and treatment
- Reliability vs. availability
- Defect fix and product refreshing
- Business decisions

---

## Applications and Examples

### Overall procedure
- A lot of preparation
- Generic: preparation/modeling/follow-up
- Routine procedure once started
- Often periodic activities
- Evaluation/feedback/improvement

### Application examples
- Data: telecommunications (Musa)
- Wide applications of Goel-Okumoto, Musa, and other models
- Shuttle: Schneidewind and Keller
- Examples in IBM

---

## Recent Applications and Examples

### New application examples
- Non-traditional (beyond commercial and telecommunication industries)
- From product to service (Lyu etc.)
- Combined with traditional statistics (Pham etc.)
- Link to metrics/risk (Khoshgoftaar etc.)

### New applications
- SMU work
- Web sites and applications (Abuta-Tian)
- Defense
- E-commerce
- Service and cloud (including APIs)
- Open source & public data/forums
- Combination with other quality concerns: safety and usability

---

## Hazard and Risk Resolution

### Components
- Hazard Resolution and Damage Control
- **Hazard Resolution Techniques:**
  - Hazard Elimination/Reduction/Control
- **Risk Resolution:**
  - Damage Reduction

---

## Safety Techniques

### Hazard and risk identification
- Accident scenarios: actual/hypothetical
- Starting points for safety
- Focus: operations and operational env.

### Hazard analysis and assessment
- Fault trees: (static) logical conditions
- Event trees: dynamic sequences
- Other analyses/assessment techniques

### Hazard and risk resolution
- Hazard elimination
- Hazard reduction
- Hazard control ⊲ Damage control

---

## Hazard and Risk Resolution

### Generic hazard resolution techniques (in order of their precedence)

1. **Hazard elimination:**
   - Eliminate (some) hazard sources

2. **Hazard reduction:**
   - Reduce hazard likelihood/severity

3. **Hazard control:**
   - Control hazard severity/scope

**Hazard resolution implies the probability of an accident reduces**

### Related issues
- Basis: hazard identification and analysis via FTA, ETA, FMEA, Cause-consequence Analysis (CCA), etc.
- Many specific techniques
- Related to QA and SRE
- Risk resolution: damage reduction too

---

## Hazard Elimination

### Elimination of hazard
- Intrinsically safe (sub-)system
- All eliminated: Feasibility & cost?
- Certain types of hazard eliminated
- Direct use of hazard identification and analysis results

### Specific techniques: "Good SE & SSE"
- Component substitution
- Fault Tree Analysis
- No single point of failure
- Event Tree Analysis
- Simplification of building blocks
- Decoupling of system architecture
- Human errors/hazardous material elimination

### Component safety certification
- Link to testing/QA activities and software safety program (SSP) process

---

## Hazard Elimination (Continued)

### FTA derived
- Negating/altering logical conditions
- Critical component: Substitution
- Structural change?

### ETA derived
- Altering/forcing event sequences
- No single point of failure
- Rollback of feature possibility?

### FMEA/etc. derived
- Environmental control/influence
- Formal verification of component and/or system
- System Theoretic Accident Mode (STAMP) (Model 4)

---

## Hazard, Controllability, & Observability

Related to hazard resolution, particularly hazard reduction and control.

### Controllability
- Between any two system states
- Desirable/safe states: maintain
- Fail ⇒ action ⇒ safe (hazard control)
- **Controllability limits:**
  - System design/structure limit
  - Energy/capacity limit

### Observability
- Observation of system states (and failures)
- Basis for control

---

## Design for Controllability

### Maintain safe states
- Use built-in control
- Monitoring: observation implies control
- Multiple checks through monitoring
- Mostly in hazard reduction

### Enhancing control opportunities
- Incremental control: More control points
- Intermediate states: More observational points
  - Gives more control opportunities
- Decision aid: Easier/more control points
- Both in hazard reduction and especially in hazard control

---

## Hazard Reduction: Techniques

### Monitoring and checks

- Hardware checks: lowest level
- Code-level checks: assertions
- Audit checks: independent monitoring
- Supervisory checks: system/highest level

---

## Hazard Reduction: Techniques (Continued)

### Locks and barriers (passive)

- Lock-outs (preventing hazard)
- Lock-ins (maintaining safety conditions)
- Interlocks (correct order/combinations)
- Other barriers (extra capital/redundancy/etc.)

---

## Hazard Reduction: Techniques (Further)

---

## Hazard Resolution: SW Interlock

### Software used as safety interlock
- Software usage: Data/control/safety
- Example: Emergency shut-down software

### More stringent safety requirement
- Most software function safety-related
- Should not rely solely on software

### Therac-25 accident lessons
- Series of 1985–1987 radiation therapy accidents
- Massive overdoses of radiation to at least six patients
- Race Condition – Tech typed commands too quickly, safety mechanism bypassed
- Lacking hardware interlocks

---

## Hazard Resolution: HW Interlock

### Hardware/software interlock

**Limitation of s/w backups:**
- Diversity and independence problems

**Hardware backups and interlocks:**
- Different characteristics
- Different failure mechanisms
- More likely to be independent

**Passive/active safety devices**
- Combine the advantages implying safety increases

---

## Hazard Control

### Hazard control
- Detecting hazard, then control it
- Built-in control: by design
- **Change after detection:**
  - Passive limits, mostly outside the system
  - Active through control devices and sub-systems

### Specific techniques
- Limiting exposure; duration is reduced
- Isolation and containment
- Protection systems
- Fail-safe design

---

## Hazard Control: Techniques

### Internal system change
- Isolation of hazard event
- Containment around hazard event
- Fail-safe design, a passive approach

### System augmentation
- **Protection system (PS) added on:**
  - Hazard ⇒ PS action ⇒ safe
  - Shut-down or partial shut-down
  - Example; automatic coolant injection or pressure relief
- Controllability limit, done earlier
- **Partial solution may be necessary:**
  - Reduce the severity
  - Bring to a neighboring state

---

## Risk Resolution: Damage Reduction

---