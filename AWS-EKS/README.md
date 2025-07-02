## Practical demos to demonstrate AWS EKS

eksctl:
. CLI tool for creating clusters on EKS
. Abstarcts lots of stuff - VPC, Subnet, Sec.Group etc. using CloudFormation

eksctl commands:
```bash
eksctl create cluster --name <name> --version 1.32 --node-type t3.micro --nodes 2
```
