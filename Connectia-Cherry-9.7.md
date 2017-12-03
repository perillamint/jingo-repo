# HW spec
* CPU: Intel Atom X5-Z8300
* RAM: 4GB DDR3
* eMMC: SK Hynix 64GB (HCG8e)
* WLAN: RTL8723BS SDIO
* Camera (front): TBD.
* Camera (back): TBD.
* PMIC: TBD.
* Accelerometer: TBD.

# eMMC partition
* 1: 0700 android_bootloader2 NTFS partition - Windows bootloader log?
* 2: EF00 android_bootloader Android EFI loader. Firmware loads loader.efi
* 3: FFFF android_boot
* 4: FFFF android_recovery
* 5: FFFF android_misc
* 6: FFFF android_metadata
* 7: 8300 android_system
* 8: 8300 android_cache
* 9: 8300 android_data
* 10: 8300 android_persistent
* 11: 8300 android_config
* 12: EF00 MS Windows EFI loader.
* 13: 0C01 MS reserved
* 14: 0700 MS Basic data - C:\
* 15: 2700 MS basic data - Recovery

It seems partition number does not affect FW to find Windows EFI loader.

# Wireless (WiFi, BT)
RTL8723BS module WiFi works with external driver(https://github.com/hadess/rtl8723bs/) without modification. Although lots of packet loss (almost 60%) observed, it works.

BT works with external userland driver (https://github.com/lwfinger/rtl8723bs_bt/). BT uses /dev/ttyS0 UART device.

RtlUart.sys has Realtech firmware blob in its .data section. Extract it and use it.

# Battery

Connectia Cherry 9.7 uses non-std ACPI calls for battery -- little bit of abstraction done, but it seems not abstract a lot -- "almost" bare PMIC.

INT33FE device driver code from Asus ZenFone 2 kernel might be help to write driver stuff: https://github.com/TheSSJ/android_kernel_asus_moorefield/blob/350f074f508463993a7cba1bb6014a5af8c32de4/drivers/external_drivers/drivers/mfd/intel_pmic/pmic_i2c.c

TODO: Possible "Galaxy Pad" scenario?

# Power, volume up/down button

It seems buttons are handled by soc_button_driver (/drivers/input/misc). However, if tablet woken up using power button, it sleeps immediatly. It seems wakeup power button press delivered into GNOME and recognized as suspend signal.

TODO: Poke ACPI with https://github.com/mkottman/acpi_call/

# GPL violation issue
Sungwoo Mobile **refused to comply GPL** like any other Korean HomeWRT corps and Chinese tablet manufacturers.

When I asked them to provide Android kernel source code, they **refused** to provide it. Yet another GPL violation case.