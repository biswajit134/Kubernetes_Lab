# ☸️ Comprehensive Kubernetes Objects & Manifests Lab

Welcome to the **Kubernetes Lab**! This repository is organized by individual Kubernetes object topics. Each topic has its own dedicated directory containing production-ready, fully commented manifest files (`.yaml`). Every manifest includes detailed explanations of key concepts, line-by-line field breakdowns, architectural best practices, and practical `kubectl` commands.

> 🛠️ **Prerequisites & Tooling**: Looking for cluster setups, CLIs, linters, or dashboards? Check out the complete [**Essential Kubernetes Tools Guide (`tools.md`)**](./tools.md) for recommendations and installation commands.
> 
> 📖 **Deep Dive Architecture & Objects**: Want a full conceptual breakdown of every component, object, and CRD? Read the [**What, Why, How Reference Manual (`explain.md`)**](./explain.md).

---

## 📂 Repository Topic Directory

| # | Topic Directory | Manifest Files | Description & Purpose |
|---|---|---|---|
| 01 | [`Namespace`](./Namespace/) | `namespace.yaml`<br>`resource-quota.yaml`<br>`limit-range.yaml` | Virtual cluster partitions, tenant isolation, compute & storage quotas, default resource boundaries. |
| 02 | [`Pod`](./Pod/) | `pod.yaml`<br>`multi-container-pod.yaml`<br>`init-container-pod.yaml`<br>`pod-lifecycle-probes.yaml` | Smallest deployable unit, sidecar pattern, sequential init containers, startup/liveness/readiness probes, and lifecycle hooks. |
| 03 | [`ReplicaSet`](./ReplicaSet/) | `replicaset.yaml` | Maintains a stable set of identical pod replicas using label selectors. |
| 04 | [`Deployment`](./Deployment/) | `deployment.yaml`<br>`deployment-recreate.yaml` | Declarative pod updates, zero-downtime rolling updates, maxSurge/maxUnavailable, rollbacks, and recreate strategies. |
| 05 | [`StatefulSet`](./StatefulSet/) | `statefulset.yaml` | Stateful workloads requiring deterministic pod identity (`pod-0`), headless DNS routing, and automated per-pod persistent storage templates. |
| 06 | [`DaemonSet`](./DaemonSet/) | `daemonset.yaml` | Ensures a copy of a pod runs on every worker/control-plane node (monitoring, log forwarding, CNI plugins). |
| 07 | [`Job`](./Job/) | `job.yaml` | Batch and run-to-completion tasks, parallel processing, retry backoff limits, and automated TTL cleanup. |
| 08 | [`CronJob`](./CronJob/) | `cronjob.yaml` | Time-based scheduled jobs (cron syntax), concurrency policies (`Allow`, `Forbid`, `Replace`), and execution deadlines. |
| 09 | [`ConfigMap`](./ConfigMap/) | `configmap.yaml`<br>`pod-using-configmap.yaml` | Storing non-sensitive configuration keys and full configuration files, injected as env vars or mounted volumes. |
| 10 | [`Secret`](./Secret/) | `secret.yaml`<br>`tls-secret.yaml`<br>`pod-using-secret.yaml` | Sensitive credentials (passwords, tokens, TLS certs), base64 encoding vs encryption, and secure tmpfs in-memory mounts. |
| 11 | [`Service`](./Service/) | `clusterip-service.yaml`<br>`nodeport-service.yaml`<br>`loadbalancer-service.yaml`<br>`headless-service.yaml`<br>`externalname-service.yaml` | Stable internal virtual IPs (ClusterIP), worker node ports (NodePort), cloud load balancers (LoadBalancer), direct DNS discovery (Headless), and external CNAME redirects (ExternalName). |
| 12 | [`Ingress`](./Ingress/) | `ingress.yaml` | Layer 7 HTTP/HTTPS reverse proxy routing, host and path matching, SSL/TLS certificate termination, and IngressControllers. |
| 13 | [`NetworkPolicy`](./NetworkPolicy/) | `network-policy.yaml` | Layer 3/4 pod firewall rules, zero-trust default deny, namespace selectors, pod selectors, and CIDR blocks. |
| 14 | [`StorageClass`](./StorageClass/) | `storageclass.yaml` | Dynamic volume provisioners, reclaim policies (`Delete`/`Retain`), volume expansion, and `WaitForFirstConsumer` binding. |
| 15 | [`PersistentVolume`](./PersistentVolume/) | `persistentvolume.yaml` | Cluster-wide persistent physical or network storage volumes with access modes (`RWO`, `ROX`, `RWX`). |
| 16 | [`PersistentVolumeClaim`](./PersistentVolumeClaim/) | `persistentvolumeclaim.yaml`<br>`pod-using-pvc.yaml` | User request for storage bound to a PV or StorageClass, mounted securely into Pod workloads. |
| 17 | [`ServiceAccount`](./ServiceAccount/) | `serviceaccount.yaml` | In-cluster identity for processes running inside Pods, automated token projection, and cloud IAM workload integration. |
| 18 | [`Role-and-RoleBinding`](./Role-and-RoleBinding/) | `role.yaml`<br>`rolebinding.yaml` | Namespace-scoped RBAC permissions (apiGroups, resources, verbs) bound to users, groups, or ServiceAccounts. |
| 19 | [`ClusterRole-and-ClusterRoleBinding`](./ClusterRole-and-ClusterRoleBinding/) | `clusterrole.yaml`<br>`clusterrolebinding.yaml` | Cluster-wide RBAC permissions for cluster-scoped resources (Nodes, PVs, Namespaces) and global bindings. |
| 20 | [`HorizontalPodAutoscaler`](./HorizontalPodAutoscaler/) | `horizontalpodautoscaler.yaml` | Dynamic workload scaling based on CPU, Memory, or custom metrics, with scaleUp/scaleDown stabilization windows. |
| 21 | [`PodDisruptionBudget`](./PodDisruptionBudget/) | `poddisruptionbudget.yaml` | High-availability guarantees preventing voluntary disruptions (node drains, cluster upgrades) from taking down services. |
| 22 | [`NodeScheduling-and-Affinity`](./NodeScheduling-and-Affinity/) | `nodeselector.yaml`<br>`node-affinity.yaml`<br>`pod-affinity-antiaffinity.yaml`<br>`taints-and-tolerations.yaml`<br>`topology-spread-constraints.yaml` | Advanced pod placement: node labels, hard/soft node affinity, pod co-location, pod anti-colocation, node taints & tolerations, and multi-zone topology spread. |
| 23 | [`CustomResourceDefinition`](./CustomResourceDefinition/) | `crd.yaml`<br>`custom-resource.yaml` | Extending Kubernetes API with custom resources, OpenAPI v3 validation schemas, status subresources, and custom objects. |
| 24 | [`GatewayAPI`](./GatewayAPI/) | `gatewayclass.yaml`<br>`gateway.yaml`<br>`httproute.yaml`<br>`grpcroute.yaml`<br>`tcproute.yaml`<br>`tlsroute.yaml`<br>`referencegrant.yaml` | Modern Kubernetes Gateway API: role-oriented networking, L4/L7 listeners, traffic splitting, gRPC/TCP/TLS passthrough, and cross-namespace ReferenceGrants. |
| 25 | [`ServiceMesh`](./ServiceMesh/) | `virtualservice.yaml`<br>`destinationrule.yaml`<br>`gateway.yaml`<br>`serviceentry.yaml`<br>`peerauthentication.yaml`<br>`authorizationpolicy.yaml`<br>`sidecar.yaml`<br>`envoyfilter.yaml`<br>`telemetry.yaml` | Cloud-native Service Mesh (Istio) CRDs: dynamic canary routing, circuit breaking, mTLS enforcement, L7 Zero Trust authorization, sidecar scoping, and distributed telemetry. |
| 26 | [`Observability`](./Observability/) | **Metrics Server** (`metrics-server.yaml`, `metrics-apiservice.yaml`)<br>**Prometheus** (`servicemonitor.yaml`, `podmonitor.yaml`, `prometheusrule.yaml`, `alertmanagerconfig.yaml`, `prometheus.yaml`)<br>**OpenTelemetry** (`opentelemetrycollector.yaml`, `instrumentation.yaml`)<br>**Jaeger** (`jaeger.yaml`)<br>**Grafana** (`grafanadashboard.yaml`) | Full-stack cloud-native observability: in-memory `metrics.k8s.io` aggregation, Prometheus scraping & alerting CRDs, OTel auto-instrumentation, Jaeger distributed tracing, and GitOps Grafana dashboards. |

---

## 🚀 Quick Start Guide

### 1. Applying a Manifest
```bash
kubectl apply -f <path-to-manifest.yaml>
```

### 2. Inspecting and Debugging Resources
```bash
# Get resource overview
kubectl get <resource-type>

# Get detailed configuration, status, and system events
kubectl describe <resource-type> <resource-name>

# View real-time container logs
kubectl logs <pod-name> -f

# Execute an interactive shell inside a container
kubectl exec -it <pod-name> -- /bin/sh
```

### 3. Deleting a Resource
```bash
kubectl delete -f <path-to-manifest.yaml>
```

