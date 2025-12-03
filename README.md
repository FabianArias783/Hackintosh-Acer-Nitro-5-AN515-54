
---

## 🧷 Kexts utilizados

| Kext | Función |
|------|---------|
| **Lilu.kext** | Framework principal |
| **WhateverGreen.kext** | Fixes de gráficos Intel |
| **VirtualSMC.kext** | SMC virtual para sensores |
| **SMCSuperIO / SMCProcessor** | Lectura de temperaturas y ventiladores |
| **AppleALC.kext** | Audio |
| **USBMap / USBToolBox** | Mapeo USB personalizado |
| **RealtekRTL8111 / IntelMausi** | Ethernet (dependiendo del chipset) |
| **VoodooPS2 / VoodooI2C** | Teclado y trackpad, según laptop |
| **AirportItlwm / IntelBluetoothFirmware** | WiFi Intel y Bluetooth (si aplica) |

> Ajusta los kexts dependiendo de tu hardware real.

---

## ⚙️ Configuraciones de OpenCore

### 🖥️ SMBIOS
- **MacBookPro15,2**  
- Serie generada con `macserial`  
- No se incluye serie real por seguridad.

### 🧩 ACPI (SSDTs)
Incluye:
- `SSDT-EC`
- `SSDT-PLUG`
- `SSDT-AWAC`
- `SSDT-PMC`
- `SSDT-SBUS-MCHC`
- `SSDT-XOSI` (si tu laptop lo requiere)
- `SSDT-USBX`

### 🧰 Drivers
- `OpenRuntime.efi`
- `OpenCanopy.efi` (si usas GUI)
- `HfsPlus.efi`

### 🔧 Quirks relevantes
- Fixes para CPU Coffee Lake  
- Configuración de DVMT para UHD 630  
- Deshabilitar la GPU NVIDIA vía ACPI o boot-args  

---

## ✅ Compatibilidad y funcionamiento

Funciona correctamente:

- Aceleración gráfica Intel UHD 630  
- Audio (ALC + layout-id adecuado)  
- WiFi y Bluetooth (si usas Intel o Broadcom compatible)  
- Sleep / Wake  
- Cámara integrada  
- Touchpad (PS2 o I2C según modelo)  
- Teclas de brillo, volumen, batería  
- iMessage, FaceTime, iCloud  
- USB 2.0 / 3.0 mapeados  

---

## ⚠️ Problemas conocidos

- **GPU NVIDIA GTX 1650 no funciona** (ninguna Turing funciona en macOS).  
- Puede requerir ajustes adicionales de USB en algunas actualizaciones.  
- El Sleep puede fallar si algún dispositivo USB queda activo.  
- Brillo puede necesitar parches dependiendo del panel.  

---

## 📓 Notas importantes
- Actualiza **OpenCore y kexts** antes de actualizar macOS.  
- La GPU NVIDIA está deshabilitada completamente.  
- Se recomienda usar SSD NVMe compatible con macOS (Samsung, WD, Kingston, etc.).  
- Siempre respaldar la EFI previo a cambios.  

---

## 🙌 Agradecimientos
- **Dortania** y sus guías completas  
- Comunidad de **OpenCore**  
- Developers de kexts: Acidanthera y otros  
- Comunidad de **r/hackintosh**  

---
