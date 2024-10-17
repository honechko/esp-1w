# WiFi 1-wire bus master

![WiFi 1-wire bus master](https://github.com/honechko/esp-1w/raw/main/esp-1w_3v3.jpg)

This firmware turns ESP8266 into a WiFi to 1-wire bus master converter
that is compatible with [ser1wm](https://github.com/honechko/ser1wm)
Linux driver.

## Flashing

    $ esptool.py -p /dev/ttyUSB0 -b 460800 write_flash \
     0x00000 firmware/0x00000_bootloader.bin \
     0x08000 firmware/0x08000_partitions.bin \
     0x10000 firmware/0x10000_ser1wm.bin

## Configuration

* To enter Setup Mode short IO0 & IO2 pins of ESP together (not to ground)
    on power-on

* In Setup Mode connect to WiFi access point `ser1wm_setup` and go to
    http://192.168.1.1/

## Usage

Attach driver to TCP-port on which network 1-wire bus master is listening:

    $ sudo ser1wm_attach 10.0.0.2:4232

