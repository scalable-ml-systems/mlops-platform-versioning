## Project Plan :  
Every dataset, model, and experiment can be tracked, stored, and rerun exactly the same way

### Goal: 
ML experiments  - reproducible, enforce discipline with automation, and provide a full end‑to‑end system for versioning.

Control Plane
control-plane/crossplane/s3-bucket.yaml → declarative storage bucket (S3/MinIO).

control-plane/crossplane/pvc.yaml → persistent volume claim for caching.

control-plane/mlflow/deployment.yaml → MLflow server manifest (CPU node).

control-plane/gitops/argo-cd-app.yaml → GitOps app definition.

control-plane/ci-cd/github-actions.yaml → CI/CD workflow enforcing reproducibility checks.

Data Plane
data-plane/dvc/dvc.yaml → pipeline definition (data → train → model).

data-plane/dvc/params.yaml → hyperparameters for reproducibility.

data-plane/models/ → placeholder for versioned model binaries.

data-plane/experiments/ → MLflow run metadata.

Docs
docs/reproduce-in-3-steps.md → onboarding guide.

docs/architecture-diagram.png → visual sketch of the platform.

🔗 Dependencies (Critical Only)
Kubernetes cluster (EKS) → base infra.

Crossplane → infra provisioning (S3, PVCs).

DVC → dataset/model versioning.

MLflow → experiment tracking.

Argo CD / Flux → GitOps enforcement.

GitHub Actions / GitLab CI → reproducibility checks.

Storage backend → S3 bucket or MinIO.

🚀 What You Need to Get Started
Cluster ready → EKS with 1 small CPU node + optional GPU node.

Install Crossplane → configure provider for AWS/MinIO.

Bootstrap GitOps → Argo CD or Flux connected to repo.

Initialize DVC → link repo to S3 bucket.

Deploy MLflow → CPU node, SQLite backend, S3 artifact store.

Set up CI/CD → enforce DVC + MLflow checks before merge.

Write onboarding doc → “Reproduce in 3 steps” guide.


