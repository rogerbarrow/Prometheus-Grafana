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

![AAC0C0EE-A6FF-4433-90FE-A2C7639CF0AD_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/e1e771de-75ff-407d-927d-73579d820483)

Step 3. Run Helm repo update

 ![CAFC484C-CEF0-4105-A819-8BB6DA449BA4_1_105_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/73b8b3b4-c3e2-4287-a496-82bf34126ed6)

Step 4. run kubectl get pods
![C11F2DEE-F26F-42DB-B70A-1BFE69CAB6EA_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/957f639c-f859-4041-9ea6-104c281529ef)

Step 5. Is expose Prometheus Server
    Commad  Kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=promethsus-server-ext
    ![026B37D9-83DB-4DDF-AABC-948A09F588CD_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/1d4f23d8-4c39-43cf-ac8b-4b89b04b8846)

Step 6: is to get the IP address of the Kube Node with commmand minikub ip. Enter Ip address and port number in web browser
![FDFC45E2-3DFF-457A-BBCA-F5C92C5DB5E1](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/5ec11e0b-b4e7-45d4-b0c6-0512f929213a)



