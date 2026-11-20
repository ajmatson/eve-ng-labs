<p align="center">
  <img src="images/rambling-architect-logo-v2.svg" alt="Rambling Architect logo" width="600">
</p>

<h1 align="center">eve-ng-labs</h1>

<p align="center">
  Shared EVE-NG network and security labs, with topologies, configurations, and step-by-step instructions.
</p>

---

## About

This repository is a shared collection of EVE-NG labs for studying, testing, and building network and security designs. The labs were created on **EVE-NG Version 7.x**. They may not work on the older 6.x Community Edition.

## Device images are not included

This repository does not contain vendor device images such as Cisco, Juniper, Palo Alto, or Aruba. These images are licensed by their vendors, and redistributing them is not permitted.

Before you import a lab, you must obtain every image it requires from a source you are licensed to use. Each lab's README lists the devices and image versions it expects.

## Lab index

| Lab | Topic | EVE-NG | Devices |
|-----|-------|--------|---------|
| [juniper-vxlan-core](aruba-vsrx-core/) | Simple VxLAN config between two Juniper vEX core layer 3 switches and two VPS on each side. | 7.x | Juniper vEX, VPCS |

## Using a lab

1. Clone this repository or download the folder for the lab you want.
2. Read the lab's README and confirm you have every required image.
3. Import the `.unl` topology file into your EVE-NG server.
4. Load the configurations from the `configs/` folder, if the lab includes them.
5. Follow the steps in the lab's README.

## Repository layout

```
eve-ng-labs/
├── README.md
├── rambling-architect-logo-v2.svg
└── <lab-name>/
    ├── README.md        # Purpose, devices, required images, and steps
    ├── <lab-name>.unl   # EVE-NG topology file
    └── configs/         # Starting device configurations
```

## Contributing

Each lab folder should include a README that covers its purpose, devices, required images with versions, IP plan, and test steps. Before you commit, remove passwords, keys, license strings, and any public or internal addresses you don't want to publish.

## Disclaimer

These labs are provided as-is, without warranty. They are intended for learning and testing in isolated environments, not on production networks. Review every configuration before use.

## License

Licensed under the [GNU General Public License v3.0](LICENSE). Vendor device images and trademarks are not covered by this license.
