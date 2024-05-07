# PYNQ for Redpitaya-122-16 (SDR)

PYNQ build for Redpitaya-16-122 SDR. Supported MIO peripherals:
* SD 0
* UART 0
* ENET 0 (static MAC address, read from i2c EEPROM during boot)
* USB 0


## Ready-to-use downloads, links and base design

* [Pynq-Redpitaya-122-16-3.0.1.img]()
* [Instructions on writing the SD card image](https://pynq.readthedocs.io/en/v2.6.1/appendix.html#writing-the-sd-card-image)
* [Getting started with PYNQ](https://pynq.readthedocs.io/en/v3.0.0/getting_started.html)
* [Vivado Redpitaya-122-16 board files](https://github.com/dspsandbox/Pynq-Redpitaya-122/tree/master/Vivado/board_files)
* [Constraint file (.xdc)](https://github.com/RedPitaya/RedPitaya-FPGA/blob/master/sdc/red_pitaya_Z20.xdc)
* Base design (the corresponding overlay is included within the build image):

<img src="/Doc/base_bd.png"/>

* Controlling the base design from a PYNQ Jupyter Notebook:

```python
import time
import pynq
pynq.PL.reset()
ol = pynq.Overlay("base.bit")

for i in range(8):
    ol.axi_gpio_0.channel1.write(val=(1<<i), mask=0xff)
    time.sleep(0.5)
```

<img src="/Doc/running_led.gif" width="400"/>


## Build process 


ℹ️ The PYNQ build process is identical for Rediptaya-122-16 (SDR) and Redpitaya-125-14 (STEMlab). The latter one is described [here](https://github.com/dspsandbox/Pynq-Redpitaya-125).