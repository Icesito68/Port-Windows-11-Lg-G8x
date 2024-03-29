<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows en el Lg G8x">

# Windows en el Lg G8x

## Instalando Windows

### Requisitos previos
- [Windows para ARM](https://worproject.com/esd)
  
- [Drivers](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/Drivers)

- [Mass storage boot image](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Files/LGG8XMassStorageBoot.img)

### Reiniciar al modo de descarga
- Mantén presionado **bajar volumen** + **encendido**.
- Sigue manteniendo mientras muestra el aviso de bootloader desbloqueado.
- Después de que la pantalla se ponga oscura, suelta el botón de **encendido** mientras continúas manteniendo presionado el botón de **subir volumen**.
- Mientras mantienes presionado el botón de **bajar volumen**, presiona el botón de **subir volumen**.

#### Configurar el modo de almacenamiento masivo
```cmd
fastboot boot LGG8XMassStorageBoot.img
```

### Diskpart
> [!WARNING]
> ¡NO BORRES NINGUNA PARTICIÓN MIENTRAS ESTÉS EN DISKPART! ¡ESTO BORRARÁ TODO TU UFS! ¡ESTO SIGNIFICA QUE TU DISPOSITIVO QUEDARÁ INUTILIZABLE DE FORMA PERMANENTE SIN SOLUCIÓN!

```cmd
diskpart
```

#### Encontrar tu teléfono
> Esto muestra todos los discos conectados
```cmd
lis dis
```

#### Selecting your phone
> Replace $ with the actual number of your phone (its size should be around 128GB)
```cmd
sel dis $
```

#### Listing your phone's partitions
> Esto muestra todas las particiones de los dispositivos
```cmd
lis par
```

#### Seleccionar la partición de Windows
> Reemplace $ con el número de partición de Windows (debería ser 32)
```cmd
sel par $
```

#### Formatear la unidad de Windows
```cmd
format quick fs=ntfs label="WINMH2LM"
```

#### Asignar letra a Windows
```cmd
assign letter x
```

#### Seleccionar la partición ESP
> Replace $ with the partition number of ESP (should be 31)
```cmd
sel par $
```

#### Formatear la unidad ESP
```cmd
format quick fs=fat32 label="ESPMH2LM"
```

#### Asignar letra a ESP
```cmd
assign letter y
```

#### Salir de diskpart
```cmd
exit
```

### Instalar Windows
> Reemplace `<ruta\al\install.esd>` con la ruta real de install.esd (también puede llamarse install.wim)

dism /apply-image /ImageFile:<ruta\al\install.esd> /index:6 /ApplyDir:X:\

> Si recibe `Error 87`, verifique el índice de su imagen con `dism /get-imageinfo /ImageFile:<ruta\al\install.esd>`, luego reemplace `index:6` con el número de índice real de Windows 11 Pro en su imagen

### Instalar controladores
> Desempaque el archivo de controladores, luego abra el archivo `OfflineUpdater.cmd`

> Ingrese la letra de unidad de `WINMH2LM`, que debería ser X, luego presione enter

#### Crear los archivos de arranque de Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Habilitar la firma de prueba
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

#### Deshabilitar la recuperación
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" recoveryenabled no
```

#### Deshabilitar las comprobaciones de integridad
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" nointegritychecks on
```

#### Reiniciar de nuevo a Android
Simply reboot your device

## [Último paso: configuremos el arranque dual](dualboot.md)
