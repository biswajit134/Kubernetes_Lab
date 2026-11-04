# ☸️ Comprehensive Kubernetes Objects & Manifests Lab

Welcome to the **Kubernetes Lab**! This repository is organized by individual Kubernetes object topics. Each topic has its own dedicated directory containing production-ready, fully commented manifest files (`.yaml`). Every manifest includes detailed explanations of key concepts, line-by-line field breakdowns, architectural best practices, and practical `kubectl` commands.

> 🛠️ **Prerequisites & Tooling**: Looking for cluster setups, CLIs, linters, or dashboards? Check out the complete [**Essential Kubernetes Tools Guide (`tools.md`)**](./tools.md) for recommendations and installation commands.
> 
> 📖 **Deep Dive Architecture & Objects**: Want a full conceptual breakdown of every component, object, and CRD? Read the [**What, Why, How Reference Manual (`explain.md`)**](./explain.md).

---

## 📂 Repository Topic Directory

| # | Topic Directory | Manifest Files | Description & Purpose |
|---|---|---|---|
| 01 | [`01-Namespace`](./01-Namespace/) | `namespace.yaml`<br>`resource-quota.yaml`<br>`limit-range.yaml` | Virtual cluster partitions, tenant isolation, compute & storage quotas, default resource boundaries. |
| 02 | [`02-Pod`](./02-Pod/) | `pod.yaml`<br>`multi-container-pod.yaml`<br>`init-container-pod.yaml`<br>`pod-lifecycle-probes.yaml` | Smallest deployable unit, sidecar pattern, sequential init containers, startup/liveness/readiness probes, and lifecycle hooks. |
| 03 | [`03-ReplicaSet`](./03-ReplicaSet/) | `replicaset.yaml` | Maintains a stable set of identical pod replicas using label selectors. |
| 04 | [`04-Deployment`](./04-Deployment/) | `deployment.yaml`<br>`deployment-recreate.yaml` | Declarative pod updates, zero-downtime rolling updates, maxSurge/maxUnavailable, rollbacks, and recreate strategies. |
| 05 | [`05-StatefulSet`](./05-StatefulSet/) | `statefulset.yaml` | Stateful workloads requiring deterministic pod identity (`pod-0`), headless DNS routing, and automated per-pod persistent storage templates. |
| 06 | [`06-DaemonSet`](./06-DaemonSet/) | `daemonset.yaml` | Ensures a copy of a pod runs on every worker/control-plane node (monitoring, log forwarding, CNI plugins). |
| 07 | [`07-Job`](./07-Job/) | `job.yaml` | Batch and run-to-completion tasks, parallel processing, retry backoff limits, and automated TTL cleanup. |
| 08 | [`08-CronJob`](./08-CronJob/) | `cronjob.yaml` | Time-based scheduled jobs (cron syntax), concurrency policies (`Allow`, `Forbid`, `Replace`), and execution deadlines. |
| 09 | [`09-ConfigMap`](./09-ConfigMap/) | `configmap.yaml`<br>`pod-using-configmap.yaml` | Storing non-sensitive configuration keys and full configuration files, injected as env vars or mounted volumes. |
| 10 | [`10-Secret`](./10-Secret/) | `secret.yaml`<br>`tls-secret.yaml`<br>`pod-using-secret.yaml` | Sensitive credentials (passwords, tokens, TLS certs), base64 encoding vs encryption, and secure tmpfs in-memory mounts. |
| 11 | [`11-Service`](./11-Service/) | `clusterip-service.yaml`<br>`nodeport-service.yaml`<br>`loadbalancer-service.yaml`<br>`headless-service.yaml`<br>`externalname-service.yaml` | Stable internal virtual IPs (ClusterIP), worker node ports (NodePort), cloud load balancers (LoadBalancer), direct DNS discovery (Headless), and external CNAME redirects (ExternalName). |
| 12 | [`12-Ingress`](./12-Ingress/) | `ingress.yaml` | Layer 7 HTTP/HTTPS reverse proxy routing, host and path matching, SSL/TLS certificate termination, and IngressControllers. |
| 13 | [`13-NetworkPolicy`](./13-NetworkPolicy/) | `network-policy.yaml` | Layer 3/4 pod firewall rules, zero-trust default deny, namespace selectors, pod selectors, and CIDR blocks. |
| 14 | [`14-StorageClass`](./14-StorageClass/) | `storageclass.yaml` | Dynamic volume provisioners, reclaim policies (`Delete`/`Retain`), volume expansion, and `WaitForFirstConsumer` binding. |
| 15 | [`15-PersistentVolume`](./15-PersistentVolume/) | `persistentvolume.yaml` | Cluster-wide persistent physical or network storage volumes with access modes (`RWO`, `ROX`, `RWX`). |
| 16 | [`16-PersistentVolumeClaim`](./16-PersistentVolumeClaim/) | `persistentvolumeclaim.yaml`<br>`pod-using-pvc.yaml` | User request for storage bound to a PV or StorageClass, mounted securely into Pod workloads. |
| 17 | [`17-ServiceAccount`](./17-ServiceAccount/) | `serviceaccount.yaml` | In-cluster identity for processes running inside Pods, automated token projection, and cloud IAM workload integration. |
| 18 | [`18-Role-and-RoleBinding`](./18-Role-and-RoleBinding/) | `role.yaml`<br>`rolebinding.yaml` | Namespace-scoped RBAC permissions (apiGroups, resources, verbs) bound to users, groups, or ServiceAccounts. |
| 19 | [`19-ClusterRole-and-ClusterRoleBinding`](./19-ClusterRole-and-ClusterRoleBinding/) | `clusterrole.yaml`<br>`clusterrolebinding.yaml` | Cluster-wide RBAC permissions for cluster-scoped resources (Nodes, PVs, Namespaces) and global bindings. |
| 20 | [`20-HorizontalPodAutoscaler`](./20-HorizontalPodAutoscaler/) | `horizontalpodautoscaler.yaml` | Dynamic workload scaling based on CPU, Memory, or custom metrics, with scaleUp/scaleDown stabilization windows. |
| 21 | [`21-PodDisruptionBudget`](./21-PodDisruptionBudget/) | `poddisruptionbudget.yaml` | High-availability guarantees preventing voluntary disruptions (node drains, cluster upgrades) from taking down services. |
| 22 | [`22-NodeScheduling-and-Affinity`](./22-NodeScheduling-and-Affinity/) | `nodeselector.yaml`<br>`node-affinity.yaml`<br>`pod-affinity-antiaffinity.yaml`<br>`taints-and-tolerations.yaml`<br>`topology-spread-constraints.yaml` | Advanced pod placement: node labels, hard/soft node affinity, pod co-location, pod anti-colocation, node taints & tolerations, and multi-zone topology spread. |
| 23 | [`23-CustomResourceDefinition`](./23-CustomResourceDefinition/) | `crd.yaml`<br>`custom-resource.yaml` | Extending Kubernetes API with custom resources, OpenAPI v3 validation schemas, status subresources, and custom objects. |
| 24 | [`24-GatewayAPI`](./24-GatewayAPI/) | `gatewayclass.yaml`<br>`gateway.yaml`<br>`httproute.yaml`<br>`grpcroute.yaml`<br>`tcproute.yaml`<br>`tlsroute.yaml`<br>`referencegrant.yaml` | Modern Kubernetes Gateway API: role-oriented networking, L4/L7 listeners, traffic splitting, gRPC/TCP/TLS passthrough, and cross-namespace ReferenceGrants. |
| 25 | [`25-ServiceMesh`](./25-ServiceMesh/) | `virtualservice.yaml`<br>`destinationrule.yaml`<br>`gateway.yaml`<br>`serviceentry.yaml`<br>`peerauthentication.yaml`<br>`authorizationpolicy.yaml`<br>`sidecar.yaml`<br>`envoyfilter.yaml`<br>`telemetry.yaml` | Cloud-native Service Mesh (Istio) CRDs: dynamic canary routing, circuit breaking, mTLS enforcement, L7 Zero Trust authorization, sidecar scoping, and distributed telemetry. |
| 26 | [`26-Observability`](./26-Observability/) | **Metrics Server** (`metrics-server.yaml`, `metrics-apiservice.yaml`)<br>**Prometheus** (`servicemonitor.yaml`, `podmonitor.yaml`, `prometheusrule.yaml`, `alertmanagerconfig.yaml`, `prometheus.yaml`)<br>**OpenTelemetry** (`opentelemetrycollector.yaml`, `instrumentation.yaml`)<br>**Jaeger** (`jaeger.yaml`)<br>**Grafana** (`grafanadashboard.yaml`) | Full-stack cloud-native observability: in-memory `metrics.k8s.io` aggregation, Prometheus scraping & alerting CRDs, OTel auto-instrumentation, Jaeger distributed tracing, and GitOps Grafana dashboards. |

---

## 🚀 Quick Start Guide

### 1. Applying a Manifest
```bash
# Apply a single file
kubectl apply -f <path-to-manifest.yaml>

# Apply an entire directory of manifests recursively
kubectl apply -f <directory-name>/ -R
```

---

## 🔍 Advanced Inspecting, Troubleshooting & Debugging Guide

When working with Kubernetes in labs or production, simple `kubectl get` is rarely enough. Use these advanced inspecting, diagnostic, and debugging workflows categorized by troubleshooting phase:

### 1. Pod & Container Diagnostics (CrashLoopBackOff, Pending, Evicted)

```bash
# 1. Inspect recent status, failure reasons, and system events (OOMKilled, ImagePullBackOff)
kubectl describe pod <pod-name> -n <namespace>

# 2. View logs of a crashed container prior to its restart (Essential for CrashLoopBackOff!)
kubectl logs <pod-name> -c <container-name> --previous

# 3. Stream logs from ALL containers in a multi-container pod simultaneously
kubectl logs <pod-name> --all-containers=true -f --tail=100

# 4. Attach an ephemeral debugging container with full networking tools (netshoot) to a running pod (K8s 1.23+)
kubectl debug -it <pod-name> --image=nicolaka/netshoot --target=<container-name>

# 5. Clone a crashing pod into a debug sandbox with an interactive shell overriding the entrypoint
kubectl debug <pod-name> -it --copy-to=debug-pod --container=<container-name> -- sh

# 6. Stream real-time cluster warning and error events chronologically
kubectl get events -A --sort-by='.metadata.creationTimestamp' -w

# 7. Find all pods that are NOT in 'Running' state across all namespaces
kubectl get pods -A --field-selector status.phase!=Running
```

---

### 2. Networking, DNS & Service Discovery Diagnostics

```bash
# 1. Launch a temporary, auto-destroying debug pod with curl/dig/nslookup
kubectl run net-debug --rm -it --image=nicolaka/netshoot -- /bin/bash

# 2. Test internal DNS resolution for a Service within the cluster
kubectl run test-dns --rm -it --image=busybox:1.36 -- nslookup <service-name>.<namespace>.svc.cluster.local

# 3. Verify active endpoints and EndpointSlices matching a Service selector
kubectl get endpoints <service-name> -o wide
kubectl get endpointslices -l kubernetes.io/service-name=<service-name>

# 4. Forward local ports to cluster resources for direct browser/API testing
# Forward to a Service:
kubectl port-forward svc/<service-name> 8080:<service-port>

# Forward to a specific Pod:
kubectl port-forward pod/<pod-name> 9090:<container-port>

# 5. Inspect Ingress routing table and TLS secret status
kubectl describe ingress <ingress-name>
```

---

### 3. Node Health, Resource Pressure & Node Draining

```bash
# 1. Check live CPU and Memory consumption across nodes and pods (requires Metrics Server)
kubectl top nodes
kubectl top pods -A --sort-by=cpu
kubectl top pods -A --sort-by=memory

# 2. Check node conditions (MemoryPressure, DiskPressure, PIDPressure, Ready)
kubectl describe node <node-name> | grep -A 8 "Conditions:"

# 3. Check allocated vs allocatable resources on a node
kubectl describe node <node-name> | grep -A 6 "Allocated resources:"

# 4. Safely cordon and drain a node for maintenance without violating PDBs
kubectl cordon <node-name>                                               # Prevent new pods from scheduling
kubectl drain <node-name> --ignore-daemonsets --delete-emptydir-data     # Evict existing pods
kubectl uncordon <node-name>                                             # Re-enable scheduling after maintenance

# 5. Debug a worker node by spawning a privileged container with root access to the node host
kubectl debug node/<node-name> -it --image=busybox
```

---

### 4. RBAC, Identity & Permission Probing

```bash
# 1. Check what actions YOUR current user/context can perform
kubectl auth can-i create deployments
kubectl auth can-i delete namespaces
kubectl auth can-i '*' '*' --all-namespaces

# 2. Impersonate a ServiceAccount to test its granular permissions
kubectl auth can-i get secrets --as=system:serviceaccount:default:app-service-account -n default
kubectl auth can-i list pods --as=system:serviceaccount:kube-system:monitoring-agent -A

# 3. Inspect ServiceAccount token mount inside a pod
kubectl exec -it <pod-name> -- cat /var/run/secrets/kubernetes.io/serviceaccount/token
```

---

### 5. Advanced JSONPath & Custom Columns (Fleet Auditing)

```bash
# 1. List every running pod with its node name, container image, and IP
kubectl get pods -A -o custom-columns=\
NAME:.metadata.name,\
NAMESPACE:.metadata.namespace,\
NODE:.spec.nodeName,\
IMAGE:.spec.containers[*].image,\
IP:.status.podIP

# 2. Find pods with the highest restart counts
kubectl get pods -A -o custom-columns=\
NAME:.metadata.name,\
NAMESPACE:.metadata.namespace,\
RESTARTS:.status.containerStatuses[*].restartCount \
--sort-by='.status.containerStatuses[0].restartCount'

# 3. Extract all image tags running in the cluster
kubectl get pods -A -o jsonpath='{range .items[*]}{.spec.containers[*].image}{"\n"}{end}' | sort -u

# 4. Query raw Kubernetes API discovery endpoints
kubectl get --raw /healthz
kubectl get --raw /readyz
kubectl get --raw /apis/metrics.k8s.io/v1beta1/nodes
```

---

### 6. Dry-Run & Diffing (Pre-Flight Safety Checks)

```bash
# 1. Server-side dry-run: validate schema, admission webhooks, and quotas without writing to etcd
kubectl apply -f <manifest.yaml> --dry-run=server

# 2. View exact line-by-line diff between your local file and live cluster state
kubectl diff -f <manifest.yaml>

# 3. Generate boilerplate YAML quickly without creating resources
kubectl create deployment demo --image=nginx:alpine --dry-run=client -o yaml > deployment.yaml
kubectl create service clusterip demo --tcp=80:80 --dry-run=client -o yaml > service.yaml
```

---

### 7. Deleting Resources Safely
```bash
# Delete by manifest file
kubectl delete -f <path-to-manifest.yaml>

# Delete without waiting for background finalizers (force delete stuck pods)
kubectl delete pod <pod-name> --grace-period=0 --force
```

