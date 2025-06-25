# Kubernetes Monitoring Stack – Trivy + Prometheus + Grafana

This repository contains the configuration for integrating [Trivy Operator](https://github.com/aquasecurity/trivy-operator) with [Prometheus](https://prometheus.io/) and [Grafana](https://grafana.com/) in a Kubernetes cluster.

## 📦 Overview

- **Trivy Operator**: Scans running workloads and nodes for vulnerabilities.
- **Prometheus**: Scrapes metrics exposed by the Trivy Operator.
- **Grafana**: Visualizes vulnerability data using Dashboard ID [17813](https://grafana.com/grafana/dashboards/17813/).

## 📁 File Structure

```
trivy/
├── trivy-values.yaml               # Helm values used to deploy Trivy Operator
├── trivy-metrics-service.yaml     # Manually created metrics service for Prometheus
├── trivy-servicemonitor.yaml      # Prometheus ServiceMonitor to scrape Trivy metrics
├── trivy-operator-rendered.yaml   # Rendered manifests from the Helm release
```

## ✅ Setup Summary

1. Trivy Operator installed with nodeCollector + metrics enabled.
2. Custom `Service` created for exposing metrics on port `8080`.
3. Prometheus ServiceMonitor created to scrape metrics.
4. Grafana dashboard (ID 17813) imported for visualizing vulnerability data.

## 🛡 Current Status

| Component        | Status   |
|------------------|----------|
| Trivy Operator   | ✅ Running |
| Prometheus       | ✅ Scraping |
| Grafana          | ✅ Dashboard Live |

## 📚 Next Steps

- [ ] Set up **alerts** in Grafana/Prometheus for CRITICAL vulnerabilities
- [ ] Integrate with **Velero + MinIO** for cluster-wide backup and disaster recovery
- [ ] GitOps-ify configuration with Helm + CI/CD
- [ ] Monitor certificate expiration and pod security policies

---

## 🧠 Notes

This configuration is built and tested on a home lab Kubernetes cluster managed by Richard Edwards, using:
- Calico CNI
- MetalLB LoadBalancer
- Internal DNS via `sleepy-puppy.com`
- Prometheus Operator stack deployed via Helm

#readme cleaned up by chatGPT
