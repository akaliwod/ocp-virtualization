# OpenShift Virtualization - Cat8000v Test Results

## Virtual Machine Instance

```
# oc get vmi -n default cat8kv-01
NAME        AGE     PHASE     IP             NODENAME                      READY
cat8kv-01   4m21s   Running   10.128.2.190   kubevirt-nn4bm-worker-9fxdj   True


# oc get vmi -n default cat8kv-01 -o yaml
apiVersion: kubevirt.io/v1
kind: VirtualMachineInstance
metadata:
  annotations:
    kubevirt.io/latest-observed-api-version: v1
    kubevirt.io/storage-observed-api-version: v1alpha3
  creationTimestamp: "2023-03-27T14:01:56Z"
  finalizers:
  - kubevirt.io/virtualMachineControllerFinalize
  - foregroundDeleteVirtualMachine
  generation: 8
  labels:
    kubevirt.io/domain: cat8kv-01
    kubevirt.io/nodeName: kubevirt-nn4bm-worker-9fxdj
    special: cat8kv-01
  name: cat8kv-01
  namespace: default
  ownerReferences:
  - apiVersion: kubevirt.io/v1
    blockOwnerDeletion: true
    controller: true
    kind: VirtualMachine
    name: cat8kv-01
    uid: fddfd8f2-649a-42f4-9534-a001c9273813
  resourceVersion: "48634838"
  uid: 3cbb32a1-f11c-4065-99e6-62ce670bff12
spec:
  domain:
    cpu:
      cores: 1
      model: host-model
      sockets: 1
      threads: 1
    devices:
      disks:
      - disk:
          bus: virtio
        name: rootdisk
      - cdrom:
          bus: sata
          readonly: true
          tray: closed
        name: cdromdisk
      interfaces:
      - macAddress: 02:6c:cf:00:00:67
        masquerade: {}
        name: default
      rng: {}
    features:
      acpi:
        enabled: true
    firmware:
      uuid: 30592aed-01ef-5ef9-8a5a-512013936f65
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
  activePods:
    23eaea49-e931-4afb-8eac-598e5936469e: kubevirt-nn4bm-worker-9fxdj
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
  guestOSInfo: {}
  interfaces:
  - infoSource: domain
    ipAddress: 10.128.2.190
    ipAddresses:
    - 10.128.2.190
    mac: 02:6c:cf:00:00:67
    name: default
  launcherContainerImageVersion: registry.redhat.io/container-native-virtualization/virt-launcher@sha256:ae751656eccca94e1f2e55dc8fb1339565b3f83256b0dbc8be6720e8a8db2d7b
  migrationMethod: BlockMigration
  migrationTransport: Unix
  nodeName: kubevirt-nn4bm-worker-9fxdj
  phase: Running
  phaseTransitionTimestamps:
  - phase: Pending
    phaseTransitionTimestamp: "2023-03-27T14:01:56Z"
  - phase: Scheduling
    phaseTransitionTimestamp: "2023-03-27T14:01:56Z"
  - phase: Scheduled
    phaseTransitionTimestamp: "2023-03-27T14:02:07Z"
  - phase: Running
    phaseTransitionTimestamp: "2023-03-27T14:02:09Z"
  qosClass: Burstable
  runtimeUser: 107
  virtualMachineRevisionName: revision-start-vm-fddfd8f2-649a-42f4-9534-a001c9273813-1
  volumeStatus:
  - name: cdromdisk
    persistentVolumeClaimInfo:
      accessModes:
      - ReadWriteOnce
      capacity:
        storage: 1Gi
      filesystemOverhead: "0.055"
      requests:
        storage: 1Gi
      volumeMode: Block
    target: sda
  - name: rootdisk
    persistentVolumeClaimInfo:
      accessModes:
      - ReadWriteOnce
      capacity:
        storage: 16Gi
      filesystemOverhead: "0.055"
      requests:
        storage: 16Gi
      volumeMode: Block
    target: vda
```
