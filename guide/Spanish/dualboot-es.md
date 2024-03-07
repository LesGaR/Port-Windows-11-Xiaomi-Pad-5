<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutar Windows en el Xiaomi Pad 5

## Arranque dual de Android y Windows sin problemas

### Requisitos previos
- ```Cerebro```
- ```Tablet roteada```
- ```Windows instalado en la tablet```
- [```Imagen UEFI```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)
- [```WOA Helper app```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk)
- [```StA Installer```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/StA_Installer_nabu.exe)

## Configurar la aplicación de arranque dual
> Esta guía asume que su tablet esta rooteada; si no lo está, siga primero la [Guía root ](2-rootguide-es.md)

### Configuración - Android
> [!NOTE]
> Si no puede mover archivos a la carpeta de Windows, significa que cerró Windows en lugar de reiniciarlo. Para solucionar este problema, reinicie Windows usando la opción de reiniciar, luego, cuando se reinicie, inicie fastboot y utilícelo para regresar a Android.

- Descargue e instale la [aplicación WOA Helper](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk)luego ábrala y concédale acceso de root.
- Descargue la [UEFI image](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img) y colóquela dentro de la carpeta nombrada `UEFI` en su almacenamiento interno, si esta carpeta no existe, créela.
- Regrese a la aplicación WOA Helper y presione el botón `Back up Android boot`. Seleccione las opciones `Windows` and `Android`.
- Presione el botón `Mount Windows`, luego descargue y mueva [StA_Installer_nabu.exe](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/StA_Installer_nabu.exe) a la carpeta recién creada  `Windows` en su almacenamiento interno.
- Regrese a la aplicación WOA Helper y presione `Quickboot to Windows`.

### Configuración: Windows
- Navegue a `C:\StA_Installer_nabu.exe` y ejecútelo. Si no funciona, asegúrese de que el software antivirus esté desactivado, ya que probablemente no permitirá que la aplicación se ejecute.

##### Arrancando en Android
  - Ejecute el nuevo acceso directo en su escritorio (también puede fijarlo en su menú de inicio/barra de tareas para facilitar el acceso)

##### Arrancando en Windows
  - Presione `Quickboot to Windows` dentro de la aplicación o use el acceso directo recién creado en su panel de configuración rápida
  
## ¡Finalizado!

