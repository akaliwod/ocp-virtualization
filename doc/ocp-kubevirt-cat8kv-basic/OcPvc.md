# OpenShift Virtualization - Cat8000v Test Results

## Persistent Volume Claim

```
# oc get pvc -n default cat8kv-01-day0
NAME             STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
cat8kv-01-day0   Bound    pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66   1Gi        RWO            thin           7m8s


# oc get pvc -n default cat8kv-01-day0 -o yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  annotations:
    cdi.kubevirt.io/storage.condition.bound: "true"
    cdi.kubevirt.io/storage.condition.bound.message: ""
    cdi.kubevirt.io/storage.condition.bound.reason: ""
    cdi.kubevirt.io/storage.condition.running: "false"
    cdi.kubevirt.io/storage.condition.running.message: Upload Complete
    cdi.kubevirt.io/storage.condition.running.reason: Completed
    cdi.kubevirt.io/storage.contentType: ""
    cdi.kubevirt.io/storage.pod.phase: Succeeded
    cdi.kubevirt.io/storage.pod.ready: "false"
    cdi.kubevirt.io/storage.pod.restarts: "0"
    cdi.kubevirt.io/storage.preallocation.requested: "false"
    cdi.kubevirt.io/storage.upload.target: ""
    cdi.kubevirt.io/storage.uploadPodName: cdi-upload-cat8kv-01-day0
    pv.kubernetes.io/bind-completed: "yes"
    pv.kubernetes.io/bound-by-controller: "yes"
    volume.beta.kubernetes.io/storage-provisioner: kubernetes.io/vsphere-volume
    volume.kubernetes.io/storage-provisioner: kubernetes.io/vsphere-volume
  creationTimestamp: "2023-03-27T13:58:21Z"
  finalizers:
  - kubernetes.io/pvc-protection
  labels:
    app: containerized-data-importer
    app.kubernetes.io/component: storage
    app.kubernetes.io/managed-by: cdi-controller
    app.kubernetes.io/part-of: hyperconverged-cluster
    app.kubernetes.io/version: 4.11.3
  name: cat8kv-01-day0
  namespace: default
  ownerReferences:
  - apiVersion: cdi.kubevirt.io/v1beta1
    blockOwnerDeletion: true
    controller: true
    kind: DataVolume
    name: cat8kv-01-day0
    uid: 14fd04f1-6323-430c-9747-0e1e4abf662c
  resourceVersion: "48629677"
  uid: f88b903c-26ca-4f4d-93d3-c785d2c2be66
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: thin
  volumeMode: Block
  volumeName: pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66
status:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 1Gi
  phase: Bound
```
