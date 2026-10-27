# Desktop Hardware Upgrade and Troubleshooting

I upgraded my personal desktop from a Ryzen 7 2700X with 16 GB of DDR4 to a Ryzen 5 9600X with 32 GB of DDR5. I also replaced the motherboard and power supply while keeping my graphics card, storage, and case.

My goal was to get the computer ready for IT study and virtual machine labs. Along the way, I ran into a no-display problem, traced it to an incomplete PSU connection, and got the system booting into Windows. This is my record of the upgrade and the checks I made afterward.

## What changed

| Component | Before | After |
| --- | --- | --- |
| Processor | AMD Ryzen 7 2700X | AMD Ryzen 5 9600X |
| Motherboard | Gigabyte B450 AORUS M | MSI PRO X670-P WIFI |
| Memory | Team Group 16 GB DDR4 | Corsair Vengeance 32 GB DDR5 |
| Power supply | BeQuiet 550 W | MSI MAG A650GL 650 W |
| Graphics card | NVIDIA GeForce GTX 1660 Ti | Kept the same card |
| Storage | Samsung 980 1 TB NVMe, SATA SSD, SATA HDD | Kept the existing drives |
| Case | Phanteks | Kept the same case |

The new memory kit is rated for 5200 MT/s. My verification screenshot shows it running at 4800 MT/s. Will be overclocked at a later time.

![Original desktop](01-original-system.jpeg)

*My original system before removing components.*

![Replacement parts](02-upgrade-components.jpeg)

*The processor, motherboard, memory, and PSU for the upgrade.*

## Taking the old system apart

I removed the original motherboard, processor, memory, and power supply. I kept the GTX 1660 Ti and existing drives to use with the new board.

![Removed components](03-removed-components.jpeg)

## Putting the new hardware together

I installed the CPU, cooler, DDR5 memory, and existing NVMe storage on the new motherboard before fitting it into the case. After mounting the board, I connected the case I/O cables and reinstalled the graphics card.

![Assembled motherboard](04-motherboard-assembly.jpeg)

*CPU, cooler, memory, and NVMe storage installed before the board went into the case.*

<details>
<summary>Case connections and initial test setup</summary>

![Case I/O](05-case-io-connections.jpeg)

*I connected the case USB and front-panel switch/LED cables to the motherboard headers.*

![PSU test setup](06-psu-test-setup.jpeg)

*I kept the new PSU outside the case for initial testing before mounting it.*

</details>

## The first power-on: fans and lights, but no display

When I first powered it on, the fans and lights came on, but nothing appeared on the monitor. A motherboard diagnostic LED stayed lit.

I checked the modular PSU connections and found that a required PSU-side plug on the motherboard power cable had been left disconnected. Once I connected it and tried again, the system displayed Windows and reached the lock screen.

| Problem | What I found | What fixed it |
| --- | --- | --- |
| Fans and lights powered on, but no display | An additional PSU-side plug on the motherboard power cable was disconnected | Connecting the missing plug allowed Windows to boot |

![No-display diagnostic light](07-no-display-diagnostic-led.jpeg)

*The system powered on, but the diagnostic light stayed illuminated.*

![PSU connection inspection](08-psu-connection-inspection.jpeg)

*I traced the incomplete connection back to the PSU side of the motherboard power cable.*

![Successful Windows boot](09-successful-windows-boot.jpeg)

*Windows loaded after I corrected the connection.*

## Checking the BIOS

I had a FAT32 USB drive with an MSI.ROM file ready in case I needed to flash the BIOS. I ended up using neither the drive nor the motherboard's Flash BIOS button during this upgrade. The existing firmware worked with the new CPU once the power connection was corrected.

I opened the BIOS to check that the CPU and memory were recognized and to look at the temperature readings. It showed the Ryzen 5 9600X, 32768 MB of memory, and BIOS version **E7D67AMS.1M6**. At the time of the photo, CPU temperature was **56°C** and motherboard temperature was **35°C**.

<details>
<summary>BIOS preparation and verification</summary>

![BIOS USB contingency](12-bios-usb-preparation.png)

*The BIOS USB was available as a backup plan. I did not use it to flash the board during this project.*

![BIOS hardware checks](13-bios-hardware-verification.jpeg)

*I checked the detected hardware, installed BIOS version, and temperature readings.*

</details>

## Drivers and Windows activation

I downloaded and successfully installed the motherboard chipset drivers. The installer screenshot shows the packages I selected before starting the installation.

I also worked with Microsoft support to reactivate Windows 11 Pro after the hardware change. I checked the Activation page afterward and confirmed that Windows showed **Active**.

![Windows activation](18-windows-11-pro-activation.png)

## What I checked afterward

| Check | Result |
| --- | --- |
| Windows boot | Reached the Windows lock screen |
| CPU | Ryzen 5 9600X detected, with 6 cores and 12 processors |
| Memory | 32 GB DDR5 detected, 2 slots used, 4800 MT/s displayed |
| Storage | NVMe system drive and both SATA drives visible in Task Manager |
| Graphics card | GTX 1660 Ti recognized in Task Manager |
| Case I/O | Connected peripherals worked through the case USB ports |
| Wi-Fi | Built in RZ616 adapter recognized, with network traffic visible |
| Cooling and lighting | Checked fan operation and case/GPU lighting |
| Chipset drivers | Installation completed successfully |
| Windows license | Windows 11 Pro showed an Active activation state |

These were basic boot and function checks. I haven't included stress-test or benchmark results in this project.

![Upgraded system running](11-running-upgraded-system.jpeg)

*The upgraded system running after I resolved the power connection issue.*

<details>
<summary>Windows and peripheral verification images</summary>

![Case USB test](10-case-usb-peripheral-test.jpeg)

*Testing peripherals through the case I/O.*

![Chipset package selection](14-chipset-package-selection.png)

*The driver packages I selected before installation.*

![CPU detected](15-cpu-detection.png)

![Memory detected](16-memory-detection.png)

![Storage detected](17-storage-detection.png)

![Wi-Fi verification](19-wifi-verification.png)

*Wi-Fi verification with my network details redacted.*

![GPU detected](20-gpu-detection.png)

</details>

## What I learned

The most useful lesson was checking every required connection on the modular PSU cable. Seeing fans spin and lights turn on didn't mean the system could complete startup. Finding the disconnected plug and then seeing Windows load gave me a clear way to connect the symptom, the fix, and the result.

This project gave me practice with hardware replacement, case and power connections, BIOS inspection, driver installation, Windows reactivation, and documenting a troubleshooting process. The computer is now available for my next IT lab projects.

