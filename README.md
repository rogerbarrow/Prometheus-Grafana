# Prometheus-Grafana

Pre-Requisite
Kubernetes Cluster (can be minikube)
Helm

If you don't have them installed. Follow the below links:

Install Minikube

Install Helm


![image](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/5c00bd08-09ed-4f69-a1bb-6f618274c8a4)

Prometheus Architecture
![image](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/551a502d-c461-4be3-b78a-f6c036c7679f)

Step 1. Install Minikube
![9CF769FE-A7EB-4E33-94E6-BD325F30B180_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/19dfb006-a93e-478f-849d-0b5c972267fc)

Run Kubectl get pods -A to verify pod is running
![3E4821FE-F350-491C-9217-4D5E01DE2646_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/8e20ddc8-457e-40d5-beb1-4e56c11138db)

Step 2. Install Helm  with command Helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
 -then Run Helm repo update
