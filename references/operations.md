# Practical operations — Omada Controller V6.3

Use this as a routing and safety checklist. It is paraphrased from the local guide; cited pages are physical PDF pages.

## Initial rollout: controller → site → devices

1. **Choose the controller form first.** The guide treats Software, Hardware, Integrated Gateway (Controller), and cloud-based controller as related but distinct setup paths. Use the exact §2 path after identifying the form. PDF pp. 19–42.
2. **Create one logical site per LAN** as the guide's stated best practice; then place the LAN's gateway, switches, and APs into its corresponding site. PDF p. 43.
3. **Use the applicable adoption section.** Adoption instructions split by controller form, so do not mix an on-premises procedure with cloud/integrated-gateway steps. PDF pp. 50–71.
4. **Check before applying WAN overrides.** On adoption, enabling controller WAN settings overrides means controller preconfiguration replaces a newly adopted gateway's standalone WAN settings. The guide warns incorrect values can prevent Internet access. Record/review the working WAN state first. PDF p. 152.
5. Validate connection state, the intended site assignment, and basic client connectivity before moving to VLANs, WLANs, or policy work.

## Backup, restore, and migration

- **Controller backup:** Global View → `Settings > Maintenance > Backup > Export`. Available data categories include settings, user info, authenticated-client data, firmware update logs, and selected retained-history period. Cloud-account retention depends on Cloud Access being enabled on the restored controller. PDF p. 95.
- **Controller/site restore or migration:** make a verified backup before changing controllers. Site migration requires source and target controllers with the same version and proceeds as export site → import/migrate site → migrate devices. It can interrupt Internet service for several minutes and wireless clients must reconnect. PDF pp. 101–105.
- **Controller migration compatibility:** the guide says the destination controller must be v5.0.x or later and have the same or higher first-three-part version. Still verify the precise target release and hardware support before scheduling. PDF p. 105.
- **Operational rule:** preserve an out-of-band/admin path and schedule a maintenance window. Do not call migration or restore non-disruptive.

## Segmentation and WLAN

- **Internet/WAN:** Site View → `Network Config > Network Settings > Internet`; choose WAN ports, configure IPv4/IPv6, then optional multi-WAN load balancing. PDF p. 152.
- **LAN/VLAN:** Site View → `Network Config > Network Settings > LAN > VLAN > Add`. The guide's sequence is: define purpose and DHCP/VLAN properties, bind VLAN to destination ports, apply, then validate through topology/port views. PDF p. 173.
- **SSID:** Site View → `Network Config > Network Settings > WLAN > Add SSID`. Choose SSID, bands, security and scope (all devices or selected AP group/gateway). 6 GHz support is model-dependent; the guide notes PPSK without RADIUS is not supported when 6 GHz is enabled. PDF p. 188.
- **Portal:** operates on SSIDs and LANs. Wireless portal authentication relies on APs; wired portal authentication relies on the gateway, so both must be connected and working for combined wired/wireless service. PDF p. 211.
- **Before applying:** test from a pilot SSID/VLAN or limited device group, ensure management traffic remains reachable, and check DHCP/DNS/routing policy as one change set.

## Remote access and site-to-site connectivity

- **Remote-client VPN server:** Site View → `Network Config > VPN > VPN > Create New VPN Server`. The guide documents WireGuard, OpenVPN, IPsec, SSL VPN, L2TP, and PPTP servers. Choose the protocol compatible with the client and gateway; confirm endpoint/WAN reachability and firewall/NAT prerequisites. PDF pp. 236–255.
- **Site-to-site VPN:** Site View → `Network Config > VPN > VPN > Create New Site-to-Site VPN`. Auto IPsec and Auto WireGuard exist for qualifying sites on the same controller; manual modes require both endpoints’ configuration. Auto IPsec is bidirectional once created from one site to the selected remote site. PDF p. 266.
- **Validation:** confirm tunnel status in §9.6 and test only explicitly allowed subnets/flows. Do not expose broad inter-site access by default. PDF p. 275.

## Access policy and threat controls

- **ACL behavior matters:** first matching rule decides; subsequent rules are not evaluated. The listed default ordering is creation-time order (earlier first), rules can be reordered, and unmatched traffic is implicitly permitted. Review ordering and include explicit tests before applying. PDF p. 327.
- **ACL scope:** gateway ACL controls LAN-to-WAN traffic, switch ACL controls traffic through switch ports, and EAP ACL controls wireless-network traffic; each supports different match criteria. PDF p. 327.
- **Other protection layers:** URL filtering/application control (PDF pp. 338–344); IDS/IPS and wireless IDS/IPS (pp. 345–351); firewall, attack defense, DAI, DHCP snooping (pp. 352–362). Verify model licensing/capability and expected throughput effect.

## Observe, troubleshoot, and update

- **Device health:** `Devices > Device List` in Global or Site View. Health score bands listed by the guide are Good 8–10, Fair 4–7, Poor 1–3; some devices (including OLT and outdated firmware) lack health statistics. PDF p. 397.
- **Monitoring:** Dashboard covers overview, topology, Wi-Fi, clients, and traffic. PDF p. 444. Logs/alerts/audit and incident workflows are indexed at PDF pp. 465–476.
- **Tools:** `Network Tools` provides network check (ping/traceroute/DNS lookup), packet capture, terminal, cable test, interference detection, and remote access; prior firmware may be necessary for tool support. PDF p. 480.
- **Firmware:** use Stable in production unless there is a deliberate test/rollback plan. The guide presents Release Candidate and Beta as less suitable for critical production use. Review upgrade scope and backup before one-time, periodic, upload, or rollback operations. PDF pp. 492–500.

## SD-WAN, MSP, and clusters — high-impact changes

- **SD-WAN:** guide uses hub-spoke; at least one gateway needs a public IP, WAN DMZ must not be enabled, and LAN segments must not conflict. It directs WAN-side adoption via controller inform address and port-forwarding on the LAN-side-adopted gateway; the guide explicitly calls out port 8043 for upgrades if needed. Prefer the source pages for exact port-forwarding/interface choices. PDF pp. 502–507.
- **MSP:** enabling MSP Mode converts a standard controller to an MSP system. It can affect the Cloud access page; reload/re-enter it if needed. Treat conversion as a planned administrative change. PDF pp. 509–513.
- **Hot-standby cluster:** supported guide scope is Software Controller on Linux v5.15.20+ or qualifying OC300/OC400/integrated hardware controller v5.15.20+, with Ubuntu 20.04/22.04 listed for Linux. It requires consistent JDK/MongoDB, static IPs (mandatory for hardware controller) and warns secondary-node data will be overwritten. PDF pp. 515–517.
- **Distributed cluster:** guide scope is Software Controller Linux v5.15.20+, Ubuntu 22.04, Java 17, MongoDB 7.0, and at least three nodes. It requires static node IPs, consistent JDK/MongoDB, close time synchronization (under 20 seconds), and system handle-limit changes. Initialization order matters: initialize the primary/exporting node first. PDF pp. 517–521.
- **Rule:** never offer cluster commands as a casual fix. Verify controller release, OS, Java/MongoDB, static addressing, time synchronization, backup, access recovery path, and maintenance window first.
