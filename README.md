#  mlops-platform-versioning

##  Project Scope
A **self‑contained versioning platform** that enforces reproducibility across **data, code, and models**.  
This project demonstrates how to build a full stack MLOps system with no external dependencies.

---

##  Tech Stack
- **Infra & Orchestration:** Kubernetes (EKS), Crossplane, Argo CD / Flux  
- **Versioning & Tracking:** Git, DVC, MLflow  
- **CI/CD Enforcement:** GitHub Actions / GitLab CI  
- **Lean Infra:** 1 small CPU node (controllers + MLflow/DVC), GPU node only for training/inference  

---

##  Platform Features
- **Crossplane Infra** → declarative provisioning of storage (S3/MinIO, PVCs).  
- **DVC Pipelines** → dataset and model versioning integrated with Git.  
- **MLflow Tracking** → experiment metadata, parameters, and artifact logging.  
- **GitOps Enforcement** → Argo CD/Flux + CI/CD workflows that block merges unless artifacts are versioned.  

---

##  Reproducibility in 3 Steps
1. **Clone the repo**  
   ```bash
   git clone https://github.com/your-org/mlops-platform-versioning
   cd mlops-platform-versioning

Pull datasets/models with DVC

bash
dvc pull
Reproduce experiments

bash
dvc repro

```

Repo Structure: 
```
mlops-platform-versioning/
├── control-plane/                 # Infra + orchestration
│   ├── cluster/                   # Bootstrap configs (EKS, nodegroups)
│   │   ├── eks-cluster.yaml
│   │   ├── nodegroup.yaml
│   │   └── provider-config.yaml
│   ├── crossplane/                # Declarative infra provisioning
│   │   ├── s3-bucket.yaml
│   │   ├── pvc.yaml
│   │   └── provider-configs/
│   ├── mlflow/                    # MLflow deployment manifests
│   │   ├── deployment.yaml
│   │   └── config/
│   ├── gitops/                    # GitOps enforcement + rollout
│   │   ├── argo-cd-app.yaml
│   │   ├── flux-kustomization.yaml
│   │   ├── rollout-canary.yaml    # Canary deployment strategy (Argo Rollouts/Flux)
│   │   └── metrics-config.yaml    # Prometheus/Grafana thresholds for canary
│   ├── ci-cd/                     # CI/CD enforcement
│   │   ├── github-actions.yaml
│   │   ├── checks/
│   │   └── canary-checks.yaml     # CI/CD gating logic for canary rollout
│   └── README.md                  # Control plane overview
│
├── data-plane/                    # Data + models + experiments
│   ├── dvc/                       # DVC pipelines + configs
│   │   ├── dvc.yaml
│   │   ├── params.yaml
│   │   └── data/                  # Versioned datasets
│   ├── models/                    # Versioned model binaries
│   ├── experiments/               # MLflow run metadata
│   └── README.md                  # Data plane overview
│
├── docs/                          # Documentation + visuals
│   ├── reproduce-in-3-steps.md    # Onboarding guide
│   ├── architecture-diagram.png   # High-level architecture
│   └── canary-flow-diagram.png    # Annotated canary rollout flow
│
└── README.md                      # Top-level project overview

```

