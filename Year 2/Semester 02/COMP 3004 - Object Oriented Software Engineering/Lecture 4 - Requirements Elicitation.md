
#### Elicitation
**Requirements elicitation** is the process of **discovering, understanding, and documenting what a system is supposed to do** and the constraints under which it must operate.



---
# Requirements

#### Functional Requirements
**Functional requirements describe _what the system must do_.**
They define **system behaviour**, services, and interactions.

**Characteristics**
- Describe **features or functions**
- Often expressed as **actions**
- Can usually be tested with “does it do X?”

Functional requirements often translate into:
- Classes
- Methods
- Interactions between objects


#### Non-Functional Requirements
**Non-functional requirements describe _how well_ the system performs its functions.**
They are about **quality attributes**, not features.

**Common Categories**
- **Performance** – speed, response time
- **Security** – authentication, authorization
- **Usability** – ease of use, accessibility
- **Reliability** – uptime, fault tolerance
- **Scalability** – handling growth
- **Maintainability** – ease of modification
- **Portability** – platforms supported



---
# Feasibility Study

A **feasibility study** answers the question:
> _Should we even build this system?_

It’s done **before** committing major time or money.

#### Main Types of Feasibility
 1. **Technical Feasibility**
	- Do we have the technology?
	- Do we have the skills?
	- Can it be built with current tools?

	Example:
	- “Can we realistically implement real-time video processing?”

2. **Economic Feasibility**
	- Is it worth the cost?
	- Do benefits outweigh expenses?

	Example:
	- Development cost vs. expected revenue or savings

3. **Operational Feasibility**
	- Will users actually use it?
	- Does it fit into existing workflows?

	Example:
	- “Will staff accept a new system replacing manual processes?”

4. **Schedule Feasibility**
	- Can it be completed on time?
	
	Example:
	- “Can we deliver before the semester ends?”

#### Outcome
- Go / No-go decision
- High-level risk assessment



---
# Requirement Specification

Where requirements become **formal, structured, and documented**.

#### Purpose
- Create a **single source of truth**
- Prevent misunderstandings
- Serve as a contract between stakeholders and developers

#### Typical Contents
- Introduction and scope
- Definitions and terminology
- Functional requirements
- Non-functional requirements
- Constraints
- Assumptions
- System interfaces

#### Good Requirements Are:
- **Clear** – unambiguous
- **Complete** – nothing important missing
- **Consistent** – no contradictions
- **Verifiable** – testable
- **Traceable** – linked to sources

#### Example Requirement (Well-Written)
> “The system shall allow registered users to reset their password via email verification within 5 minutes.”



---
# Traceability

**Requirements traceability** is about tracking requirements throughout the project lifecycle.

#### Core Question
> _Where did this requirement come from, and what does it affect?_

#### Types of Traceability
**Forward Traceability**
- Requirement → design → code → tests
- Ensures every requirement is implemented

**Backward Traceability**
- Feature/test → requirement
- Ensures nothing extra is built

#### Tools
- Traceability matrices
- Requirement IDs
- Issue trackers


Example:

|Requirement ID|Design Module|Code|Test Case|
|---|---|---|---|
|FR-12|AuthService|login()|TC-07|


---
# Requirement Validation

**Validation ensures the requirements are the _right_ requirements.**

This answers:
> _Are we building the correct system?_

#### Validation Techniques
- Reviews and walkthroughs
- Stakeholder meetings
- Prototypes
- Use-case simulations
- Acceptance criteria checks

#### Common Problems Found
- Missing requirements
- Ambiguous wording
- Conflicting requirements
- Unrealistic constraints

#### Characteristics
completeness
consistency
clarity
correctness
realism
verifiability
traceability

