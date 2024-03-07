<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutar Windows en el Xiaomi Pad 5

## Obtener root
> [!NOTE]
> **Si ya tienes root, omite este paso y ve a la página siguiente.**

### Requisitos previos
- ```Cerebro```
  
- [```Android boot backup```](/guide/Spanish/1-partition-es.md#Haga-una-copia-de-seguridad-de-su-imagen-de-arranque-existente) (con la copia de seguridad que hizo en la primera página de la guía)


## Parchear boot

- Copie el archivo ```normal_boot.img``` de la carpeta ```platform tools``` a la tableta

- Descargue e instale la [aplicación Magisk ](https://github.com/topjohnwu/Magisk/releases/latest) en la tableta
  
- Abra la aplicación Magisk y haga clic en el botón  ```Instalar```. Seleccione la opción ```Seleccionar y Parchear Archivo``` y busque el archivo ```normal_boot.img``` que copió en la tableta. Haga clic en el botón ```Let's Go``` y espere a que se complete el proceso de parcheo.
  
- Copie el archivo ```magisk_patched....img``` de la carpeta ```Descargas``` de la tableta a la carpeta ```platform tools``` de su computadora.

- Reinicie a fastboot
  
- Abra el símbolo del sistema en la carpeta de herramientas de la plataforma

 ## Flashee el boot parcheado
 > Reemplace `<magisk_patched.img>` con el ```magisk_patched.img``` nombre/ruta real.
```cmd
fastboot flash boot <magisk_patched.img>
```

### [Siguiente paso: instalar Windows](/guide/Spanish/3-install-es.md)
