<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutando Windows en el Xiaomi Pad 5

## Reinstalación
Si no le gusta su versión de Windows o ha bloqueado su instalación de Windows, o cualquier otra cosa, probablemente simplemente reinstale Windows. Afortunadamente este proceso es muy sencillo.

> [!IMPORTANT]
> Obviamente, esto borrará todos sus archivos de Windows. Si desea hacer una copia de seguridad de alguno de ellos, puede hacerlo montando Windows usando la aplicación [WOA Helper](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk) y copiando manualmente cualquier archivo que desee conservar.


### Requisitos previos

- ```Windows preexistente y particiones de arranque``` (*Si no se cumple, [regrese y pretenda que esta guía nunca existió](/guide/Spanish/1-partition-es.md)*)

- [```Recovery Image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)


### Recuperación de arranque para formatear Windows y particiones de arranque

```cmd
fastboot boot <recovery.img>
```

### Formatear las particiones
> Si te pide que lo ejecutes una vez más, hazlo.
```cmd
adb shell format
```
## [Siguiente paso: reinstalar Windows](/guide/Spanish/3-install-es.md#Ejecute-msc)
