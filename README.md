Cisco Switch VLAN Configuration
Guide





Step-by-Step Implementation for Campus Network Segmentation
1. Introduction
This document provides the standard command-line interface (CLI) procedures for
configuring Virtual Local Area Networks (VLANs) on Cisco Catalyst switches. This
configuration is essential for segmenting departments, improving security, and
reducing broadcast traffic.


3. Basic VLAN Creation
Follow these steps to create a VLAN and assign it a descriptive name.
Switch# configure terminal
Switch(config)# vlan 10
Switch(config-vlan)# name Management
Switch(config-vlan)# exit
Switch(config)# vlan 20
Switch(config-vlan)# name HR
Switch(config-vlan)# exit


5. Assigning Ports to VLANs (Access Ports)
To connect end-user devices (PCs, Printers) to a specific VLAN, the physical interface
must be configured as an access port.Single Port Configuration
Switch(config)# interface FastEthernet 0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# exit

Range of Ports Configuration
Switch(config)# interface range FastEthernet 0/2 - 10
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit

Pro Tip: Use the description command on interfaces to keep track of what device is connected
(e.g., description Link to HR PC).


7. Configuring Trunk Ports
Trunk ports are used to carry traffic for multiple VLANs between switches or between
a switch and a router.
Switch(config)# interface GigabitEthernet 0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk allowed vlan all
Switch(config-if)# exit


9. Verification Commands
Use these commands to verify your configuration and troubleshoot issues.CommandPurpose
show vlan briefDisplays all VLANs, their status, and assigned ports.
show interfaces trunkShows active trunking links and allowed VLANs.
show running-configDisplays the entire current configuration.
10. Saving Configuration
Always save your work to ensure configurations persist after a reboot.
Switch# copy running-config startup-config
(or simply)
Switch# write memory
Cisco Campus Network Documentation | Building A, B, & C Reference
