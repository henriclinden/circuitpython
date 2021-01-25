# PCTEL WSC-1450

For details about this board navigate to https://pctel.com for general information about PCTEL and https://www.pctel.com/products/industrial-iot-devices/wireless-sensors/ for information about IoT devices and sensors.

# Build instructions

## Get repo and update all submodules

    git clone https://github.com/henriclinden/circuitpython.git
    cd circuitpython
    git submodule update --init --recursive

## Build mpy tool

    make -C mpy-cross

## Build circuitpython for WSC-1450

    cd ports/nrf
    make BOARD=pctel_wsc_1450

## Program to target

TBD
