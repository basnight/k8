# Kustomize Basics

## What You'll Learn
In this section, you'll learn the fundamental concepts of Kustomize:
- How to organize your Kubernetes configurations
- How to make simple changes without touching the original files
- Understanding base and overlay structure

## Directory Structure
```
.
├── base/                  # Your original configuration
│   ├── deployment.yaml    # A basic nginx deployment
│   └── kustomization.yaml # Tells Kustomize what to include
└── overlay/              # Your customizations
    └── kustomization.yaml # Defines how to modify the base
```

## Understanding the Files

### Base Configuration
The `base/` directory contains your original, unchanged configuration:
- `deployment.yaml`: A simple nginx web server deployment
- `kustomization.yaml`: Lists which files to include

### Overlay Configuration
The `overlay/` directory shows how to customize the base:
- Adds a prefix to all resources (`dev-`)
- Updates the nginx image version to 1.20
- Adds environment labels

## Try It Yourself

1. View the base deployment:
```bash
kubectl kustomize base/
```

2. View the customized version:
```bash
kubectl kustomize overlay/
```

3. Apply to your cluster:
```bash
kubectl apply -k overlay/
```

## What's Happening?
1. Kustomize reads the base configuration
2. It applies the changes specified in the overlay:
   - Adds "dev-" prefix to names
   - Updates the nginx image
   - Adds environment labels
3. Generates the final configuration

## Key Concepts
- **Base**: Your original configuration
- **Overlay**: Your customizations
- **kustomization.yaml**: Tells Kustomize what to do
- **Resources**: The Kubernetes files you want to modify
