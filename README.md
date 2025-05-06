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

**Task 1: Setting up the Environment**
=====================================

### Objective

The objective of this task is to set up a Linux environment with Open vSwitch (OVS) and Open Virtual Network (OVN) installed, and configure the network interface to use OVS as the network bridge.

### Step-by-Step Instructions

1. **Install a Linux Distribution**:
	* Install a Linux distribution (e.g., Ubuntu) on a virtual machine (VM) or a physical machine.
	* You can use a virtualization platform like VirtualBox, VMware, or KVM to create a VM.
	* Make sure the Linux distribution is 64-bit and has a minimum of 4GB RAM and 20GB disk space.
2. **Install OVS and OVN Packages**:
	* Install the OVS and OVN packages on the Linux machine.
	* You can use the following command to install OVS and OVN on Ubuntu:
```
sudo apt-get update
sudo apt-get install -y openvswitch-switch openvswitch-common ovn-host ovn-central ovn-northd
```
3. **Configure the Network Interface**:
	* Configure the network interface to use OVS as the network bridge.
	* You can use the following command to create an OVS bridge:
```
sudo ovs-vsctl add-br br0
```
	* This will create an OVS bridge named `br0`.
4. **Add Ports to the Bridge**:
	* Add ports to the OVS bridge.
	* You can use the following command to add a port to the bridge:
```
sudo ovs-vsctl add-port br0 eth0
```
	* This will add the `eth0` interface to the `br0` bridge.
5. **Configure the IP Address**:
	* Configure the IP address on the OVS bridge.
	* You can use the following command to set the IP address on the bridge:
```
sudo ip addr add 192.168.1.100/24 dev br0
```
	* This will set the IP address on the `br0` bridge to `192.168.1.100/24`.
6. **Bring Up the Interface**:
	* Bring up the OVS bridge interface.
	* You can use the following command to bring up the interface:
```
sudo ip link set br0 up
```
	* This will bring up the `br0` bridge interface.

### Verification

To verify that the environment is set up correctly, you can use the following commands:

* `sudo ovs-vsctl show` : This will show the OVS configuration.
* `sudo ip addr show` : This will show the IP address configuration.
* `sudo bridge link show` : This will show the bridge configuration.

### Troubleshooting Tips

* Make sure the OVS and OVN packages are installed correctly.
* Make sure the network interface is configured correctly.
* Make sure the IP address is set correctly on the OVS bridge.
* Use the `sudo ovs-vsctl` and `sudo ip` commands to troubleshoot any issues.

### Example Configuration

Here is an example configuration for the `br0` bridge:
```markdown
sudo ovs-vsctl add-br br0
sudo ovs-vsctl add-port br0 eth0
sudo ip addr add 192.168.1.100/24 dev br0
sudo ip link set br0 up
```
This configuration creates an OVS bridge named `br0`, adds the `eth0` interface to the bridge, sets the IP address on the bridge to `192.168.1.100/24`, and brings up the bridge interface.
**Task 2: Basic OVS Configuration**
=====================================

### Verify with tcpdump

To verify with `tcpdump` that everything is working as expected in Task 2, you can use the following steps:

1. **Capture traffic on the ports**:
	* Use `tcpdump` to capture traffic on the ports that you configured in Task 2, such as `eth0` and `eth1`.
	* You can use the following command to capture traffic on `eth0`:
```
tcpdump -i eth0 -n -vv -s 0 -c 100
```
	* This command will capture 100 packets on `eth0` and display them in a verbose format.
2. **Verify VLAN tags**:
	* If you configured VLANs on the ports, you can verify that the VLAN tags are being properly added to the packets.
	* Look for the `802.1Q` header in the `tcpdump` output, which should indicate the VLAN ID.
	* For example:
```
14:34:22.123456  00:11:22:33:44:55 > 00:66:77:88:99:00, ethertype 802.1Q (0x8100), length 64: vlan 10, p 0, ethertype IPv4, ...
```
	* In this example, the packet has a VLAN ID of 10.
3. **Verify packet forwarding**:
	* To verify that packets are being properly forwarded between the bridges, you can use `tcpdump` to capture traffic on both `eth0` and `eth1`.
	* Use the following command to capture traffic on both `eth0` and `eth1`:
```
tcpdump -i eth0 -n -vv -s 0 -c 100 -w capture.pcap &
tcpdump -i eth1 -n -vv -s 0 -c 100 -w capture.pcap &
```
	* This will capture traffic on both `eth0` and `eth1` and write it to a file called `capture.pcap`.
	* You can then use `tcpdump` to read the capture file and verify that packets are being properly forwarded between the bridges.
4. **Verify trunk port configuration**:
	* If you configured a trunk port, you can verify that the trunk port is properly configured by capturing traffic on the trunk port and verifying that the VLAN tags are being properly added to the packets.
	* Use the following command to capture traffic on the trunk port:
```
tcpdump -i trunk0 -n -vv -s 0 -c 100
```
	* This command will capture 100 packets on the trunk port and display them in a verbose format.

### Examples of tcpdump filters

Some examples of `tcpdump` filters that you can use to verify the configuration:

* `tcpdump -i eth0 vlan 10` : Capture traffic on `eth0` with VLAN ID 10.
* `tcpdump -i eth1 -n -vv -s 0 vlan 20` : Capture traffic on `eth1` with VLAN ID 20.
* `tcpdump -i trunk0 -n -vv -s 0 vlan 10 or vlan 20` : Capture traffic on the trunk port with VLAN ID 10 or 20.

**Task 3: OVN Introduction**
==========================

### Create an OVN database and configure the OVN controller

1. **Create an OVN database**:
	* Use `ovn-nbctl` to create an OVN database.
	* You can use the following command to create an OVN database:
```
ovn-nbctl init
```
2. **Configure the OVN controller**:
	* Use `ovn-nbctl` to configure the OVN controller.
	* You can use the following command to configure the OVN controller:
```
ovn-nbctl set-controller ovn-controller
```
3. **Create a logical network**:
	* Use `ovn-nbctl` to create a logical network.
	* You can use the following command to create a logical network:
```
ovn-nbctl lswitch-add ln0
```
4. **Attach the logical network to an OVS bridge**:
	* Use `ovn-nbctl` to attach the logical network to an OVS bridge.
	* You can use the following command to attach the logical network to an OVS bridge:
```
ovn-nbctl lswitch-set-external-id ln0 bridge=br0
```

### Verify correctness

To verify the correctness of the OVN configuration, you can use the following steps:

1. **Verify the OVN database**:
	* Use `ovn-nbctl` to verify the OVN database.
	* You can use the following command to verify the OVN database:
```
ovn-nbctl show
```
2. **Verify the logical network**:
	* Use `ovn-nbctl` to verify the logical network.
	* You can use the following command to verify the logical network:
```
ovn-nbctl lswitch-list
```
3. **Verify the attachment to the OVS bridge**:
	* Use `ovn-nbctl` to verify the attachment to the OVS bridge.
	* You can use the following command to verify the attachment to the OVS bridge:
```
ovn-nbctl lswitch-get-external-id ln0 bridge
```

**Task 4: Advanced OVN Configuration**
=====================================

### Configure OVN logical switches, routers, and ports

1. **Create a logical switch**:
	* Use `ovn-nbctl` to create a logical switch.
	* You can use the following command to create a logical switch:
```
ovn-nbctl lswitch-add ls0
```
2. **Create a logical router**:
	* Use `ovn-nbctl` to create a logical router.
	* You can use the following command to create a logical router:
```
ovn-nbctl lrouter-add lr0
```
3. **Create a logical port**:
	* Use `ovn-nbctl` to create a logical port.
	* You can use the following command to create a logical port:
```
ovn-nbctl lport-add lp0
```
4. **Configure security groups and ACLs**:
	* Use `ovn-nbctl` to configure security groups and ACLs.
	* You can use the following command to configure security groups and ACLs:
```
ovn-nbctl sg-add sg0
ovn-nbctl acl-add acl0
```

### Verify correctness

To verify the correctness of the advanced OVN configuration, you can use the following steps:

1. **Verify the logical switch**:
	* Use `ovn-nbctl` to verify the logical switch.
	* You can use the following command to verify the logical switch:
```
ovn-nbctl lswitch-list
```
2. **Verify the logical router**:
	* Use `ovn-nbctl` to verify the logical router.
	* You can use the following command to verify the logical router:
```
ovn-nbctl lrouter-list
```
3. **Verify the logical port**:
	* Use `ovn-nbctl` to verify the logical port.
	* You can use the following command to verify the logical port:
```
ovn-nbctl lport-list
```
4. **Verify security groups and ACLs**:
	* Use `ovn-nbctl` to verify security groups and ACLs.
	* You can use the following command to verify security groups and ACLs:
```
ovn-nbctl sg-list
ovn-nbctl acl-list
```
5. **Verify packet forwarding**:
	* Use `tcpdump` to verify packet forwarding between the logical ports.
	* You can use the following command to capture traffic on a logical port:
```
tcpdump -i lp0 -n -vv -s 0 -c 100
```
6. **Verify security policies**:
	* Use `tcpdump` to verify that security policies are being enforced.
	* You can use the following command to capture traffic on a logical port and verify that packets are being dropped or allowed based on the security policies:
```
tcpdump -i lp0 -n -vv -s 0 -c 100
```

### Task 5: Integration with Other Technologies

* Integrate OVN with other technologies like OpenStack, Kubernetes, or Docker.
* Configure network policies and security groups for the integrated environment.
* Test and verify the network connectivity and security policies.
