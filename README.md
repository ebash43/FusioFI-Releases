# FusionFi v2026.07.13

Public release for both platforms. Downloads are grouped below — **MikroTik** (portals, NodeMCU bins, web flasher) and **OpenWrt** (router image, downgrade firmware, NodeMCU bins, desktop flasher).

---

## MikroTik

### Portals

| File | What it is |
|---|---|
| `FusionFi.zip` | Standard hotspot portal |
| `FusionFi_dark.zip` | Dark theme portal |
| `FusionFi_light.zip` | Light theme portal |
| `FusionFi_MultiFast.zip` | Multi-router portal + `MikrotikScript/` (`OnLogin`, `OnLogout`, `HotspotProfileRules.rsc`) |
| `SingleHotpot.zip` | Single-vendo portal + `MikrotikScript/` (`OnLogin`, `OnLogout`, `HotspotProfileRules.rsc`) |

Upload the portal folder to the router's `flash/` directory and point the Hotspot
Server Profile's `html-directory` at it. For MultiFast and SingleHotpot, apply
`MikrotikScript/HotspotProfileRules.rsc` and paste `OnLogin` / `OnLogout` into the
`FusionFi` hotspot user profile. Keep `HTTP PAP` enabled in the server profile
for fast relogin.

**SingleHotpot note:** this package intentionally ships **without** the full
auto-provision scripts (`startup.rsc`, `FusionfiSingle.rsc`, `SingleVendo.data`)
that configured users, WiFi keys, and NodeMCU bindings. Create your own admin
user, set your own wireless key, and see `README.md` inside the zip for the
required profile names (`FusionFi` user profile, `flash/FusionFi_Single` paths,
NodeMCU at `10.0.0.2`).

### NodeMCU firmware

| File | What it is |
|---|---|
| `ESP32.zip` | ESP32 set: `fusionfi32.bin` + `bootloader.bin` + `partitions.bin`, `esptool.exe`, `start_flash.bat`, readme |
| `ESP8226.zip` | ESP8266/NodeMCU set: `firmware.bin` / `firmware8226.bin`, `NodeMCU-PyFlasher.exe`, `start_flash.bat`, readme |
| `fusionfi32.bin` | ESP32 app image only (for the web flasher) |
| `firmware8226.bin` | ESP8266 image only (for the web flasher) |
| `Flasher.zip` | Browser-based ESP flasher (`bin_flasher.html`, esptool-js) + CP210x / CH341 USB drivers for Windows and Mac |

---

## OpenWrt (Ruijie RG-EW1200G PRO v1.1)

FusionFi is **not** shipped as a pre-baked image. Flash stock OpenWrt, then the
FusionFi Flasher installs and licenses the unit over the network. Each unit gets
its own random root password and license binding.

| File | What it is |
|---|---|
| `ReyeeOS-1.317-downgrade-EW1200G-PRO.tar.gz` | Stock ReyeeOS 1.317 — the tested downgrade path |
| `openwrt-24.10.0-ramips-mt7621-ruijie_rg-ew1200g-pro-v1.1-squashfs-sysupgrade.bin` | Stock OpenWrt 24.10.0 |
| `FusionFi-Flasher-0.7.8-win-x64.exe` | FusionFi Flasher — Windows (portable, no install) |
| `FusionFi-Flasher-0.7.8-mac-arm64.dmg` | FusionFi Flasher — Mac (Apple Silicon; unsigned, right-click → Open first time) |
| `fusionfi-openwrt-esp32-app.bin` | FusionFi OpenWrt NodeMCU firmware — ESP32 |
| `fusionfi-openwrt-esp8266.bin` | FusionFi OpenWrt NodeMCU firmware — ESP8266 |

### Install steps

1. **Confirm the label says RG-EW1200G PRO v1.1.** Stop if the revision differs.
2. **Downgrade:** in the ReyeeOS upgrade page, install
   `ReyeeOS-1.317-downgrade-EW1200G-PRO.tar.gz` and wait for a full reboot.
3. **Flash OpenWrt:** from ReyeeOS 1.317's upgrade page, flash the
   `...squashfs-sysupgrade.bin`. Do not refresh, unplug, or reset while it
   writes. After ~5 minutes the router boots plain OpenWrt at `192.168.1.1`.
4. **Install FusionFi:** plug WAN into internet, run the FusionFi Flasher
   (Windows exe or Mac dmg), enter your license key, set Router IP to
   `192.168.1.1`, and click **Flash FusionFi + Activate** (~3–4 min).
   The unit comes up with the portal at `http://10.0.0.1/` and admin at
   `http://10.0.0.1/admin/`.
5. **NodeMCU:** flash `fusionfi-openwrt-esp32-app.bin` or
   `fusionfi-openwrt-esp8266.bin` to the coin node with the flasher.

Verify the OpenWrt image before flashing:

```
sha256: 4ab9d7097eba89dbc570107470730daef9a487d664b95fb97280506bda615810
```

Re-licensing an existing unit: point the flasher at `10.0.0.1` — it detects
FusionFi and only re-licenses + rotates the root password.

---

*This release replaces all earlier releases, which have been removed.*
