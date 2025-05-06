**Introduction to OVS and OVN Project**
=====================================

### Objective

The objective of this project is to provide hands-on experience with Open vSwitch (OVS) and Open Virtual Network (OVN) technologies, introducing the intern to the fundamentals of virtual networking and network virtualization.

### Project Overview

The project will consist of the following tasks:

1. **Setting up the Environment**: Install a Linux distribution (e.g., Ubuntu) on a virtual machine (VM) or a physical machine, install OVS and OVN packages, and configure the network interface to use OVS as the network bridge.
2. **Basic OVS Configuration**: Create a simple network topology using OVS bridges and ports, configure VLANs and trunk ports, and test and verify the network connectivity using tools like `ovs-vsctl` and `tcpdump`.
3. **OVN Introduction**: Introduce the concept of network virtualization and OVN architecture, create an OVN database, configure the OVN controller, create a logical network, and attach it to an OVS bridge.
4. **Advanced OVN Configuration**: Configure OVN logical switches, routers, and ports, implement security groups and ACLs, and test and verify the network connectivity and security policies.
5. **Integration with Other Technologies**: Integrate OVN with other technologies like OpenStack, Kubernetes, or Docker, configure network policies and security groups for the integrated environment, and test and verify the network connectivity and security policies.

### Task 1: Setting up the Environment

* Install a Linux distribution (e.g., Ubuntu) on a virtual machine (VM) or a physical machine.
* Install OVS and OVN packages on the Linux machine.
* Configure the network interface to use OVS as the network bridge.

### Task 2: Basic OVS Configuration

* Create a simple network topology using OVS bridges and ports.
* Configure VLANs and trunk ports.
* Test and verify the network connectivity using tools like `ovs-vsctl` and `tcpdump`.

#### Verify with tcpdump

To verify with `tcpdump` that everything is working as expected in Task 2, you can use the following steps:

1. **Capture traffic on the ports**:
	* Use `tcpdump` to capture traffic on the ports that you configured in Task 2, such as `eth0` and `eth1`.
	* You can use the following command to capture traffic on `eth0`:
```
tcpdump -i eth0 -n -vv -s 0 -c 100
```
2. **Verify VLAN tags**:
	* If you configured VLANs on the ports, you can verify that the VLAN tags are being properly added to the packets.
	* Look for the `802.1Q` header in the `tcpdump` output, which should indicate the VLAN ID.
3. **Verify packet forwarding**:
	* To verify that packets are being properly forwarded between the bridges, you can use `tcpdump` to capture traffic on both `eth0` and `eth1`.
4. **Verify trunk port configuration**:
	* If you configured a trunk port, you can verify that the trunk port is properly configured by capturing traffic on the trunk port and verifying that the VLAN tags are being properly added to the packets.

### Task 3: OVN Introduction

* Introduce the concept of network virtualization and OVN architecture.
* Create an OVN database and configure the OVN controller.
* Create a logical network and attach it to an OVS bridge.

#### Verify Correctness

To verify the correctness of the OVN configuration, you can use the following steps:

1. **Verify the OVN database**:
	* Use `ovn-nbctl` to verify the OVN database.
2. **Verify the logical network**:
	* Use `ovn-nbctl` to verify the logical network.
3. **Verify the attachment to the OVS bridge**:
	* Use `ovn-nbctl` to verify the attachment to the OVS bridge.

### Task 4: Advanced OVN Configuration

* Configure OVN logical switches, routers, and ports.
* Implement security groups and ACLs.
* Test and verify the network connectivity and security policies.

#### Verify Correctness

To verify the correctness of the advanced OVN configuration, you can use the following steps:

1. **Verify the logical switch**:
	* Use `ovn-nbctl` to verify the logical switch.
2. **Verify the logical router**:
	* Use `ovn-nbctl` to verify the logical router.
3. **Verify the logical port**:
	* Use `ovn-nbctl` to verify the logical port.
4. **Verify security groups and ACLs**:
	* Use `ovn-nbctl` to verify security groups and ACLs.
5. **Verify packet forwarding**:
	* Use `tcpdump` to verify packet forwarding between the logical ports.
6. **Verify security policies**:
	* Use `tcpdump` to verify that security policies are being enforced.

### Task 5: Integration with Other Technologies

* Integrate OVN with other technologies like OpenStack, Kubernetes, or Docker.
* Configure network policies and security groups for the integrated environment.
* Test and verify the network connectivity and security policies.
