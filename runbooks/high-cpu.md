# High CPU Runbook

## Description
CPU usage is above 80% for more than 2 minutes on one or more nodes.

**Alert:** `HighCPUUsage`
**Severity:** Warning
**Threshold:** > 80% CPU for 2 minutes

## Investigation

### 1. Check node CPU usage
```bash
kubectl top nodes
```

### 2. Check pods consuming CPU
```bash
kubectl top pods -n observability
```

### 3. Cross-check in Prometheus (localhost:9090)
Run this query to confirm and see which node is affected:
```promql
(1 - avg by (instance)(rate(node_cpu_seconds_total{mode="idle"}[2m]))) * 100
```

## Actions

### Identify the high CPU pod
```bash
kubectl top pods -n observability --sort-by=cpu
```

### Scale the deployment if overloaded
```bash
kubectl scale deployment <deployment-name> -n observability --replicas=<desired>
```

### Restart a problematic pod
```bash
kubectl rollout restart deployment <deployment-name> -n observability
```

## Escalation

Escalate to the next on-call engineer if:
- CPU remains above 80% after scaling
- Multiple nodes are affected simultaneously
- The issue cannot be tied to a specific pod or deployment