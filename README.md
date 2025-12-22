# mlops-platform-versioning
Versioning Platform — a modular, end‑to‑end MLOps stack for reproducibility.

Versioning Platform — a modular, end‑to‑end MLOps stack for reproducibility.
This project establishes a complete versioning platform by combining:

Crossplane Infra → declarative provisioning of storage (S3/MinIO, PVCs).

DVC Pipelines → dataset and model versioning integrated with Git.

MLflow Tracking → experiment metadata, parameters, and artifact logging.

GitOps Enforcement → Argo CD/Flux + CI/CD workflows that block merges unless artifacts are versioned.

👉 Outcome: A lean, reproducible platform where any experiment can be reproduced in 3 steps — clone, pull, and rerun.
