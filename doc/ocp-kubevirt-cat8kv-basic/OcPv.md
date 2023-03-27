# OpenShift Virtualization - Cat8000v Test Results

## Persistent Volume

```
# oc get pv -n default pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66
NAME                                       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                    STORAGECLASS   REASON   AGE
pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66   1Gi        RWO            Delete           Bound    default/cat8kv-01-day0   thin                    7m14s


# oc get pv -n default pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66 -o yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  annotations:
    kubernetes.io/createdby: vsphere-volume-dynamic-provisioner
    pv.kubernetes.io/bound-by-controller: "yes"
    pv.kubernetes.io/provisioned-by: kubernetes.io/vsphere-volume
  creationTimestamp: "2023-03-27T13:58:23Z"
  finalizers:
  - kubernetes.io/pv-protection
  name: pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66
  resourceVersion: "48628946"
  uid: 370dbc31-74c1-46c3-af9f-762f9de2402e
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 1Gi
  claimRef:
    apiVersion: v1
    kind: PersistentVolumeClaim
    name: cat8kv-01-day0
    namespace: default
    resourceVersion: "48628935"
    uid: f88b903c-26ca-4f4d-93d3-c785d2c2be66
  persistentVolumeReclaimPolicy: Delete
  storageClassName: thin
  volumeMode: Block
  vsphereVolume:
    volumePath: '[EU-SPDC-k8s-Datastore-WNAS] kubevols/kubevirt-nn4bm-dynamic-pvc-f88b903c-26ca-4f4d-93d3-c785d2c2be66.vmdk'
status:
  phase: Bound
```
