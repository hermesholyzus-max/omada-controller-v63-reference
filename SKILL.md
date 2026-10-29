---
name: omada-controller-v63
description: "Use when working with Omada Controller V6.3."
version: 1.0.0
author: "Local reference derived from TP-Link Omada SDN Controller V6.3 User Guide"
license: "Reference-only; do not redistribute source"
metadata:
  hermes:
    tags: [omada, tplink, networking, controller, vlan, vpn, sdwan]
  source_revision: "REV6.3.0, © 2026 TP-Link"
  source_pages: 521
  scope: "Omada Controller / Omada Network system management UI"
---

# Omada Controller V6.3 Reference

## Start here

- **People:** read [`START_HERE.md`](START_HERE.md) for the source requirement, safety boundaries, and portable setup.
- **Agents:** load this `SKILL.md` before answering Omada Controller V6.3 questions, then load the matching file under [`references/`](references/).
- **Source verification:** follow [`SOURCE.md`](SOURCE.md). The PDF itself is deliberately not included in this distribution.

## When to Use

Use for Omada Controller V6.3 UI configuration, deployment, operational troubleshooting, or source-page routing. It is appropriate for planning and explaining changes; it does not authorize live controller, device, cloud, SSH, CLI, or network changes.

Use this skill for questions about the **Omada SDN Controller V6.3** management UI, its supported deployment modes, planning a configuration, or locating the documented procedure. Load the matching reference before giving procedural steps.

## Scope and citation convention

- **Source:** the separately retained PDF identified in [`SOURCE.md`](SOURCE.md), 521 physical PDF pages; cover identifies revision **REV6.3.0** (© 2026 TP-Link).
- **Controller scope:** the guide calls the On-Premises Controller the Software Controller, Hardware Controller, or Integrated Gateway (Controller); it also covers the Omada Network system in Omada Central. It does **not** instruct for Omada Guard/VMS.
- **Feature caveat:** availability can vary by region, controller type/version, device model, firmware, and deployment. Treat the cited guide as V6.3 documentation, not proof a feature exists on a particular device.
- **Page labels in these references use physical PDF pages** (`PDF p.`). The guide's printed body page is given only where useful. For body pages 2–510, physical PDF page = printed page + 11; this mapping was checked at printed pp. 8→PDF 19, 491→PDF 502, and 503→PDF 514.
- These local notes are a compact index/paraphrase, not a substitute for the 521-page source. Consult the source page(s) before quoting detailed fields, defaults, limits, ports, or model prerequisites.

## Safety and answer pattern

1. Identify **deployment surface** (Software/Hardware/Integrated/Cloud), **site vs Global View**, device model/firmware, and desired outcome.
2. State dependencies and interruption risk before any proposed action: adoption/WAN overrides, VPN, migrations, firmware, MSP conversion, backup/restore, or clustering can disrupt service or overwrite data.
3. Give the documented navigation path and a reversible validation/checkpoint. Do not claim an unverified setting is harmless.
4. Do not execute controller, SSH, CLI, cloud, or network changes unless the user specifically authorizes the change.

## Reference routing

| Need | Load |
|---|---|
| Find a feature/chapter and page | `references/topic-index.md` |
| Safe practical workflows and common navigation paths | `references/operations.md` |
| Verify the separately retained source | `SOURCE.md` |

## Fast routing

- **First deployment, sites, adoption:** topic index §§2–3; operations “Initial rollout”.
- **Controller health, access, certificate, backups, migration, API/webhooks/SSO:** §§4–5.
- **Internet/WAN, LAN/VLAN, SSID, portal/802.1X:** §§6–8.
- **VPN, routing/NAT/QoS, profiles, security:** §§9–12.
- **Device/client/account administration:** §§13–16.
- **Monitoring, packet capture, backup, firmware:** §§17–18.
- **Multi-site SD-WAN, MSP, HA/distributed clusters:** §§19–21; read prerequisites and warnings in `operations.md` before advising a change.
