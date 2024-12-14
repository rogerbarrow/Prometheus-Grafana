# Kubernetes Monitoring Prometheus and Grafanaa

![image](https://github.com/user-attachments/assets/69bcd56b-1a47-4bad-8738-f5914f9cae21)

In today’s rapidly advancing world of cloud-native technologies, Kubernetes has become the go-to platform for orchestrating containerized applications. To maintain the reliability and performance of these applications and their supporting infrastructure, robust monitoring is essential. Prometheus and Grafana are two widely-used tools that make this possible. In this guide, we’ll demonstrate how to set up Prometheus and Grafana on a Kubernetes cluster using Helm, a powerful package manager for Kubernetes applications.

 # Why Choose Prometheus and Grafana?

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

# Architecture

![image](https://github.com/user-attachments/assets/ab5f083e-6253-40fa-aeef-f7853b510615)

# What is Grafana?

![image](https://github.com/user-attachments/assets/e2e25e62-f3b5-4cd1-a7b5-448976e4d36a)


Grafana is a popular open-source platform for monitoring, visualization, and observability. It enables users to query, analyze, and visualize data from a wide range of sources through highly customizable, interactive dashboards. Grafana is often used in combination with monitoring tools like Prometheus, InfluxDB, or Elasticsearch to provide actionable insights into system performance, application metrics, and business data.

Key Features of Grafana:
Data Visualization:
Create dynamic and customizable dashboards with charts, graphs, and alerts.
Supports various visualization types, such as heatmaps, pie charts, and time-series graphs.
2. Multiple Data Sources:

Integrates with a wide range of data sources, including Prometheus, Elasticsearch, AWS CloudWatch, InfluxDB, MySQL, and more.
3. Alerting:

Set up real-time alerts based on defined thresholds or conditions, and deliver them via email, Slack, PagerDuty, or other channels.
4. Plugins and Extensibility:

Extend functionality with plugins for new visualizations, data sources, and applications.

5. User Management:

Provides multi-user support with role-based access control, allowing collaboration across teams.
6. Open Source and Community Support:

As an open-source project, Grafana benefits from a large community and frequent updates.
Use Cases:
System Monitoring: Visualize server performance metrics like CPU usage, memory, and disk I/O.
Application Monitoring: Track API response times, error rates, and throughput.
Business Metrics: Monitor KPIs like website traffic, sales performance, or user behavior.
IoT and Industrial Data: Display sensor readings and machine performance in real-time.
Why Grafana?
Grafana stands out for its flexibility, ease of use, and ability to unify data from disparate sources into a single cohesive view. Whether you’re managing cloud infrastructure, troubleshooting application performance, or analyzing business trends, Grafana simplifies the process of turning raw data into actionable insights.




# Pre-Requisite
Before we dive into the setup process, make sure you have the following prerequisites:

A Kubernetes cluster up and running to install minikube
Helm installed on your local machine and configured to work with your Kubernetes cluster.

# Step 1: Installing Prometheus with Helm
Open your terminal and navigate to the directory where you want to install Prometheus.
Run the following command to add the Prometheus Helm chart repository:
![image](https://github.com/user-attachments/assets/fd25dd93-c1ee-4cdc-9aa7-71dd348f4e7c)

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

![image](https://github.com/user-attachments/assets/fc24e9bb-0eeb-44b3-be0b-aaff719f90c0)


![7CDE1AF2-EED8-4CA1-8D9F-4928D90276DA_1_105_c](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/25a90246-edcc-4301-a4f4-ec93331ce4ac)



![3B63F747-8E0E-465B-9BE1-4DBD48666A84](https://github.com/rogerbarrow/Prometheus-Grafana/assets/46138186/8b8edfd1-c51d-4a0a-a643-375896ae7619)


