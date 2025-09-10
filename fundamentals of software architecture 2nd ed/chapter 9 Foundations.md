# Chapter 9: Foundations

## TLDR: Architecture Foundation Concepts

| Concept | Description | When to Use |
|---------|-------------|-------------|
| **Technical Partitioning (Layered)** | Separate components by technical capabilities (MVC layers) | Clear technical separation needed, traditional enterprise apps |
| **Domain Partitioning (Modular)** | Separate components by business workflows/domains | Business-focused teams, preparing for microservices |
| **Client/Server** | Two-tier architecture with frontend and backend | Simple applications, clear UI/data separation |
| **Three-tier** | Database, application server, and frontend tiers | Enterprise applications, need for scalability |
| **Big Ball of Mud** | No real structure, everything coupled | Avoid - legacy or emergency situations only |

### Architecture Decision Matrix
- **Clear technical layers needed** → Use Technical Partitioning (Layered)
- **Business domain focus** → Use Domain Partitioning (Modular) 
- **Planning for microservices** → Use Domain Partitioning
- **Simple application** → Use Client/Server
- **Enterprise scale** → Use Three-tier

## Definitions

### Component Topology
An architectural style defines how components and their dependencies are organized.

### Physical Architecture
Often, the style dictates the type of physical architecture: either monolithic or distributed.

### Deployment
A system's granularity and its deployment frequency are often associated with its architectural style. Teams generally deploy monolithic architectures as a single deployment along with a single relational database.

### Communication Style
How components communicate with each other (REST APIs, Method calls, etc)

### Data Topology
Monolithic architectures tend to have a monolithic database, whereas distributed architectures sometimes separate data.

## Architecture Styles

### Big Ball of Mud
Big Ball of Mud might describe a simple scripting application with no real internal structure that has its event handlers wired directly to database calls.

**Problems:**
- Lack of structure
- Everything coupled to everything else
- Changes have hard-to-predict rippling side effects
- Developers spend time chasing bugs rather than building features

### Client/Server Architectures

#### Desktop and Database Server
Desktop applications in user interfaces like Windows, separating data into a separate database server. This architecture coincided with the appearance of standalone database servers that could connect through standard network protocols.

#### Browser and Web Server
A web browser connected to a web server (which, in turn, was connected to a database server).

#### Single-Page JavaScript Apps
JavaScript implementations in browsers. A family of client/server style applications emerged that resembles the original desktop variation, but with the rich client written in JavaScript in the browser, rather than as a desktop application.

### Three-tier Architecture
A database tier using an industrial-strength database server; an application tier managed by an application server; and a frontend coded in generated HTML and, increasingly, JavaScript. The three-tier architecture corresponded with network-level protocols such as Common Object Request Broker Architecture (CORBA) and Distributed Component Object Model (DCOM) to facilitate building distributed architectures.

## Processes

### Architecture Partitioning
Software can be partitioned into a layered system or modular approach.

![Layered vs Modular Architecture](images/layered%20vs%20modular%20architecture.png)

### Technical Partitioning (Layered Architecture)
Technical partitioning separates top-level components based on technical capabilities rather than domains. Ex: Model-View-Controller.

**Advantages:**
- Clearly separates customization code
- Aligns more closely to the layered architecture pattern

**Disadvantages:**
- Higher degree of global coupling
- Changes to Common or Local components affect all other components
- Developers may duplicate domain concepts in both Common and Local layers
- Typically higher coupling at the data level

### Domain Partitioning (Modular)
In Domain Driven Design, the architect identifies domains or workflows, independent and decoupled from each other. The microservices architecture style is based on this philosophy. Domain-partitioned architectures separate top-level components by workflows and/or domains.

**Advantages:**
- Modeled more closely on how the business functions rather than implementation details
- Easier to build cross-functional teams around domains
- Aligns more closely to modular monolith and microservices architecture styles
- Message flow matches the problem domain
- Easy to migrate data and components to a distributed architecture

**Disadvantages:**
- Customization code appears in multiple places

## Distributed Architecture Fallacies

### The Network Is Reliable
The more a system relies on the network (as microservices architectures notably do), the more potential it has to become unreliable.

### Latency Is Zero
When considering using any distributed architecture, particularly microservices, architects must know the latency average. For example, assuming 100ms latency per request, chaining service calls adds 1,000ms to the request! Knowing the 95th to 99th percentile latency is even more important than averages.

### Bandwidth Is Infinite
Once a system is broken apart into smaller deployment units in a distributed architecture, communication between services uses significant bandwidth.

**Example:** Service A calls Service B 2,000 times per second. If Service B returns 500KB when only 200 bytes are needed, this consumes 1GBps of bandwidth instead of 400Kbps.

### The Network Is Secure
Most architects get comfortable using VPNs, trusted networks, and firewalls, but the network is not secure.

### The Topology Never Changes
Architects assume that network topology is fixed and never changes. Network upgrades can invalidate latency assumptions, triggering timeouts and circuit breakers.

### There Is Only One Administrator
There are dozens of network administrators in a typical large company. This fallacy points to the complexity of distributed architecture and the coordination required.

### Transport Cost Is Zero
Distributed architectures cost significantly more than monolithic architectures, primarily due to increased needs for hardware, servers, gateways, firewalls, new subnets, and proxies.

### The Network Is Homogeneous
Most companies have multiple network-hardware vendors that don't always integrate seamlessly, creating an endless loop of confusion when dealing with networks.

### Versioning Is Easy
When services communicate through contracts, internal implementation changes require contract versioning. This seemingly simple decision leads to complex trade-offs.

### Compensating Updates Always Work
Compensating updates ensure that related services all update jointly, with reversal if they don't. However, what happens if the compensating update itself fails?

### Observability Is Optional
While logging is useful in monolithic architectures, it is critical in distributed architectures, which offer many communication failure modes that are hard to debug without comprehensive interaction logs.

---

**Note:** The perpetual advice to favor simple designs is in many ways a future-proofing strategy.