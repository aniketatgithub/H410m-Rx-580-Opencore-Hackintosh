# OpenCore EFI: Gigabyte H410M H + Intel i3-10100F + RX 580

OpenCore EFI setup for a Gigabyte H410M H Hackintosh build with an Intel Core i3-10100F and an Asus RX 580 8GB. Copy the EFI files to a USB drive, boot from it, and install macOS.

## Hardware

| Part | Used in this build |
| --- | --- |
| Motherboard | Gigabyte H410M H |
| CPU | Intel Core i3-10100F |
| GPU | Asus RX 580 8GB OC |
| RAM | 2 x 8GB DDR4 3200MHz |
| Storage | 2 x 120GB SSD, 1 x 500GB HDD |
| CPU cooler | DeepCool |
| PSU | 550W Cooler Master |

## Versions

| Item | Version |
| --- | --- |
| OpenCore | [UNKNOWN: not recorded when this EFI was uploaded] |
| macOS | [UNKNOWN: not recorded; this build dates from October 2021] |
| BIOS settings | See the screenshots further down |

If you get this running on a newer macOS or OpenCore release, please open an issue with what you changed so the notes here can be updated.

## What works and what does not

| Feature | Status |
| --- | --- |
| Ethernet | Works |
| Audio | Works |
| iMessage, FaceTime, App Store | Work (after generating your own serial, see below) |
| USB ports | Work |
| Dual boot with Windows | Works (install macOS on a separate drive) |
| Wi-Fi | Not working on this build |
| Bluetooth | Not working on this build |
| Sleep, iGPU, DRM, sidecar | Not tested |

Wi-Fi and Bluetooth were never enabled on this hardware. If you add a compatible card, you will need the matching kexts in the Kexts folder of your EFI.

## Before you start

1. Generate your own serial number and SMBIOS values. Do not reuse anyone else's serial: Apple can block the Apple ID tied to it.
2. Edit `config.plist` with ProperTree and fill in your generated values.
3. Match the BIOS settings in the screenshots below before booting.

Downloads:

- SMBIOS generator: https://gitamin-my.sharepoint.com/:f:/g/personal/121810314010_gitam_in/EulmQIkzvSlKsMq6B5-KAKQBQjNgCnbW8mmgfA2Q4b3lkQ?e=WWwzxN
- ProperTree: https://gitamin-my.sharepoint.com/:f:/g/personal/121810314010_gitam_in/Eg5_YqxqWrBPnKnl7qGOpVAByM0WYFO2g0sIeLzKv7fqAA?e=YTQdFp
- EFI files for the USB drive: https://gitamin-my.sharepoint.com/:f:/g/personal/121810314010_gitam_in/EqaosVFr6-BGnWsZubQKjvkBKAosna_GE-1vSbuXFVJW-A?e=YqYg1V

## Install steps

1. Download the EFI files from the link above.
2. Format a USB drive and copy the files to it.
3. Set the BIOS options to match the screenshots in the next section.
4. Boot from the USB drive and choose the macOS installer.
5. Install macOS on an SSD if you have one; it runs noticeably smoother than on a hard drive.
6. After install, copy the EFI from the USB drive to the EFI partition of your macOS drive so you can boot without the USB.

For dual boot, keep Windows and macOS on separate drives, then pick OpenCore in the boot menu.

## BIOS settings (Gigabyte H410M H)

BIOS configuration matters on this board. These are the settings used on this build:

![BIOS settings](https://user-images.githubusercontent.com/42694864/137506942-9e60f53f-4102-40a1-b843-c76947d0bc9e.jpeg)
![BIOS settings](https://user-images.githubusercontent.com/42694864/137506946-5a98c367-155a-4107-93ca-ad4122516b18.jpeg)
![BIOS settings](https://user-images.githubusercontent.com/42694864/137506952-0e1e9043-67cb-4c2c-9cd7-2e91d77c6eb2.jpeg)
![BIOS settings](https://user-images.githubusercontent.com/42694864/137506955-8a336c6d-eb86-4caa-81c6-51d9bd88f069.jpeg)
![BIOS settings](https://user-images.githubusercontent.com/42694864/137506958-f3620ab2-6b0d-443e-bd33-c3e466c95b4d.jpeg)

Boot screenshot:

![Booting macOS](https://user-images.githubusercontent.com/42694864/137506916-c5b6dfa5-2474-40b7-aced-584d1f2d8869.jpeg)

## Notes on config.plist

- Always replace the serial number, MLB, and UUID with your own generated values before signing in to any Apple service.
- Keep a copy of the working config.plist before editing; most boot problems on this setup come from plist edits.
- If you change hardware (especially the GPU or a Wi-Fi/Bluetooth card), expect to adjust kexts and device properties.

## Demo

Booting and gaming on this build:

https://user-images.githubusercontent.com/42694864/137507258-bd50c786-93d1-40d9-9a40-b8a21f101551.mp4

https://user-images.githubusercontent.com/42694864/137507289-54dc1e4d-62f2-461f-b3a0-82cbb2a393d7.mp4

https://user-images.githubusercontent.com/42694864/137507598-5def0d98-ba7f-4381-8800-f35c3500f9b4.mp4

## Guides and credits

- Dortania OpenCore Install Guide (start here for installs and troubleshooting): https://dortania.github.io/OpenCore-Install-Guide/
- Video tutorials used for this build:
  - https://www.youtube.com/watch?v=j-Cm30I_DEw&t=156s
  - https://www.youtube.com/watch?v=KV9AsF95QwU
  - https://www.youtube.com/watch?v=lztH7BUxIoM&t=1188s

Thanks to the Hackintosh community for the guides and help behind this build.

## Disclaimer

This project is for educational and experimental purposes. Running macOS on non-Apple hardware may violate Apple's terms of service and can carry legal risk. Back up important files before trying any of this; a bad EFI or BIOS change can leave a system unbootable. The author is not responsible for crashes, data loss, or blocked Apple IDs resulting from the use of these files. Use macOS only in compliance with Apple's licensing agreements.
