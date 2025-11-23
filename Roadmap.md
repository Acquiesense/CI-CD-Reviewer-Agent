# Version Roadmap

This project will be built in clear iterations. Each version reflects real capability growth.

## v1: CICD v1 (Minimum Agent Reviewer)
### What it includes
- Parse PR diffs for Terraform, Kubernetes YAML, Dockerfiles, and application code.
- Run a single LLM reasoning step to identify risky patterns.
- Basic OPA/Conftest policy checks on Terraform and Kubernetes files.
- Output a summarised review as PR comments.

### Purpose
- Establish the foundation.
- Understand diff parsing, policy scanning, and LLM integration.
- Produce a working CI/CD GitHub Action.

### Skills learned
- GitHub Actions
- Diff parsing
- Basic OPA/Conftest
- First LLM pipeline
- Dockerising tools


## v1.5: CICD v1.5 (Structured Multi-Agent Refactor)
### What it includes
- Split the reviewer into 4 focused agents:
  - Code Safety Agent
  - Terraform Agent
  - Kubernetes Agent
  - Dockerfile Agent
- Supervisor agent to coordinate tasks.
- Each agent has its own input, reasoning, and output block.
- More detailed policy enforcement.

### Purpose
- Move from “one brain” to a modular distributed design.
- Prepares groundwork for future real cluster/Terraform execution.

### Skills learned
- LangGraph or DSPy agent orchestration
- Multi-agent tool planning
- Modular design patterns for LLM systems


## v2: CICD v2 (Infra-Aware Reviewer)
### What it includes
- Terraform plan runner (init, plan, show-json).
- Kubernetes dry-run validation using a real cluster or kind cluster.
- Drift detection:
  - Terraform drift
  - Kubernetes spec drift
- Detection of deprecated API versions.
- Policy packs (security, networking, cost, best practices).

### Purpose
- Move from static code review to infra-aware validation.
- Demonstrate real-world infra reasoning.

### Skills learned
- Terraform automation
- Kubernetes dry-run and schema validation
- Drift detection strategies
- Policy design

## v3: CICD v3 (Security-Enhanced Reviewer)
### What it includes
- Supply-chain scanning:
  - Trivy
  - SBOM generation
- LLM interpretation of vulnerability reports.
- Combined infra + security + code risk scoring.
- Structured remediation plans.

### Purpose
- Combine DevSecOps + AI.
- Demonstrate security maturity.

### Skills learned
- Container scanning
- Vulnerability summarisation
- SBOM workflows

## v4: CICD v4 (Enterprise Aware: OpenShift Edition)
### What it includes
- Recognition of OpenShift resources:
  - Routes
  - Projects
  - BuildConfigs
  - ImageStreams
- Policy pack for OpenShift-specific security and networking constraints.

### Purpose
- Demonstrate awareness of enterprise Kubernetes ecosystems.
- Widen the tool’s applicability.

### Skills learned
- OpenShift architecture
- Enterprise-grade resource validation

## v5: CICD Platform (Full Autonomous Reviewer)
### What it includes
- Multi-stage agent pipeline with:
  - Supervisor agent
  - Infra agent
  - Security agent
  - Governance agent
  - Cost agent
- Dashboard UI showing:
  - PR score
  - Issues
  - Fix suggestions
  - Drift reports
  - Policy compliance
- Long-context project summary memory.
- Optional Slack/Teams integration.

### Purpose
- Transform from a script into a platform.
- End-to-end autonomous review pipeline.

### Skills learned
- Full-stack integration
- Platform thinking
- Deep agentic coordination
- Infra governance

## v6: Dashboard and General Compatibility Layer
### What it includes
- A minimal web dashboard that displays:
  -  PR issues
  -  Policy Violations
  -  Suggested Fixes.
- A unified compatibility layer so the reviewer can work with:
  - GitHub
  - GitLab
  - Bitbucket
  - Generic CI runners.
- Support for multiple manifest types beyond Terraform/Kubernetes/Docker, such as Helm charts and generic YAML.
- Optional API endpoint to trigger reviews manually or integrate with other tools.

### Purpose
- Provide a clean visual interface for understanding review results.
- Make the system usable outside GitHub Actions by supporting multiple CI providers.
- Move toward a production-ready platform instead of a single CI workflow.

### Skills learned
Not much but it'll make it prettier
