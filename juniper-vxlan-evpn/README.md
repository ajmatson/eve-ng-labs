# Juniper VXLAN/EVPN Lab

Two Juniper vJunos-switch cores run a stretched 10.100.0.0/24 segment using EVPN-VXLAN. Each core has a PC on the same subnet, at two different sites.

## Devices

| Node | Role | Address |
|---|---|---|
| CaliforniaCore | Leaf switch | ge-0/0/0 10.1.1.1/30, ge-0/0/1 10.100.0.1/24, lo0 172.16.255.1/32 |
| NewYorkCore | Leaf switch | ge-0/0/0 10.1.1.2/30, ge-0/0/1 10.100.0.2/24, lo0 172.16.255.2/32 |
| CaliforniaPC | VPCS host | 10.100.0.11/24, gateway 10.100.0.1 |
| NewYorkPC | VPCS host | 10.100.0.12/24, gateway 10.100.0.2 |

## Required image

- `vjunosswitch-24.4R1.9`

This repository does not include the image. You must obtain it yourself from a source you are licensed to use.

## Login

Juniper vJunos-switch login (lab use only):

- Username: `root`
- Password: `Jun1p3r`

Never reuse this password on real equipment.

## Files

- `Juniper-VXLAN-Lab.unl`: EVE-NG topology file
- `configs/CaliforniaCore.set` and `configs/NewYorkCore.set`: step 1 core configs
- `PC-instructions.md`: how to set the two PCs

## Step 1: Physical and addressing layer

Import the lab, start the four nodes, then paste the matching `.set` file into each core:

```
configure
load set terminal
(paste the file, then press Ctrl-D)
commit
```

Set the PCs using `PC-instructions.md`.

**Expected result:** each PC pings its own gateway. Pings between the two sites fail, which is expected until step 2.

Tag: `step1-baseline`

## Step 2: Routing and EVPN-VXLAN

Step 2 is on the lab canvas and in the `step2-routing-vxlan` branch. It covers:

1. eBGP underlay between the cores over 10.1.1.0/30
2. VLAN 100 mapped to VNI 10100
3. EVPN-VXLAN using the loopbacks as VTEPs
4. Moving `ge-0/0/1` into VLAN 100
5. Gateway addresses on `irb.100`

**Goal:** CaliforniaPC and NewYorkPC can ping each other.

Status: not yet tested end to end. Report any differences from these steps so the instructions can be corrected.
