# Lab 03 — DHCP Validation

## Environment

* DHCP Server: `DC01`
* Active Directory Domain: `caustech.local`
* DHCP Scope: `CausTech-LAN`
* Address Pool: `192.168.10.100`–`192.168.10.200`
* DNS Server: `192.168.10.10`

## Validation Checklist

| Test                            | Expected Result                                    | Status |
| ------------------------------- | -------------------------------------------------- | ------ |
| DHCP role installation          | DHCP Server role is installed                      | Passed |
| Post-installation configuration | DHCP configuration completed                       | Passed |
| DHCP scope                      | `CausTech-LAN` scope configured                    | Passed |
| Address pool                    | Scope matches the configured range                 | Passed |
| Exclusions                      | No excluded addresses configured                   | Passed |
| Lease duration                  | Default lease duration retained                    | Passed |
| DNS configuration               | DNS server configured for the lab domain           | Passed |
| Client DHCP configuration       | Ethernet adapter obtains its address automatically | Passed |
| IP release and renewal          | Client releases and renews its address             | Passed |
| IP configuration                | `ipconfig /all` displays the client configuration  | Passed |
| Domain controller connectivity  | Client can ping `DC01`                             | Passed |
| DNS resolution                  | `nslookup caustech.local` returns DNS information  | Passed |

## Conclusion

The DHCP configuration and client validation tasks were completed in the existing CausTech Technologies lab environment. DHCP runs on `DC01` alongside Active Directory Domain Services and DNS.

The screenshots in the repository provide supporting evidence of the configuration and validation steps.
