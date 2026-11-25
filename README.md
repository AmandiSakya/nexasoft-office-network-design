# NexaSoft Office Network Design

> A two-floor wired and wireless office network design for NexaSoft Solutions (Pvt) Ltd, covering requirement analysis, logical and physical design, device specifications and a full cost estimate.

**Course:** IE2004 Computer Networks, Faculty of Computing, Sri Lanka Institute of Information Technology (SLIIT)
**Type:** Group assignment (5 members)
**Submitted:** 19 October 2026

📄 Full report: [`NexaSoft_Network_Design_Report_Final.pdf`](./NexaSoft_Network_Design_Report_Final.pdf)

---

## Project Overview

NexaSoft Solutions is a small software company with about 25 staff working in a two-storey building. Each floor measures 16 m × 8 m. The task was to design a network that provides wired and wireless connectivity for at least 32 wired and 32 wireless end devices, and to justify every design decision with calculations, diagrams and real supplier prices.

### Design at a Glance

| Item | Design |
|---|---|
| Building | 2 floors, 16 m × 8 m each, comms room on the ground floor, storage room above it |
| Wired devices | 33 (17 ground floor, 16 first floor), including 2 access points |
| Wireless devices | 41 (21 ground floor, 20 first floor) |
| Topology | Star: ISP router → ground floor switch (SW-GF) → first floor switch (SW-FF) |
| Switches | 2 × TP-Link JetStream TL-SG3428 (managed, 24 × 1 Gbps + 4 SFP) |
| Access points | 2 × TP-Link Omada EAP610 (Wi-Fi 6), one per floor |
| Cabling | Cat6 UTP to 37 wall outlets (longest run about 26 m); multimode fibre between floors |
| Racks and power | 12U and 9U wall-mount racks, one line-interactive UPS per rack |
| Internet | Dialog Fibre Unlimited, 600 Mbps |
| One-time cost | LKR 868,249 |
| Monthly cost | LKR 33,950 (Internet, including tax) |

---

## Report Contents

1. **Requirement Analysis**: floor plans, wired and wireless device counts, Internet options, bandwidth and data volume estimates
2. **Logical Network Design**: network schematic, link speeds, wired links and port allocation
3. **Physical Design, Cabling and AP Placement**: UTP and fibre cabling, outlet placement, patch cords, rack layout, access point placement
4. **Physical Design, Device Specifications**: switches, access points, PoE, UPS sizing
5. **Cost Estimate**: itemised costs with supplier sources, labour, monthly subscription and totals
6. **Conclusion and References**

---

## My Contribution: Part 4, Physical Network Design: Device Specifications

This part selects and justifies the active network devices used in the design, and checks that each one meets the requirements of the network.

### 4.1 Switches
- Selected one **TP-Link JetStream TL-SG3428** per floor: a managed Layer 2+ switch with 24 × 1 Gbps RJ45 ports and 4 SFP slots.
- Supports **SNMP, RMON and IEEE 802.1Q VLANs**, so the network can be segmented later without replacing hardware.
- Port usage: SW-GF uses 18 of 24 ports (17 devices + router), SW-FF uses 16 of 24 ports, with spare ports left for growth.
- The two switches are linked by fibre using a **TP-Link TL-SM311LM SFP module** in one SFP port on each switch.
- Non-PoE switches were chosen deliberately to keep cost down, since only two access points need power.

### 4.2 Access Points
- Selected one **TP-Link Omada EAP610** per floor: a Wi-Fi 6 (802.11ax) dual-band, ceiling-mount AP (AX1800: 1201 Mbps on 5 GHz, 574 Mbps on 2.4 GHz).
- Each AP serves about 20 wireless clients, far below its 250+ client capability, with roughly 115 m² of coverage.
- The 2.4 GHz band provides reach through walls and the 5 GHz band provides higher speed at close range.

### 4.3 Power over Ethernet
- Used one **TP-Link TL-POE150S** (IEEE 802.3af, 15.4 W) PoE injector per AP instead of PoE switches.
- The AP draws 10.9 W, which leaves about 4.5 W of headroom on the injector.
- A PoE switch would leave at least six ports unused per floor and cost much more. PoE switches become the better option if more APs are added later.

### 4.4 Uninterruptible Power Supplies
- Each rack has a line-interactive UPS so the active equipment survives power cuts and voltage drops.
  - **Ground floor:** APC Smart-UPS SMC1000I (1000 VA / 600 W)
  - **First floor:** APC Back-UPS BX650CI (650 VA / 390 W)
- Sizing method: estimate the equipment load (about 75 W and 60 W), add a **50% safety margin** (about 115 W and 90 W), then select a UPS well above that figure, leaving room for extra equipment and longer runtime.

---

## Group Members and Work Allocation

| Part | Section  | Member |
|---|---|---|---|
| 1 | Requirement analysis | Nimradha G. S. |
| 2 | Logical network design | Perera M.R.S |
| 3 | Physical design, cabling and AP placement | Elead E.M.P |
| 4 | Physical design, device specifications | **Senevirathne A.S.W** |
| 5 | Cost estimate | Sandupama G.D.D.S. |

---

## Notes

- End devices (PCs, printers, phones, laptops) are not included in the schematic or cost estimate.
- Items marked "Estimate" in the cost tables (access points, UPS units, 2 m patch cords and labour) are planning figures and should be replaced with supplier or contractor quotations before ordering.
- Prices were checked on 19 October 2026. USD-priced items were converted at Rs 335.95 per US dollar.

## Tools and Technologies

Cisco Packet Tracer (network schematic), Cat6 UTP, multimode fibre, Wi-Fi 6 (802.11ax), IEEE 802.3af PoE, IEEE 802.1Q VLANs.

## License

This repository is for academic purposes. All rights to the original report content belong to the authors.
