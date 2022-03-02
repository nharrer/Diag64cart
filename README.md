# Rev. 3

This is a fork of [Sven Petersen's excellent C64 Diagnostic Cartridge Board](https://github.com/svenpetersen1965/Diag64cart).

The only change is that JP3 is implemented as a real jumper instead of a solder bridge. That way the Cart can quickly be reconfigured to be used on a C64 and a C128 without having to cut and resolder a solder bridge. And C64 Dead Test Roms are still possible.

__Example Configuration__:

```
EEPROM
ADDRESS  SW1  SW2  ROM                  JP7     JP3
-------------------------------------------------------
C64 Mode:
$0000    OFF  OFF  Diagnostic 586220    closed  closed
$2000    ON   OFF  DeadTest 781220      closed  closed
$4000    OFF  ON   Diag 4.1.1           closed  closed
$6000    ON   ON   DeadTest STID 1.2.0  closed  closed

C128 Mode:
$8000    OFF  OFF  Diag C128 785260     open    open
$C000    OFF  ON   Diag C128 789010     open    open
```

Now follows the original README:

# Diag64cart
The Diag64cart is a C64/C128 cartridge PCB, that is especially made for the need of diagnostic software, like Dead Test Rev. 781220 and Diagnostic Rev. 586220. The Diag64cart is derived from the Versa64cart (https://github.com/bwack/Versa64Cart), it lacks of the ability to be a 16k cartridge, though.
The geometry of this cart was especially made for the cheap Maszczyk KM-20 and the Kradex Z7 cartridge cases. Those are available from https://restore-store.de/ or https://www.tme.eu.
Dead Test and Diagnostic reside in two different address spaces of the C64. Also, they are differently configured via GAME  or EXROM and use different chip select signals (ROMH or ROML).

<img src="https://github.com/svenpetersen1965/Diag64cart/blob/main/Rev.%200/Pictures/6771a_diag64cart.JPG" width="300" alt="Diag64cart">

This repository contains binary files from other projects. The sources can be found in documen 164-6-01-** or here:
1.	(Commodore) Diagnostic Rev. 586220 (C64) (Version +0.5):  http://blog.worldofjani.com/?p=164
2.	(Commodore) Dead Test Rev. 781220 (C64):  http://blog.worldofjani.com/?p=164
3.	STID Dead Test (v1.2.0): https://github.com/stid/kick-c64-dead-test
4.	(Commodore) Diagnostic Rev. 785260 (C128):  http://blog.worldofjani.com/?p=164
5.	(Commodore) Diagnostic Rev. 588121 (C128):  http://blog.worldofjani.com/?p=164
6.	1541 Diagnostic (World of Jani): : http://blog.worldofjani.com/?p=2180
7.	Diag 4.1.1.: http://blog.worldofjani.com/?p=164

BOM value (12.12.2020): 9.79€

Check out the 3D printed cartridge case from <a href="https://www.thingiverse.com/thing:4759098">retrorewind.ca</a>.

# The burn-In Software
This software requires modification of the default Configuration, since all four cartridges require EXROM=0 and Chip Select=ROML.
