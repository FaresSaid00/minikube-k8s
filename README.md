Minikube Kubernetes Project

This project demonstrates how to set up a local Kubernetes cluster using Minikube and deploy a simple application.

📌 Step 1: Prepare the Environment

Before we begin, we need to set up the required tools:

1️⃣ Install Minikube
To install Minikube on Mac, run the following command in the Terminal:

brew install minikube
After installation, verify the version:

minikube version
2️⃣ Install kubectl
To install kubectl, run:

brew install kubectl
Verify the installation:

kubectl version --client
3️⃣ Install a Hypervisor (if not already installed)
Minikube requires virtualization, and the available options on macOS are:

Docker Desktop (recommended)
HyperKit
VirtualBox (for Intel CPUs)
If you don't have Docker Desktop, install it using:

brew install --cask docker
Make sure to launch Docker Desktop before starting Minikube.

📌 Step 2: Start Minikube

Now that we have the tools set up, let's start Minikube and create a local cluster.

1️⃣ Start Minikube
Open the Terminal and run the following command to create the cluster:

minikube start
By default, Minikube will use the appropriate driver based on your environment (like Docker or VirtualBox). If you want to specify the driver manually, use:

minikube start --driver=docker
(Replace docker with any other driver like virtualbox if you prefer).

2️⃣ Check the Cluster Status
After starting Minikube, use the following command to ensure the cluster is running:

kubectl cluster-info
You should see output like:

Kubernetes control plane is running at https://192.168.49.2:8443
CoreDNS is running at https://192.168.49.2:8443/api/v1/namespaces/kube-system/services/kube-dns
To check the available nodes:

kubectl get nodes
You should see something like:

NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   2m    v1.27.0
If the status is Ready, you're all set to proceed to the next step! 🎉

3️⃣ Open Minikube Dashboard (Optional)
If you want a graphical interface to monitor the cluster:

minikube dashboard
This will open a web page displaying the cluster information.



Next Steps




✅ 1️⃣ Create a Deployment to Run the Application

We will deploy a very simple application using the nginx image (a lightweight web server).

📌 Create a YAML file called deployment.yaml 

📌 To apply this Deployment, run the following command:

kubectl apply -f deployment.yaml
📌 Check that the Pods are running:

kubectl get pods
If everything is correct, you should see output like:

NAME                        READY   STATUS    RESTARTS   AGE
my-app-xxxxxx-yyyyy         1/1     Running   0          30s
my-app-xxxxxx-zzzzz         1/1     Running   0          30s


✅ 2️⃣ Create a Service to Access the Application

By default, Pods are not accessible from outside the Cluster, so we need to create a Service.

📌 Create a YAML file called service.yaml

📌 To apply this Service, run:

kubectl apply -f service.yaml
📌 Check that the Service is running:

kubectl get services
You should see output like:

NAME              TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
my-app-service   NodePort    10.108.226.95    <none>        80:30007/TCP   10s
✅ 3️⃣ Open the Application in a Browser

📌 Run the following command to get the Minikube IP address:

minikube ip
You will get an IP address like 192.168.49.2 (it may vary).

📌 Open your browser and enter:

http://<minikube-ip>:30007
🚀 If the Nginx page appears, the project is successfully running! 🎉
