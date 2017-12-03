# Basic info
* Model name: XMTZC01HM
* Korean version specific: Unit selection switch is sealed with sticker. Cheap chinese battery is removed during sealing process.

# Protocol
## Overview
* It uses BLE.
* It broadcasts its data on Bluetooth advertisement frame.
  * It means our weight data is not secured at all. Use it with care!
* https://github.com/chaeplin/Xiaomi_scale_scan can parse Mi scale advertisement frame and can get data.
* It only sends lbs and jin(chinese Catty) over bluetooth. Host app have to convert jin to kg (just divide it with 2) according to its switch configuration. (included in received data)

## Detailed info
Example data: 5701880f10a0fa470d161d18023c23b208

### 0-1st byte
* In example: 5701
* Company ID: Anhui Huami Information Technology Co., Ltd. (0x0157)

### 2-7th byte
* In example: 880f10a0fa47
* Unknown data.

### 8-15th byte
* In example: 0d161d18023c23b208


#### 8th byte
* In example: 0d
* Length : 13

#### 9th byte
* in example: 16
* Service data - 16-bit UUID

#### 10-11th byte
* In example: 1d18
* UUID of service. (181d - weight scale)

#### 12th byte
* In example: 02
* Contains information about scale state and switch configuration.
  * First 4 bit contains scale state (not stabilized, stabilized, locked, sleeping) and information about part of unit system.
    * first bit (from LSB): true if config switch is on chinese Catty.
    * second bit (from LSB): stabilized bit?
    * third bit (from LSB): Unknown.
    * fourth bit (from LSB): Load removed?
  * Second 4 bit contains information about unit system.
    * See BT Weight scale service doc.
    * first bit (from LSB): Imperial(true) or MKS(false). 
    * second bit (from LSB): Time stamp present. (research needed)
    * third bit (from LSB): UserID present (for multi-user scale) (research needed)
    * fourth bit (from LSB): BMI and height present (research needed)
      * 0011: imperial unit system (lbs).
      * 0010: MKS or chinese Catty. (example)
      * Note: It seems it does not comply BT standard strictly.

#### 13-14th byte
* In example: 3c23
* Contains weight data * 100 in little endian endianness.
  * 3c23 represents 90.20 in chinese Catty and 45.10 in kg.

#### 15-16th byte
* In example: b208
* Some kind of sequence number.

# Node.JS implementation
* https://github.com/perillamint/node-xiaomi-scale
* https://www.npmjs.com/package/node-xiaomi-scale

# Other implementations
* Open-source Android app: https://github.com/Mnkai/OpenXiaomiScale

# Thanks to
http://github.com/chaeplin