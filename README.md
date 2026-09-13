# WaveRig

An open-hardware ESP32-S3 BLE bridge between amateur radio transceivers and [Wavelog Mobile](https://github.com/MaviKulubeliAdam/Wavelog-Mobile) / [Wavelog](https://github.com/wavelog/wavelog).

WaveRig connects to your radio's CI-V (ICOM) or CAT (Yaesu/Kenwood) interface, reads live frequency, mode and power, and streams it over Bluetooth Low Energy straight into your QSO log — no more typing frequency and mode by hand for every contact.

---

## Status: Early hardware development

- 🔧 Schematic in progress
- ⬜ PCB layout not started yet (65×45 mm, 2-layer target)
- ⬜ Firmware not started yet
- ⬜ No boards fabricated/tested yet

This repository will track schematic/PCB sources, the bill of materials, and firmware once development begins. Contributions, feedback and testing help are welcome even at this stage.

---

## Planned Features

- **CI-V support** — ICOM radios (IC-7300, IC-705, IC-9700, IC-7610, and others) via a 3.5mm jack
- **CAT support** — Yaesu / Kenwood radios (FT-891, FT-991A, FT-DX10, TS-590, TS-890, and others) via RS-232 (DB9) through a MAX202 level shifter
- **BLE GATT service** — frequency, mode, submode, TX power and rig model pushed live to any connected app
- **Rechargeable** — LiPo battery with USB-C charging (TC4056A) and protection (DW01A + FS8205A)
- **USB-C native flashing** — no external USB-serial adapter needed; flash directly over the same USB-C port
- **OLED status display** — shows frequency, mode and connection status at a glance
- **BLE OTA firmware updates** — update via the companion phone app, no cable required (planned)

## Hardware Overview

| | |
|---|---|
| MCU | ESP32-S3-WROOM-1 (N16R8, 16MB flash) |
| Power | LiPo 3.7V, USB-C charging, boost to 3.3V (MT3608) |
| CI-V | 3.5mm jack, open-drain driver (2N7000) |
| CAT / RS-232 | DB9, MAX202EESE+T level shifter |
| Display | I2C OLED (SSD1306, 4-pin connector) |
| PCB | 65×45mm, 2-layer |

Schematic and PCB design are being developed by **Süalp, TA4HCK**. Full BOM, pin assignments and net-by-net connection notes will be published in this repo as the hardware design is finalized.

## Firmware Roadmap

1. BLE GATT service (frequency / mode / submode / power / rig model, notify-based)
2. CI-V protocol parsing (ICOM)
3. CAT protocol parsing (Yaesu / Kenwood)
4. OLED UI
5. BLE OTA updates (phone acts as the bridge to the internet — no Wi-Fi needed on-device)

## Related Projects

- [Wavelog Mobile](https://github.com/MaviKulubeliAdam/Wavelog-Mobile) — the Android companion app WaveRig connects to
- [Wavelog](https://github.com/wavelog/wavelog) — the self-hosted amateur radio logging server

## Contributing

This project is in early hardware development — schematic and PCB files, along with contribution guidelines, will be added as the design stabilizes. Issues and discussion are welcome in the meantime.

## License

Licensed under the [Apache License 2.0](LICENSE).

---

By TA4RX / SP9AQG (firmware / software) and Süalp, TA4HCK (schematic / PCB)
