<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows en el Lg G8x">

# Windows en el Lg G8x

## Dualbooting Android y Windows sin Problemas

### Requisitos Previos
- [Imagen UEFI](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/UEFI)
  
- [Aplicación WOA Helper](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Dualboot/woahelper.apk)
  
- [Instalador StA](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Dualboot/StA_Installer_mh2lm.exe) 

## Configurando la Aplicación de Dualboot
> Esta guía asume que tienes acceso root. Si no es así, por favor hazlo primero.

### Configuración - Android
> [!NOTA]
> Si no puedes mover archivos a la carpeta de Windows, significa que apagaste Windows en lugar de reiniciarlo. Para solucionar este problema, reinicia Windows y utiliza la opción de reinicio. Luego, al reiniciar, arranca en modo fastboot y utilízalo para volver a Android.

- Descarga e instala la aplicación WOA Helper, luego ábrela y otórgale acceso root.
- Descarga la imagen UEFI y colócala dentro de la carpeta llamada `UEFI` en tu almacenamiento interno. Si esta carpeta no existe, créala.
- Regresa a la aplicación WOA Helper y presiona el botón `Respaldo del inicio de Android`. Selecciona tanto las opciones `Windows` como `Android`.
- Presiona el botón `Montar Windows`, luego descarga y mueve StA_Installer_mh2lm.exe a la carpeta recién creada `Windows` en tu almacenamiento interno.
- Regresa a la aplicación WOA Helper y presiona `Arranque rápido a Windows`.

### Configuración - Windows
- Navega a `C:\StA_Installer_mh2lm.exe` y ejecútalo. Si no funciona, asegúrate de que cualquier software antivirus esté desactivado, ya que probablemente no permitirá que se ejecute la aplicación.

#### Arrancando a Android
  - Ejecuta el nuevo acceso directo en tu escritorio (también puedes anclarlo al menú de inicio / barra de tareas para facilitar el acceso)

#### Arrancando a Windows
  - Presiona `Arranque rápido a Windows` dentro de la aplicación, o utiliza el interruptor recién creado en tu panel de configuración rápida
  
## ¡Terminado!
