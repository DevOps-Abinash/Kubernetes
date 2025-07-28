**Kubernetes Architect**

<img width="1090" height="468" alt="image" src="https://github.com/user-attachments/assets/60e205e3-6550-4f6b-afb0-ab9705f9e61f" />

 
🔷 **Master Node Components (Control Plane)**
The Master Node manages the cluster and schedules workloads.
1.	Kubectl
o	A CLI tool used by users/admins to communicate with the cluster.
o	Sends commands to the API Server.
2.	API Server
o	Frontend of the control plane.
o	Accepts and processes REST operations (create, delete, scale, etc.).
o	Acts as the communication hub between all components.
3.	Scheduler
o	Assigns newly created pods to appropriate worker nodes based on resources and policies.
4.	Controller Manager
o	Manages controllers like ReplicationController, NodeController, etc.
o	Ensures the desired state matches the actual state.
5.	etcd
o	Key-value store used to store all cluster data (configuration, state, secrets, etc.).
o	Acts as Kubernetes’ database.
________________________________________


🔶 **Worker Node Components**
Worker Nodes run your application workloads in Pods.
1.	Kubelet
o	Agent that runs on each worker node.
o	Communicates with the API Server to receive instructions.
o	Ensures containers are running as expected in pods.
2.	Kube-Proxy
o	Manages networking for the node.
o	Forwards traffic to the correct pod using IP tables or IPVS.
3.	Pods
o	Smallest unit in Kubernetes.
o	Contains one or more containers (typically Docker).
o	Each pod runs on a Worker Node.
4.	Docker
o	Container runtime used to run containerized applications inside pods.
________________________________________

🔁 **How it works:**

•	kubectl sends a command to the API Server.

•	Scheduler picks a worker node to place the pod.

•	Kubelet on that node runs the pod using Docker.

•	Kube-Proxy ensures network communication to/from the pod.

•	Controller Manager ensures the pod keeps running.

•	Cluster state is saved in etcd.
