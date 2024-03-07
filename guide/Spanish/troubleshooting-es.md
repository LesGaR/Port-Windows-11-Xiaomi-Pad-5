<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutando Windows en el Xiaomi Pad 5

## Solución de problemas

## La carga en Windows no funciona
> [!WARNING]
> No utilice un concentrador USB con alimentación con el modo host habilitado, ya que esto puede dañar su dispositivo. Si utiliza un concentrador USB con alimentación, utilice la [guía para desactivar el modo de host USB](/guide/Spanish/Additional-materials-es.md#Desactivar-el-modo-de-host-USB)

La carga en Windows solo funciona con cables específicos. Los cables que se sabe que funcionan son el cable original Poco X3 Pro (identificado por el pin naranja/rojo adicional en el puerto USB-A) y el cable de carga rápida Nimaso de 100 W USB-C a USB-C.


## El dispositivo puede iniciarse en Android pero no en el gestor de arranque

### Requisitos previos:

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

> [!WARNING]
 Probablemente estos pasos no te ayuden porque Xiaomi Pad 5 no tiene una recuperación personalizada completamente funcional para actualizarla en el dispositivo. Además, como la mayoría de los dispositivos A/B más nuevos, no tenemos un zip del instalador TWRP, etc. y no puede iniciar la imagen de recuperación existente debido a un fastboot roto. Si ya instaló la rom AOSP, probablemente tenga una recuperación AOSP preinstalada y pueda iniciarla directamente, por lo que puede seguir estos pasos. Si has desrooteado MIUI, estos pasos no te ayudarán.
>
> Por lo tanto, evite utilizar etiquetas de disco que contengan espacios y caracteres especiales y, si es posible, utilice etiquetas de ESPNABU y WINNABU que se prueban un millón de veces. Si bloquea el fastboot con etiquetas de disco y tiene MIUI desrooteado, debe flashear la ROM a través de EDL con una cuenta autorizada y debe pagar por ello.


Esto se debe a particiones con nombres de volúmenes que el gestor de arranque no puede manejar. Para solucionarlo:

- Arranque en modo recovery

- Conecte tableta al PC

- Abrir cmd en la PC

- Ejecute ```adb shell```

- Ejecute ```parted```

- Ejecute ```print``` to list all partitions

- Busque particiones que tengan espacios en los nombres, por ejemplo, "Partición de datos básicos" y anote su número de volumen.

- Ahora ejecute, ```rm <vol number>``` por ejemplo ```rm 99```


## fsa4480.sys BSOD en el arranque

- Abrir carpeta de drivers

- Quitar la carpeta ```components\QC8150\Device\DEVICE.SOC_QC8150.NABU\Drivers\USB```

- Reinstale el controlador

- Arrancar UEFI

- Después de que arranque, lea el controlador y reinstálelo nuevamente.


## Bootloop después de cambiar a Android

- Ejecute fastboot

- ```fastboot set_active other```

- ```fastboot flash boot <boot.img>```

- ```fastboot reboot```
