# SRE Observability Platform
Kubernetes-based observability stack to monitor containerized workloads using Prometheus and Grafana.

## Overview
This project demonstrates how to build a complete observability stack for Kubernetes, including:

- Metrics collection
- Visualization dashboards
- Alerting system
- Incident response via runbooks

The goal is to replicate a **real-world SRE monitoring setup** used in production environments.

## Stack
- Kubernetes
- Prometheus
- Node Exporter
- Grafana
- Alertmanager

## Features
- Cluster-wide metrics collection
- Node and container monitoring
- Custom Grafana dashboards
- Prometheus alerting rules
- Runbooks for incident response

## Architecture diagram
K8s → Prometheus → Grafana

Prometheus scrapes metrics from Kubernetes components and exporters, and Grafana visualizes them through dashboards.

## Prometheus UI (localhost:9090)
![prometheus ui kubernetes](images/prometheus-ui-kub.png)
![count by job up](images/count-by-job-up.png)

## Grafana Dashboard (localhost:3000)

Cluster overview dashboard visualizing system health and resource usage:

![Grafana Dashboard](images/grafana-dashboard.png)

## Getting Started

1. Enable Kubernetes (Docker Desktop)
```
kubectl config use-context docker-desktop
kubectl get nodes
```
2. Create namespace
```
kubectl create namespace observability
```
3. Install Prometheus
```
helm install prometheus prometheus-community/prometheus \
  -n observability \
  -f kubernetes/prometheus/values.yaml
```
4. Install Grafana
```
helm install grafana grafana/grafana -n observability
```
5. Access services
```
kubectl port-forward -n observability svc/prometheus-server 9090:80
kubectl port-forward -n observability svc/grafana 3000:80
```