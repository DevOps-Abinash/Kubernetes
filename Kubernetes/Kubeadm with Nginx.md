✅ Step-by-Step: Kubernetes on EC2 with NGINX Deployment
🔸 1. Launch Two EC2 Instances
Instance Type: t2.medium

OS: Ubuntu 20.04 or 22.04

Name one master-node, another worker-node

Security Group Inbound Rules:

TCP 22 (SSH)

TCP 6443 (Kubernetes API)

TCP 30080 (NodePort for NGINX)

ICMP (Optional: Ping)

🔸 2. Follow the Kubeadm Installtion Guide 


🔸 3. Create YAML Files (on master-node)

✅ deployment.yml
```bash
sudo vim deployment.yml
```
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

*Paste and save with :wq*

✅ service.yml
```bash
sudo vim service.yml
```
```bash
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  labels:
    app: nginx
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30080
```
*Paste and save with :wq*

🔸 4. Deploy to Kubernetes
```bash
kubectl apply -f deployment.yml
kubectl apply -f service.yml
kubectl get all
```
🔸 9. Access NGINX
Open your browser and access:

```bash
http://<any-ec2-public-ip>:30080
```
Make sure port 30080 is added to your EC2 security group.

