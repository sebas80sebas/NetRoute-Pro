# NetRoute-Pro: Static Routing and Network Redundancy

A professional implementation of static routing and network redundancy protocols. This project documents the configuration and verification of a multi-router network designed for high availability and fault tolerance.

## Environment

This project was developed using a specialized VirtualBox virtual machine image tailored for network laboratory simulations. This environment provides the necessary virtualization layer to simulate multiple routers (R1-R4) and host offices (hstOfi1-hstOfi2) within a controlled sandbox.

## Project Topology

The following diagram represents the logical connection between the hosts and routers within the lab environment:

```text
      [ hstOfi1 ]
           |
           |
           |
        [  R1  ] ------------------ [  R2  ]
        /      \
    (eth0.2) (eth0.3)           (eth0.2) (eth0.3)
      /          \                /          \
  [  R3  ] ------- \ ------------/-------- [  R4  ]
      \             \           /             /
    (eth0.1)         \         /           (eth0.2)
        \             \       /               /
         -------------- [ hstOfi2 ] -----------
```

## Documentation and Procedures

### Milestone 2: Configuration and Verification

#### Diagnostic Phase

The initial state of the network is verified through standard Linux and Cisco-style diagnostic commands.

**Host Offices (hstOfi1, hstOfi2):**
- Routing table inspection: `ip route show`
- Interface address verification: `ip address show`

**Routers (R1, R2, R3, R4):**
- Configuration audit: `show running-config`
- Routing table audit: `show ip route`

#### Connectivity Testing

Standard verification from hstOfi1:
- To hstOfi2: `ping -c3 <IP_ADDRESS_HST_OFI2>`
- To R3 (eth0.1): `ping -c3 <IP_ADDRESS_R3_ETH0_1>`
- To R4 (eth0.2): `ping -c3 <IP_ADDRESS_R4_ETH0_2>`

### Fault Tolerance Scenarios

#### Scenario A: Primary Link Failure (R1-R2)
To test redundancy between hstOfi1 and hstOfi2:
1. Deactivate `eth0.3` on R1 and `eth0.2` on R2.
2. Execute path discovery from hstOfi2: `traceroute -n <IP_ADDRESS_HST_OFI1>`.

#### Scenario B: Secondary Link Failure (R1-R3)
To test path re-routing to R3 and R4:
1. Restore previous interfaces.
2. Deactivate `eth0.2` on R1 and `eth0.3` on R3.
3. Execute path discovery from hstOfi1 to R3: `traceroute -n <IP_ADDRESS_R3_ETH0_1>`.
4. Execute path discovery from hstOfi2 to R4: `traceroute -n <IP_ADDRESS_R4_ETH0_2>`.

## Project Structure

- `commands/`: Automated scripts and command reference files.
    - `host_diag.sh`: Automated host diagnostic script.
    - `router_cmds.txt`: Reference for Cisco router commands.
- `README.md`: Full project documentation and topology.
