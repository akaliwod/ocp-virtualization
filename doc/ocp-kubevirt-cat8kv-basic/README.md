# OpenShift Virtualization

## Cat8kv Test Results - Basic

Deployment files
- [virtual machine](../../tests/ocp/kubevirt/cat8kv/01/vm.yaml)
- [day0](../../tests/ocp/kubevirt/cat8kv/01/iosxe_config.txt)
- [day0 pvc](../../tests/ocp/kubevirt/cat8kv/01/day0.yaml)
- [service ssh](../../tests/ocp/kubevirt/cat8kv/01/svc.yaml)
- [deployment](../../tests/ocp/kubevirt/cat8kv/01/deployment.yaml)

Features
- 1 vCPU
- 4G RAM
- 1x Disk
- Virtual Machine image based on existing pvc
- Day0 configuration loaded in iso format to pvc
- Single interface (pod networking)
- SSH kubernetes service

## Day0 iso generation (example)

```
# genisoimage -r -o /tmp/c8000v_config.iso /tmp/iosxe_config.txt
Generate iso: genisoimage -r -o /tmp/c8000v_config.iso /tmp/iosxe_config.txt
I: -input-charset not specified, using utf-8 (detected in locale settings)
Total translation table size: 0
Total rockridge attributes bytes: 257
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
176 extents written (0 MB)
```

```
# virtctl image-upload dv cat8kv-01-day0 --no-create --insecure --image-path /tmp/c8000v_config.iso
Using existing PVC default/cat8kv-01-day0
Waiting for PVC cat8kv-01-day0 upload pod to be ready...
Pod now ready

Uploading data to https://cdi-uploadproxy-openshift-cnv.apps.kubevirt.ocp.lan
352.00 KiB / 352.00 KiB [==========================================] 100.00% 0s

Uploading data completed successfully, waiting for processing to complete, you can hit ctrl-c without interrupting the progress

Processing completed successfully
```

## Results

OpenShift Client (oc) outputs
- [Virtual Machine](./OcVm.md)
- [Virtual Machine Instance](./OcVmi.md)
- [Virtual Machine Launcher Pod](./OcPod.md)
- [Persistent Volume](./OcPv.md)
- [Persistent Volume Claim](./OcPvc.md)
- [Data Volume](./OcDv.md)

KVM
- [KVM Domain](./OcKvm.md)

SSH
- [show version](./SshVersion.md)
- [show interface](./SshInterface.md)
- [show ip interface](./SshIpInterface.md)
- [show ip interface brief](./SshIpBrief.md)
- [show ip route](./SshRoute.md)
- [show arp](./SshArp.md)
- [show running-config](./SshConfig.md)
