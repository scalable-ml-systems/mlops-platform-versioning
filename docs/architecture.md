Reproducible ML Platform with GitOps Control Plane 

              Git (Source of Truth)
                       |
          CI/CD (Reproducibility Gates)
                       |
                Argo CD / Flux
                       |
        --------------------------------
        |          Control Plane        |
        |        (CPU Node only)        |
        |                               |
        |  Crossplane  → Storage (S3)   |
        |  MLflow     → Metadata        |
        |  DVC        → Dataset refs    |
        --------------------------------
                       |
                 PVC / Object Storage
                       |
        --------------------------------
        |          Compute Plane        |
        |         (GPU Node only)       |
        |                               |
        |  Training Jobs                |
        |  Inference (Triton)           |
        --------------------------------


