<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows en el Lg G8x">

# Windows en el Lg G8x

## Actualización de controladores

### Requisitos previos
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Controladores](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/Drivers)

- [Qfil](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/Qfil)

- [Imagen de arranque de almacenamiento masivo](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Files/LGG8XMassStorageBoot.img)

### Reiniciar al modo de descarga
- Mantén presionados los botones **volumen abajo** + **encendido**.
- Sigue presionando mientras muestra la advertencia de bootloader desbloqueado.
- Después de que la pantalla se oscurezca, suelta el botón **encendido** mientras continúas manteniendo presionado el botón **volumen arriba**.
- Mientras mantienes presionado el botón **volumen abajo**, presiona el botón **volumen arriba**.

#### Configuración del modo de almacenamiento masivo
```cmd
fastboot boot LGG8XMassStorageBoot.img
```

### Diskpart
```cmd
diskpart
```

#### Seleccionar el volumen de Windows del teléfono
> Usa `list volume` para encontrarlo, debería llamarse **WINMH2LM**
```diskpart
select volume <número>
```

#### Asignar la letra x
```diskpart
assign letter x
```

#### Salir de diskpart:
```diskpart
exit
```

### Instalación de Drivers
> Descomprime el archivo de controladores, luego abre el archivo **OfflineUpdater.cmd**

> Ingresa la letra de unidad de **WINMH2LM**, que debería ser X, luego presiona enter

#### Reinicia tu dispositivo
> Una vez que los controladores hayan terminado de instalarse

## ¡Terminado!









