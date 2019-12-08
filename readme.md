# GBFlasher-Firmware

Custom version of [Tauwasser](https://github.com/Tauwasser/GBCartFlasher)'s cart flasher firmware with added support for 4MB MBC30 

Requires [GBFlasher-Software](https://github.com/MrHDR/GBFlasher-Software) if you want to flash 4MB MBC30 carts

**Flashing the bootloader:**

Raspberry Pi:

```
sudo avrdude -p atmega8515 -C ~/avrdude_gpio.conf -c pi_1 -U lfuse:w:0x1f:m -U hfuse:w:0xda:m -B 6
sudo avrdude -p atmega8515 -C ~/avrdude_gpio.conf -c pi_1 -U flash:w:GBFlasher-Bootloader.hex -B 6
```

USBISP:

```
avrdude -c USBasp -p atmega8515 -U lfuse:w:0x1f:m -U hfuse:w:0xda:m -B 6
avrdude -c USBasp -p atmega8515 -U flash:w:GBFlasher-Bootloader.hex -B 6
```


**Flashing the firmware:**

- Download and extract [tsbloader_adv](https://github.com/seedrobotics/tinysafeboot/raw/master/software/tsbloader_advanced/binaries/tsbloader_adv_1.0.8.zip)

- Download the [firmware](https://github.com/HDR/GBFlasher-Firmware/releases/latest/download/GBFlasher-Firmware.hex) and put it in the folder with the files you just extracted

- Open command line and flash the firmware by writing "tsbloader_adv -port=com# -fop=wv -ffile=GBFlasher-Firmware.hex" (Replace # with whatever com port number the flasher shows up as in Device Manager)
