# observability-

**Observability** is the ability to understand the internal state and behavior of a system by examining its external outputs, such as logs, metrics, and traces. It helps teams proactively identify, debug, and resolve issues in complex, distributed systems.

### **Key Pillars of Observability**  
1. **Logs**  
   - Records of discrete events that happened within a system.  
   - Help in troubleshooting errors and understanding what happened at a specific point in time.

2. **Metrics**  
   - Numerical data that represents the system's performance and health over time.  
   - Examples: CPU usage, memory consumption, error rates, and latency.

3. **Traces**  
   - Show the flow of requests across different services in a distributed system.  
   - Provide end-to-end visibility into a request's lifecycle.

### **Why Observability is Important**  
- **Faster Troubleshooting:** Quickly identify and resolve issues.  
- **Proactive Monitoring:** Detect problems before they impact users.  
- **Improved Performance:** Optimize system performance based on collected insights.  
- **Scalability:** Ensure reliable operations even as systems grow more complex.

### **Observability vs Monitoring**  
- **Monitoring:** Collecting and analyzing predefined metrics and logs.  
- **Observability:** Understanding and exploring unknown issues by analyzing data from logs, metrics, and traces.

### **Popular Observability Tools**  
- **Prometheus** (Metrics)  
- **Grafana** (Visualization)  
- **ELK Stack** (Elasticsearch, Logstash, Kibana for Logs)  
- **Jaeger / Zipkin** (Tracing)  
- **Datadog** (Comprehensive Observability Platform)  
![image](https://github.com/user-attachments/assets/0460bb9a-4b38-46cd-8d9d-16d977d5149b)

**K8s Applictaion  monitoring Using Prometheus and Grafana** 
<img width="1680" alt="Screenshot 2025-01-01 at 2 09 03 PM" src="https://github.com/user-attachments/assets/05f38b94-f0e7-482a-abe0-50b245daed85" />

**Tech Stack:**
- AWS EC2 (t2. medium)
- Helm
- K8S Cluster
- Prometheus
- Grafana


  Step 1 : install.sh
Commands:
chmod 777 install.sh
./install.sh 

Step 2: Install Docker for Kind Cluster
Commands:
sudo apt-get install docker.io -y
sudo apt-get update
docker --version
sudo usermod -aG docker $USER && newgrp
docker ps 



Step 3: kind Cluster Insatlling
-config .yml

Commands:
kubectl version
kind create cluster --name=mycluster --config=config.yml # command for create cluster
kubectl get nodes

Step 4: Install Helm 


 **kubectl get namespaces
 kubectl create namespace monitoring 
 helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
 helm repo list
 helm repo update
helm install prometheus-stack prometheus-community/kube-prometheus-stack --namespace monitoring --set prometheus.service.nodePort=3000 --set grafana.service.nodePort=31000 --set grafana.service.type=NodePort --set prometheus.service.type=NodePort
kubectl get pods -n monitoring
kubectl get nodes
kubectl get svc -n monitoring
kubectl port-forward svc/prometheus-stack-kube-prom-prometheus 9090:9090 -n monitoring --address=0.0.0.0 &
kubectl port-forward svc/prometheus-stack-grafana 3000:80 -n monitoring --address=0.0.0.0 &
sudo apt-get update 
kubectl port-forward svc/prometheus-stack-grafana 3000:80 -n monitoring --address=0.0.0.0 &
kubectl get secret prometheus-stack-grafana  -n monitoring -o jsonpath="{.data.admin-password}" | base64 --decode # this is grafana password


Step 5 : Now Install any appliction for monitoring 
Commands: 
git clone https://github.com/LondheShubham153/k8s-kind-voting-app.git
cd k8s-kind-voting-app/
ls
cd k8s-specifications/
ls
 kubectl apply -f .
 kubectl get pods
 k get svc
kubectl get svc 
kubectl port-forward svc/vote 5000:5000 --address=0.0.0.0 &
kubectl port-forward svc/result 5001:5001 --address=0.0.0.0 &

AWS Inbound Security (open Ports )
<img width="1680" alt="Screenshot 2025-01-01 at 5 36 42 PM" src="https://github.com/user-attachments/assets/45c079fc-f66c-446d-9b05-601b8ce15216" />


Prometheus :
<img width="1680" alt="Screenshot 2025-01-01 at 5 37 08 PM" src="https://github.com/user-attachments/assets/e39c3400-fe00-4006-b96a-9c40656abc9c" />

Grafana Dasboard::
<img width="1680" alt="Screenshot 2025-01-01 at 5 37 39 PM" src="https://github.com/user-attachments/assets/bbbb2eeb-ca74-425f-849f-c256c6e1d6ae" />


OutPut:

<img width="1680" alt="Screenshot 2025-01-01 at 5 37 47 PM" src="https://github.com/user-attachments/assets/0de406f4-8c15-47eb-b8ca-0113624c082d" />
<img width="1680" alt="Screenshot 2025-01-01 at 5 37 58 PM" src="https://github.com/user-attachments/assets/c1bab8f7-bee4-4516-a83d-074131be7ea9" />












