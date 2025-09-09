# Chapter 8: Component-Based Thinking

Overview

## Definitions

### Software Component
```mermaid
block-beta
    columns 3
    
    block:UI["User interface"]:9
        columns 3
        OP["Order placement"]
        OV["Order validation"] 
        OF["Order fulfillment"]
        OH["Order history"]:3
        IM["Inventory management"]
        CT["Customer tracking"]
        N["Notification"]
        RC["Returns and credits"]
        OS["Order shipment"]
        space
        space
        PP["Payment processing"]
    end
```
A piece of software that performs a business function. Requirements can be applied to logical components to define their responsibilities and behaviors that developers will implement.
### logical Architecture
```mermaid
flowchart TD
    User[👤 User] --> A[Component A]
    A --> B[Component B]
    A --> C[Component C]
    B --> DR1[(Data repository)]
    C --> DR2[(Data repository)]
    C --> D[Component D]
    
    style DR1 fill:#1e5091,color:#fff
    style DR2 fill:#1e5091,color:#fff
```
Structure of a system's logical components and the actors, external interfaces they interact with.
### Physical Architecture
```mermaid
flowchart TD
    Client[💻 Client/Computer] 
    
    Client --> ServiceA[Service A]
    Client --> ServiceB[Service B] 
    Client --> ServiceC[Service C]
    
    ServiceA --> DB1[(Database)]
    ServiceB --> DB1
    ServiceC --> DB1
    ServiceC --> Queue[📨 Message Queue]
    
    Queue --> ServiceD[Service D]
    ServiceD --> DB2[(Database)]
    
    ServiceA -.-> ServiceB

    style DB1 fill:#1e5091,color:#fff
    style DB2 fill:#1e5091,color:#fff
```
Structure of a system's code that implements the logic of the components.
### Component Coupling
When components communicate with each other, or when a change to one compo nent might impact other components, the components are said to be coupled together. The more coupled a system’s components are, the harder it is to maintain and test the system (see Figure 8-11). Therefore, it’s important to pay close attention to coupling.


```mermaid
flowchart LR
    A[Order Shipment] --> B[Customer Notification]
```
Components coupled because they are communicating

```mermaid
classDiagram
    class OrderPlacement {
    }
    
    class OrderShipment {
    }
    
    OrderPlacement *-- OrderShipment : creates
```
Components coupled because a change in one impacts the other, even though they aren't communicating

### Static Coupling
Occurs when components communicate synchronously with each other. Architects need to be concerned about two types of coupling: afferent and efferent.

- **Afferent Coupling**: The degree to which other components depend on a target component.
- **Efferent Coupling**: The degree to which a target component depends on other components.
### The Law of Demeter/loose coupling
A component or service should have limited knowledge of other components or services.

![Law of Demeter](images/law%20of%20demeter.png)

## Processes

### Creating logical architecture

Logical architecture describes the structure and behavior of the system, and the external objects the system interacts with. The process to create a logical architecure is:

- Identify the core components
- Assign responsibilities to core components
- refactor based on core system requirements


### Workflow Approach
A common approach architects use for identifying the initial core components of a logical architecture is the Workflow approach. Identify the workflow a user might take through the system and allocate components to each action.

```mermaid
flowchart TD
    start((start)) --> A
    subgraph user [user actions]
        A[User browses the catalog of items] --> B[User places an order]
        B --> C[User pays for the order]
        C --> D[Send user an email with order details]
    end
    
    %% Components serving each user action
    IB[Item Browser Service] --- A
    IB ~~~ OP
    OP[Order Placement Service] --- B
    OPay[Order Payment Service] --- C
    CN1[Customer Notification Service] --- D

    %% Style components as blue
    classDef componentStyle fill:#4A90E2,stroke:#2E5C8A,stroke-width:2px,color:#fff
    class IB,OP,OPay,CN1,OF,OS,CN2,OT componentStyle
```

### Actor/Action Approach

Another way architects identify initial core components is the Actor/Action approach. This approach is particularly useful when a system has multiple actors.
- Identify the major business logic performed
- Identify the actors and systems
- Identify the actions each actor and system can take
- Allocate the actions to the business logic

![Actor Approach](images/actor%20approach.png)