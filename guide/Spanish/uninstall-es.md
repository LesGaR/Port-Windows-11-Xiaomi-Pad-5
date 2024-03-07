<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">

# Ejecutando Windows en el Xiaomi Pad 5

## Desinstalación

### ¿Por qué es necesario esto?

Si desea desinstalar Windows, esto se utiliza en lugar de eliminar particiones manualmente para evitar errores humanos + escribir una guía completa dedicada simplemente a la desinstalación.

Si desea volver a bloquear su gestor de arranque, necesitará que su tabla de particiones esté de fábrica.

### Requisitos previos

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)
  
- [```Recovery Image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

#### Inicie la recuperación modificada
```cmd
fastboot boot <recovery.img>
```

#### Restaurar el diseño de la partición
> [!Warning]
> Esto borrará tus archivos de Android. Haga una copia de seguridad primero si es necesario..
```cmd
adb shell restore
```

### Reiniciar en Android
```cmd
adb reboot 
```
## ¡Hecho!
