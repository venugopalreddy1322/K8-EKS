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

