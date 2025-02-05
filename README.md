# Network Configuration for Enterprise Deployment

## Overview
This repository contains the network configuration files for a hierarchical enterprise network design. It includes VLAN allocation, routing protocols, security configurations, and access control mechanisms to ensure a robust and secure network infrastructure.

## VLAN Allocation

| VLAN ID | Name          | Subnet             |
|---------|--------------|--------------------|
| 10      | Admin        | 192.168.59.0/27    |
| 20      | Sales        | 192.168.59.32/27   |
| 30      | HR           | 192.168.59.64/27   |
| 40      | IT           | 192.168.59.96/27   |
| 50      | Development  | 192.168.59.128/27  |
| 60      | Server       | 192.168.59.160/28  |
| 70      | VoIP         | 192.168.59.192/27  |
| 80      | Guest        | 192.168.59.224/28  |

## Configuration Files
The following configuration files are included in this repository:

- **ISP Configuration** (`isp_config.txt`)
- **ASA Firewall Configuration** (`asa_config.txt`)
- **Core1 Router Configuration** (`core1_config.txt`)
- **Core2 Router Configuration** (`core2_config.txt`)
- **Distribution1 Switch Configuration** (`distribution1_config.txt`)
- **Distribution2 Switch Configuration** (`distribution2_config.txt`)
- **Access Switches Configuration** (`access1_config.txt`, `access2_config.txt`, etc.)

## Features Implemented
- **VLAN Segmentation**: All VLANs are properly allocated and configured across access and distribution layers.
- **OSPF Routing**: Implemented for inter-VLAN communication and redundancy.
- **ACLs for Security**: Restricts Guest VLAN from accessing internal resources while allowing internet access.
- **NAT for Internet Access**: Configured on ASA to enable internal users to access external networks.
- **Web VPN for Remote Users**: Implemented on ASA to allow Development VLAN remote access.

## Deployment Steps
### 1. Clone the Repository
```sh
git clone https://github.com/your-username/network-config.git
cd network-config
```
### 2. Upload Configurations to Devices
Using TFTP:
```sh
copy tftp running-config
```
### 3. Verify OSPF and Routing
Check OSPF neighbors:
```sh
show ip ospf neighbor
```
Check routing table:
```sh
show ip route
```
### 4. Test Connectivity
- **Internal VLANs:** Ping between devices in different VLANs.
- **Internet Access:** Test from the Guest VLAN.
- **Remote VPN Access:** Test via Web VPN interface.

## Troubleshooting
- If VLANs are not communicating, check `show vlan brief` and `show spanning-tree`.
- If internet access is not working, verify NAT and ACLs on ASA.
- If VPN is not accessible, check the Web VPN configuration.

## Contributors
- **Julana Premasekara** - 

## License
This project is licensed under the MIT License - see the LICENSE file for details.
