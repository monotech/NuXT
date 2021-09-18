These files are provided for repairing or updating the BIOS on your NuXT v1.2.
They contain Sergey Kiselev's 8088_BIOS Version 0.9.8 (https://github.com/skiselev/8088_bios/tree/master)

It is recommended to update from older versions to 0.9.8 if you use floppy drives, as it fixes some floppy issues.

The NuXT has a 128K flash chip which is split into two halves,
so you effectively have two System ROMs you can switch between with a DIP switch.

The NuXT cannot be bricked by doing something wrong here. The worst that can happen is needing a programmer device to reflash the 128K System ROM chip.

***

The 128K images below are for writing to a Flash ROM IC with a programmer device.
The 8088_BIOS is in both halves of the ROM.

NuXT 128K image - Hybrid (recommended)
- Contains: V20-compatible XT-IDE BIOS in first half, and all-compatible in second half (selectable with DIP switch on NuXT).
- SHA1: F08E5B4535F3B758265380C4431B774A5FB9DB4A
- Last updated: 1 Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

NuXT 128K image - V20
- Contains: identical first and second half, with V20-compatible XT-IDE BIOS.
- SHA1: 8A28444BC0F5A41992EACA92667CF80D4FE29C25
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

NuXT 128K image - 8088
- Contains: identical first and second half, with all-compatible XT-IDE BIOS.
- SHA1: DB6ECFA6CE50F35B4DC05F80BBD6B205BCA8B8DA
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

***

WARNING: The below files can be flashed in-system with UFLASH.EXE,
but you must use the correct command-line options, or the flash could be corrupted, and require a programmer device and the 128K image to fix.

If you don't have a programmer device handy in case you make a mistake, do not flash anything if the system is working as expected,
If you just wish to update the System BIOS, you needn't reflash the entire ROM. And vice-versa for just updating the XT-IDE BIOS.

The provided images are padded so the data ends up at the correct location, and old data is overwritten if a programmed BIOS is smaller than the previous one.
If you are programming a customized XT_IDE BIOS, you should pad the end of the file with FF's until it's 32768 bytes, then use the same flashing command as the XT-IDE BIOS below.

UFLASH can provide a delay before flashing, to allow switching to and flashing the other half of the System ROM while the system is running.
This is useful if you wish to change the XT-IDE BIOS from V20 to 8088 type (the system will hang if you are using an 8088 CPU and the V20-compatible XT-IDE BIOS tries to initialize).
To add a delay of 30 seconds, add the following to the end of the command line: -t 30
(The timer is only accurate on 4.77MHz 8088. Set a longer timer value for faster CPUs)

uFlash is Sergey's XiFlash tool, adapted by Aitor Gomez to work on Micro 8088 and NuXT (https://github.com/spark2k06/micro_8088/tree/master/BIOS)

*** System BIOS ***

NuXT System BIOS image (BIOS098.BIN)
- Bare Micro 8088 BIOS image by Sergey Kiselev
- UFLASH Command: UFLASH -p -i BIOS098.BIN -a F800
- SHA1: 712F9D12C2F67B4FA86B582EB8C98ACBB5E5400D
- Last updated: 17th May 2020
- Update reason: Updated to 0.9.8

***

*** XT-IDE BIOS ***

XT-IDE BIOS image - V20-CPU-compatible (XTIDEV20.BIN)
- Contains: V20-compatible XT-IDE BIOS, configured for the NuXTv1.2 - faster, but not compatible with 8088 CPU
- UFLASH Command: UFLASH -p -i XTIDEV20.BIN -a F000
- SHA1: 1030B38BC6BA17A8A6F463DCAA1378289CCFD2E0
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

XT-IDE BIOS image - All-CPU-compatible (XTIDE88.BIN)
- Contains: all-compatible XT-IDE BIOS, configured for the NuXTv1.2 - slower, but works with all CPUs
- UFLASH Command: UFLASH -p -i XTIDE88.BIN -a F000
- SHA1: 205AD526669D371AFCD53FD883090DB238DCDF12
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

***

*** Entire ROM (System BIOS and XT-IDE BIOS) ***

NuXT 64K image - V20 (098_NV20.BIN)
- Contains: V20-compatible XT-IDE BIOS, configured for the NuXTv1.2 - faster, but not compatible with 8088 CPU
- UFLASH Command: UFLASH -p -i 098_NV20.BIN -a F000
- SHA1: 539255278C08D5E9B152EBF442620CB9583BFD32
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

NuXT 64K image - 8088 (098_8088.BIN)
- Contains: all-compatible XT-IDE BIOS, configured for the NuXTv1.2 - slower, but works with all CPUs
- UFLASH Command: UFLASH -p -i 098_8088.BIN -a F000
- SHA1: A8BE7594E317C050F9B1B5C7CED91B72390143A7
- Last updated: 18th Sep 2021
- Update reason: Updated XT-IDE BIOS to R618 (31st Aug 2021).

***

Note1: When XT-IDE BIOS version R606 came out, a bug was fixed relating to incorrectly addressing small CF cards in CHS mode when they support LBA.
NuXT v1.2 boards all shipped with an XT-IDE BIOS version older than R606.

As a consequence of the bug fix, CF cards formatted on an XT-IDE BIOS older than R606 will not be bootable in an R606 or later BIOS, and vice versa.

If your CF card fails to boot, I recommend updating the XT-IDE BIOS version in all XT-IDE devices you own where you wish to swap the CF card between devices,
and then reformat the CF cards to the new format.

The easiest way to do this, is to backup the files off the card, then prepare it in a system with the updated XT-IDE BIOS, as per instructions for preparing
a CF card, described in any NuXT user manual.

Note2: The files here are intended for the NuXT v1.2, which has an XT-CF interface at I/O address 300h.
They are not interchangeable with the NuXT v2.0, which has an XT-IDE Rev2 interface at I/O address 170h. Only the XT-IDE BIOS portion of these images differ.
