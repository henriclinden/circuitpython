# PCTEL WSC-1450

For details about this board navigate to https://pctel.com for general information about PCTEL and https://www.pctel.com/products/industrial-iot-devices/wireless-sensors/ for information about IoT devices and sensors.

# Build instructions

## Get repo and update all submodules

    git clone https://github.com/henriclinden/circuitpython.git
    cd circuitpython
    git submodule update --init --recursive

## Build mpy tool

    make -C mpy-cross

## Build CircuitPython for PCTEL WSC-1450

    cd ports/nrf
    make BOARD=pctel_wsc_1450

## Installing a bootloader / SoftDevice

While most Adafruit devices come with an Adafruit-provided bootloader (supporting niceties like UF2 flashing), the PCTEL WSC-1450 board comes with DAPLink which handles everything from debugging to programming the device, as well as the boot sequence. 

What's particularly awesome about this board is that there is no physical interaction with the board required to flash new code - the device is _always_ listening for new firmware uploads even if userspace code like CircuitPython is running.

1. Connect the WSC-1450 dev kit unsing a USB cable to the `DHD USB` port. This will power up the board and open a file browser showing the contents of the target. (DAPlink magic)
2. Drag the 6.1.0 version of nRF SoftDevice to the DAPlink directory. The SoftDevice binary is found in `circuitpython/ports/nrf/bluetooth/s140_nrf52_6.1.0/s140_nrf52_6.1.0_softdevice.hex` 
3. Wait for the file to upload.
4. Bootload install complete.

## Installing CircuitPython

Use the same DAPlink directory to upload the circuitpython binary. Procedure as above. The file to upload is `circuitpython/ports/nrf/build-pctel_wsc_1450/firmware.hex`

# Running

Connect an additional USB cable to the `Target USB` port on the development board and open a terminal like `screen` on Mac or `TeraTerm` on Windows. Or use the MU development IDE.

Happy hacking.

