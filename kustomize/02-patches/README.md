# Working with Patches in Kustomize

## What You'll Learn
This section teaches you how to make specific changes to your Kubernetes resources using patches:
- Strategic Merge Patches: Easy way to modify configurations
- JSON 6902 Patches: More precise modifications
- When to use each type of patch

## Directory Structure
```
.
├── base/                  # Original configuration
│   └── deployment.yaml    # Basic deployment with resource limits
└── overlay/              # Your modifications
    ├── increase-memory.yaml    # Strategic merge patch
    ├── add-label.yaml         # JSON patch
    └── kustomization.yaml     # Combines both patch types
```

## Understanding Patches

### Strategic Merge Patch
- File: `increase-memory.yaml`
- Purpose: Updates memory limit from 128Mi to 256Mi
- How it works: Overlays matching fields in the original
- When to use: For simple modifications to existing fields

### JSON 6902 Patch
- File: `add-label.yaml`
- Purpose: Adds a new label to the deployment
- How it works: Specifies exact operations (add, remove, replace)
- When to use: For precise changes or when working with arrays

## Try It Yourself

1. View the original deployment:
```bash
kubectl kustomize base/
```

2. See the patched version:
```bash
kubectl kustomize overlay/
```

## Key Concepts
- **Strategic Merge Patch**: 
  - Easier to write
  - Works well with Kubernetes resources
  - Good for simple changes
  
- **JSON 6902 Patch**:
  - More precise control
  - Can add/remove/replace specific values
  - Better for complex changes

## Common Use Cases
1. Updating resource limits
2. Adding labels or annotations
3. Modifying container arguments
4. Updating environment variables
