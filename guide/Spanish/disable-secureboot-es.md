<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutando Windows en el Xiaomi Pad 5

## Deshabilitar el arranque seguro
> [!Important]
> Siga esta guía sólo si desea desactivar el arranque seguro.

### Requisitos previos
- ```Cerebro```

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

- [```Recovery Image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```UEFI image (Secureboot off)```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/UEFI/uefi-NoSecureboot-v3.img)

## Pros y contras del arranque seguro
> De forma predeterminada, el arranque seguro está habilitado en esta guía.

##### Pros y contras del arranque seguro
- √ Sin marca de agua en la pantalla de inicio
- √ Las aplicaciones que no funcionan con el modo de prueba funcionarán
- √ Puede actualizar versiones mayores (por ejemplo, 22h2 a 23h2) directamente en la actualización de Windows
- × No puedes actualizar los controladores sin una PC

##### Pros y contras del arranque seguro deshabilitado
- √ Puede actualizar los controladores directamente desde su tableta; no se necesita PC
- × Marca de agua del modo de prueba en la pantalla de inicio
- × Es posible que algunas aplicaciones/juegos con software antitrampas no funcionen
- × No puede actualizar versiones mayores (por ejemplo, 22h2 a 23h2) a través de Windows Update

## Deshabilitar el arranque seguro

#### Haga una copia de seguridad de su imagen de arranque rooteada
> Necesitará esto para regresar a Android, pero puede omitir este paso si ya realizó una copia de seguridad.

Utilice la opción `Backup Android boot` en la aplicación WOA Helper, o inicie la recuperación modificada y ejecute
```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/rooted_boot.img" && adb pull /tmp/rooted_boot.img
```

#### Arrancar en modo recuperación
> Reemplace <ruta\a\recuperación> con la ruta real de la imagen de recuperación
```cmd
fastboot boot <path\to\recovery.img>
```

#### Activar el modo de almacenamiento masivo
> Una vez que el Xiaomi Pad 5 se haya iniciado en la recuperación modificada
```cmd
adb shell msc
```

#### Inicie el administrador de discos de Windows
> Una vez detectada la Xiaomi Pad 5 como disco
```cmd
diskpart
```

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

#### Modificar los archivos del gestor de arranque
> Para habilitar la firma de prueba
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Eliminando SiPolicy
> Suponiendo que está deshabilitando el arranque seguro en una instalación existente, debe eliminar este archivo o el sistema no arrancará.
```cmd
del Y:\EFI\Microsoft\Boot\SiPolicy.p7b
```

#### Eliminar la letra de unidad de ESPNABU
> Si esto no funciona, ignórelo y pase al siguiente comando. Esta unidad fantasma desaparecerá la próxima vez que reinicies tu PC.
```cmd
mountvol y: /d
```

#### Reiniciar modo fastboot
```cmd
adb reboot bootloader
```

#### Flasheando la UEFI
> Asegúrese de utilizar UEFI sin arranque seguro desde esta página, reemplace <path\to\uefi-NoSecureboot-v3.img> con la ruta real a la imagen UEFI
```cmd
fastboot flash boot <path\to\uefi-NoSecureboot-v3.img>
```

> [!Important]
> Asegúrese también de reemplazar su antiguo UEFI en la carpeta UEFI en su almacenamiento interno de Android, para no actualizarlo accidentalmente la próxima vez que intente cambiar a Windows desde Android.

#### Reiniciar en Windows
```cmd
fastboot reboot
```

## ¡Finalizado!



















