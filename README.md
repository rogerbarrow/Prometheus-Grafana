# Kubernetes Monitoring Prometheus and Grafanaa

![image](https://github.com/user-attachments/assets/69bcd56b-1a47-4bad-8738-f5914f9cae21)

In today’s rapidly advancing world of cloud-native technologies, Kubernetes has become the go-to platform for orchestrating containerized applications. To maintain the reliability and performance of these applications and their supporting infrastructure, robust monitoring is essential. Prometheus and Grafana are two widely-used tools that make this possible. In this guide, we’ll demonstrate how to set up Prometheus and Grafana on a Kubernetes cluster using Helm, a powerful package manager for Kubernetes applications.

 Why Choose Prometheus and Grafana?

Prometheus is a powerful open-source toolkit for monitoring and alerting, designed to collect and store time-series data from your applications and infrastructure. Known for its reliability, scalability, and simplicity, Prometheus is a go-to solution for modern monitoring needs. Complementing this, Grafana is a widely-used open-source platform for observability and data visualization. It allows you to create dynamic, customizable dashboards to visualize metrics collected by Prometheus and other data sources, making it easier to monitor and analyze system performance.

1. Ensures System Reliability
Monitoring tracks key metrics like uptime, ensuring services are available.
Example: If a service uptime drops below 99.9% (target is 99.99%), monitoring tools like Nagios or CloudWatch can alert you immediately.
2. Optimizes Performance
By analyzing metrics like response time, you can identify performance bottlenecks.
Example: If API latency increases from 200ms to 1s, a spike in requests or inefficient queries might be the cause, prompting action.
3. Enhances Security
Continuous monitoring flags anomalies, such as unusual login attempts or spikes in traffic.
Example: If failed login attempts rise from 5/hour to 500/hour, monitoring tools like Splunk or Datadog can alert your security team to investigate.
4. Supports Proactive Scaling
Tracking metrics like CPU usage helps predict resource needs and trigger scaling.
Example: If CPU usage consistently exceeds 80% during peak hours, auto-scaling can add instances before service degrades.
5. Improves Troubleshooting
Detailed logs and historical metrics aid in root cause analysis.
Example: If an application crash coincides with memory usage spiking from 2GB to 8GB, logs can pinpoint which process caused the issue.
By focusing on these, monitoring ensures systems remain reliable, secure, and performant while providing actionable insights to maintain and improve operations.

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

Step 7. istall Grafana      Command   Helm repo add grafana https://grafana.githube.io/helm-chart

![BBD26BD7-F1CD-41B9-A1DD-8F3EBC915CCC](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/8568e61f-0f06-433e-a125-d180685dcdac)


Step 8. Get admin password and Kubetcl sercet by running command on line 1 then expose grafana node

![363F6BAC-6D75-4807-AE53-86B5FBA2B218_4_5005_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/18f75d0f-6422-4b58-ae69-01b2fc39344d)


![A13D9A62-355F-49A9-ACD5-6D0A46EB1500](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/cfa6331b-e1dc-413c-b76d-a1b5670b031b)

![9BFB96B6-A557-4E23-8742-DF4F0A59764C](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/58276f23-2a8a-40f4-ab73-962739b28bea)



![7CDE1AF2-EED8-4CA1-8D9F-4928D90276DA_1_105_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/25a90246-edcc-4301-a4f4-ec93331ce4ac)



![3B63F747-8E0E-465B-9BE1-4DBD48666A84](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/8b8edfd1-c51d-4a0a-a643-375896ae7619)


