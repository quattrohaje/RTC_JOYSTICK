# RTC_JOYSTICK
RTC and Joystick interface ISA 8bit for XT/AT PC

V mém IBM5160 zbyl ještě jeden volný ISA8bit slot a tak jsem se rozhodl, že si postavím kartu RTC. Chtěl jsem si také vyzkoušet kreslit v novém
programu Kicad a  vyzkoušet export a objednání u výrobce DPS.

Celý projekt se skládá ze dvou částí RTC a gamertu. Proč takto ? Původně jsem chtěl jen RTC, ale bál jsem se , že by karta špatně držela v ISA slotu
a tak jsem přidal gameport, který je přišroubován k frézované záslepce.
Jak jsem již psal, dá se to rozdělit na dvě části 
RTC se skládá ze součástek U1,U2,Y1,BT1,JP1,J1,R1,R2,R3
Gameport pak z U3,U4,U5,U7,C2,C3,C4,C5,C6,C7,C8,C9,C10,C11,R4,R5,R6,R7,RN1 a RN2
Kondenzátor C1 je společný pro obě zapojení a měl by být vždy osazen.
Hodnoty součástek nejsou kritické 
- odpory 10k jsou klasické metalické
- kondenzátory 10n jsou keramické
- kondenzátory 51p jsou keramické, zde není důležité dodržet přesnou hodnotu můžou být s velkou tolerancí 30-100p (ale asi všechny stejně)
- RN1 8x1k0 8xrezistor se společným jedním vstupem, RN2 4x10k 4x rezistor se společným jedním vstupem . U RN2 je dobré dodržet 10k hodnotu

JP1 slouží k výmazu RTC hodin v obvodu DS12885
J1 slouží k nastavení adresy na které bude komunikovat RTC obvod. Doporučuji 0x240 tj. A1 zkratovaný pomocí jumperu

Osazení není složité, není tam žádná záludnost.

Programy pro GAL jsem kompiloval pomocí Wincurl

Driver pro ovládání RTC obvodu je psán v ASM a přeložen pomocí NASM. Použití driveru je v config.sys
device=c:\ibm\dsclock.sys 0x240
Driver ještě není úplně hotov, v originál byly nějaké chyby, ty jsem upravil, ale ještě to musím doladit. Driver funguje jak s RTC tak gameportem 

Pár fotek z projektu
![rtc1](https://github.com/user-attachments/assets/96d01788-2fb6-4262-b954-b4a0ba77a517)
![rtc2](https://github.com/user-attachments/assets/5bd82b7f-a29e-481f-a63c-f595b514e8e8)
![rtc4](https://github.com/user-attachments/assets/7d08d716-1c16-4986-93d1-36ae1502f4d4)
![rtc5](https://github.com/user-attachments/assets/b63085b2-44ef-4949-b006-0e90560cf58b)
![rtc6](https://github.com/user-attachments/assets/9734a088-53b7-4616-b7cc-abdc777a827f)
![rtc7](https://github.com/user-attachments/assets/f145c380-9755-40e9-94e6-5a5e6a110987)

https://github.com/user-attachments/assets/15338810-2ce5-4af2-8db0-e2d07ca02ab5





Inspirace byla v těchto projektech na github
https://github.com/spark2k06/RTC8088
https://github.com/roybaer/game_control_adapter


