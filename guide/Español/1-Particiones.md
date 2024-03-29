<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows en el Lg G8x">

# Windows en el Lg G8x 

## Particionando tu dispositivo

### Requisitos previos
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Qfil](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/Qfil) (para hacer copias de seguridad de las particiones)
  
- [Script de Parted](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Files/parted)
  
- [TWRP o Orange Fox](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/Recoveries)

### Notas
> [!Warning]  
> 
> No ejecutes el mismo comando dos veces a menos que se especifique.
>  
> No ejecutes todos los comandos a la vez, ¡ejecútalos en orden!
>
> ¡PUEDES DAÑAR TU DISPOSITIVO CON LOS COMANDOS A CONTINUACIÓN SI LOS HACES MAL!
>
> ¡NO REINICIES TU TELÉFONO! Si crees que cometiste un error, pide ayuda en el [chat de Telegram](https://t.me/winong8x).

### Haciendo copias de seguridad de las particiones
> Si no haces esto y algo sale mal, estarás por tu cuenta

#### Arrancar en EDL
- Abre **Administrador de dispositivos** en tu PC
- Con el teléfono apagado, mantén presionado **bajar volumen** + **encendido**.
- Sigue manteniendo mientras muestra el aviso de bootloader desbloqueado.
- Después de que la pantalla se ponga oscura, suelta el botón de **encendido** mientras continúas manteniendo presionado el botón de **bajar volumen**.
- Mientras mantienes presionado el botón de **bajar volumen**, comienza a presionar rápidamente el botón de **subir volumen**.
- Continúa haciendo esto hasta que veas **QDLoader 9008** o **QUSB_BULK** en el Administrador de dispositivos en tu PC.
- Si el dispositivo tiene un triángulo de advertencia amarillo ⚠️, necesitas instalar los controladores de fastboot antes de poder continuar con el siguiente paso.

#### Reinciar al modo de descarga
- Mantén presionado **bajar volumen** + **encendido**.
- Sigue manteniendo mientras muestra el aviso de bootloader desbloqueado.
- Después de que la pantalla se ponga oscura, suelta el botón de **encendido** mientras continúas manteniendo presionado el botón de **subir volumen**.
- Mientras mantienes presionado el botón de **bajar volumen**, presiona el botón de **subir volumen**.

#### Configurar Qfil
- Abre **Qfil**.
- En "Seleccionar tipo de compilación", selecciona **compilación plana**.
- En "Seleccionar programador", selecciona el firehose descargado.
- En Configuración, asegúrate de que el "Tipo de dispositivo" esté configurado en **UFS**.

#### Haciendo copias de seguridad de tus particiones
- En **Qfil**, selecciona Herramientas > Administrador de particiones y haz clic en **Aceptar**.
- Haz clic derecho en **laf_a** > **Administrar datos de partición** y presiona **Leer datos**.
- Haz lo mismo para **laf_b**, **boot_a**, **boot_b**, **abl_a**, **abl_b**, **aop_a**, **aop_b**, **xbl_a**, **xbl_b**, **ftc**, **fsg**, **fsc**, **modemst1**, **modemst2**, **modem_a**, **modem_b**

> [!Nota]
> Esto hará copias de seguridad de tus particiones en `C:\usuarios\nombre\AppData\roaming\qualcomm\qfil\comportno\`. Puedes restaurarlas más tarde con la función **Cargar imagen**.

#### Borrando la partición `laf`
- En **Qfil**, selecciona Herramientas > Administrador de particiones y haz clic en **Aceptar**.
- Haz clic derecho en **laf_a** > **Administrar datos de partición** y presiona **Borrar**.
- Haz lo mismo para **laf_b**

#### Reiniciar tu teléfono
> Mantén presionado **encendido** para reiniciar de nuevo a Android

#### Flashear TWRP u Orange Fox
> Usa los archivos proporcionados y flashealos en Magisk, luego reinicia en modo de recuperación
>
> Si tienes Lineage recovery, también puedes usar eso en su lugar

#### Desmontar todas las particiones
Ve a montar en TWRP/Orange Fox y desmonta todas las particiones

#### Preparando para particionar
> Descarga el archivo parted y muévelo a la carpeta platform-tools, luego ejecuta
```cmd
adb push parted /cache/ && adb shell "chmod 755 /cache/parted" && adb shell /cache/parted /dev/block/sda
```

### Borrar la partición `grow` 
> Para asegurarte de que la partición 31 es grow puedes usar
>  `print all`
```sh
rm 31
```

### Redimensionar la partición `userdata` 
> Para asegurarte de que la partición 30 es Userdata puedes usar
>  `print all`
```sh
resizepart 30
```
> Reemplaza XX con la cantidad de almacenamiento que quieras para Userdata, el resto se usara en Windows
```sh
XXGB
```

### Crear particiones
> Si recibes cualquier advertencia que te diga ignorar o cancelar, solo escribe i y dale a enter enter

#### Para todos los modelos:
- Crea la partición ESP (Aqui estará el bootloader de Windows y los archivos EFI)
>Necesitamos que esta particion tenga 500MB, reemplaza XX con lo que diga "END" en Userdata
```sh
mkpart esp fat32 XXGB XX.5GB
```

- Creamos la partición principal donde instalaremos Windows
> Reemplazamos XX con lo que diga "END" en ESP
```sh
mkpart win ntfs XX.5GB 126GB
```

#### Hacer que ESP sea arrancable
> Use `print` para ver todas las particiones. Reemplace "$" con el número de partición ESP, que debería ser 31
```cmd
set $ esp on
```

### Salir de parted
```sh
quit
```

### Reiniciar a TWRP
- Formatea data
Ve a Wipe en TWRP y presiona Format Data, 
después escribe `yes`.

### Comprueba si android inicia
Solo reinicia el teléfono y comprueba si Android inicia

## [Siguiente paso: Instalar Windows](2-Instalacion.md)
