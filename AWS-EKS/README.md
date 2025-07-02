## Practical demos to demonstrate AWS EKS

eksctl:
. CLI tool for creating clusters on EKS
. Abstarcts lots of stuff - VPC, Subnet, Sec.Group etc. using CloudFormation

eksctl commands:
```bash
eksctl create cluster --name democluster --version 1.32 --node-type t3.micro --nodes 2
```
This command will create EKS cluster with k8s version 1.32 with 2 t3.micro nodes 

```bash
eksctl create cluster --name mycluster --version 1.32 --nodegroup-name <nodegroupname> --node-type t3.micro --nodes 2 --managed
```
This command create EKS cluster with managed node group

```bash
eksctl create cluster <name> --fargate
```
This command creates EKS cluster with Fargate Profile