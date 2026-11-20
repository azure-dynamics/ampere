# Ampere

**Power distribution board for Azure Dynamics' Radiance ROV**

Ampere distributes main battery power to the logic branch and to each thruster. It adds input protection, per-thruster fusing, and a physical arming plug so propulsion can only be armed with the hull open.

Ampere pairs with [Navigator](../navigator), the flight-controller Pi HAT it powers.

---

## Features

* **Battery Input:** XT60/XT90 connectors with support for parallel battery packs, fused per pack.
* **Input Protection:** TVS diode across the main bus.
* **Logic Branch:** Always-on, fused supply to Navigator, which regulates it down for the Raspberry Pi and logic.
* **Propulsion Branch:** Gated by a physical arming plug, then split into six individually fused outputs, one per ESC.
* **Current Sensing:** Shunt-based pack current measurement on the propulsion branch.
* **Heavy Copper:** Wide pours sized for the thruster current budget.

---

## Safety Model

* Propulsion is armed only by inserting the arming plug, which is only possible with the hull open.
* Logic power is independent of the plug, so the flight controller stays alive while thrusters are disarmed.
* Firmware holds neutral PWM at boot and requires an explicit arm command before ramping.

---

## Board Layout & Architecture

* **Layers:** 4-layer board design with 2 oz outer copper.
* **Form Factor:** Sized to fit the electronics sled inside the 96 mm ID hull.

---

## Project Status

* **Schematic:** In progress
* **Layout:** Not started
* **Fabrication:** Not yet ordered

---

## Repository Layout

```text
ampere/
├── hardware/       KiCad project and local symbol/footprint libraries
├── fabrication/    Manufacturing outputs (BOM, Gerbers, drill files)
├── docs/           Project documentation
├── LICENSE
└── README.md
```

---

## License

Copyright (C) 2026 Azure Dynamics.

This project is licensed under the
[CERN Open Hardware Licence Version 2 - Strongly Reciprocal](LICENSE)
(`CERN-OHL-S-2.0`). See [LICENSE](LICENSE) for the full text.

Third-party symbols, footprints, and STEP models in `hardware/library/` are
included for convenience and remain subject to their original terms.
