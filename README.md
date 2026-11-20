# eve-ng-labs

A shared collection of EVE-NG network labs, provided so others can study, test, and build on them.

## About this repository

This repository contains lab topologies and instructions created in **EVE-NG Version 7.x**. Each lab includes a topology file, device configurations where applicable, and a README that describes the devices used and the steps to run the lab.

## Compatibility

These labs were created on EVE-NG 7.x and may not work on the older 6.x Community Edition. Check the README in each lab folder for the exact EVE-NG version and device images used.

## Device images are not included

This repository does not include vendor device images, such as Cisco, Juniper, Palo Alto, or Aruba images. These images are licensed by their vendors, and redistributing them is not permitted.

To run a lab, you must obtain every required image yourself, from a source you are licensed to use. Each lab's README lists the devices and image versions it expects. Verify that you have the correct images and the right to use them before you import a lab.

## Repository layout

```
eve-ng-labs/
├── README.md
└── <lab-name>/
    ├── README.md        # Devices, required images, and step-by-step instructions
    ├── <lab-name>.unl   # EVE-NG topology file
    └── configs/         # Starting device configurations
```

## Using a lab

1. Clone this repository or download the lab folder you want.
2. Read the lab's README and confirm you have every listed device image.
3. Import the `.unl` file into your EVE-NG server.
4. Load the configurations from the `configs/` folder, if the lab includes them.
5. Follow the lab's instructions.

## Disclaimer

These labs are provided as-is, without warranty of any kind. They are intended for learning and testing in isolated environments. Do not use them on production networks. Review all configurations before use, and remove any credentials or addresses you do not want to use.

## License

This repository is licensed under the GNU General Public License v3.0. See [LICENSE](LICENSE) for details. Vendor device images and trademarks are not covered by this license.
