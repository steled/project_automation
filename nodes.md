# master & worker node

## Preparing the master & worker nodes - detailed
### Update RPi 4 firmware, kernel and packages
Source: [Raspberry Pi 4 boot EEPROM](https://www.raspberrypi.org/documentation/hardware/raspberrypi/booteeprom.md)

- update system's package list
```bash
sudo apt update
```

- upgrade all installed packages to their latest versions
```bash
sudo apt full-upgrade -y
```

- select the stable bootloader release series
```bash
sudo sh -c 'echo FIRMWARE_RELEASE_STATUS=\"stable\" > /etc/default/rpi-eeprom-update'
```

- install current stable bootloader
```bash
sudo rpi-eeprom-update -a
```

- reboot
```bash
sudo reboot
```

### Enable network boot
Source: [Pi4 Bootloader Configuration](https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2711_bootloader_config.md)

- extract configuration file
```bash
sudo cp /lib/firmware/raspberrypi/bootloader/stable/pieeprom-*-*-*.bin pieeprom.bin
sudo rpi-eeprom-config pieeprom.bin > bootconf.txt
```

- change BOOT_ORDER to be 0x21 instead of 0x1
```bash
sed -i s/0x1/0x12/g bootconf.txt
```

- apply the configuration change to the EEPROM image file
```bash
sudo rpi-eeprom-config --out pieeprom-netboot.bin --config bootconf.txt pieeprom.bin
```

- install the new EEPROM image and reboot
```bash
sudo rpi-eeprom-update -d -f ./pieeprom-netboot.bin
sudo reboot
```