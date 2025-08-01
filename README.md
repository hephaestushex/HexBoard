# HexBoard

![IMG_0879](https://github.com/user-attachments/assets/2a0d8ee2-14fa-4057-817f-6e4ccde94790)

![image](https://hc-cdn.hel1.your-objectstorage.com/s/v3/aa89db46a0616ceec7e96bbd6a2fd4cc0817f5ea_render.png)

![image](https://github.com/user-attachments/assets/466e8cf9-62c7-4722-b00c-87eb7bb91e9b)

A wireless split keyboard designed by HephaestusHex. It uses the SEEED Studio XIAO nRF52840 for wireless bluetooth connectivity

I made this split keyboard because it was a great project for learning PCB design, ergonomics, case design, keyboard firmware, and more. I wanted to make a split keyboard specifically because during my research, I found it's better than a regular keyboard because of ergonomics that I won't get into. Ben Vallack has [videos](https://www.youtube.com/@BenVallack) that gets into the details.

# CAD
## PCB

![image](https://github.com/user-attachments/assets/01b26dde-56ff-483b-b14a-a8f3ce19261a)


![image](https://github.com/user-attachments/assets/b695c5c2-49b6-4c80-aaf9-4e54865751d7)

![image](https://github.com/user-attachments/assets/90f76e46-734e-4ae8-8dd2-ed004ada812d)


![image](https://github.com/user-attachments/assets/11d7a824-fa69-4ea1-83cb-c59e825c36d7)

![image](https://github.com/user-attachments/assets/26250ff4-b56e-4483-9b6d-395384a4eb98)


## Case

![image](https://github.com/user-attachments/assets/54c539ad-4426-4495-a85a-a3825bd8dee1)

# Firmware

This kb uses ZMK for firmware. Due to ZMK's requirement of using another repo, all of the zmk code is in this [repo](https://github.com/hephaestushex/zmk-config-hexboard)

# BOM

| Name | Reference | Quantity | Value | Footprint | Part Link | Description | Price (USD) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1N4148 Diodes | D1-18 | 36 | 1N4148 | D_DO-35_SOD27_P7.62mm_Horizontal | [AliExpress](https://www.aliexpress.us/item/1005004962400215.html) | Used for switch matrix | $1.01 |
| Gateron KS-33 Low Profile Switches | SW1-18 | 36 |  | Gateron-KS33-Solderable-1U | [AliExpress](https://www.aliexpress.us/item/1005006637645158.html) | Low-profile switches | $25.22 |
| Seeed XIAO nRF52840 | U1 | 2 |  | XIAO-nRF52840-DIP-Batt | [AliExpress](https://www.aliexpress.us/item/1005008484816031.html) | Bluetooth MCU for wireless split connectivity | $31.09 |
| 601730 3.7V LiPo Battery | J1 | 2 | 250mAh | PinHeader_1x02_P2.54mm_Vertical | [AliExpress](https://www.aliexpress.us/item/1005006584143607.html) | Battery for MCU | $5.47 |
| PCB | hexboard-left, hexboard-right | 2 |  |  | [JLC PCB](https://jlcpcb.com/) | PCB for the left and right halves of the keyboard | $24.33 |
| M3x5x4 Heatset Inserts |  | 8 |  |  | [AliExpress](https://www.aliexpress.us/item/4000232858343.html) | Heatset inserts for mounting components | $6.23 |
| M3x6 Screws | H1-4 | 8 |  | MountingHole_3.2mm_M3 | [AliExpress](https://www.aliexpress.us/item/32794842281.html) | Screws for securing the PCB to the case | $2.89 |
| Slide SPDT Switches | SW19 | 2 |  | SW_Slide_SPDT_Straight_CK_OS102011MS2Q | [AliExpress](https://www.aliexpress.us/item/1005007162182882.html) | Slide switch for power control | $1.46 |
| Case |  |  |  |  |  | Free since I already have filament | $2.78 |
| Keycaps |  |  |  |  |  | Free since I already have filament | $0.66 |
| AliExpress Total  |  |  |  |  |  |  | $75.80 |
| JLCPCB Total  |  |  |  |  |  |  | $30.80 |
| Grand Total |  |  |  |  |  |  | $113.04 |




