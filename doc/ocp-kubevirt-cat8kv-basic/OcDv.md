# OpenShift Virtualization - Cat8000v Test Results

## Data Volume

```
# oc get dvs -n default cat8kv-01
NAME        PHASE       PROGRESS   RESTARTS   AGE
cat8kv-01   Succeeded   100.0%     1          6m32s


# oc get dvs -n default cat8kv-01 -o yaml
apiVersion: cdi.kubevirt.io/v1beta1
kind: DataVolume
metadata:
  annotations:
    cdi.kubevirt.io/cloneType: network
    cdi.kubevirt.io/storage.clone.token: eyJhbGciOiJQUzI1NiJ9.eyJleHAiOjE2Nzk5MjU4MzAsImlhdCI6MTY3OTkyNTUzMCwiaXNzIjoiY2RpLWFwaXNlcnZlciIsIm5hbWUiOiJjYXQ4a3YtZHYiLCJuYW1lc3BhY2UiOiJkZWZhdWx0IiwibmJmIjoxNjc5OTI1NTMwLCJvcGVydGF0aW9uIjoiQ2xvbmUiLCJwYXJhbXMiOnsidGFyZ2V0TmFtZSI6ImNhdDhrdi0wMSIsInRhcmdldE5hbWVzcGFjZSI6ImRlZmF1bHQifSwicmVzb3VyY2UiOnsiZ3JvdXAiOiIiLCJyZXNvdXJjZSI6InBlcnNpc3RlbnR2b2x1bWVjbGFpbXMiLCJ2ZXJzaW9uIjoidjEifX0.g9r62Yi6BE2u5QQhf68Ixuy8jjGpGtljkDdKEEa3lcfY4HC3I4Zzeb3gpPLfyGp_qXSVMJP7wr8HGtubiPaebM4hjMadaF9boAHZC1wufW40MKI3xoq4AMsR_jbLd1MAtCp8qjimw_iuE7nUQdenvs7k2MXipxQP76tLRQM2Q9yCdc-qUeW4YUujH3O9CpQDroMt9qqS5AXw757YD6SJOcQsz9vfqv0kMDR31-_9CE7finb9zqSjoyY65PknbTJB3DdCvm8VDn5ljEcbD6dQP8WTQ9c2kdujfYp0ESpk13ROn_njSbBU5CiHEs8mHWavZECUNfJgKTr_38YBtuSYpw
  creationTimestamp: "2023-03-27T13:58:50Z"
  generation: 113
  labels:
    kubevirt.io/created-by: fddfd8f2-649a-42f4-9534-a001c9273813
  name: cat8kv-01
  namespace: default
  ownerReferences:
  - apiVersion: kubevirt.io/v1
    blockOwnerDeletion: true
    controller: true
    kind: VirtualMachine
    name: cat8kv-01
    uid: fddfd8f2-649a-42f4-9534-a001c9273813
  resourceVersion: "48634454"
  uid: ac4a1f24-ac80-41b3-973a-9ecf9bd69ded
spec:
  pvc:
    accessModes:
    - ReadWriteOnce
    resources:
      requests:
        storage: 16Gi
    storageClassName: thick
    volumeMode: Block
  source:
    pvc:
      name: cat8kv-dv
      namespace: default
status:
  claimName: cat8kv-01
  conditions:
  - lastHeartbeatTime: "2023-03-27T13:58:56Z"
    lastTransitionTime: "2023-03-27T13:58:56Z"
    message: PVC cat8kv-01 Bound
    reason: Bound
    status: "True"
    type: Bound
  - lastHeartbeatTime: "2023-03-27T14:01:56Z"
    lastTransitionTime: "2023-03-27T14:01:56Z"
    status: "True"
    type: Ready
  - lastHeartbeatTime: "2023-03-27T14:01:53Z"
    lastTransitionTime: "2023-03-27T14:01:53Z"
    message: Clone Complete
    reason: Completed
    status: "False"
    type: Running
  phase: Succeeded
  progress: 100.0%
  restartCount: 1
```
