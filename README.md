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
 kubectl expose -f flaskdemo-deploy.yaml --port=5000 --type=NodePort --dry-run=client -o yaml > svc.yaml

```