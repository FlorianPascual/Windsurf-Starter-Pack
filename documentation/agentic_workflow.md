An agentic workflow is a a software engineering workflow with IDE-integrated LLMs and external validation LLMs.
It helps LLM agents to follow a defined software engineering workflow in order to get better at designing, automating and developping an application.
The workflow is composed of several markdown files that are given to the agents to help them know exactly what to do.

Here is an example of a very good workflow that you can memorized and reuse.
This workflow is composed of the following files :

1 - tech_requirements.md
2 - dir_setup.md
3 - general_workflow.md
4 - project_init_guide.md
5 - readme_generation.md
6 - vcs_llm_workflow.md

Here are below the content of all those files :

1 - tech_requirements.md

# Defining Technical Requirements Guide

## Technical Requirements Components 🔍

### 1. System Constraints
```markdown
- Performance Requirements
  - Response time targets (e.g., API responses < 200ms)
  - Throughput expectations (e.g., 1000 requests/second)
  - Concurrent user capacity (e.g., 10,000 simultaneous users)

- Availability Requirements
  - Uptime target (e.g., 99.9%)
  - Maintenance windows
  - Recovery time objectives (RTO)
  - Recovery point objectives (RPO)

- Resource Limitations
  - Development machine specs
  - Production environment specs
  - Budget constraints for cloud services
```

### 2. Functional Requirements
```markdown
- Core Features
  - User authentication
  - Data processing capabilities
  - Integration requirements
  - Real-time requirements

- Data Requirements
  - Expected data volume
  - Data retention policies
  - Backup requirements
  - Data privacy needs
```

### 3. Security Requirements
```markdown
- Authentication needs
- Authorization levels
- Data encryption requirements
- Compliance requirements (GDPR, HIPAA, etc.)
```

## Requirements Template 📝

```markdown
# Technical Requirements Document

## 1. System Environment
### Development Environment
- Hardware Specifications
  - CPU: [specs]
  - RAM: [specs]
  - Storage: [specs]
- Operating System: [OS details]
- Development Tools: [IDE, etc.]

### Production Environment
- Deployment Platform: [Cloud/On-premise]
- Server Specifications
  - Compute: [specs]
  - Memory: [specs]
  - Storage: [specs]
- Network Requirements
  - Bandwidth: [specs]
  - Latency requirements: [specs]

## 2. Performance Requirements
- Response Time: [target]
- Throughput: [target]
- Concurrent Users: [number]
- Data Processing: [volume/time]

## 3. Scalability Requirements
- Growth Projections
  - User base: [numbers]
  - Data volume: [size]
  - Transaction volume: [numbers]
- Scaling Needs
  - Horizontal scaling capabilities
  - Vertical scaling limits

## 4. Security Requirements
- Authentication Method: [specify]
- Authorization Levels: [specify]
- Data Protection: [requirements]
- Compliance Needs: [standards]

## 5. Integration Requirements
- External Systems: [list]
- APIs: [specifications]
- Data Exchange Formats: [formats]
- Integration Frequency: [timing]

## 6. Data Requirements
- Storage Volume: [size]
- Data Types: [specify]
- Retention Policy: [duration]
- Backup Requirements: [frequency]

## 7. Operational Requirements
- Monitoring Needs
- Logging Requirements
- Maintenance Windows
- Support Requirements
```

## Example Requirements Document 📋

```markdown
# Technical Requirements Document

## 1. System Environment
### Development Environment
- Hardware Specifications
  - CPU: Apple M1 Pro
  - RAM: 16GB
  - Storage: 512GB SSD
- Operating System: macOS Monterey
- Development Tools: VS Code, Docker Desktop

### Production Environment
- Deployment Platform: AWS
- Server Specifications
  - Compute: t3.large instances
  - Memory: 8GB per instance
  - Storage: 100GB EBS volumes
- Network Requirements
  - Bandwidth: 1Gbps
  - Latency: <100ms

## 2. Performance Requirements
- Response Time: 95% of API requests under 200ms
- Throughput: 1000 requests/second
- Concurrent Users: 5000
- Data Processing: 1GB/hour

## 3. Scalability Requirements
- Growth Projections
  - User base: 100K users Year 1
  - Data volume: 5TB/year
  - Transaction volume: 10M/month
- Scaling Needs
  - Auto-scaling group: 2-10 instances
  - Database: Vertical scaling up to db.r6g.2xlarge

## 4. Security Requirements
- Authentication: JWT with OAuth2
- Authorization: RBAC with 4 role levels
- Data Protection: At-rest and in-transit encryption
- Compliance: GDPR, SOC2

## 5. Integration Requirements
- External Systems
  - Payment Gateway: Stripe
  - Email Service: SendGrid
  - Storage: AWS S3
- APIs: RESTful, OpenAPI 3.0
- Data Exchange: JSON
- Integration Frequency: Real-time

## 6. Data Requirements
- Storage Volume: 500GB initial
- Data Types: JSON, Binary files
- Retention: 7 years
- Backup: Daily incremental, weekly full

## 7. Operational Requirements
- Monitoring: CloudWatch metrics
- Logging: ELK stack
- Maintenance: Sundays 2-4 AM EST
- Support: 24/7 on-call rotation
```

## How to Define Requirements 🎯

1. **Start with Business Needs**
   ```markdown
   - What problem are you solving?
   - Who are your users?
   - What's your expected scale?
   - What's your budget?
   ```

2. **Define Performance Expectations**
   ```markdown
   - How fast should it be?
   - How many users?
   - How much data?
   - What's acceptable downtime?
   ```

3. **Consider Constraints**
   ```markdown
   - Development resources
   - Production environment
   - Budget limitations
   - Time constraints
   ```

4. **Security & Compliance**
   ```markdown
   - What data are you handling?
   - What regulations apply?
   - What security level needed?
   ```

## Prompt for Requirements Generation

```markdown
Based on the following project context:

Business Context:
[Describe your business case]

Scale Requirements:
- Expected users: [number]
- Data volume: [size]
- Transaction volume: [number]

Environment Details:
- Development: [specs]
- Production: [platform/specs]

Security Needs:
- Data sensitivity: [level]
- Compliance requirements: [standards]

Budget Constraints:
- Development budget: [amount]
- Operational budget: [amount]

Please generate a comprehensive technical requirements document following the template structure above, ensuring all requirements are:
- Specific and measurable
- Realistic within constraints
- Aligned with business needs
- Technically feasible
```

Remember:
- Technical requirements are about WHAT the system needs to do, not HOW it will do it
- They should be measurable and verifiable
- They form the basis for architecture decisions
- They should align with business goals and constraints

2 - dir_setup.md

# Project Documentation Structure & Organization

## Recommended Directory Structure 📁

```markdown
project_root/
├── project_specification/
│   ├── project_overview.md
│   ├── architecture.md
│   └── milestones/
│       ├── milestone_1/
│       │   ├── milestone_spec.md
│       │   └── features/
│       │       ├── feature_1/
│       │       │   ├── contract.md
│       │       │   ├── validation.md
│       │       │   └── integration.md
│       │       └── feature_2/
│       │           └── ...
│       └── milestone_2/
│           └── ...
├── implementations/
│   ├── milestone_1/
│   │   ├── project_1/
│   │   │   ├── specs/
│   │   │   │   ├── project_spec.md
│   │   │   │   └── features/
│   │   │   │       ├── auth_contract.md
│   │   │   │       └── user_contract.md
│   │   │   └── src/
│   │   └── project_2/
│   │       └── ...
│   └── milestone_2/
│       └── ...
└── docs/
    ├── templates/
    │   ├── feature_contract_template.md
    │   ├── project_spec_template.md
    │   └── validation_template.md
    └── guidelines/
        └── naming_conventions.md
```

## File Naming Conventions 📝

### 1. Milestone Level
```markdown
milestone_[number]_[short_name].md
Example: milestone_1_authentication.md
```

### 2. Project Level
```markdown
[project_name]_spec.md
Example: user_service_spec.md
```

### 3. Feature Contracts
```markdown
[feature_name]_contract.md
Example: jwt_auth_contract.md
```

### 4. Validation Documents
```markdown
[feature_name]_validation.md
Example: jwt_auth_validation.md
```

## LLM Reference Strategy 🔗

### 1. Context Loading

```markdown
Please load these specification files for context:

1. Project Overview:
[Copy content from project_specification/project_overview.md]

2. Current Milestone:
[Copy content from project_specification/milestones/milestone_1/milestone_spec.md]

3. Feature Contract:
[Copy content from implementations/milestone_1/project_1/specs/features/auth_contract.md]
```

### 2. Reference Management

#### Single Feature Implementation
```markdown
Working on: Authentication Feature
Contract Reference: implementations/milestone_1/project_1/specs/features/auth_contract.md

Please implement according to this contract:
[Paste relevant contract sections]
```

#### Multi-Feature Integration
```markdown
Integrating: Auth + User Features

Contracts:
1. Auth: [Paste key points]
2. User: [Paste key points]

Integration Requirements:
[Paste integration requirements]
```

## Document Templates 📄

### 1. Feature Contract Template
```markdown
# Feature: [Name]
Version: [x.y.z]
Last Updated: [YYYY-MM-DD]

## Interface Contract
### Input
- Type definitions
- Validation rules

### Output
- Return types
- Error states

## Dependencies
- List dependencies

## Validation Criteria
- Success conditions
- Test cases
```

### 2. Project Spec Template
```markdown
# Project: [Name]
Milestone: [Number]
Status: [Planning/In Progress/Complete]

## Overview
- Purpose
- Scope

## Features
- List features
- Link to contracts

## Integration Points
- System interfaces
- Dependencies
```

## LLM Interaction Examples 💬

### 1. Initial Load
```markdown
Please load the following project context:

1. Project Overview:
[project_specification/project_overview.md contents]

2. Current Milestone:
[project_specification/milestones/milestone_1/milestone_spec.md contents]

Please confirm you've processed these documents and are ready for feature-level work.
```

### 2. Feature Implementation
```markdown
Working on Feature: JWT Authentication
Reference Files:
1. Feature Contract: implementations/milestone_1/project_1/specs/features/jwt_auth_contract.md
[paste contract]

2. Integration Requirements: implementations/milestone_1/project_1/specs/features/integration.md
[paste relevant sections]

Please implement the JWT validation middleware according to these specifications.
```

### 3. Validation Check
```markdown
Validate implementation against:
1. Feature Contract: [paste relevant sections]
2. Test Cases: [paste test requirements]
3. Integration Points: [paste integration requirements]

Current Implementation:
[paste code]
```

## Best Practices 🎯

1. **Document References**
   - Use relative paths in documentation
   - Keep contracts atomic and focused
   - Version control documentation

2. **Context Management**
   - Load only relevant sections
   - Reference parent documents when needed
   - Keep feature contracts self-contained

3. **Organization Tips**
   - Group related features
   - Maintain clear hierarchy
   - Use consistent naming

4. **Version Control**
   - Track documentation changes
   - Link commits to specs
   - Update validation status

3 - general_workflow.md

# Contract-Based LLM Development Workflow

## Phase 1: Project Initialization 🎯

### Step 1: High-Level Project Spec Generation
Use a high-capability LLM (like Claude) with this prompt template:

```markdown
Please help me create a detailed project specification for the following project:

Project Description:
[Your prose description]

Generate:
1. Project Overview
2. Technical Requirements
3. System Architecture
4. Core Features List
5. Non-functional Requirements
6. Integration Points
7. Success Criteria

Format the output as a structured markdown document with clear sections and subsections.
```

### Step 2: Feature Breakdown
Use the same LLM to break down features:

```markdown
Based on this project specification:
[Paste project spec]

Please break this down into individual feature contracts. For each feature:
1. Input/Output Contracts
2. Dependencies
3. Integration Points
4. Success Criteria
5. Validation Steps

Format each feature as a separate markdown document.
```

## Phase 2: Feature Implementation Loop 🔄

### Step 1: Contract Generation
For each feature, use this prompt:

```markdown
Create a detailed technical contract for this feature:
[Paste feature description]

Generate:
1. Interface Definition
   - Input parameters
   - Output format
   - Error states
2. Validation Rules
   - Input constraints
   - Business rules
   - Edge cases
3. Test Scenarios
   - Happy path
   - Error cases
   - Edge cases
```

### Step 2: Implementation Workflow

#### A. Initial Implementation (IDE-integrated LLM)
```markdown
Implement the following contract:
[Paste contract]

Requirements:
1. Follow the exact interface specification
2. Implement input validation first
3. Add error handling as specified
4. Include inline documentation
5. Add type hints/annotations

Current codebase context:
[Relevant code snippets]
```

#### B. Validation Loop
For each implementation:

1. **Contract Compliance Check**
```markdown
Verify this implementation against the contract:
[Paste implementation]

Contract:
[Paste contract]

Check:
1. Interface compliance
2. Input validation
3. Error handling
4. Type safety
```

2. **Iteration Prompt (if needed)**
```markdown
The implementation violates these contract points:
[List violations]

Please modify only the affected components while maintaining:
1. Existing working functionality
2. Interface compliance
3. Error handling patterns
```

## Phase 3: Integration 🔗

### Step 1: Integration Contract
```markdown
Create an integration contract for:
Feature: [Feature name]
Existing Systems: [List systems]

Generate:
1. Integration points
2. Data flow
3. Error handling
4. Rollback procedures
```

### Step 2: Integration Implementation
```markdown
Implement the integration according to this contract:
[Paste integration contract]

Existing integration points:
[Paste relevant code]

Requirements:
1. Maintain existing interfaces
2. Add error handling
3. Include rollback logic
```

## Workflow Management Template 📋

### 1. Project Documentation Structure
```markdown
project/
├── specs/
│   ├── project_spec.md
│   └── features/
│       ├── feature1_contract.md
│       ├── feature2_contract.md
│       └── ...
├── implementations/
│   ├── feature1/
│   │   ├── contract.md
│   │   ├── implementation.md
│   │   └── validation.md
│   └── ...
└── integration/
    ├── contracts/
    └── implementations/
```

### 2. LLM Usage Guidelines

1. **Project-Level Planning (Claude/GPT-4)**
   - Project specification
   - Feature breakdown
   - Contract generation

2. **Implementation (IDE LLM)**
   - Code generation
   - Basic modifications
   - Simple fixes

3. **Contract Validation (Claude/GPT-4)**
   - Complex analysis
   - Architecture decisions
   - Integration planning

### 3. Context Management

1. **Essential Context per Prompt**
```markdown
ALWAYS INCLUDE:
1. Current contract
2. Immediate dependencies
3. Relevant error states

ROTATE AS NEEDED:
1. Implementation details
2. Test cases
3. Integration points
```

2. **Context Rotation Strategy**
- Keep contracts in separate files
- Reference by link/name
- Include only relevant sections

## Example Workflow

1. **Start with prose requirement:**
   ```
   "We need a user authentication system with JWT"
   ```

2. **Generate project spec** (Using Claude):
   ```markdown
   Please create a project specification for:
   [Paste requirement]
   ```

3. **Generate feature contracts** (Using Claude):
   ```markdown
   Based on this project spec:
   [Paste spec]
   Generate individual feature contracts
   ```

4. **Implementation loop** (IDE LLM):
   ```markdown
   Contract: [Paste current feature contract]
   Task: Implement the login endpoint
   Context: Express.js API
   ```

5. **Validation** (Claude):
   ```markdown
   Verify this implementation:
   [Paste code]
   Against this contract:
   [Paste contract]
   ```

## Key Success Factors 🎯

1. **Contract Clarity**
   - Explicit interfaces
   - Clear validation rules
   - Defined error states

2. **Context Management**
   - Rotate context efficiently
   - Keep contracts separate
   - Reference only needed parts

3. **LLM Selection**
   - Use powerful LLMs for planning
   - Use IDE LLMs for implementation
   - Use powerful LLMs for validation

4. **Documentation Structure**
   - Maintain clear hierarchy
   - Keep contracts accessible
   - Track validations

Would you like me to elaborate on any specific part or provide more detailed examples?

4 - project_init_guide.md

# Project Initialization

## 1. Project Overview File (`project_overview.md`)

### Template Structure
```markdown
# Project Overview

## 1. Project Information
- Project Name
- Version
- Last Updated
- Status
- Team/Owner

## 2. Business Context
- Problem Statement
- Business Objectives
- Success Criteria
- Key Stakeholders

## 3. Project Scope
- Core Features
- Feature Priority Matrix
- Out of Scope Items
- Dependencies

## 4. Timeline & Milestones
- Project Phases
- Key Deliverables
- Critical Deadlines
- Release Schedule

## 5. Resources & Constraints
- Team Resources
- Technical Requirements
- Budget Constraints
- Time Constraints

## 6. Risk Assessment
- Technical Risks
- Business Risks
- Mitigation Strategies
- Contingency Plans

## 7. Success Metrics
- KPIs
- Performance Metrics
- Quality Metrics
- Acceptance Criteria
```

### Prompt to Generate Project Overview
```markdown
Please create a comprehensive project overview document following this structure:

Project Context:
[Your project description]

Generate a detailed project overview document that includes:
1. Project Information
2. Business Context
3. Project Scope
4. Timeline & Milestones
5. Resources & Constraints
6. Risk Assessment
7. Success Metrics

Requirements:
- Be specific and quantifiable where possible
- Include clear success criteria
- Define measurable KPIs
- List concrete deliverables
- Identify key stakeholders
- Outline major risks and mitigation strategies

Format the output as a structured markdown document following the template above.
```

## 2. Architecture File (`architecture.md`)

### Template Structure
```markdown
# System Architecture

## 1. System Overview
- Architecture Style
- Design Principles
- System Context
- Key Constraints

## 2. Component Architecture
- Core Components
- Component Relationships
- Interface Definitions
- Data Flow

## 3. Technical Stack
- Programming Languages
- Frameworks
- Libraries
- Tools & Services

## 4. Data Architecture
- Data Models
- Storage Solutions
- Data Flow
- Data Security

## 5. Integration Architecture
- External Systems
- APIs
- Integration Points
- Authentication/Authorization

## 6. Deployment Architecture
- Infrastructure
- Deployment Strategy
- Scaling Approach
- Monitoring & Logging

## 7. Security Architecture
- Security Model
- Access Control
- Data Protection
- Security Protocols

## 8. Performance Architecture
- Performance Requirements
- Scalability Strategy
- Caching Strategy
- Load Handling

## 9. Development Architecture
- Development Environment
- Build Process
- Testing Strategy
- CI/CD Pipeline
```

### Prompt to Generate Architecture Document
```markdown
Please create a detailed system architecture document based on these requirements:

Project Context:
[Your project description]

Technical Requirements:
[Your technical requirements]

Generate a comprehensive architecture document that covers:
1. System Overview
2. Component Architecture
3. Technical Stack
4. Data Architecture
5. Integration Architecture
6. Deployment Architecture
7. Security Architecture
8. Performance Architecture
9. Development Architecture

Requirements:
- Focus on maintainability and scalability
- Include clear component relationships
- Define all integration points
- Specify security measures
- Detail performance considerations
- Outline development workflows

Format the output as a structured markdown document following the template above.
```

## 3. Usage Guidelines

1. **Initial Generation**
   - Use a powerful LLM (Claude/GPT-4) for initial document generation
   - Provide comprehensive project context
   - Review and refine generated content

2. **Document Maintenance**
   - Update documents when requirements change
   - Version control all documentation
   - Keep timestamps of last updates

3. **Integration with Development**
   - Reference documents in implementation tasks
   - Update based on technical discoveries
   - Maintain traceability to requirements

4. **Review Process**
   - Regular documentation reviews
   - Stakeholder sign-off
   - Change tracking
   - Version history

## 4. Best Practices

1. **Content**
   - Be specific and measurable
   - Use clear, concise language
   - Include diagrams where helpful
   - Maintain consistency across documents

2. **Structure**
   - Follow template hierarchy
   - Use consistent formatting
   - Include table of contents
   - Cross-reference related sections

3. **Maintenance**
   - Regular updates
   - Version control
   - Change logs
   - Review cycles

4. **Integration**
   - Link to related documents
   - Reference implementation details
   - Track dependencies
   - Maintain traceability

Would you like me to elaborate on any specific aspect of these documentation templates or provide more detailed examples?

5 - readme_generation.md

# README.md Generation Workflow

## Initial Project Context Prompt 📋

```markdown
# Project Documentation Request

Please generate a comprehensive README.md for my project based on the following context:

Project Overview:
[Paste relevant sections from project_overview.md]

Architecture Summary:
[Paste key points from architecture.md]

Technical Stack:
[List your main technologies]

Target Audience:
[Specify: developers, users, stakeholders]

Please structure the README to be clear, informative, and following modern best practices.
```

## README.md Template Structure 📝

```markdown
# Project Name

## Overview
- Brief description
- Key features
- Current status
- Live demo (if applicable)

## Quick Start
- Prerequisites
- Installation
- Basic usage
- Environment setup

## Documentation
- Architecture overview
- API documentation
- Configuration
- Development guidelines

## Project Structure
- Directory layout
- Key components
- Configuration files
- Documentation location

## Development
- Setup instructions
- Development environment
- Testing
- Contributing guidelines

## Deployment
- Deployment instructions
- Environment variables
- Production considerations
- Monitoring

## Support
- Issue reporting
- Contact information
- Community guidelines
- License
```

## Staged Generation Workflow 🔄

### Stage 1: Basic Information
```markdown
Generate the initial sections of a README.md with:

Context:
- Project Name: [name]
- Description: [description]
- Main Features: [features]
- Target Users: [users]

Focus on:
1. Project overview
2. Key features
3. Basic prerequisites
4. Quick start guide
```

### Stage 2: Technical Details
```markdown
Enhance the README with technical details:

Technical Context:
- Stack: [technologies]
- Architecture: [key points]
- Dependencies: [list]
- Development Requirements: [requirements]

Add sections for:
1. Development setup
2. Project structure
3. Configuration
4. API overview
```

### Stage 3: Deployment & Operations
```markdown
Add deployment and operational information:

Deployment Context:
- Environments: [list]
- Configuration: [details]
- Monitoring: [tools]
- Maintenance: [procedures]

Include:
1. Deployment instructions
2. Environment setup
3. Monitoring guidelines
4. Troubleshooting
```

### Stage 4: Community & Support
```markdown
Complete with community and support information:

Support Context:
- Contributing Guidelines: [details]
- Support Channels: [list]
- License: [type]
- Community Standards: [rules]

Add:
1. Contributing guide
2. Support information
3. License details
4. Community guidelines
```

## Review & Refinement Prompt 🔍

```markdown
Please review and enhance this README.md:

Current Content:
[Paste current README.md]

Evaluate and improve:
1. Clarity and completeness
2. Technical accuracy
3. Structure and organization
4. Documentation links
5. Examples and code snippets

Add or enhance:
1. Badges (build status, version, etc.)
2. Visual elements (diagrams, screenshots)
3. Troubleshooting section
4. FAQ section
```

## Best Practices Checklist ✅

1. **Content Quality**
   - Clear and concise language
   - Logical flow of information
   - Complete setup instructions
   - Updated contact information

2. **Technical Accuracy**
   - Verified installation steps
   - Correct dependency versions
   - Valid configuration examples
   - Tested commands

3. **Visual Elements**
   - Project logo/banner
   - Status badges
   - Architecture diagrams
   - Screenshots

4. **Maintenance**
   - Version information
   - Last update date
   - Changelog link
   - Roadmap

## Example Final Validation Prompt 🎯

```markdown
Please validate this README.md against these criteria:

1. Completeness
- All sections present
- No missing information
- Clear instructions
- Proper links

2. Technical Accuracy
- Installation steps verified
- Dependencies correct
- Commands tested
- Configurations valid

3. User Experience
- Clear navigation
- Logical flow
- Helpful examples
- Troubleshooting guidance

4. Maintenance
- Version info present
- Update date included
- Contact details valid
- Support channels listed

Please suggest any improvements or missing elements.
```

## Maintenance Update Prompt 🔄

```markdown
Please update this README.md with:

New Changes:
- [List new features/changes]
- [Updated requirements]
- [New dependencies]
- [Changed configurations]

Update:
1. Version information
2. Installation instructions
3. Configuration details
4. Feature documentation

Ensure all existing sections remain accurate and update the last modified date.
```

6 - vcs_llm_workflow.md

# Version Control Integration in LLM Development Workflow

## Git Strategy 🔄

### 1. Commit Structure

#### Atomic Commits
- One logical change per commit
- Tied to contract validation points
- Clear, traceable history

#### When to Commit

1. **Contract Implementation Milestones**
   - Initial interface implementation
   - Input validation complete
   - Error handling added
   - Tests implemented
   - Contract fully satisfied

2. **Integration Points**
   - Dependencies integrated
   - API endpoints connected
   - Database schemas updated

### 2. Commit Message Template

```markdown
<type>(<scope>): <summary>

<body>

Contract: <contract-reference>
Validation: <validation-status>
Breaking Changes: <yes/no>

Related Issues: <issue-references>
```

Where:
- `type`: feat|fix|docs|style|refactor|test|chore
- `scope`: feature-name|module|component
- `summary`: imperative mood, no period
- `body`: detailed changes
- `contract-reference`: link/reference to relevant contract
- `validation-status`: passed|partial|pending

### 3. LLM Git Integration

#### IDE LLM Should:
✅ **Suggest commit points**
```markdown
Recommendation: Changes ready for commit
- Interface implementation complete
- Input validation added
- Tests passing
```

✅ **Generate commit messages**
```markdown
Suggested commit message:
feat(auth): implement JWT validation middleware

- Add token verification
- Implement expiry checking
- Add role validation

Contract: auth/jwt-validation.md
Validation: passed
Breaking Changes: no
```

❌ **Should NOT:**
- Execute git commands
- Push changes
- Merge branches
- Modify git history

### 4. Developer Responsibilities

1. **Review Changes**
   - Verify contract compliance
   - Check for unintended modifications
   - Validate test coverage

2. **Execute Git Commands**
   - Commit changes manually
   - Push to remote
   - Manage branches
   - Handle merges

### 5. Git Workflow Integration

```markdown
Feature Development Loop:

1. Create feature branch
   ```bash
   git checkout -b feat/auth-jwt
   ```

2. Implementation Cycles:
   - LLM implements contract point
   - Developer reviews changes
   - LLM suggests commit message
   - Developer commits:
     ```bash
     git add .
     git commit -m "feat(auth): implement JWT validation"
     ```

3. Push Changes:
   - Developer reviews branch
   - Developer pushes:
     ```bash
     git push origin feat/auth-jwt
     ```


### 6. Version Control Best Practices

#### Branch Strategy
```markdown
main
├── develop
│   ├── feature/auth-jwt
│   ├── feature/user-profile
│   └── fix/login-validation
└── release/v1.0
```

#### Commit Guidelines
1. **Frequency**
   - Commit after each contract validation point
   - Keep changes atomic and focused
   - Include relevant tests

2. **Message Quality**
   ```markdown
   ✅ Good:
   feat(auth): implement JWT validation middleware
   
   - Add token verification with RS256
   - Implement 15min token expiry
   - Add role-based validation
   
   Contract: auth/jwt-validation.md
   Validation: passed

   ❌ Bad:
   updated auth code
   ```

3. **Contract Traceability**
   - Reference contract in commit message
   - Link to validation results
   - Note any deviations

### 7. Integration with Workflow

```markdown
Implementation Phase:
1. Create feature branch
2. [LLM] Implement contract point
3. [Developer] Review changes
4. [LLM] Suggest commit message
5. [Developer] Commit changes
6. Repeat until contract satisfied
7. [Developer] Push changes
8. Create PR

Validation Phase:
1. [LLM] Review PR changes
2. [Developer] Address feedback
3. [Developer] Merge PR
```

### 8. Example Workflow

```markdown
1. Start Feature:
   ```bash
   git checkout -b feat/auth-jwt
   ```

2. LLM Implementation:
   "I've implemented the JWT validation middleware according to contract."

3. LLM Commit Suggestion:
   ```markdown
   Suggested commit:
   feat(auth): implement JWT validation

   - Add middleware setup
   - Implement token verification
   - Add error handling

   Contract: auth/jwt-validation.md
   Validation: passed
   ```

4. Developer Review & Commit:
   ```bash
   git add src/middleware/auth.js
   git add tests/middleware/auth.test.js
   git commit -m "..."
   ```

5. Continue Development Loop

6. Final Push:
   ```bash
   git push origin feat/auth-jwt
   ```


### 9. Version Control Tips

1. **Keep Contract References**
   - Link contracts in commits
   - Track validation status
   - Document deviations

2. **Maintain Clean History**
   - Use meaningful commit messages
   - Keep changes atomic
   - Reference issues/tickets

3. **Review Before Commit**
   - Check for unintended changes
   - Verify contract compliance
   - Ensure test coverage

4. **Push Strategy**
   - Push when feature milestone complete
   - Push after significant changes
   - Push before end of day

Remember: Version control is the developer's responsibility. While LLMs can suggest commit points and messages, all git operations should be manually reviewed and executed by the developer to maintain code quality and history integrity.