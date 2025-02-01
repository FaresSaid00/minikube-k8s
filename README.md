Minikube Kubernetes Project

This project demonstrates how to set up a local Kubernetes cluster using Minikube and deploy a simple application.

📌 Step 1: Prepare the Environment


1️⃣ Install Minikube
brew install minikube
After installation, verify the version:

2️⃣ Install kubectl
brew install kubectl
Verify the installation:

3️⃣ Install Docker
brew install --cask docker
Make sure to launch Docker Desktop before starting Minikube.

📌 Step 2: Start Minikube

1️⃣ Start Minikube
Open the Terminal and run the following command to create the cluster:

minikube start
minikube start --driver=docker


2️⃣ Check the Cluster Status
After starting Minikube, use the following command to ensure the cluster is running:
-kubectl cluster-info

To check the available nodes:
-kubectl get nodes

3️⃣ Open Minikube Dashboard (Optional)
If you want a graphical interface to monitor the cluster:
minikube dashboard

🔥Next Steps

✅ 1️⃣ Create a Deployment to Run the Application

We will deploy a very simple application using the nginx image (a lightweight web server).

📌 Create a YAML file called deployment.yaml 

📌 To apply this Deployment, run the following command:

kubectl apply -f deployment.yaml

📌 Check that the Pods are running:
kubectl get pods

✅ 2️⃣ Create a Service to Access the Application

By default, Pods are not accessible from outside the Cluster, so we need to create a Service.

📌 Create a YAML file called service.yaml

📌 To apply this Service, run:

kubectl apply -f service.yaml
📌 Check that the Service is running:
-kubectl get services

✅ 3️⃣ Open the Application in a Browser

📌 Run the following command to get the Minikube IP address:

minikube ip
You will get an IP address like 192.168.49.2 (it may vary).

📌 Open your browser and enter: http://< ip address of minikube>:30007

🚀 If the Nginx page appears, the project is successfully running! 🎉
