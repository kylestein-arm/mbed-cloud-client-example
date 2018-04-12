Modified to run on ODIN WEM hardware and allow fota.

Follow the instruction linked below with the following additions:

1. When building mbed-cloud-client-example:

first deploy libraries
>mbed deploy --protocol ssh

patch the spif driver
>cd storage-selector/spif-driver
>git am < ../../0001-SPI-pins.patch
>cd ../..

then compile
>mbed compile --app-config configs/wifi_odin_v4.json


2. Before combining, we need to replace the bootloader

clone https://github.com/kylestein-arm/mbed-bootloader  and build it using the tiny profile

>mbed compile --profile tiny.json

replace tools/mbed-bootloader-ublox_evk_odin_w2-block_device-sotp-v3_3_0.bin  (in the mbed-cloud-client-example tree) with the resultant mbed-bootloader.bin

then run the combine script.





The full documentation for this example is [available on our documentation site](https://cloud.mbed.com/docs/current/connecting/mbed-cloud-client-tutorials.html)
