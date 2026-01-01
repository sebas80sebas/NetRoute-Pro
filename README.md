# NetLab: Router Configuration and Routing Practice

This repository contains the full documentation and command references for the Router Configuration practice. The focus of this project is on static routing, interface management, and network fault tolerance verification.

## Project Information

- **Authors:** Iván Sebastián Loor Weir, Álvaro González Fúnez
- **Subject:** Computer Networking (Redes de Ordenadores)
- **Note:** Routing was configured starting from R100 towards the other nodes.

## Documentation and Procedures

### Milestone 2 (Hito 2)

#### Diagnostic Phase

For both host offices (hstOfi1 and hstOfi2), the following commands are used to verify the initial state:

1. Display routing table: `ip route show`
2. Display interface addresses: `ip address show`

For routers R1, R2, R3, and R4, the following commands are used:

1. Show running configuration: `show running-config`
2. Show IP routing table: `show ip route`

#### Connectivity Verification

Connectivity tests are performed from hstOfi1 using the following commands:

- Ping hstOfi2: `ping -c3 <IP_ADDRESS_HST_OFI2>`
- Ping R3 (eth0.1): `ping -c3 <IP_ADDRESS_R3_ETH0_1>`
- Ping R4 (eth0.2): `ping -c3 <IP_ADDRESS_R4_ETH0_2>`

#### Fault Tolerance and Route Redundancy Tests

**Test 1: Interface Failover (R1/R2)**

1. Set interfaces `eth0.3` of R1 and `eth0.2` of R2 to `shutdown` mode.
2. Verify the path from hstOfi2 to hstOfi1 using:
   `traceroute -n <IP_ADDRESS_HST_OFI1>`

**Test 2: Interface Failover (R1/R3)**

1. Restore interfaces `eth0.3` of R1 and `eth0.2` of R2 to normal mode.
2. Set interfaces `eth0.2` of R1 and `eth0.3` of R3 to `shutdown` mode.
3. Verify connectivity from hstOfi1 to R3 (eth0.1) using:
   `traceroute -n <IP_ADDRESS_R3_ETH0_1>`
4. Maintaining this configuration, verify the path from hstOfi2 to R4 (eth0.2) using:
   `traceroute -n <IP_ADDRESS_R4_ETH0_2>`

## Usage

Diagnostic scripts and command references can be found in the `commands/` directory:

- `commands/host_diag.sh`: Script for host-level diagnostics.
- `commands/router_cmds.txt`: Reference for router-specific commands.