# Campus Area Network (CAN) Design using Packet Tracer

## Overview

This project demonstrates the design and configuration of a Campus Area Network (CAN) using Cisco Packet Tracer. The network includes a variety of components such as routers, switches, PCs, wireless access points (Wi-Fi), and a DHCP server. Additionally, the network utilizes the Open Shortest Path First (OSPF) routing protocol for dynamic routing between routers.

## Components

1. **Router**: Provides the main connectivity between different subnets in the network.
2. **Switches**: Used to interconnect the devices within the campus.
3. **PCs**: End devices connected to the network that can send and receive data.
4. **Wireless Access Points (Wi-Fi)**: Provide wireless connectivity to the network for mobile devices.
5. **DHCP Server**: Automatically assigns IP addresses to devices on the network.
6. **OSPF Routing**: A dynamic routing protocol used to route traffic between routers.

## Topology Diagram

![Network Topology](images/topology.png) *(Image of network topology to be added)*

## Steps for Network Design

### 1. **Basic Network Setup**

- Place the devices on the Packet Tracer workspace: Routers, Switches, PCs, Wireless Access Points.
- Connect the devices using appropriate cables:
  - Use **Ethernet cables** (copper straight-through) to connect routers to switches and PCs to switches.
  - Use **serial cables** to interconnect routers.
  - Use **wireless connections** between wireless devices and access points.

### 2. **Router Configuration**

#### a. Configure Router Interfaces:
- Assign IP addresses to each router interface.
- Enable interfaces and ensure proper connectivity.
- Use the following sample command for interface configuration:

    ```bash
    Router> enable
    Router# configure terminal
    Router(config)# interface gigabitethernet 0/0
    Router(config-if)# ip address 192.168.1.1 255.255.255.0
    Router(config-if)# no shutdown
    ```

#### b. Configure OSPF:
- Enable OSPF and configure router OSPF process.
- Define the OSPF network type and advertise the connected networks.

    ```bash
    Router(config)# router ospf 1
    Router(config-router)# network 192.168.1.0 0.0.0.255 area 0
    Router(config-router)# network 192.168.2.0 0.0.0.255 area 0
    ```

### 3. **Switch Configuration**

- Ensure switches are configured to allow proper VLAN segmentation if necessary.
- Enable **port security** and **trunking** if required for VLAN management.

### 4. **DHCP Server Configuration**

- Set up a DHCP server to dynamically assign IP addresses to the PCs and wireless devices.
- Configure the DHCP pool with the network address, subnet mask, and default gateway.

    ```bash
    Router(config)# ip dhcp pool NetworkPool
    Router(dhcp-config)# network 192.168.1.0 255.255.255.0
    Router(dhcp-config)# default-router 192.168.1.1
    Router(dhcp-config)# dns-server 8.8.8.8
    ```

- Assign the DHCP server role to the router or dedicated server device in the network.

### 5. **Wi-Fi Setup**

- Add wireless access points to the network.
- Configure the SSID and security settings for wireless clients.
- Ensure the access points are connected to the switches and can communicate with other devices on the network.

    ```bash
    Access-Point(config)# ssid CampusWiFi
    Access-Point(config-ssid)# security wpa2 psk
    Access-Point(config-ssid)# wpa2 psk ascii 12345678
    ```

### 6. **PC Configuration**

- Configure PCs to obtain IP addresses automatically from the DHCP server.
- Ensure each PC has connectivity and can communicate with others through ping tests.

    ```bash
    PC> ip dhcp
    ```

### 7. **Verification and Testing**

- Use **ping** commands from PCs to test connectivity between devices.
- Check routing tables using the `show ip route` command on routers.
- Verify OSPF routes with `show ip ospf neighbor` and `show ip ospf route`.
- Verify DHCP lease assignments using `show ip dhcp binding` on the DHCP server.

### 8. **Troubleshooting**

- If devices cannot communicate, check interface statuses, IP address assignments, and routing configurations.
- Ensure OSPF neighbors are correctly established and that routers are advertising their networks.
- Verify DHCP lease assignments on the DHCP server.
- Check wireless devices to ensure correct SSID and security settings.

## Conclusion

This project successfully sets up a functional Campus Area Network (CAN) using Cisco Packet Tracer. The network incorporates dynamic IP addressing with DHCP, wireless connectivity, and OSPF for routing. The design can be expanded by adding more subnets, VLANs, or devices as needed.

## Future Enhancements

- **Security**: Implement access control lists (ACLs) to restrict unauthorized access.
- **VLANs**: Introduce VLANs for better network segmentation.
- **Redundancy**: Add additional routers or links for network fault tolerance.

## References

- Cisco Packet Tracer Documentation
- Cisco OSPF Routing Configuration Guide

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
