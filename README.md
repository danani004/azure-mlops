# Azure MLOps — LLM Training Automation for KRSP Research

## Project Overview

This repository supports an **Azure MLOps** project that automates Large Language Model (LLM) training workflows for the **KRSP research project**. The goal is to provide a repeatable, versioned, and auditable pipeline so the research team can train and evaluate models with minimal manual setup and consistent environments.

---

## Understanding MLOps

**MLOps** (Machine Learning Operations) applies DevOps practices to machine learning: versioning code and data, automating builds and tests, and deploying models in a controlled way.

### Key Concepts

- **CI/CD (Continuous Integration / Continuous Delivery)**  
  Code changes are built and tested automatically. When ready, training or deployment can be triggered from the same pipeline, reducing human error and keeping environments consistent.

- **Automation**  
  Training jobs, data preparation, and model registration can be triggered by code commits, schedules, or manual runs—all defined in configuration rather than ad‑hoc scripts.

- **Azure DevOps Tools**  
  Azure Pipelines run the automation; Azure Machine Learning provides managed compute, experiment tracking, and model registry. Together they support versioned experiments and reproducible training runs.

---

## Proposed Architecture

```
┌─────────────────┐     ┌─────────────────────┐     ┌──────────────────┐
│  React Client   │────▶│  Azure Pipelines    │────▶│  Azure ML        │
│  (Frontend)     │     │  (CI/CD & Triggers) │     │  (Training Jobs) │
└─────────────────┘     └─────────────────────┘     └──────────────────┘
```

- **React client** — Web interface for the research team to configure runs, view status, and access results.
- **Azure Pipelines** — Orchestrates validation, build, and trigger of training workflows; can run on branch or schedule.
- **Azure ML** — Hosts training jobs, manages compute (e.g., GPU clusters), tracks experiments, and stores/versions models.

This keeps the UI, orchestration, and heavy compute clearly separated and scalable.

---

## Project Structure

```
azure-mlops/
├── client/                 # React frontend for run configuration and monitoring
├── docs/                   # Architecture notes, runbooks, and project documentation
├── azure-pipelines/        # Azure Pipelines YAML and related configs
├── tests/                  # Unit and integration tests for pipeline and tooling
└── README.md
```

| Folder | Purpose |
|--------|--------|
| **client** | React app for researchers to start runs and view training status. |
| **docs** | Design docs, setup guides, and operational notes. |
| **azure-pipelines** | Pipeline definitions that validate code, trigger training, and (later) deployment. |
| **tests** | Tests for scripts, pipeline logic, and any shared utilities. |

---

## Next Steps and Future Work

1. **Connect Azure Pipelines** — Link this repo to an Azure DevOps project and run the initial pipeline.
2. **Define training pipeline** — Add steps for data validation, environment setup, and Azure ML job submission.
3. **Build React client** — Implement screens for run configuration, job submission, and basic result views.
4. **Document runbooks** — Add docs for common tasks (new dataset, new model config, troubleshooting).
5. **Model registry and deployment** — Extend pipelines to register approved models and optional deployment to endpoints.

---

## Getting Started

After cloning the repository, see the `docs/` folder for setup instructions and the `azure-pipelines/` folder for pipeline configuration. The `client/` app can be run locally for development (see `client/README.md` when added).
