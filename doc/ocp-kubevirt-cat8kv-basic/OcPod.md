# OpenShift Virtualization - Cat8000v Test Results

## Virtual Machine Launcher Pod

```
# oc get pod -n default virt-launcher-cat8kv-01-8dzl7
NAME                            READY   STATUS    RESTARTS   AGE
virt-launcher-cat8kv-01-8dzl7   1/1     Running   0          3m54s


# oc get pod -n default virt-launcher-cat8kv-01-8dzl7 -o yaml
apiVersion: v1
kind: Pod
metadata:
  annotations:
    k8s.v1.cni.cncf.io/network-status: |-
      [{
          "name": "openshift-sdn",
          "interface": "eth0",
          "ips": [
              "10.128.2.190"
          ],
          "default": true,
          "dns": {}
      }]
    k8s.v1.cni.cncf.io/networks-status: |-
      [{
          "name": "openshift-sdn",
          "interface": "eth0",
          "ips": [
              "10.128.2.190"
          ],
          "default": true,
          "dns": {}
      }]
    kubectl.kubernetes.io/default-container: compute
    kubevirt.io/domain: cat8kv-01
    kubevirt.io/migrationTransportUnix: "true"
    post.hook.backup.velero.io/command: '["/usr/bin/virt-freezer", "--unfreeze", "--name",
      "cat8kv-01", "--namespace", "default"]'
    post.hook.backup.velero.io/container: compute
    pre.hook.backup.velero.io/command: '["/usr/bin/virt-freezer", "--freeze", "--name",
      "cat8kv-01", "--namespace", "default"]'
    pre.hook.backup.velero.io/container: compute
    traffic.sidecar.istio.io/kubevirtInterfaces: k6t-eth0
  creationTimestamp: "2023-03-27T14:01:56Z"
  generateName: virt-launcher-cat8kv-01-
  labels:
    kubevirt.io: virt-launcher
    kubevirt.io/created-by: 3cbb32a1-f11c-4065-99e6-62ce670bff12
    kubevirt.io/domain: cat8kv-01
    special: cat8kv-01
    vm.kubevirt.io/name: cat8kv-01
  name: virt-launcher-cat8kv-01-8dzl7
  namespace: default
  ownerReferences:
  - apiVersion: kubevirt.io/v1
    blockOwnerDeletion: true
    controller: true
    kind: VirtualMachineInstance
    name: cat8kv-01
    uid: 3cbb32a1-f11c-4065-99e6-62ce670bff12
  resourceVersion: "48634763"
  uid: 23eaea49-e931-4afb-8eac-598e5936469e
spec:
  automountServiceAccountToken: false
  containers:
  - command:
    - /usr/bin/virt-launcher-monitor
    - --qemu-timeout
    - 275s
    - --name
    - cat8kv-01
    - --uid
    - 3cbb32a1-f11c-4065-99e6-62ce670bff12
    - --namespace
    - default
    - --kubevirt-share-dir
    - /var/run/kubevirt
    - --ephemeral-disk-dir
    - /var/run/kubevirt-ephemeral-disks
    - --container-disk-dir
    - /var/run/kubevirt/container-disks
    - --grace-period-seconds
    - "45"
    - --hook-sidecars
    - "0"
    - --ovmf-path
    - /usr/share/OVMF
    - --run-as-nonroot
    env:
    - name: XDG_CACHE_HOME
      value: /var/run/kubevirt-private
    - name: XDG_CONFIG_HOME
      value: /var/run/kubevirt-private
    - name: XDG_RUNTIME_DIR
      value: /var/run
    - name: POD_NAME
      valueFrom:
        fieldRef:
          apiVersion: v1
          fieldPath: metadata.name
    image: registry.redhat.io/container-native-virtualization/virt-launcher@sha256:ae751656eccca94e1f2e55dc8fb1339565b3f83256b0dbc8be6720e8a8db2d7b
    imagePullPolicy: IfNotPresent
    name: compute
    resources:
      limits:
        devices.kubevirt.io/kvm: "1"
        devices.kubevirt.io/tun: "1"
        devices.kubevirt.io/vhost-net: "1"
      requests:
        cpu: 100m
        devices.kubevirt.io/kvm: "1"
        devices.kubevirt.io/tun: "1"
        devices.kubevirt.io/vhost-net: "1"
        ephemeral-storage: 50M
        memory: "4555014145"
    securityContext:
      capabilities:
        add:
        - NET_BIND_SERVICE
        - SYS_PTRACE
        drop:
        - NET_RAW
      privileged: false
      runAsGroup: 107
      runAsNonRoot: true
      runAsUser: 107
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeDevices:
    - devicePath: /dev/rootdisk
      name: rootdisk
    - devicePath: /dev/cdromdisk
      name: cdromdisk
    volumeMounts:
    - mountPath: /var/run/kubevirt-private
      name: private
    - mountPath: /var/run/kubevirt
      name: public
    - mountPath: /var/run/kubevirt-ephemeral-disks
      name: ephemeral-disks
    - mountPath: /var/run/kubevirt/container-disks
      mountPropagation: HostToContainer
      name: container-disks
    - mountPath: /var/run/kubevirt/hotplug-disks
      mountPropagation: HostToContainer
      name: hotplug-disks
    - mountPath: /var/run/libvirt
      name: libvirt-runtime
    - mountPath: /var/run/kubevirt/sockets
      name: sockets
  dnsPolicy: ClusterFirst
  enableServiceLinks: false
  hostname: cat8kv-01
  imagePullSecrets:
  - name: default-dockercfg-9tgqh
  nodeName: kubevirt-nn4bm-worker-9fxdj
  nodeSelector:
    kubevirt.io/schedulable: "true"
  preemptionPolicy: PreemptLowerPriority
  priority: 0
  readinessGates:
  - conditionType: kubevirt.io/virtual-machine-unpaused
  restartPolicy: Never
  schedulerName: default-scheduler
  securityContext:
    runAsGroup: 107
    runAsNonRoot: true
    runAsUser: 107
    seLinuxOptions:
      type: virt_launcher.process
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 60
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  - effect: NoSchedule
    key: node.kubernetes.io/memory-pressure
    operator: Exists
  volumes:
  - emptyDir: {}
    name: private
  - emptyDir: {}
    name: public
  - emptyDir: {}
    name: sockets
  - name: rootdisk
    persistentVolumeClaim:
      claimName: cat8kv-01
  - name: cdromdisk
    persistentVolumeClaim:
      claimName: cat8kv-01-day0
  - emptyDir: {}
    name: virt-bin-share-dir
  - emptyDir: {}
    name: libvirt-runtime
  - emptyDir: {}
    name: ephemeral-disks
  - emptyDir: {}
    name: container-disks
  - emptyDir: {}
    name: hotplug-disks
status:
  conditions:
  - lastProbeTime: "2023-03-27T14:01:56Z"
    lastTransitionTime: "2023-03-27T14:01:56Z"
    message: the virtual machine is not paused
    reason: NotPaused
    status: "True"
    type: kubevirt.io/virtual-machine-unpaused
  - lastProbeTime: null
    lastTransitionTime: "2023-03-27T14:01:56Z"
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2023-03-27T14:02:07Z"
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2023-03-27T14:02:07Z"
    status: "True"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2023-03-27T14:01:56Z"
    status: "True"
    type: PodScheduled
  containerStatuses:
  - containerID: cri-o://ca0b81c710c44921c01e6fbd3057278bcb99261d9febbc03e7b113c37cba93ce
    image: registry.redhat.io/container-native-virtualization/virt-launcher@sha256:ae751656eccca94e1f2e55dc8fb1339565b3f83256b0dbc8be6720e8a8db2d7b
    imageID: registry.redhat.io/container-native-virtualization/virt-launcher@sha256:1a7996616acb7a7e0e5616be3fa2f591c663999d89f53c3cd1affda5b1ea3db1
    lastState: {}
    name: compute
    ready: true
    restartCount: 0
    started: true
    state:
      running:
        startedAt: "2023-03-27T14:02:07Z"
  hostIP: 10.58.24.218
  phase: Running
  podIP: 10.128.2.190
  podIPs:
  - ip: 10.128.2.190
  qosClass: Burstable
  startTime: "2023-03-27T14:01:56Z"
```
