# OpenShift Virtualization

## Fedora Test Results - Extra Disks

Deployment files
- [virtual machine](../../samples/fedora/fedora-disk-vm.yaml)
- [service](../../samples/fedora/fedora-disk-svc.yaml)

Features
- 1 vCPU
- 1G RAM
- 1x 30G Disk
- Virtual Machine image based on existing pvc
- Extra Disks
- Cloud-init with ssh credentials
- Single interface (pod networking)

## Results

OpenShift Client (oc) outputs
- [Virtual Machine](./FedoraDiskOcVm.md)
- [Virtual Machine Instance](./FedoraDiskOcVmi.md)
- [Virtual Machine Launcher Pod](./FedoraDiskOcPod.md)
- [Persistent Volume](./FedoraDiskOcPv.md)
- [Persistent Volume Claim](./FedoraDiskOcPvc.md)
- [Data Volume](./FedoraDiskOcDv.md)

Other outputs
- [KVM Domain](./FedoraDiskOcKvm.md)
