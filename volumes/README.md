# Kubernetes StorageClass with Local Path Provisioner

## Overview
In Kubernetes, a **StorageClass** defines how storage volumes are dynamically provisioned. It abstracts storage configurations and enables automatic volume creation when a PersistentVolumeClaim (PVC) requests storage. This eliminates the need for manually creating PersistentVolumes (PVs).

For our demo, we will set up **Local Path Provisioner** in a kubeadm cluster to dynamically provision `hostPath` volumes.

---

## StorageClass Significance
- **Dynamic Provisioning**: Automatically creates PVs when a PVC requests storage.
- **Storage Policies**: Defines reclaim policies (`Delete` or `Retain`).
- **Supports Various Backends**: Works with cloud storage (AWS EBS, GCE PD), local storage (`hostPath`), and CSI drivers.
- **Volume Binding Modes**:
  - `Immediate`: PV is provisioned instantly when a PVC is created.
  - `WaitForFirstConsumer`: PV is provisioned when a pod requests storage.

---

## Install Local Path Provisioner on Kubeadm

### 1️⃣ **Install Local Path Provisioner**
Apply the Local Path Provisioner manifest:

```bash
kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/master/deploy/local-path-storage.yaml

```