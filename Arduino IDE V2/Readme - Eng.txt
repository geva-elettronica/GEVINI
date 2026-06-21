This is primarily for the SD bootloader.
To load the program from USB you can simply use Arduino Zero Native USB Port.

Copy the files provided in the relevant folders:
boards.txt in
C:\Users\(UTENTE)\AppData\Local\Arduino15\packages\arduino\hardware\samd\1.8.14\
flash_with_SDbootloader.ld  in
C:\Users\(UTENTE)\AppData\Local\Arduino15\packages\arduino\hardware\samd\1.8.14\variants\arduino_zero\linker_scripts\gcc
You can find the correct path by doing, from inside the arduino IDE 'File/Settings/Show verbose during building' Compiling the project you see the address where the compiler is installed.

You will find three new tabs in "Tools - Board":
GEVINO SD bootloader
GEVINO SAM-BA bootloader
GEVINO no bootloader
The first compiles the schetch from the address 0x8000, the second from the address 0x2000, the third from 0x0000

SD usage:
Select GEVINO SD bootloader
Compile doing, "Sketch / Export Compiled Binary"
Rename the file in the scheck folder to firmware.bin and copy it to the FAT32 formatted SD card
At power up, if the GEVINO finds the files, the yellow LED flashes, then makes two lenses flash and launches the app.
After that delete the file or remove the SD, otherwise each power-up will re-flash the flash.


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