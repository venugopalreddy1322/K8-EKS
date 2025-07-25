## Practical demos to demonstrate AWS EKS

Installation of eksctl
Prerequisites
1. AWS CLI installed and configured
2. kubectl installed
After
3. Install eksctl using chocolatey for windows
```bash
choco install -y eksctl
```
Update eksctl:
```bash
choco upgrade -y eksctl
```

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

## Declarative way
Create cluster using yaml manifest
```bash
eksctl create cluster --config-file=<file-name>
```
This will create a EKS cluster with configurations specified in yaml file

Create and add nodegroups to cluster using yaml file
```bash
eksctl create nodegroup --config-file=eksctl-create-ng.yaml
```
This will create nodegroups specified in the yaml  file 'eksctl-create-ng.yaml'

```bash
eksctl delete cluster --name=config-file --region us-west-2
```
to delete a cluster in specific region 

```bash
 eksctl delete cluster --name=config-file --region=us-west-2 --disable-nodegroup-eviction
```
Ignore nodegroup eviction while deleting cluster