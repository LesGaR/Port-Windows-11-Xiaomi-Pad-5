<img align="right" src="https://raw.githubusercontent.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/main/nabu.png" width="425" alt="Windows 11 Running On A Xiaomi Pad 5">


# Ejecutar Windows en el Xiaomi Pad 5

## Instalación



### Requisitos previos
-  ```Cerebro```
  
- [```Recovery Image```](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/1.0/recovery.img)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

### Notas:
> [!NOTE]
> ¿No sabes cómo empezar? Simplemente descomprima el archivo descargando [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools), por ejemplo ```"C:\platform-tools"``` luego abra ```command prompt``` o `powershell` como administrador y escriba:
```cmd
cd "path\to\platform-tools"
```
> Reemplace  `"path\to\platform-tools"` con la ruta real de la carpeta de herramientas de la plataforma.


> Si elimina alguna partición a través de diskpart más adelante o ahora, Windows enviará un comando ufs que se malinterpreta y borrará todos sus ufs.
> 
> ¡Todos tus datos serán borrados! Haga una copia de seguridad ahora si es necesario.
> 
> Estos comandos han sido probados.
> 
> NO REINICIES TU TABLETA si crees que cometiste un error, pide ayuda en el [Telegram chat](https://t.me/nabuwoa)
>
> **¡POR FAVOR, NO USE GUÍAS DE VIDEO DESACTUALIZADAS DE YOUTUBE O CUALQUIER OTRA PLATAFORMA! ¡ESTOS VIDEOS ESTÁN DESACTUALIZADOS Y PUEDES BLOQUEAR TU DISPOSITIVO SI LAS USAS! SI NECESITAS UNA VIDEOGUÍA, UTILIZA ESTA [NEW VIDEO GUIDE](https://youtu.be/BbgTbTGbXYg) DE [ArtoSeVeN](https://www.youtube.com/channel/UCYjwfxlYlJ7Nnzv01oszQvA)**


### Particionar su dispositivo y realizar una copia de seguridad del arranque

#### Recuperación de arranque a través de la PC con el comando
```cmd
fastboot boot <recovery.img>
```
#### Particionar su dispositivo

> Si te pide que lo ejecutes una vez más, hazlo.

> Esto es **opcional**, pero también puedes **establecer tamaños personalizados (de forma predeterminada, se divide el almacenamiento a la mitad)**

> Para establecer tamaños personalizados, haga ```adb shell partition [OBJETIVO WINDOWS ESPACIO EN GB]```

> Asegúrate de no agregar GB al final, solo el número

```cmd
adb shell partition
```

### Haga una copia de seguridad de su imagen de arranque existente
```cmd
adb shell "dd if=/dev/block/platform/soc/1d84000.ufshc/by-name/boot$(getprop ro.boot.slot_suffix) of=/tmp/normal_boot.img" && adb pull /tmp/normal_boot.img
```


#### Comprueba si Android todavía se inicia
> Reinicie para comprobar si Android todavía funciona. Si no arranca, borre todos los datos en recuperación y vuelva a intentarlo.

```cmd
adb reboot
```


### [Siguiente paso: obtener root](/guide/Spanish/2-rootguide-es.md)
