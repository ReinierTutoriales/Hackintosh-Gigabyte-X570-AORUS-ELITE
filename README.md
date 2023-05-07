# Bienvenido al repositorio oficial de ReinierTutoriales Compatible con macOS BigSur Monterrey y Ventura
[![X570 AORUS ELITE](https://static.gigabyte.com/StaticFile/Image/Global/907eecfe94da125eb443dc223715d8cd/Product/22419/webp/1000 "X570 AORUS ELITE")](https://static.gigabyte.com/StaticFile/Image/Global/907eecfe94da125eb443dc223715d8cd/Product/22419/webp/1000 "X570 AORUS ELITE")

## Apóyame con una donación 
Mediante [👉PayPal💵](https://www.paypal.com/paypalme/ReinierTutoriales?country.x=US&locale.x=es_XC)


## **Qué contiene este repositorio  👇**
Este repositorio contiene el directorio EFI para el combo Ryzen 5 3600 y MotherBoard Gigabyte X570 Aorus Elite.
## Especificaciones

| Componente   | Nombre del Producto                              | Notas                                          |
|--------------|--------------------------------------------------|------------------------------------------------|
| CPU          | AMD Ryzen 5 3600                                 | PBO Activado                                   |
| Motherboard  | Gigabyte X570 Aorus Elite                        | BIOS F38b                                      |
| Memoria RAM  | 16GB DDR4 3200MHz                                | Overclocked a 3200MHz                          |
| Gráficos     | Gigabyte AMD Radeon RX 5500XT 8GB                |                                                |
| Disco Duro   | NMVe XPG Atom 50 1TB PCIe Gen4                   |                                                |
| Red Ethernet | Intel® GbE LAN                                   |                                                |
| BT/WIFI      | Fenvi T919 (BCM94360CD)                          |                                                |

##onfiguración del BIOS
Enter BIOS -> Press Delete -> Enter Setup​
Exit -> Load Optimised Defaults​
Ai Tweaker -> Ai Overclock Tuner -> D.O.C.P.​
Advanced -> APM Configuration -> Power On By PCIe -> Disabled​
Advanced -> PCI Subsystem Settings -> Above 4G Decoding -> Disabled​
Advanced -> PCI Subsystem Settings -> Re-Size BAR Support -> Disabled​
Advanced -> USB Configuration -> Legacy USB Support -> Auto or Disabled​
Boot -> Boot Configuration -> Fast boot -> Disabled​
Boot -> CSM -> Launch CSM -> Disabled​
Boot -> Secure boot -> OS Type -> Windows UEFI mode​
Boot -> Secure boot -> Key Management -> Clear Secure Boot Keys


- **MotherBoard**: Gigabyte X570 Aorus Elite [👉Compr Aquí💵](https://amzn.to/30KCO2k "Gigabyte X570 Aorus Elite")
- **Procesador**: Ryzen 5 3600 [👉Compr Aquí💵](https://amzn.to/3Ag2N0q "Ryzen 5 3600")
- **RAM**: 32GB Corsair Vengeance RGB Pro (2 x 16 GB)DDR4 3600(PC4-28800)memoria optimizada AMD [👉Compr Aquí💵](https://amzn.to/3JPyWiu "32GB Corsair Vengeance RGB Pro (2 x 16 GB)DDR4 3600(PC4-28800)memoria optimizada AMD")
- **BT / WIFI**: Fenvi T919 BCM94360CD [👉Compr Aquí💵](https://amzn.to/3w3fkBX "Fenvi T919 (BCM94360CD)")
### Recomendación
- Te recomiendo que uses esto solo como un recurso de referencia.
- Este EFI contiene kexts adicionales en config.plist en lugar de solo las cosas esenciales para la CPU X570 + Zen2. Debe eliminarlos antes de usar esto en su PC.

### Verifique esto antes de usar
En el archivo config.plist , genere códigos de serie nuevos ya que este carece de ellos, pues son personales y cada Mac necesita los de ella propios. Para generar la clave de serie, consulte la Guía OpenCore de Dortania . Cuando genere uno, debe seleccionar MacPro7,1 para un correcto funcionamiento.

### Otro apartado a verificar es
- En los nuevos parches de CPU de AMD, ahora tenemos que especificar los recuentos de núcleos de CPU en los algrey - Force cpuid_cores_per_packagenodos. Actualmente, mi configuración de EFI establece para el modelo de CPU de 6 núcleos porque estoy usando Ryzen 5 3600.

- El parche Core Count debe modificarse para iniciar su sistema. Encuentre los cuatro parches `algrey - Force cpuid_cores_per_package`  y modifique el valor  `Replace`.

|   macOS Version      | Replace Value | New Value |
|----------------------|---------------|-----------|
| 10.13.x, 10.14.x     | B8000000 0000 | B8 < Core Count > 0000 0000 |
| 10.15.x, 11.x        | BA000000 0000 | BA < Core Count > 0000 0000 |
| 12.x, 13.0 to 13.2.1 | BA000000 0090 | BA < Core Count > 0000 0090 |
| 13.3                 |  BA000000 00  | BA < Core Count > 0000 00 |


- De la tabla anterior, sustitúyalo `< Core Count >` por el valor hexadecimal que coincida con su recuento de núcleos físicos. No utilice el número de thread o hilos de su CPU. Consulte la siguiente tabla para ver los valores que coinciden con el número de núcleos de su CPU.

| Core Count | Hexadecimal |
|------------|-------------|
|   4 Core   |     `04`    |
|   6 Core   |     `06`    |
|   8 Core   |     `08`    |
|   12 Core  |     `0C`    |
|   16 Core  |     `10`    |
|   24 Core  |     `18`    |
|   32 Core  |     `20`    |

[Consulte la descripción del autor para obtener más información.](https://github.com/AMD-OSX/AMD_Vanilla#instructions "Consulte la descripción del autor para obtener más información.")
## OpenCore
**Versión**: 0.9.2
### Estructura EFI
## ACPI
- SSDT-USBX.aml

## Drivers
- HfsPlus.efi
- OpenCanopy.efi
- OpenRuntime.efi
- ResetNvramEntry.efi
- ToggleSipEntry.efi
## Kexts
- AMDRyzenCPUPowerManagement.kext
- AppleALC.kext
- AppleIGB.kext
- AppleMCEReporterDisabler.kext
- Lilu.kext
- NVMeFix.kext
- RestrictEvents.kext
- SMCAMDProcessor.kext
- VirtualSMC.kext
- WhateverGreen.kext
## Tools
- OpenShell.efi
- ResetSystem.efi
## Que funciona y que no funciona
### Finciona
- Casi todo, incluida las actualizaciones de Apple (Handoff, iMessage, Airdrop, Facetime, ...)
### Funciona parcialmente
- Tomas de audio de 3,5 mm
- La salida de altavoz en el panel frontal / posterior funciona.
- La entrada de micrófono en el panel frontal / posterior no funciona.
- No he probado la entrada / salida de línea y la salida digital.
- Los problemas habituales de Ryzentosh. Consulte la parte de soporte de CPU de la Guía OpenCore de Dortania
- Es posible que sea necesario parchear aplicaciones profesionales específicas para procesadores AMD, como aplicaciones de Adobe, Davinci Resolve, etc.
- La virtualización (Apple Hypervisor y las aplicaciones que usan esto como AVD en Android Studio, Parallels) no funciona, pero VirtualBox sí.
### No funciona

## Referencias
- [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/ "Dortania's OpenCore Install Guide")
- [Forum ReinierTutoriales](https://www.reiniertutoriales.com)
😎
