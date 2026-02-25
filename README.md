# sre-observability-platform

This project demonstrates a production-style observability and reliability setup for Kubernetes-based workloads.

It provisions a Kubernetes environment using Infrastructure as Code and deploys a sample application instrumented with Prometheus metrics. The platform includes monitoring, alerting, SLO definitions, and incident runbooks designed to reflect real-world SRE practices.

The goal is to model how production systems are observed, measured, and operated — focusing on reliability, signal quality, and operational readiness rather than just dashboards.

## Key Capabilities

- Infrastructure as Code (Terraform-based cluster provisioning)
- Prometheus metrics collection using RED methodology
- Grafana dashboards for service and cluster visibility
- Alertmanager with actionable alerts (latency, error rate, crashloops, resource pressure)
- Service Level Objectives (SLOs) with burn-rate alert examples
- Load testing with k6 to simulate traffic and validate alerts
- Incident runbooks for common production scenarios
- Secure and modular Kubernetes deployment patterns

## Focus Areas

- Production reliability thinking (not demo monitoring)
- Clear separation of signal vs noise in alerting
- Operational readiness (runbooks + rollback strategy)
- Scalable and repeatable infrastructure patterns
