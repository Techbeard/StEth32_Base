# StEth32_Base

Das STEth32_Base ist ein auf STM32 Basiendes Ethernet Board. Es ist eine Fortführung des schon bestehenden [StEth32](https://github.com/Techbeard/StEth32). Dieses mal ist das Board allerdings darauf optimiert/ausgelegt in einm [Alu-Gehäuse](https://www.reichelt.de/profilgehaeuse-1455-l-120-x-103-x-31-mm-silber-1455l1202-p221363.html?&nbc=1)  eingesetzt zu werden. 


Um das Board möglichst vielseitig nutzen zu können sind auf dem Base Board alle unverwendeten Pins auf die Hinteren Vier Buchsenleisten geführt, wodurch Sie auf einem Erweiterungsboard für alles mögliche eingestezt werden können.

![alt text](/Docs/Pictures/StEth32_Base_PCB.png "StEth32 Base Board")

## Fetures auf dem Base Board

Eingangsspannung: 5 - 28 V

- [OLED](https://lcsc.com/product-detail/OLED-Displays-Modules_Shenzhen-Allvision-Tech-QG-2864KLBLG01_C90547.html)
- [Drehencoder](https://www.conrad.de/de/p/alps-stec11b02-encoder-5-v-dc-0-01-a-360-1-700696.html)
- Ethernet mit W5500
- 5.5x2.1 Hohlbuchse zur Stromversorgung
- POE Module zur Stromversorgung
- Footprint für [NRF24](https://lcsc.com/product-detail/Wireless-Modules_Chengdu-Ebyte-Elec-Tech-E01-ML01SP4_C97340.html)
- 2x Status LED

## Pinout

J3                                                                
| STM32 | Function | Pin    | Pin    | Function  | STM32   |
| :-----| :------- | :----- | :----- | :-------- | :----   | 
|       |   Vcc    | **1**  | **2**  | Vcc       |         |  
|       |   TX3    | **3**  | **4**  | RX3       |         |   
|       |   RX2    | **5**  | **6**  | TX2       |         |    
|       |   TX1    | **7**  | **8**  | RX1       |         |

J4
| STM32 | Function | Pin    | Pin    | Function  | STM32   |
| :-----| :------- | :----- | :----- | :-------- | :----   |
|       |   SCL    | **1**  | **2**  | SDA       |         |  
|  PB3  |          | **3**  | **4**  |  USB/CAN  | PA12    |   
|       |          | **5**  | **6**  |           | PB4     |    
|       |   3,3V   | **7**  | **8**  |   GND     |         |


J5                                                          
| STM32 | Function | Pin    | Pin    | Function  | STM32   |
| :-----| :------- | :----- | :----- | :-------- | :----   |
|       |   3,3V   | **1**  | **2**  |           | PB8     |  
| PA15  |          | **3**  | **4**  | RX1       | PB9     |   
| PB5   |          | **5**  | **6**  | Reset     | NRST    |    
|       |          | **7**  | **8**  | GND       | GND     |

J6
| STM32 | Function | Pin    | Pin    | Function  | STM32   |
| :-----| :------- | :----- | :----- | :-------- | :----   | 
|       |   3,3V   | **1**  | **2**  |           |  PA8    |  
|       |   CS     | **3**  | **4**  |           | PB1     |   
|       |   SCK    | **5**  | **6**  | MOSI      | PA3     |    
|       |   MISO   | **7**  | **8**  | GND       |         |
  
  
## Intern verwendete Pins

### Ethernet SPI

Der Ethernet Chip W5500 hängt auf dem SPI2 des STM32:

    MOSI => PB15
    MISO => PB14
    SCK  => PB13
    CS   => PB12
    INT  => PA8

### Serial RS485

Der MAX485 hängt an den Pins für den Serial1 des STM32
 
    RX => PB11
    TX => PB10
    EN => PB1

### Staus Led

    LED => PC13 LOW aktiv

### MOSFET Ausgänge

    T1 => PB3
    T2 => PA15
    T3 => PB5
    T4 => PB4
 

# Einsatzzwecke / Erweiterungsboards

## Artnet2DMX

Das erste Erweiterungsboard verwandelt das Baseboard in einen Artnet to DMX Converter zu verwandeln. Es Werden die 3 Serielen Schnittstellen des STM32 zu RS4
85 gewandelt und über 3 XLR Buchsen ausgegeben. 

Die dazugehörige Software findest man hier:

https://github.com/LeoDJ/StEth32_Artnet2DMX



|||
|:--:|:--:|
| ![alt text](/Docs/Pictures/DMX_OUTPUT_Top.png "Rückseite des Erweiterungsboards") | ![alt text](/Docs/Pictures/DMX_OUTPUT_Bottom.png "Vorderseite des Erweiterungsboards")|
|*Rückseite des Erweiterungsboards*|*Vorderseite des Erweiterungsboards*|
| ![StEth32](/Docs/Pictures/StEth32_Base+DMX_OUT_Front.png) | ![StEth32](/Docs/Pictures/StEth32_Base+DMX_OUT_Back.png)|
|*StEth32_Base + DMX Erweiterung im Gehäuse*|*StEth32_Base + DMX Erweiterung im Gehäuse*|

