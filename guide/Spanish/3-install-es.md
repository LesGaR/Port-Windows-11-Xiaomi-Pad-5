<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutar Windows en el Xiaomi Pad 5
> [!Warning]
> **¡¡¡POR FAVOR, NO USE NINGUNA GUÍA DE VIDEO, YA QUE ESTÁN GENERALMENTE DESACTUALIZADAS Y PUEDEN Y PROBABLEMENTE BLOQUEARÁN SU NABU AL USARLAS!!! SI NECESITAS UNA GUÍA EN VIDEO, UTILIZA ESTA [VIDEO GUIDE](https://youtu.be/BbgTbTGbXYg) POR [ArtoSeVeN](https://www.youtube.com/channel/UCYjwfxlYlJ7Nnzv01oszQvA)**

## Instalación
> [!NOTE]
> Se recomienda abrir CMD o PowerShell como administrador ahora y luego acceder a la carpeta de herramientas de la plataforma usando el comando `cd C:\path\to\platform-tools`, rreemplazando la ruta con la ruta real de la carpeta.
> Utilice la misma ventana en toda la guía, no la cierre.

### Requisitos previos
- ```Cerebro```

- [```Imagen UEFI```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)
  
- [```ARM Windows esd```](https://worproject.com/esd) (Seleccione - Versión: ```11``` Build:  ```22631.2861``` Arquitectura:  ```ARM64``` Edición:  ```CLIENT``` Idioma ```selecione su idioma```)
    
- [```Drivers```](https://github.com/map220v/MiPad5-Drivers/releases/latest)

### Vuelva a iniciar la recuperación para comenzar a instalar Windows

```cmd
fastboot boot <recovery.img>
```

#### Ejecute msc

> Si te pide que lo ejecutes una vez más, hazlo.

```cmd
adb shell msc
```
### Asignar letras a los discos.
  

#### Inicie el administrador de discos de Windows

> Una vez detectada la Xiaomi Pad 5 como disco

```cmd
diskpart
```


#### Asignar `X` al volumen de Windows

#### Seleccione el volumen de Windows de la tableta.
> Use `list volume` para encontrarlo, es el que se llama "WINNABU".

```diskpart
select volume <number>
```

#### Asigne la letra X
```diskpart
assign letter x
```

### Asignar `Y` al volumen ESP

#### Seleccione el volumen esp de la tableta.
> Use `list volume` para encontrarlo, es el que se llama "ESPNABU"

```diskpart
select volume <number>
```

#### Asigne la letra Y

```diskpart
assign letter y
```

#### Salir de diskpart
```diskpart
exit
```

  
  

### Instalar

> Reemplace `<path\to\install.esd>` con la ruta real de install.esd (también puede llamarse install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> Si obtiene  `Error 87`, verifique el índice de su imagen `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, y luego reemplace `index:6` con el número de índice real de Windows 11 Pro en su imagen.


### Instalar controladores

> Puede descargar los controladores [Aquí](https://github.com/map220v/MiPad5-Drivers/releases/latest)

> Si dijese `"Automatic WINNABU detection failed! Enter Drive Letter manually"` escriba **`X`**

```cmd
 Open the folder with Drivers and run OfflineUpdater.cmd
```

### Cree archivos del gestor de arranque de Windows para EFI
> Si ocurre un error al copiar archivos de arranque, verifique con `diskpart` si ESPNABU todavía tiene la letra Y. Si no es así, agregue cualquier otra letra (como K) y reemplace la Y en el siguiente comando con dicha letra respectivamente.
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

## Eliminar la letra de unidad de ESPNABU
> Si esto no funciona, ignórelo y pase al siguiente comando. Esta unidad fantasma desaparecerá la próxima vez que reinicies tu PC.
```cmd
mountvol y: /d
```


## Arrancar en Windows

### Haga una copia de seguridad de su imagen de arranque rooteada

```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/rooted_boot.img" && adb pull /tmp/rooted_boot.img
```

### Reinicie al gestor de arranque

```cmd
adb reboot bootloader
```

### Descargue y actualice la imagen UEFI
> Descargue la [Imagen UEFI](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)

```cmd
fastboot flash boot <path to image>
```

## Reiniciar en Windows
```cmd
fastboot reboot
```

> [!NOTE]
> En el primer inicio de Windows, no verá ninguna red Wi-Fi. Reinicie su tableta manteniendo presionado el botón de encendido hasta que se reinicie. Después del reinicio, se solucionará. Si aparece una ventana emergente que dice "No se pudo conectar", presione Reintentar hasta que funcione (generalmente 5 veces).

### Reiniciar en Android
Después de configurar Windows, presione el botón de reinicio en Windows (NO APAGADO), luego, cuando se reinicie, mantenga presionado `volume down` + `power`para reiniciar de nuevo al modo fastboot.
> Utilice su imagen de arranque de respaldo y actualícela en fastboot para regresar a Android

```cmd
fastboot flash boot rooted_boot.img
```

```cmd
fastboot reboot
```

### [Último paso: configurar el arranque dual](dualboot-es.md)
