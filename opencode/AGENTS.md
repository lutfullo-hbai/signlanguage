# AGENTS.md

# Global Engineering Constitution

**Version:** 1.0.0
**Status:** Mandatory
**Scope:** Entire repository
**Authority:** Highest project-level engineering policy
**Applies To:** All AI agents, developers, automation, CI/CD pipelines, and engineering workflows

---

## 1. Purpose

This document defines the global engineering standards, architectural principles, coding rules, development workflow, quality requirements, security requirements, and operational constraints for this project.

Every agent operating inside this repository MUST follow this document.

Individual agent instructions MAY extend these rules but MUST NOT contradict them.

If an individual agent instruction conflicts with this document, this document takes precedence.

---

# 2. Core Engineering Principles

The project MUST follow these principles:

1. **Correctness over speed**
2. **Clarity over cleverness**
3. **Simplicity over unnecessary abstraction**
4. **Maintainability over short-term convenience**
5. **Explicitness over hidden behavior**
6. **Loose coupling**
7. **High cohesion**
8. **Separation of concerns**
9. **Single Responsibility**
10. **Dependency inversion**
11. **Testability**
12. **Observability**
13. **Security by design**
14. **Failure-aware design**
15. **Automation where it improves reliability**
16. **Documentation of important decisions**
17. **Backward compatibility where required**
18. **Incremental and reversible changes whenever possible**

No agent may sacrifice long-term system quality merely to complete a task faster.

---

# 3. Engineering Philosophy

The system MUST be designed as a professional production-grade software system.

Agents MUST NOT treat the repository as a temporary prototype unless the project explicitly defines a prototype phase.

The following mindset is mandatory:

> Build the simplest system that correctly satisfies the requirements while preserving a clear path toward future growth.

Avoid both extremes:

* under-engineering
* premature over-engineering

Every architectural complexity MUST have a reason.

---

# 4. Requirement First

No implementation should begin before understanding the requirement.

For every non-trivial task, the responsible agent MUST identify:

* What problem is being solved?
* Who is the consumer?
* What are the inputs?
* What are the outputs?
* What are the constraints?
* What are the expected failure cases?
* What are the security implications?
* What are the performance requirements?
* What are the dependencies?
* What existing architecture is affected?

If requirements are ambiguous and the ambiguity materially affects implementation, the agent MUST escalate to the Orchestrator or request clarification.

Agents MUST NOT silently invent important business requirements.

---

# 5. Architecture Before Implementation

Non-trivial features MUST have an architectural plan before implementation.

The plan SHOULD define:

* affected components
* dependencies
* interfaces
* data flow
* API contracts
* database changes
* security considerations
* testing strategy
* deployment implications
* rollback considerations

Architecture decisions MUST be documented when they introduce meaningful long-term consequences.

Use Architecture Decision Records (ADR) for significant decisions.

Example:

```text
docs/
└── architecture/
    ├── ADR-001-database-choice.md
    ├── ADR-002-authentication-strategy.md
    └── ADR-003-caching-strategy.md
```

---

# 6. System Design Principles

The system MUST be designed with the following principles:

## 6.1 Scalability

Agents MUST identify potential scaling bottlenecks.

Consider:

* CPU
* memory
* network
* database
* storage
* external APIs
* queues
* caches
* concurrency
* traffic patterns

Do not introduce distributed systems unless the requirements justify them.

---

## 6.2 Reliability

Critical operations MUST consider:

* timeouts
* retries
* idempotency
* graceful failure
* dependency failures
* partial failures
* recovery
* health checks

Failures MUST be explicit and observable.

---

## 6.3 Availability

Critical services SHOULD avoid unnecessary single points of failure.

Where high availability is required, architecture MUST explicitly define:

* failure domains
* redundancy
* health checking
* recovery strategy
* data consistency requirements

---

## 6.4 Performance

Performance optimization MUST be evidence-driven.

Agents MUST NOT introduce complicated optimizations without a measurable reason.

Preferred order:

```text
Correctness
    ↓
Clarity
    ↓
Measurement
    ↓
Optimization
```

Never optimize based solely on assumptions.

---

# 7. Clean Code Standards

All production code MUST follow Clean Code principles.

## 7.1 Naming

Names MUST clearly communicate intent.

Avoid:

```text
x
tmp
data
obj
foo
bar
manager
helper
util
```

unless their meaning is genuinely obvious from context.

Prefer:

```text
user_repository
payment_transaction
authentication_service
calculate_order_total
```

Names MUST reflect domain meaning.

---

# 8. Functions

Functions SHOULD:

* do one logical thing
* be small enough to understand easily
* have meaningful names
* minimize side effects
* avoid excessive parameters
* avoid hidden dependencies

A function MUST NOT become a dumping ground for unrelated responsibilities.

---

# 9. Classes and Modules

Classes and modules MUST have clear responsibilities.

Avoid:

* God classes
* God modules
* massive service classes
* unrelated utility collections
* circular dependencies

High-level architecture MUST remain understandable without reading every implementation detail.

---

# 10. SOLID

Where applicable, code SHOULD follow:

* Single Responsibility Principle
* Open/Closed Principle
* Liskov Substitution Principle
* Interface Segregation Principle
* Dependency Inversion Principle

SOLID MUST NOT be applied mechanically.

Do not introduce abstractions merely to demonstrate SOLID.

---

# 11. DRY

Avoid unnecessary duplication.

However:

> Duplication is sometimes preferable to a wrong abstraction.

Do NOT create abstractions merely because two pieces of code currently look similar.

Abstract when the underlying behavior or concept is genuinely shared.

---

# 12. KISS

Prefer the simplest solution that satisfies the requirements.

Avoid:

* unnecessary frameworks
* unnecessary services
* unnecessary design patterns
* unnecessary abstractions
* unnecessary dependencies
* unnecessary distributed architecture

Complexity MUST be justified.

---

# 13. YAGNI

Do not implement functionality that is not currently required unless it is necessary for architecture, security, reliability, or future compatibility.

Do not build speculative features.

---

# 14. Separation of Concerns

Responsibilities MUST remain separated.

Typical boundaries include:

```text
Presentation
    ↓
Application
    ↓
Domain
    ↓
Infrastructure
```

The exact architecture MAY vary by project.

The important rule is:

> Business logic MUST NOT become tightly coupled to infrastructure details.

---

# 15. Dependency Rules

Dependencies MUST point in a controlled direction.

High-level business rules SHOULD NOT depend directly on:

* databases
* HTTP frameworks
* UI frameworks
* cloud providers
* external service SDKs

where doing so would unnecessarily couple the domain to infrastructure.

Dependency inversion SHOULD be used where appropriate.

---

# 16. API-First Principle

APIs MUST have explicit contracts.

API design SHOULD define:

* endpoints
* methods
* request schemas
* response schemas
* status codes
* authentication
* authorization
* validation
* error formats
* versioning strategy

Frontend and backend MUST NOT depend on undocumented assumptions.

When practical, API contracts SHOULD be machine-readable.

Example:

```text
OpenAPI
JSON Schema
Protocol Buffers
```

---

# 17. Database Standards

Database design MUST be intentional.

Agents MUST consider:

* schema integrity
* relationships
* indexes
* constraints
* transactions
* migrations
* consistency
* concurrency
* query performance
* backup/recovery requirements

Database changes MUST be version controlled.

Manual production schema modifications SHOULD be avoided.

---

# 18. Configuration

Configuration MUST be separated from application code.

Environment-specific values MUST NOT be hardcoded.

Examples include:

* database URLs
* API keys
* secrets
* credentials
* service endpoints
* feature configuration

Never commit secrets to source control.

Use environment variables or an approved secret-management system.

---

# 19. Dependencies

Every dependency MUST have a reason.

Before introducing a new dependency, the responsible agent SHOULD evaluate:

* necessity
* maintenance status
* security
* license
* community adoption
* compatibility
* performance
* project complexity

Avoid dependency bloat.

Unused dependencies MUST be removed.

---

# 20. Twelve-Factor / Cloud-Native Principles

Where applicable, services SHOULD follow cloud-native principles:

* explicit dependencies
* configuration through environment
* backing services treated as resources
* build/release/run separation
* stateless processes
* disposable processes
* externally managed logs
* development/production parity
* explicit concurrency
* independent service processes
* fast startup and graceful shutdown
* telemetry
* automation
* secure authentication and authorization

The exact implementation MAY differ according to infrastructure.

---

# 21. Statelessness

Application processes SHOULD remain stateless whenever practical.

Persistent state SHOULD be stored in appropriate backing services.

Do not rely on:

* local filesystem state
* process memory
* local session state

for data that must survive process restart or scaling.

---

# 22. Logging

Logs MUST provide useful operational information.

Logs SHOULD include:

* timestamp
* severity
* service/component
* event
* relevant correlation/request ID

Sensitive information MUST NOT be logged.

Never log:

* passwords
* access tokens
* API keys
* secrets
* private credentials

---

# 23. Observability

Production systems SHOULD provide:

* logs
* metrics
* traces where appropriate
* health checks
* error monitoring

Critical operations SHOULD be observable.

An agent MUST consider observability when introducing a new service or critical workflow.

---

# 24. Security

Security is a mandatory requirement.

Agents MUST follow:

* least privilege
* secure defaults
* input validation
* output validation
* authentication
* authorization
* secret protection
* dependency security
* safe error handling
* secure communication

Never trust user input.

Never assume external services are safe or reliable.

---

# 25. Error Handling

Errors MUST be handled deliberately.

Do not:

* silently ignore exceptions
* catch errors without reason
* return misleading success responses
* expose internal stack traces to users
* hide infrastructure failures

Errors SHOULD be:

```text
Detected
→ Classified
→ Logged/Observed
→ Handled
→ Communicated appropriately
```

---

# 26. Testing

Every meaningful feature MUST have appropriate tests.

Testing SHOULD exist at multiple levels:

```text
Unit Tests
    ↓
Integration Tests
    ↓
API Tests
    ↓
End-to-End Tests
```

Not every feature requires every level, but the responsible agent MUST choose the appropriate level intentionally.

Tests MUST verify behavior, not implementation details whenever practical.

---

# 27. Test Quality

Tests MUST be:

* deterministic
* isolated where appropriate
* readable
* maintainable
* meaningful

Avoid tests that pass while providing little confidence.

A large test count does NOT automatically mean high quality.

---

# 28. Code Review

No significant production change should be considered complete without review.

Review MUST consider:

### Correctness

Does it solve the actual problem?

### Architecture

Does it fit the system?

### Maintainability

Can another engineer understand it?

### Security

Does it introduce vulnerabilities?

### Performance

Does it introduce unnecessary bottlenecks?

### Testing

Is behavior sufficiently tested?

### Operational impact

Can it be deployed and observed safely?

---

# 29. Git Standards

Git history SHOULD communicate meaningful engineering decisions.

Commits SHOULD be:

* focused
* atomic where practical
* descriptive
* logically grouped

Avoid massive unrelated commits.

Do not mix:

```text
feature implementation
+
unrelated refactoring
+
formatting
+
dependency upgrades
```

unless there is a clear reason.

---

# 30. Branching

The project SHOULD use a consistent branching strategy.

Agents MUST NOT create arbitrary long-lived branches without reason.

Feature work SHOULD remain isolated until validated.

---

# 31. Change Management

Before modifying an existing architecture, the agent MUST determine:

1. What currently depends on it?
2. What behavior could change?
3. What APIs could break?
4. What data could be affected?
5. What tests must change?
6. Is migration required?
7. Is rollback possible?

Breaking changes MUST be explicitly identified.

---

# 32. Backward Compatibility

Existing public contracts SHOULD remain compatible unless a breaking change is explicitly approved.

Breaking changes MUST include:

* affected consumers
* migration strategy
* versioning strategy where applicable
* documentation
* testing

---

# 33. Documentation

Documentation MUST exist for important system behavior.

At minimum, projects SHOULD maintain:

```text
README.md
ARCHITECTURE.md
API.md
CONTRIBUTING.md
docs/
```

Important architectural decisions MUST be documented.

Documentation MUST describe reality, not intended future behavior.

---

# 34. Agent Rules

Every AI agent MUST:

1. Read `AGENTS.md` before performing work.
2. Understand its assigned role.
3. Inspect existing code before modifying it.
4. Follow existing architecture unless explicitly authorized to change it.
5. Avoid unnecessary modifications.
6. Avoid destructive operations.
7. Validate its work.
8. Report important assumptions.
9. Report failures honestly.
10. Never claim success without verification.

---

# 35. Agent Boundaries

An agent MUST NOT perform work outside its assigned responsibility unless:

* explicitly authorized by the Orchestrator
* required for a necessary dependency
* required to prevent a critical failure

Agents MUST escalate architectural conflicts.

---

# 36. No Silent Architecture Changes

An agent MUST NOT silently:

* change database architecture
* change public APIs
* introduce new infrastructure
* change authentication strategy
* change service boundaries
* replace major dependencies
* introduce distributed systems

Such changes require architectural review.

---

# 37. Existing Code First

Before creating new code, agents MUST inspect:

* existing implementations
* reusable abstractions
* existing services
* existing utilities
* existing tests
* existing API contracts
* existing architecture documentation

Do not duplicate functionality that already exists.

---

# 38. Minimal Change Principle

Prefer the smallest change that correctly solves the problem.

Do not modify unrelated files.

Do not refactor unrelated code during feature implementation unless the refactoring is necessary.

---

# 39. No Fake Completion

An agent MUST NOT report:

```text
Implemented
Fixed
Tested
Completed
Production-ready
```

unless the corresponding claim has actually been verified.

If something could not be verified, explicitly state:

```text
NOT VERIFIED
```

and explain why.

---

# 40. Definition of Done

A task is considered complete only when applicable conditions are satisfied:

* [ ] Requirements understood
* [ ] Architecture considered
* [ ] Implementation completed
* [ ] Code follows project standards
* [ ] Tests added or updated
* [ ] Tests executed
* [ ] Security implications reviewed
* [ ] API contracts updated if necessary
* [ ] Database migrations created if necessary
* [ ] Documentation updated if necessary
* [ ] No unrelated changes introduced
* [ ] Final result verified

---

# 41. Agent Communication

Agents MUST communicate using structured information.

When handing work to another agent, provide:

```text
Task
Context
Changes
Dependencies
Assumptions
Known Risks
Files Affected
Validation Performed
Remaining Work
```

Do not rely on implicit context.

---

# 42. Decision Authority

Authority hierarchy:

```text
Project Requirements
        ↓
Global Engineering Constitution
        ↓
Architecture Decisions
        ↓
Agent Role Rules
        ↓
Implementation Details
```

Lower-level decisions MUST NOT contradict higher-level decisions.

---

# 43. Conflict Resolution

When agents disagree:

1. Check project requirements.
2. Check this constitution.
3. Check existing architecture.
4. Check ADRs.
5. Evaluate engineering trade-offs.
6. Escalate to the Orchestrator.
7. Record the final decision if significant.

Agents MUST NOT resolve major architectural conflicts through silent assumptions.

---

# 44. Quality Gates

A feature SHOULD pass the following gates:

```text
Requirement Gate
      ↓
Architecture Gate
      ↓
Implementation Gate
      ↓
Test Gate
      ↓
Code Quality Gate
      ↓
Security Gate
      ↓
Operational Gate
      ↓
Documentation Gate
      ↓
Release
```

Failure at a critical gate SHOULD block release.

---

# 45. Production Readiness

Before production deployment, the system SHOULD have:

* validated configuration
* secure secrets management
* health checks
* logging
* monitoring
* error handling
* backups where required
* rollback strategy
* deployment procedure
* tested critical paths
* documented operational behavior

---

# 46. Technology Neutrality

This constitution is technology-independent.

Specific frameworks, languages, databases, cloud providers, and tools MUST be defined elsewhere.

Agents MUST NOT assume:

* a specific programming language
* a specific database
* a specific cloud provider
* a specific frontend framework
* a specific deployment platform

unless the project configuration explicitly defines them.

---

# 47. Source of Truth

The repository itself is the primary source of truth.

Agents MUST prioritize:

1. Current project requirements
2. Current architecture documentation
3. ADRs
4. Existing tested behavior
5. Global engineering constitution
6. Agent-specific instructions
7. External assumptions

When documentation conflicts with tested reality, the discrepancy MUST be reported.

---

# 48. Engineering Trade-Offs

There is no universally perfect architecture.

Every major architectural decision SHOULD consider:

```text
Complexity
Cost
Performance
Reliability
Scalability
Security
Maintainability
Developer Experience
Operational Burden
```

The chosen solution MUST be justified by the actual project requirements.

---

# 49. Anti-Patterns

Agents MUST actively avoid:

* God objects
* God services
* spaghetti code
* circular dependencies
* hidden global state
* magic numbers
* magic strings
* duplicated business logic
* premature optimization
* premature abstraction
* unnecessary microservices
* unnecessary dependencies
* undocumented breaking changes
* hardcoded secrets
* silent failures
* untested critical logic
* dead code
* abandoned TODOs without ownership

---

# 50. Final Engineering Rule

The ultimate goal is not:

> Write more code.

The goal is:

> Build a correct, understandable, secure, testable, observable, maintainable, and evolvable system with the minimum justified complexity.

Every agent is responsible for protecting this principle.

---

# 51. Mandatory Agent Completion Report

At the end of every significant task, the responsible agent MUST provide:

```text
## Task
<what was requested>

## Completed
<what was implemented>

## Files Changed
<list>

## Architecture Impact
<none / description>

## Tests
<tests executed>

## Validation
<verification performed>

## Risks
<known risks>

## Assumptions
<assumptions made>

## Not Verified
<anything that could not be verified>

## Remaining Work
<any remaining work>
```

---

# 52. Final Authority

This document is the global engineering constitution of the repository.

All agents MUST treat it as mandatory policy.

Individual agent instructions may specialize these rules but MUST NOT weaken or contradict them without an explicit architecture decision.

**End of Global Engineering Constitution.**
