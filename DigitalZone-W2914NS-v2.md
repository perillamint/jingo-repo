## Device info
* Model name: W2914NS v2
* Vendor DigitalZone

## Chips
* SoC
  * MT7621AT
* DRAM
  * K4B2G1646Q-BCK0
  * DDR3 SDRAM
  * 2Gb (256MB)
* SPI flash
  * MX25L12835F
    * mx25l12805d and mx25l12835f have the same JEDEC ID
  * 128Mb (16MB)
* Wireless
  * MT7612
    * PCI bus No. (TBD)
    * With LNA
  * MT7603
    * PCI bus No. (TBD)
    * Without LNA

## Features
* Power
  * 12V 1.5A barral jack
* Buttons
  * WPA
  * Reset
* Network ifaces
  * 5 Ethernet ports (maybe wired to switch?)
  * 2 WLANs
    * MT7612
    * MT7603
* USB
  * One USB 3.0 port
* Unpopulated pads
  * UART
    * Pin 1: Vcc (3V3)
    * Pin 2: Rx
    * Pin 3: Tx
    * Pin 4: GND

## GPIO map
* GPIO 29: Reset
* GPIO 18: WPS
* GPIO 27: USB 3.0 LED

## Extra note
* Need extra heatsink for MT7621, MT7612, MT7603 to avoid thermal throttling.
* Stock UART shell login is admin but password is SHA-1 hashed.
* ~~LEDE port (WIP): https://github.com/perillamint/lede-wevo-11ac-nas~~
* LEDE support mainlined!