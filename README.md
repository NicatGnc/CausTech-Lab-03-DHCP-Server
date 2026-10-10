# CausTech Technologies — Lab 03: DHCP Server Configuration

## 1. Overview

This project documents the installation, configuration, and validation of the Dynamic Host Configuration Protocol (DHCP) service in the CausTech Technologies Windows Server lab.

DHCP automatically assigns IP addresses and network configuration to client devices, reducing the need for manual configuration.

The DHCP service is hosted on the existing Windows Server domain controller, `DC01`, alongside Active Directory Domain Services and DNS. This is a separate documentation project within the same lab environment, not a separate server deployment.

## 2. Lab Environment

| Component               | Configuration                               |
| ----------------------- | ------------------------------------------- |
| Domain Controller       | `DC01`                                      |
| Active Directory Domain | `caustech.local`                            |
| DHCP Server             | `DC01`                                      |
| Client User             | `CAUSTECH\jcarter`                          |
| Virtual Network         | `CausTech-LAN`                              |
| DHCP Address Pool       | `192.168.10.100` – `192.168.10.200`         |
| Subnet Mask             | `255.255.255.0`                             |
| DNS Server              | `192.168.10.10`                             |
| Default Gateway         | Not configured for the isolated lab network |

## 3. Selecting the DHCP Server Role

The DHCP Server role was selected through Server Manager on `DC01` using the Add Roles and Features wizard.

This step prepares the existing Windows Server to provide dynamic IP address assignment to clients on the internal lab network.

![Opening DC01](screenshots/01.png)

![Selecting the DHCP Server role](screenshots/03.png)

![Confirming the DHCP Server role selection](screenshots/04.png)

## 4. Completing DHCP Installation

The installation process was completed, followed by the DHCP post-installation configuration workflow.

The configuration screens include the required credentials and the initial DHCP setup steps.

![DHCP installation completed](screenshots/05.png)

![DHCP configuration screen](screenshots/06.png)

![DHCP credentials configuration](screenshots/07.png)

## 5. Creating the DHCP Scope

A DHCP scope named `CausTech-LAN` was configured to define the IPv4 addresses available for client devices.

The address pool was set to `192.168.10.100` through `192.168.10.200`. No exclusions were configured, and the default lease duration was retained.

![Starting the DHCP scope wizard](screenshots/09.png)

![Naming the scope CausTech-LAN](screenshots/10.png)

![Configuring the DHCP address range](screenshots/11.png)

![Address exclusion configuration](screenshots/12.png)

![Default lease duration](screenshots/13.png)

## 6. Configuring DHCP and DNS Options

The option to configure the scope immediately was selected. DNS configuration was then completed so clients could use the lab's existing DNS service.

The DNS server is `192.168.10.10`, and the Active Directory domain is `caustech.local`.

![Choosing to configure the scope now](screenshots/14.png)

![Configuring DNS server options](screenshots/16.png)

## 7. Verifying the DHCP Management Console

The DHCP management console was opened from Server Manager through Tools. The console was inspected to review the configured DHCP server and its scope.

![Opening DHCP from Server Manager Tools](screenshots/17.png)

![DHCP management console](screenshots/18.png)

## 8. Configuring the Windows Client for DHCP

The Ethernet adapter on the Windows client used by `jcarter` was configured to obtain its IP address automatically.

This allows the client to request network settings from the DHCP server instead of relying on a manually assigned IPv4 address.

![Configuring the Ethernet adapter for DHCP](screenshots/23.png)

## 9. Releasing and Renewing the Client Address

The Windows command-line utilities `ipconfig /release` and `ipconfig /renew` were used to release the existing DHCP-assigned configuration and request a fresh lease.

These commands help verify that the DHCP client can communicate with the DHCP server and obtain an address from the configured scope.

![Releasing the client IP configuration](screenshots/24.png)

![Renewing the client IP configuration](screenshots/25.png)

## 10. Verifying Network Configuration

The `ipconfig /all` command was used to inspect the client's network configuration, including the IPv4 address, DHCP status, DHCP server, DNS server, and connection-specific DNS suffix where shown.

The output provides evidence that the client received network configuration from the lab environment.

![Client network configuration using ipconfig all](screenshots/26.png)

## 11. Testing Connectivity and DNS Resolution

The client used `ping` to test network connectivity to `DC01` and `nslookup caustech.local` to verify DNS resolution for the Active Directory domain. Together, these commands help validate connectivity to the domain controller and access to the lab's DNS service.

![Ping and DNS resolution tests](screenshots/27.png)

## 13. Results

This lab documents:

* DHCP Server role installation on the existing domain controller.
* DHCP post-installation configuration.
* Creation of the `CausTech-LAN` IPv4 scope.
* Configuration of the `192.168.10.100`–`192.168.10.200` address pool.
* DNS configuration for `caustech.local`.
* Windows client DHCP configuration and lease renewal.
* Network connectivity and DNS resolution tests.

Refer to `documentation/validation.md` for the validation checklist.
