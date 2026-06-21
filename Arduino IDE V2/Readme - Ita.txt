Questa operazione serve principalmente per il bootloader da SD.
Per caricare il programma da USB potete semplicemente usare Arduino Zero Native USB Port.

Copiare i file forniti nelle relative cartelle:
boards.txt in
C:\Users\(UTENTE)\AppData\Local\Arduino15\packages\arduino\hardware\samd\1.8.14\
flash_with_SDbootloader.ld  in
C:\Users\(UTENTE)\AppData\Local\Arduino15\packages\arduino\hardware\samd\1.8.14\variants\arduino_zero\linker_scripts\gcc
Puoi trovare il percorso corretto facendo, da dentro all IDE arduino "File/Settings/Show verbose during building"   Compilando il progetto si vede l'indirizzo dove è installato il compilatore.

Troverete in "Tools - Board" tre nuove schede:
GEVINO SD bootloader
GEVINO SAM-BA bootloader
GEVINO no bootloader
Il primo compila lo schetch dall'indirizzo 0x8000, il secondo dall'indirizzo 0x2000, il terzo da 0x0000

USO da SD
Impostare GEVINO SD bootloader
Compilare facendo, "Sketch/Export Compiled Binary"  "Sketch/Esporta Sketch compilato"
Rinominare il file presente nella cartella dello scheck in firmware.bin e copiarlo nella SD formattata FAT32
All'accensione, se il GEVINO trova il files, lampeggia il led giallo, poi fa due lenti lampeggi e lancia la app.
Dopo di che cancellare il file o rimuovere la SD, altrimenti ogni accensione si ripropgramma la flash.


----------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------
If this file board.txt is not compatible with new version of Compiler, add to existing file this:
----------------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------------

# GEVINO_SAM-BA_boot
# --------------------------------------
GEVINO_SAM-BA_boot.name=GEVINO SAMBA USB Boot
GEVINO_SAM-BA_boot.vid.0=0x2341
GEVINO_SAM-BA_boot.pid.0=0x804d
GEVINO_SAM-BA_boot.vid.1=0x2341
GEVINO_SAM-BA_boot.pid.1=0x004d
GEVINO_SAM-BA_boot.vid.2=0x2341
GEVINO_SAM-BA_boot.pid.2=0x824d
GEVINO_SAM-BA_boot.vid.3=0x2341
GEVINO_SAM-BA_boot.pid.3=0x024d
GEVINO_SAM-BA_boot.upload_port.0.vid=0x2341
GEVINO_SAM-BA_boot.upload_port.0.pid=0x804d
GEVINO_SAM-BA_boot.upload_port.1.vid=0x2341
GEVINO_SAM-BA_boot.upload_port.1.pid=0x004d
GEVINO_SAM-BA_boot.upload_port.2.vid=0x2341
GEVINO_SAM-BA_boot.upload_port.2.pid=0x824d
GEVINO_SAM-BA_boot.upload_port.3.vid=0x2341
GEVINO_SAM-BA_boot.upload_port.3.pid=0x024d
GEVINO_SAM-BA_boot.upload_port.4.board=GEVINO_SAM-BA_boot
GEVINO_SAM-BA_boot.upload.tool=bossac
GEVINO_SAM-BA_boot.upload.tool.default=bossac
GEVINO_SAM-BA_boot.upload.tool.network=arduino_ota
GEVINO_SAM-BA_boot.upload.protocol=sam-ba
GEVINO_SAM-BA_boot.upload.maximum_size=262144
GEVINO_SAM-BA_boot.upload.maximum_data_size=32768
GEVINO_SAM-BA_boot.upload.use_1200bps_touch=true
GEVINO_SAM-BA_boot.upload.wait_for_upload_port=true
GEVINO_SAM-BA_boot.upload.native_usb=true
GEVINO_SAM-BA_boot.build.mcu=cortex-m0plus
GEVINO_SAM-BA_boot.build.f_cpu=48000000L
GEVINO_SAM-BA_boot.build.usb_product="GEVINO"
GEVINO_SAM-BA_boot.build.usb_manufacturer="GEVA elettronica"
GEVINO_SAM-BA_boot.build.board=GEVINO
GEVINO_SAM-BA_boot.build.core=arduino
GEVINO_SAM-BA_boot.build.extra_flags=-D__SAMD21G18A__ {build.usb_flags}
GEVINO_SAM-BA_boot.build.ldscript=linker_scripts/gcc/flash_with_bootloader.ld
GEVINO_SAM-BA_boot.build.openocdscript=openocd_scripts/arduino_zero.cfg
GEVINO_SAM-BA_boot.build.variant=arduino_zero
GEVINO_SAM-BA_boot.build.variant_system_lib=
GEVINO_SAM-BA_boot.build.vid=0x2341
GEVINO_SAM-BA_boot.build.pid=0x804d
GEVINO_SAM-BA_boot.bootloader.tool=openocd
GEVINO_SAM-BA_boot.bootloader.tool.default=openocd
GEVINO_SAM-BA_boot.bootloader.file=zero/samd21_sam_ba.bin

# GEVINO_SD_boot
# --------------------------------------
GEVINO_SD_boot.name=GEVINO SD Boot
GEVINO_SD_boot.vid.0=0x2341
GEVINO_SD_boot.pid.0=0x804d
GEVINO_SD_boot.vid.1=0x2341
GEVINO_SD_boot.pid.1=0x004d
GEVINO_SD_boot.vid.2=0x2341
GEVINO_SD_boot.pid.2=0x824d
GEVINO_SD_boot.vid.3=0x2341
GEVINO_SD_boot.pid.3=0x024d
GEVINO_SD_boot.upload_port.0.vid=0x2341
GEVINO_SD_boot.upload_port.0.pid=0x804d
GEVINO_SD_boot.upload_port.1.vid=0x2341
GEVINO_SD_boot.upload_port.1.pid=0x004d
GEVINO_SD_boot.upload_port.2.vid=0x2341
GEVINO_SD_boot.upload_port.2.pid=0x824d
GEVINO_SD_boot.upload_port.3.vid=0x2341
GEVINO_SD_boot.upload_port.3.pid=0x024d
GEVINO_SD_boot.upload_port.4.board=GEVINO_SD_boot

GEVINO_SD_boot.upload.tool=bossac
GEVINO_SD_boot.upload.tool.default=bossac
GEVINO_SD_boot.upload.tool.network=arduino_ota
GEVINO_SD_boot.upload.protocol=sam-ba
GEVINO_SD_boot.upload.maximum_size=262144
GEVINO_SD_boot.upload.maximum_data_size=32768
GEVINO_SD_boot.upload.use_1200bps_touch=true
GEVINO_SD_boot.upload.wait_for_upload_port=true
GEVINO_SD_boot.upload.native_usb=true
GEVINO_SD_boot.build.mcu=cortex-m0plus
GEVINO_SD_boot.build.f_cpu=48000000L
GEVINO_SD_boot.build.usb_product="GEVINO"
GEVINO_SD_boot.build.usb_manufacturer="GEVA elettronica"
GEVINO_SD_boot.build.board=GEVINO
GEVINO_SD_boot.build.core=arduino
GEVINO_SD_boot.build.extra_flags=-D__SAMD21G18A__ {build.usb_flags}
GEVINO_SD_boot.build.ldscript=linker_scripts/gcc/flash_with_SDbootloader.ld
GEVINO_SD_boot.build.openocdscript=openocd_scripts/arduino_zero.cfg
GEVINO_SD_boot.build.variant=arduino_zero
GEVINO_SD_boot.build.variant_system_lib=
GEVINO_SD_boot.build.vid=0x2341
GEVINO_SD_boot.build.pid=0x804d
GEVINO_SD_boot.bootloader.tool=openocd
GEVINO_SD_boot.bootloader.tool.default=openocd
GEVINO_SD_boot.bootloader.file=zero/samd21_sam_ba.bin


# GEVINO_NO_boot
# --------------------------------------
GEVINO_NO_boot.name=GEVINO NO Boot
GEVINO_NO_boot.vid.0=0x2341
GEVINO_NO_boot.pid.0=0x804d
GEVINO_NO_boot.vid.1=0x2341
GEVINO_NO_boot.pid.1=0x004d
GEVINO_NO_boot.vid.2=0x2341
GEVINO_NO_boot.pid.2=0x824d
GEVINO_NO_boot.vid.3=0x2341
GEVINO_NO_boot.pid.3=0x024d
GEVINO_NO_boot.upload_port.0.vid=0x2341
GEVINO_NO_boot.upload_port.0.pid=0x804d
GEVINO_NO_boot.upload_port.1.vid=0x2341
GEVINO_NO_boot.upload_port.1.pid=0x004d
GEVINO_NO_boot.upload_port.2.vid=0x2341
GEVINO_NO_boot.upload_port.2.pid=0x824d
GEVINO_NO_boot.upload_port.3.vid=0x2341
GEVINO_NO_boot.upload_port.3.pid=0x024d
GEVINO_NO_boot.upload_port.4.board=GEVINO_NO_boot

GEVINO_NO_boot.upload.tool=bossac
GEVINO_NO_boot.upload.tool.default=bossac
GEVINO_NO_boot.upload.tool.network=arduino_ota
GEVINO_NO_boot.upload.protocol=sam-ba
GEVINO_NO_boot.upload.maximum_size=262144
GEVINO_NO_boot.upload.maximum_data_size=32768
GEVINO_NO_boot.upload.use_1200bps_touch=true
GEVINO_NO_boot.upload.wait_for_upload_port=true
GEVINO_NO_boot.upload.native_usb=true
GEVINO_NO_boot.build.mcu=cortex-m0plus
GEVINO_NO_boot.build.f_cpu=48000000L
GEVINO_NO_boot.build.usb_product="GEVINO"
GEVINO_NO_boot.build.usb_manufacturer="GEVA elettronica"
GEVINO_NO_boot.build.board=GEVINO
GEVINO_NO_boot.build.core=arduino
GEVINO_NO_boot.build.extra_flags=-D__SAMD21G18A__ {build.usb_flags}
GEVINO_NO_boot.build.ldscript=linker_scripts/gcc/flash_without_bootloader.ld
GEVINO_NO_boot.build.openocdscript=openocd_scripts/arduino_zero.cfg
GEVINO_NO_boot.build.variant=arduino_zero
GEVINO_NO_boot.build.variant_system_lib=
GEVINO_NO_boot.build.vid=0x2341
GEVINO_NO_boot.build.pid=0x804d
GEVINO_NO_boot.bootloader.tool=openocd
GEVINO_NO_boot.bootloader.tool.default=openocd
GEVINO_NO_boot.bootloader.file=zero/samd21_sam_ba.bin