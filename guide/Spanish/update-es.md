<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutando Windows en el Xiaomi Pad 5

## Actualización de controladores

### Requisitos previos


- [```UEFI image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-v3.img)

- [```Recovery image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```Drivers```](https://github.com/map220v/MiPad5-Drivers/releases/latest)

### Inicie la recuperación a través de la PC con el comando

```cmd
fastboot boot <recovery.img>
```


### Activar el modo de almacenamiento masivo
> Si te pide que lo ejecutes una vez más, hazlo.
```cmd
adb shell msc
```

### Asignar letras a los discos.

#### Inicie el administrador de discos de Windows

> Una vez que el Pad 5 se detecta como un disco

```cmd
diskpart
```


### Asignar `X` al volumen de Windows

#### Seleccione el volumen de Windows de la tableta.
> Use `list volume` para encontrarlo, es el que se llama "WINNABU".

```diskpart
select volume <number>
```

#### Asigne la letra X
```diskpart
assign letter x
```

### Salir de diskpart
```diskpart
exit
```


### Instalar controladores

> Puedes descargar los controladores [Aquí](https://github.com/map220v/MiPad5-Drivers/releases/latest)

> Si recibe el mensaje `"Automatic WINNABU detection failed! Enter Drive Letter manually"` escriba **`X`**
```cmd
 Abra la carpeta Drivers y ejecute OfflineUpdater.cmd
```

### Reinicie en fastboot para flashear UEFI
> O si su UEFI ya ha sido actualizado, simplemente reinicie con ```adb reboot```
```cmd
adb reboot bootloader
```

#### Arrancar con imagen UEFI de arranque de Windows
> Reemplace <uefi.img> con la ruta real de la imagen UEFI
```cmd
fastboot flash boot <uefi.img>
```

## ¡Finalizado!!









