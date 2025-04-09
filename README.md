# SIT323 6.2C - Interacting with a Deployed Kubernetes Application

This task builds upon my previous work in 6.1P, where I successfully deployed a Node.js calculator app to a local Kubernetes cluster. In this part, I focused on interacting with the deployed application using `kubectl` commands and port-forwarding techniques to explore service accessibility and cluster interaction.

## 📂 Repository

All code and configuration files are hosted on GitHub:  
[https://github.com/yuwei-zhui/sit323-2025-prac6c](https://github.com/yuwei-zhui/sit323-2025-prac6c)

## 🎯 Task Objective

- Confirm that the Node.js application is running correctly on the Kubernetes cluster.
- Use `kubectl` to inspect Pods and Services.
- Use `kubectl port-forward` to map a Service port to a local port.
- Access the application via a browser at `localhost:<port>` using the forwarded connection.

## 🛠️ Prerequisites

- Docker Desktop (with Kubernetes enabled)
- Node.js
- Git
- Visual Studio Code (or any code editor)
- Kubernetes CLI (`kubectl`)
- A basic understanding of Docker & Kubernetes

## 🔍 Step-by-Step Instructions

### Step 1: Check Pod and Service Status

After deploying the application in 6.1P, I first verified that my application is running:

```bash
kubectl get pods
kubectl get services
```

This confirmed that:
- The Pods were in a `Running` state.
- The Service `nodejs-service` was up and had a proper target port (`3323`) and nodePort (`30323`).

### Step 2: Use Port Forwarding

To access the application using a local port instead of the nodePort, I used `kubectl port-forward`. This method is especially useful in controlled environments or cloud platforms that don’t expose `NodePort`.

```bash
kubectl port-forward service/nodejs-service 323:3323
```

- This mapped local port `323` to the Service's target port `3323`.
- Then I was able to open the app in my browser using:

```
http://localhost:323
```

### Step 3: Interact with the Application

The app was accessible and fully functional through the port-forwarded address. This approach provided a seamless way to test and debug my deployed microservice without modifying the existing Kubernetes configurations.

### Step 4: Document the Work and Push to GitHub

After verifying the application’s behavior, I committed all updates and documentation to GitHub:

```bash
git add .
git commit -m "Add 6.2C interaction instructions"
git push origin main
```

My repository includes:
- `Dockerfile`
- `deployment.yaml`
- `service.yaml`
- Source code for the Node.js calculator app
- README documentation for 6.1P and 6.2C

## ✅ Result

By interacting with the application using `kubectl`, I practiced Kubernetes fundamentals like inspecting Pods and Services and forwarding local traffic. This hands-on experience further strengthened my understanding of cloud native deployment workflows.

## 🌐 Useful Commands Summary

| Command | Description |
|--------|-------------|
| `kubectl get pods` | List all pods in the cluster |
| `kubectl get services` | List services and their cluster IPs/ports |
| `kubectl port-forward service/nodejs-service 8080:3323` | Forward Service port to localhost for browser access |
| `kubectl describe pod <pod-name>` | Inspect pod details, including container port |

## 📘 Conclusion

This task extended my practical experience with Kubernetes by shifting from deployment to interaction. I learned how to inspect my application’s runtime status, access it securely via port-forwarding, and ensure smooth communication with the running microservice—all essential skills for building and maintaining cloud native applications.
