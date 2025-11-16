# CI/CD AI Reviewer

## What is it?
An autonomous agent that reviews pull requests, checks security and infrastructure changes, and generates actionable remediation suggestions. It basically keeps me in check when I binge code.

Built with Python, Docker, Kubernetes, Terraform, OPA/Conftest, and GitHub Actions.

## Key Features

- Natural language analysis of pull requests (Terraform, Kubernetes, Dockerfiles, Python/JS)

- Automated detection of misconfigurations, security risks, and policy violations

- OPA/Conftest policy engine for infra best-practice enforcement

- Inline review comments with suggested fixes

- Pluggable agent pipeline for custom workflows

## How It Works

1. GitHub Action triggers on PR open or update.

2. Action passes PR diff → containerized agent.

3. Agent parses diffs and runs:

  - LLM reasoning

  - Policy validation (OPA/Conftest)

4. Agent generates review comments + recommendations.

5. GitHub bot posts results directly to the PR.

## Architecture

The system has four main components:

1. Diff Collector
Extracts changes from pull requests and converts them into structured diff blocks for Terraform, Kubernetes YAML, Dockerfiles, and application code.

2. Policy Engine
Runs OPA and Conftest rules against Terraform files, Kubernetes manifests, and Dockerfiles to detect violations in security, networking, and resource configuration.

3. LLM Reasoner
Uses an agent loop to interpret diffs, merge policy results, generate explanations, and propose code fixes. Handles Terraform resources, Kubernetes specifications, and container instructions.

4. CI Integration Layer
A Dockerized runner invoked by GitHub Actions. It receives diffs, calls the agent, and posts review comments back to the pull request.

Data flow:
1. PR event
2. Diff Collector
3. Policy Engine
4. LLM Reasoner
5. CI Integration Layer
6. GitHub Review

## Local Setup
git clone https://github.com/<Acquiesense>/CI-CD-Reviewer-Agent

cd CI-CD-Reviewer-Agent

pip install -r requirements.txt

python agent/analyzer.py --diff tests/sample_diffs/terraform.diff

## Docker Build

docker build -t CI-CD-Reviewer-Agent .

docker run -v $(pwd):/app CI-CD-Reviewer-Agent
