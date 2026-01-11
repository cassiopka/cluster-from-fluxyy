# cluster-from-fluxyy

### 📝 Usage Guide (Directory-Driven)

To deploy a new app, you no longer care about naming the file metadata.

**1. Create the Directory path:**
`apps / <my-namespace> / <my-app-name>`

**2. Drop the Standard File:**
Copy this exact block into `apps/<my-namespace>/<my-app-name>/release.yaml`. You only change the `chart` and `values`.

```yaml
apiVersion: helm.toolkit.fluxcd.io/v2
kind: HelmRelease
metadata:
  name: app         # LEAVE AS IS
  namespace: default # LEAVE AS IS
spec:
  interval: 5m
  chart:
    spec:
      chart: redis  # <--- CHANGE THIS
      version: 18.x # <--- CHANGE THIS
      sourceRef:
        kind: HelmRepository
        name: bitnami  # <--- CHANGE THIS
        namespace: flux-system
  values:           # <--- CHANGE THIS
    architecture: standalone
```