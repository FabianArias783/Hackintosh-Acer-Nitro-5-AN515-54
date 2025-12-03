[🇲🇽 Ver este README en español](README.md)

# 🖥️ Hackintosh – Intel i5-9300H Configuration (Laptop)

This repository documents my macOS installation (Ventura / Sonoma / Sequoia) on a laptop with a 9th-gen Intel CPU using **OpenCore 1.0.6**.  
Here you will find my EFI folder, installation notes, kext configuration, and all adjustments needed to keep the system stable.

---

## 📌 Table of Contents
1. [Project Description](#project-description)  
2. [Hardware Specifications](#hardware-specifications)  
3. [macOS Versions](#macos-versions)  
4. [Repository Structure](#repository-structure)  
5. [Kexts Used](#kexts-used)  
6. [OpenCore Configuration](#opencore-configuration)  
7. [Compatibility and Functionality](#compatibility-and-functionality)  
8. [Known Issues](#known-issues)  
9. [Important Notes](#important-notes)  
10. [Credits](#credits)

---

## 📝 Project Description
This project includes all files and configurations required to run macOS on a laptop with an Intel Coffee Lake processor (i5-9300H).  
The goal is to have a **clean, stable, upgradable, and well-documented installation**, following Dortania's OpenCore guides.

Includes:
- Full **EFI** folder  
- Organized and tuned `config.plist`  
- USB mapping  
- Updated kexts  
- Installation and troubleshooting notes  

---

## 🧩 Hardware Specifications

| Component | Model |
|-----------|--------|
| **CPU** | Intel Core i5-9300H @ 2.40 GHz (Coffee Lake) |
| **iGPU** | Intel UHD Graphics 630 — **Compatible** |
| **dGPU** | NVIDIA GTX 1650 — **NOT compatible with macOS** |
| **RAM** | *(Add your RAM here)* |
| **Storage** | *(Add your NVMe or SATA SSD)* |
| **Audio** | *(Realtek chip — add model if known)* |
| **Ethernet / WiFi / BT** | *(Add exact models if known)* |
| **Recommended SMBIOS** | MacBookPro15,2 |

> The GTX 1650 is fully disabled; macOS uses the Intel UHD 630 exclusively.

---

## 🍏 macOS Versions
Tested and working on:

- **macOS Ventura (13.x)**  
- **macOS Sonoma (14.x)**  
- **macOS Sequoia (15.x)**  

> ### ⚠️ WiFi Compatibility by macOS Version
> - **Ventura:** Intel WiFi works normally using *AirportItlwm*.  
> - **Sonoma & Sequoia:** No functional WiFi kext during installation. Only **Ethernet** works initially.  
> - After installation, WiFi can be enabled using the **Heliport** app.

Bootloader:
- **OpenCore 1.0.6**

---

## 🧷 Kexts Used

| Kext | Function |
|------|----------|
| **Lilu.kext** | Core patching framework |
| **WhateverGreen.kext** | Intel graphics fixes |
| **VirtualSMC.kext** | SMC virtualization for sensors |
| **SMCSuperIO / SMCProcessor** | Temperature and fan sensors |
| **AppleALC.kext** | Audio |
| **USBMap / USBToolBox** | Custom USB mapping |
| **RealtekRTL8111 / IntelMausi** | Ethernet (depending on chipset) |
| **VoodooPS2 / VoodooI2C** | Keyboard and trackpad (depends on laptop) |
| **AirportItlwm / IntelBluetoothFirmware** | Intel WiFi + Bluetooth (if applicable) |

> Adjust kexts depending on your actual hardware.

---

## ⚙️ OpenCore Configuration

### 🖥️ SMBIOS
- **MacBookPro15,2**  
- Serial generated using `macserial`  
- Real serial is not included for security reasons.

---

### 🧩 ACPI (SSDTs)
Includes:
- `SSDT-EC`
- `SSDT-PLUG`
- `SSDT-AWAC`
- `SSDT-PMC`
- `SSDT-SBUS-MCHC`
- `SSDT-XOSI` (if required for your laptop)
- `SSDT-USBX`

---

### 🧰 Drivers
- `OpenRuntime.efi`
- `OpenCanopy.efi` (if using GUI)
- `HfsPlus.efi`

---

### 🔧 Relevant Quirks
- Fixes for Coffee Lake CPU  
- DVMT configuration for UHD 630  
- Fully disabling NVIDIA GPU via ACPI or boot-args  

---

## ✅ Compatibility and Functionality

Working properly:

- Intel UHD 630 graphics acceleration  
- Audio (ALC + correct layout-id)  
- WiFi & Bluetooth (Intel/Broadcom depending on hardware)  
- Sleep / Wake  
- Integrated camera  
- Touchpad (PS2 or I2C depending on laptop)  
- Brightness, volume, battery indicators  
- iMessage, FaceTime, iCloud  
- USB 2.0 / 3.0 correctly mapped  

---

## ⚠️ Known Issues

- **NVIDIA GTX 1650 does not work** (no Turing GPU works on macOS).  
- USB configuration may need updates after system upgrades.  
- Sleep may fail if a USB device keeps the system active.  
- Brightness control may require extra patches depending on the panel.  

---

## 📓 Important Notes
- Update **OpenCore and kexts** before updating macOS.  
- NVIDIA GPU is fully disabled.  
- Recommended to use macOS-friendly NVMe SSDs (Samsung, WD, Kingston, etc.).  
- Always back up your EFI before making changes.  

---

## 🙌 Credits
- **Dortania** and their guides  
- **OpenCore** community  
- Kext developers: Acidanthera and others  
- **r/hackintosh** community  

---
