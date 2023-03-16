# OpenShift Virtualization

## Fedora Test Results - Basic

Deployment files
- [virtual machine](../../samples/fedora/fedora-basic-vm.yaml)
- [service](../../samples/fedora/fedora-basic-svc.yaml)

Features
- 1 vCPU
- 1G RAM
- 1x 30G Disk
- Virtual Machine image based on existing pvc
- Cloud-init with ssh credentials
- Single interface (pod networking)

## Results

OpenShift Client (oc) outputs
- [Virtual Machine](./FedoraBasicOcVm.md)
- [Virtual Machine Instance](./FedoraBasicOcVmi.md)
- [Virtual Machine Launcher Pod](./FedoraBasicOcPod.md)
- [Persistent Volume](./FedoraBasicOcPv.md)
- [Persistent Volume Claim](./FedoraBasicOcPvc.md)
- [Data Volume](./FedoraBasicOcDv.md)

Other outputs
- [KVM Domain](./FedoraBasicOcKvm.md)
