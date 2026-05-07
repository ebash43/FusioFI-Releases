# FusioFI Releases

Public downloads for FusioFI firmware and web packages.

## Downloads

Open the latest item in **Releases** and download the ZIP files you need.

## Which ZIP Do I Need?

- `ESP32.zip` - Use this when flashing an ESP32 board. Includes the ESP32 firmware binary, bootloader, partitions, Windows flashing tool, and flashing readme.
- `ESP8226.zip` - Use this when flashing an ESP8266/NodeMCU board. Includes the ESP8266 firmware binaries, NodeMCU PyFlasher, vendo data file, and flashing readme.
- `FusionFi_MultiFast.zip` - Use this for the MultiFast hotspot web files and MikroTik scripts.
- `SingleHotpot.zip` - Use this for the Single Hotpot package, including web files and vendo data.

## What's Inside?

```text
ESP32.zip
└── ESP32/
    ├── Readme.md
    ├── bootloader.bin
    ├── partitions.bin
    ├── firmware.bin
    ├── fusionfi32.bin
    ├── esptool.exe
    └── start_flash.bat

ESP8226.zip
└── ESP8226/
    ├── Readme.md
    ├── firmware.bin
    ├── firmware8226.bin
    ├── VendoCentralized.data
    └── NodeMCU-PyFlasher.exe

FusionFi_MultiFast.zip
└── FusionFi_MultiFast/
    ├── README.md
    ├── MikrotikScript/
    │   ├── OnLogin
    │   └── OnLogout
    └── flash/FusionFi/
        ├── alogin.html
        ├── error.html
        ├── login.html
        ├── logout.html
        ├── redirect.html
        ├── rlogin.html
        ├── status.html
        └── assets/
            ├── css/
            ├── img/
            ├── js/
            ├── coin-received.mp3
            ├── insertcoinbg.mp3
            └── loading.svg

SingleHotpot.zip
└── SingleHotpot/
    ├── README.md
    ├── SingleVendo.data
    ├── MikrotikScript/
    │   ├── OnLogin
    │   └── OnLogout
    └── flash/FusionFi_Single/
        ├── alogin.html
        ├── error.html
        ├── login.html
        ├── logout.html
        ├── redirect.html
        ├── rlogin.html
        ├── status.html
        └── assets/
            ├── css/
            ├── img/
            ├── js/
            ├── coin-received.mp3
            ├── insertcoinbg.mp3
            └── loading.svg
```

## Notes

- `SingleHotpot` is the folder name used by the package.
- Always use the latest GitHub Release unless you specifically need an older version.
- Firmware binaries are prebuilt and ready to flash.
