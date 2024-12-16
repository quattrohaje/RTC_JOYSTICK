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

Driver pro ovládání RTC obvodu je psán v ASM a přeložen pomocí NASM

Inspirace byla v těchto projektech na github
https://github.com/spark2k06/RTC8088
https://github.com/roybaer/game_control_adapter


