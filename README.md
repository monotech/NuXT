Note: Current schematic files are for v1.1 draft. This has some errors fixed. These changes have not been made in the PCB files, which are still v1.0.

The changes in the schematic:
> Swapped power rails for DIP oscillator.

> Changed VGA enable switch to connect AEN to VGA-AEN, instead of RESET to VGA-RESET. Added pull-up to VGA-AEN.

> Added pull-up to FDC CS.

> Optimized resistors and resistor packs.


Known bugs:
> VGA disable still doesn't work correctly after fix above. Works for another VGA, but not MDA/CGA.

> Mouse stops working in graphics mode applications, but works fine in text mode. A different serial card doesn't help.


Based on schematics by Sergey Kiselev, with some small changes for combining optimization and board layout efficiency:

http://www.malinov.com/Home/sergeys-projects/isa-fdc-and-uart

http://www.malinov.com/Home/sergeys-projects/xt-cf-lite

http://www.malinov.com/Home/sergeys-projects/isa-supervga

https://github.com/skiselev/micro_8088

https://github.com/skiselev/isa8_backplane
