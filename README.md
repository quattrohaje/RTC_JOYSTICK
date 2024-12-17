# RTC_JOYSTICK
There was one free ISA8bit slot left in my IBM5160, so I decided to build an RTC card. I also wanted to try drawing in the new one
the Kicad program and try exporting and ordering from the DPS manufacturer.

The whole project consists of two parts RTC and gamert. Why like this? Originally, I only wanted RTC, but I was afraid that the card wouldn't hold well in the ISA slot
so i added the gameport which is bolted to the milled blank.
As I already wrote, it can be divided into two parts
- "RTC" consists of components U1,U2,Y1,BT1,JP1,J1,R1,R2,R3
- "Gameport" then from U3,U4,U5,U7,C2,C3,C4,C5,C6,C7,C8,C9,C10,C11,R4,R5,R6,R7,RN1 and RN2
- "Common" Capacitor C1 is common to both connections and should always be fitted.
Component values ​​are not critical
- 10k resistors are classic metallic
- the 10n capacitors are ceramic
- the 51p capacitors are ceramic, it is not important to observe the exact value here, they can be 30-100p with a large tolerance (but probably all the same)
- RN1 8x1k0 8xresistor with common one input, RN2 4x10k 4x resistor with common one input. For RN2 it is good to stick to the 10k value

JP1 is used to clear the RTC clock in the DS12885 circuit
J1 is used to set the address to which the RTC circuit will communicate. I recommend 0x240 i.e. A1 shorted using a jumper

The installation is not complicated, there is no trickery.

I compiled the programs for GAL using Wincurl

The driver for controlling the RTC circuit is written in ASM and translated using NASM. Driver usage is in config.sys
device=c:\ibm\dsclock.sys 0x240
The driver is not completely finished yet, there were some errors in the original, I corrected them, but I still have to fine-tune it. The driver works with both RTC and gameport

A few photos from the project
![rtc1](https://github.com/user-attachments/assets/96d01788-2fb6-4262-b954-b4a0ba77a517)
![rtc2](https://github.com/user-attachments/assets/5bd82b7f-a29e-481f-a63c-f595b514e8e8)
![rtc4](https://github.com/user-attachments/assets/7d08d716-1c16-4986-93d1-36ae1502f4d4)
![rtc5](https://github.com/user-attachments/assets/b63085b2-44ef-4949-b006-0e90560cf58b)
![rtc6](https://github.com/user-attachments/assets/9734a088-53b7-4616-b7cc-abdc777a827f)
![rtc7](https://github.com/user-attachments/assets/f145c380-9755-40e9-94e6-5a5e6a110987)

https://github.com/user-attachments/assets/15338810-2ce5-4af2-8db0-e2d07ca02ab5





The inspiration was in these projects on github
https://github.com/spark2k06/RTC8088
https://github.com/roybaer/game_control_adapter


