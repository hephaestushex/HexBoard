# HexBoard
A wireless split keyboard designed by HephaestusHex. It uses the nRF52840 chip for wireless connectivity

I made this split keyboard because it was a great project for learning PCB design, ergonomics, case design, keyboard firmware, and more. I wanted to make a split keyboard specifically because during my research, I found it's better than a regular keyboard because of ergonomics that I won't get into. Ben Vallack has [videos](https://www.youtube.com/@BenVallack) that gets into the details.

# CAD
## PCB

![image](https://github.com/user-attachments/assets/b695c5c2-49b6-4c80-aaf9-4e54865751d7)

![image](https://github.com/user-attachments/assets/11d7a824-fa69-4ea1-83cb-c59e825c36d7)

# BOM

| Name | Reference | Quantity | Value | Footprint | Part Link | Description | Price (USD) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1N4148 Diodes | D1-18 | 36 | 1N4148 | D_DO-35_SOD27_P7.62mm_Horizontal | [AliExpress](https://www.aliexpress.us/item/1005004962400215.html) | Used for switch matrix | $0.99 |
| Gateron KS-33 Low Profile Switches | SW1-18 | 36 |  | Gateron-KS33-Solderable-1U | [AliExpress](https://www.aliexpress.us/item/1005006637645158.html) | Low-profile switches | $23.19 |
| Seeed XIAO nRF52840 | U1 | 2 |  | XIAO-nRF52840-DIP-Batt | [AliExpress](https://www.aliexpress.us/item/1005008484816031.html) | Bluetooth MCU for wireless split connectivity | $31.11 |
| 601730 3.7V LiPo Battery | J1 | 2 | 250mAh | PinHeader_1x02_P2.54mm_Vertical | [AliExpress](https://www.aliexpress.us/item/4000859116608.html) | Battery for MCU | $11.08 |
| PCB | hexboard-left, hexboard-right | 2 |  |  | [JLC PCB](https://jlcpcb.com/) | PCB for the left and right halves of the keyboard | $24.33 |
| M3x5x4 Heatset Inserts |  | 8 |  |  | [AliExpress](https://www.aliexpress.us/item/4000232858343.html) | Heatset inserts for mounting components | $0.99 |
| M3x16 Screws | H1-4 | 8 |  | MountingHole_3.2mm_M3 | [AliExpress](https://www.aliexpress.us/item/32794842281.html) | Screws for securing the PCB to the case | $0.99 |
| Slide SPDT Switches | SW19 | 2 | | SW_Slide_SPDT_Straight_CK_OS102011MS2Q | https://www.aliexpress.us/item/1005007162182882.html | Slide switch for power control | $0.99 |


