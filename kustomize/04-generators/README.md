# Generators in Kustomize

## What You'll Learn
This section explores Kustomize's powerful generators for ConfigMaps and Secrets:
- Creating ConfigMaps from different sources
- Generating Secrets safely
- Understanding when to use each generator type

## Understanding the Configuration

### ConfigMap Generators
1. **From Literals**
```yaml
configMapGenerator:
- name: app-settings
  literals:
  - DATABASE_URL=localhost:5432
  - APP_PORT=8080
```

2. **From Files**
```yaml
configMapGenerator:
- name: app-config
  files:
  - config.json
  - settings.properties
```

### Secret Generator
```yaml
secretGenerator:
- name: app-secrets
  literals:
  - api-key=my-secret-key
  - password=very-secret
```

## Key Features

1. **Automatic Hashing**
   - Generates unique names when content changes
   - Forces pods to restart when configuration updates
   - Ensures configuration changes are applied

2. **Multiple Sources**
   - Literals: Key-value pairs in YAML
   - Files: External configuration files
   - Env files: Environment variable files

3. **Behavior Control**
   - Replace: Complete replacement
   - Merge: Combine with existing values

## Try It Yourself

1. Generate the resources:
```bash
kubectl kustomize ./
```

2. Apply to your cluster:
```bash
kubectl apply -k ./
```

## Best Practices

1. **Secret Management**
   - Don't commit real secrets to version control
   - Use sealed secrets or external secret management
   - Consider using environment-specific secrets

2. **ConfigMap Organization**
   - Group related configurations
   - Use meaningful names
   - Document the purpose of each configuration

3. **File Structure**
   - Keep configuration files close to usage
   - Use clear file names
   - Maintain proper documentation

## Common Use Cases
1. Application configuration
2. Environment variables
3. API keys and credentials
4. Feature flags
5. Connection strings
