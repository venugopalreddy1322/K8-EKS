# K8-EKS

A collection of imperative `kubectl` commands to create and manage Kubernetes resources on Amazon EKS.

---

## 📌 Prerequisites
Ensure you have the following before executing these commands:
- Kubernetes CLI (`kubectl`) installed and configured.
- Access to an EKS cluster.
- Admin privileges (especially on Windows, for editing the hosts file).

---

## ⚙️ Imperative Commands

### 1. Create a Pod
Generate a Pod YAML for an Nginx container:

```bash
kubectl run nginx-pod --image=nginx --dry-run=client -o yaml > pod.yaml
```
For syntax and help:
```bash
kubectl create pod -h
```
---
### 2. Create Deployment
```bash
kubectl create deploy flaskdemo --image=venu1322/vproject:5 --replicas=2 --port=5000 --dry-run=client -o yaml > flaskdemo-deploy.yaml
```

---
### 3. Create a Service to Expose the Deployment
```bash
kubectl expose deploy flaskdemo --port=5000 --target-port=50000 --type=NodePort --dry-run=client -o yaml > svc.yaml
```
**OR**

```bash
kubectl expose -f flaskdemo-deploy.yaml --port=5000 --type=NodePort --dry-run=client -o yaml > svc.yaml
```

---
### 4. Create an Ingress

#### a. Simple Ingress
```bash
kubectl create ingress simple-ingress --rule="flaskdemo.com/*=svc-clusterip:5000" --class=default --annotation nginx.ingress.kubernetes.io/rewrite-target=/ --annotation nginx.ingress.kubernetes.io/ssl-redirect="false" --dry-run=client -o yaml > simple-ingress.yaml
```
#### b. Multi-path, Single Host Ingress
```bash
kubectl create ingress simple-ingress --rule="flaskdemo.com/app1*=svc-svc1:5000" --rule="flaskdemo.com/app2*=svc-svc2:8080" --class=default --annotation nginx.ingress.kubernetes.io/rewrite-target=/ --annotation nginx.ingress.kubernetes.io/ssl-redirect="false" --dry-run=client -o yaml > simple-ingress.yaml
```

---

-------------------------------------------------------
# K8-EKS

## Imperative commands:
1. create pod:
```bash
$  kubectl run nginx-pod --image nginx --dry-run=client -o yaml > pod.yaml
```
For syntax and help:
```bash
$ kubectl create pod -h
```

2. create deployment:
```bash
 kubectl create deploy flaskdemo --image=venu1322/vproject:5 --replicas=2 --port=5000 --dry-run=client -o yaml > flaskdemo-deploy.yaml

```
3. create a service to expose the above created deployment
```bash
 kubectl expose deploy flaskdemo --port=5000 --target-port=50000 --type=NodePort --dry-run=client -o yaml > svc.yaml

```
OR

```bash
 kubectl expose -f flaskdemo-deploy.yaml --port=5000 --type=NodePort --dry-run=client -o yaml > svc.yaml

```
4. Create a Ingress
    Simple:
```bash
 kubectl create ingress simple-ingress --rule="flaskdemo.com/*=svc-clusterip:5000" --class=default --annotation nginx.ingress.kubernetes.io/rewrite-target=/ --annotation nginx.ingress.kubernetes.io/ssl-redirect="false" --dry-run=client -o yaml > simple-ingress.yaml
 ```
    Multi-path single host

```bash
 kubectl create ingress simple-ingress --rule="flaskdemo.com/app1*=svc-svc1:5000" --rule="flaskdemo.com/app2*=svc-svc2:8080" --class=default --annotation nginx.ingress.kubernetes.io/rewrite-target=/ --annotation nginx.ingress.kubernetes.io/ssl-redirect="false" --dry-run=client -o yaml > simple-ingress.yaml
 ```
 NOTE: when you are working on Windows laptop 
 Update windows hosts file with adminstrative previliges
 ```bash
  vi C:/Windows/System32/drivers/etc/hosts
```
example: 
172.30.130.64 flaskdemo.com