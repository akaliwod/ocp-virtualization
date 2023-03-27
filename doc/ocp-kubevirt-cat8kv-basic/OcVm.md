# OpenShift Virtualization - Cat8000v Test Results

## Virtual Machine

```
# oc get vm -n default cat8kv-01
NAME        AGE     STATUS    READY
cat8kv-01   7m21s   Running   True


# oc get vm -n default cat8kv-01 -o yaml
apiVersion: kubevirt.io/v1
kind: VirtualMachine
metadata:
  annotations:
    kubemacpool.io/transaction-timestamp: "2023-03-27T13:58:50.130270995Z"
    kubevirt.io/latest-observed-api-version: v1
    kubevirt.io/storage-observed-api-version: v1alpha3
  creationTimestamp: "2023-03-27T13:58:50Z"
  generation: 1
  labels:
    app: cat8kv-01
  name: cat8kv-01
  namespace: default
  resourceVersion: "48634840"
  uid: fddfd8f2-649a-42f4-9534-a001c9273813
spec:
  dataVolumeTemplates:
  - apiVersion: cdi.kubevirt.io/v1beta1
    kind: DataVolume
    metadata:
      creationTimestamp: null
      name: cat8kv-01
      namespace: default
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
  running: true
  template:
    metadata:
      creationTimestamp: null
      labels:
        kubevirt.io/domain: cat8kv-01
        special: cat8kv-01
    spec:
      domain:
        cpu:
          cores: 1
          sockets: 1
          threads: 1
        devices:
          disks:
          - disk:
              bus: virtio
            name: rootdisk
          - cdrom:
              bus: sata
            name: cdromdisk
          interfaces:
          - macAddress: 02:6c:cf:00:00:67
            masquerade: {}
            name: default
          rng: {}
        machine:
          type: pc-q35-rhel8.6.0
        resources:
          requests:
            memory: 4Gi
      evictionStrategy: LiveMigrate
      hostname: cat8kv-01
      networks:
      - name: default
        pod: {}
      volumes:
      - dataVolume:
          name: cat8kv-01
        name: rootdisk
      - name: cdromdisk
        persistentVolumeClaim:
          claimName: cat8kv-01-day0
status:
  conditions:
  - lastProbeTime: null
    lastTransitionTime: "2023-03-27T14:02:07Z"
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: null
    message: 'cannot migrate VMI: PVC cat8kv-01 is not shared, live migration requires
      that all PVCs must be shared (using ReadWriteMany access mode)'
    reason: DisksNotLiveMigratable
    status: "False"
    type: LiveMigratable
  created: true
  printableStatus: Running
  ready: true
  volumeSnapshotStatuses:
  - enabled: false
    name: rootdisk
    reason: 'No VolumeSnapshotClass: Volume snapshots are not configured for this
      StorageClass [thick] [rootdisk]'
  - enabled: false
    name: cdromdisk
    reason: 'No VolumeSnapshotClass: Volume snapshots are not configured for this
      StorageClass [thin] [cdromdisk]'
```
