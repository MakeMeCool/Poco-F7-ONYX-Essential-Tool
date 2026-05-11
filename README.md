# 📱 Poco F7 (ONYX) Essential Tool

![Poco F7 Essential Tool Banner](poster.png)

An all-in-one, fully automated Windows utility designed to completely simplify device management, custom recovery installation, and custom ROM flashing for the **Poco F7 (Codename: ONYX)**. 

Built with a sleek, mathematically centered terminal UI, this tool eliminates the need to manually type tedious command-line instructions. Just drag, drop, and flash.

## ✨ Key Features
* **Zero Setup Required:** Automatically downloads the latest Google Platform Tools (ADB/Fastboot), `7-Zip`, and `payload-dumper-go` the first time you run it.
* **Drag-and-Drop Interface:** No need to move files to specific folders or type long file paths. Just drag your `.zip` or `.img` directly into the tool.
* **Automated ROM Flashing:** Automatically extracts `payload.bin` (with a live progress percentage), dumps the required boot images, flashes them, and initiates an ADB sideload in one seamless sequence.
* **Direct Image Extraction:** Intelligently extracts `recovery` and `vendor_boot` directly out of a full ROM zip without unpacking the whole file.
* **Integrated Bootloader Unlocking:** Features direct integration with the community Python-based Mi Unlock Tool.

---

## ⚙️ Prerequisites
Before using this tool, ensure you have:
1. A Windows PC.
2. An unlocked bootloader (required for flashing custom recoveries and ROMs).
3. **USB Debugging** enabled in your phone's Developer Options.
4. Proper Xiaomi/Android USB drivers installed.
5. **[Python 3](https://www.python.org/downloads/)** installed (Only required if you plan to use the *Mi Unlock Tool* feature).

---

## 🚀 How to Use
1. Download the [Poco_F7_Essential_Tool.bat](https://github.com/MakeMeCool/Poco-F7-ONYX-Essential-Tool/releases) script to your PC.
2. Double-click to run it.
3. On the first launch, wait a few seconds while it downloads the required background engines (ADB, Fastboot, Payload Dumper).
4. Connect your phone via USB.
5. Type the number of the action you want to perform and press **Enter**.

---

## 🛠️ Feature Breakdown: What the Tool Does in Action

### 1-3. Power & Reboot Management
Easily bounce between device states without touching your phone's physical buttons.
* **Reboot to System:** Sends commands via both ADB and Fastboot to boot the phone normally.
* **Reboot to Bootloader:** Reboots an active device into Fastboot/Bootloader mode.
* **Reboot to Recovery:** Reboots a Fastboot-connected device straight into Recovery mode.

### 4. Flash Custom Recovery Only
* **What it does:** Flashes a custom recovery (like TWRP, OrangeFox, or PBRP).
* **In Action:** Prompts you to drag and drop your `recovery.img` file. It waits for your device to be in Fastboot mode, and then executes `fastboot flash recovery_ab <your_file>`.

### 5. Extract & Flash Recovery + Vendor_Boot
* **What it does:** Instantly extracts and flashes just the essential boot images without running a full ROM installation.
* **In Action:** Drag and drop either a `payload.bin` OR a full custom ROM `.zip`. The tool intelligently extracts only `recovery.img` and `vendor_boot.img` directly from the archive and flashes them to both slots in seconds.

### 6. Flash Full Custom ROM (The Big One)
* **What it does:** Automates the complex process of installing modern A/B slot Custom ROMs.
* **In Action:** 
  1. You drag and drop the Custom ROM `.zip`.
  2. The tool uses `7-Zip` to extract the `payload.bin` file with a live percentage bar.
  3. It uses `payload-dumper-go` to selectively extract exactly what it needs: `vendor_boot.img` and `recovery.img`.
  4. It flashes those two images to both slots via Fastboot.
  5. It automatically reboots your phone into the newly installed recovery.
  6. It pauses, waiting for you to tap *Apply from ADB* on your phone screen.
  7. Once ready, it automatically triggers `adb sideload` to install the full ROM OS.
  8. Finally, it cleans up all the temporary extracted files to save your hard drive space.

### 7. Sideload Any .zip
* **What it does:** Pushes modular flashable zips (GApps, Magisk/KernelSU, custom Kernels) to your device.
* **In Action:** While your phone is in Recovery mode (Apply from ADB), drag and drop the zip file into the terminal, and it executes the sideload command.

### 8-10. Fastboot Wiping (Miscellaneous)
* **Erase FRP (8):** Executes `fastboot erase frp` to wipe the Factory Reset Protection partition.
* **Erase Metadata (9):** Executes `fastboot erase metadata` to clear encryption states.
* **Erase Userdata (10):** Executes `fastboot erase userdata` to completely format your internal storage (essential when clean-flashing a new ROM).

### 11. Mi Unlock Tool (Python)
* **What it does:** Bypasses the official Xiaomi unlock app restrictions using the open-source community tool.
* **In Action:** The script checks your PC for Python. If found, it uses `pip` to pull the latest official branch of [offici5l/MiUnlockTool](https://github.com/offici5l/MiUnlockTool) directly from GitHub and launches the GUI interface.

---

## ⚠️ Disclaimer
**Use at your own risk.** Flashing custom firmware, modifying system partitions, and unlocking the bootloader will void your warranty and can potentially brick your device. The creator of this script is not responsible for broken devices, lost data, or thermonuclear war. Always back up your data before wiping `userdata` or flashing a new ROM.

---

## 🤝 Credits
* [Google](https://developer.android.com/studio/releases/platform-tools) for the official ADB and Fastboot Platform Tools.
* [ssut](https://github.com/ssut/payload-dumper-go) for the incredibly fast `payload-dumper-go` engine.
* [offici5l](https://github.com/offici5l/MiUnlockTool) for the Python-based Mi Unlock Tool.
