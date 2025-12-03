[🇺🇸 View this README in English](README_en.md)

# 🖥️ Hackintosh – Configuración Intel i5-9300H (Laptop)

Este repositorio documenta mi instalación de macOS (Ventura / Sonoma / Sequoia) en una laptop con CPU Intel 9ª generación, usando **OpenCore 1.0.6**.  
Aquí encontrarás mi carpeta EFI, notas de instalación, configuración de kexts y ajustes necesarios para mantener el sistema estable.

---

## 📌 Tabla de contenido
1. [Descripción del proyecto](#descripción-del-proyecto)  
2. [Especificaciones del hardware](#especificaciones-del-hardware)  
3. [Versiones de macOS](#versiones-de-macos)  
4. [Estructura del repositorio](#estructura-del-repositorio)  
5. [Kexts utilizados](#kexts-utilizados)  
6. [Configuraciones de OpenCore](#configuraciones-de-opencore)  
7. [Compatibilidad y funcionamiento](#compatibilidad-y-funcionamiento)  
8. [Problemas conocidos](#problemas-conocidos)  
9. [Notas importantes](#notas-importantes)  
10. [Agradecimientos](#agradecimientos)

---

## 📝 Descripción del proyecto
Este proyecto reúne todos los archivos y configuraciones necesarios para ejecutar macOS en una laptop con procesador Intel Coffee Lake (i5-9300H).  
El objetivo es una instalación **limpia, estable, actualizable y documentada**, siguiendo las guías de Dortania para OpenCore.

Incluye:
- Carpeta completa **EFI**
- `config.plist` ajustado y ordenado
- USB mapping
- Kexts actualizados
- Notas de instalación y troubleshooting

---

## 🧩 Especificaciones del hardware

| Componente | Modelo |
|-----------|--------|
| **CPU** | Intel Core i5-9300H @ 2.40 GHz (Coffee Lake) |
| **iGPU** | Intel UHD Graphics 630 — **Compatible** |
| **dGPU** | NVIDIA GTX 1650 — **NO compatible con macOS** |
| **RAM** | *(Agregar tu RAM)* |
| **Almacenamiento** | *(Agregar tu SSD NVMe o SATA)* |
| **Audio** | *(Chip Realtek / añadir modelo si lo tienes)* |
| **Ethernet / WiFi / BT** | *(Modelos exactos si los conoces)* |
| **SMBIOS recomendado** | MacBookPro15,2 |

> La GTX 1650 queda deshabilitada; macOS usa exclusivamente la Intel UHD 630.

---

## 🍏 Versiones de macOS
Probado y funcional en:

- **macOS Ventura (13.x)**  
- **macOS Sonoma (14.x)**  
- **macOS Sequoia (15.x)**  

> ### ⚠️ Compatibilidad de WiFi por versión de macOS
> - **Ventura:** El WiFi Intel funciona con *AirportItlwm* sin problemas.  
> - **Sonoma y Sequoia:** No hay kext funcional durante la instalación. Solo funciona **Ethernet** al inicio.  
> - Después de instalar, se puede activar WiFi usando la app **Heliport**.

Bootloader:
- **OpenCore 1.0.6**

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
