# github-actions-essentials

## What is GitHub Actions?

- A CI/CD and automation platform built directly into GitHub
- Executes workflows defined as YAML files under `.github/workflows/`
- Similar to Jenkins/GitLab CI, but easier, integrated, and cloud-hosted
- Uses runners (VMs) to execute jobs
- Triggered by GitHub events (push, PR, dispatch, cron, etc.)

## Why GitHub Actions?

- No external server setup like Jenkins
- Maintained by GitHub team (secure, stable, updated)
- Integrates tightly with repos and GitHub ecosystem
- Free unlimited minutes for public repos
- YAML config → easy to version/control

## Runners

Runners are the machines that execute workflows.

Types of runners:

1. GitHub-hosted runners
   - Free/shared VMs provided by GitHub
   - Ex: `ubuntu-latest`, `ubuntu-24.04`, `windows-latest`, `macos-latest`

2. Self-hosted runners
   - Your own machine/VM/container
   - Useful for special hardware (GPU), enterprise setups

## Core Concepts

### Workflow

A YAML file that defines automation.

```YAML
name: My Workflow
on: push
jobs: ...
```

### Job

A collection of steps executed on a runner.

- Runs in parallel by default
- Can define dependencies using needs

```YAML
jobs:
  build:
  test:
    needs: build
```

### Step

A single command or action inside a job.

```YAML
steps:
  - run: echo "Hello"
  - uses: actions/checkout@v4
```

### Action

A reusable chunk of logic like:

- checkout source code
- setup a language
- run a reusable script

```YAML
- uses: actions/setup-go@v5
```

### Triggers (Events)

Most common:

```YAML
on:
  push:
  pull_request:
  workflow_dispatch:     # run manually
  schedule:
    - cron: "0 * * * *"  # every hour
```

## Example Workflows

1. [Hello World](./.github/workflows/hello.yml)
2. [Inline Step Types](./.github/workflows/step-types.yml)
3. [Job Dependencies (Sequential Execution)](./.github/workflows/job-dependencies.yml)
