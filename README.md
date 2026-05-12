# 📱 Poco F7 (ONYX) Essential Tool

![Poco F7 Essential Tool Banner](poster.png)

An all-in-one, fully automated Windows & Linux utility designed to completely simplify device management, boot image extraction, and custom ROM flashing for the **Poco F7 (Codename: ONYX)**. 

Built with a sleek, mathematically centered terminal UI, this tool eliminates the need to manually type tedious command-line instructions. Just drag, drop, and flash.

## ✨ Key Features
* **Zero Setup Required:** Automatically downloads the latest Google Platform Tools (ADB/Fastboot), `7-Zip`, and `payload-dumper-go` the first time you run it.
* **Smart UI:** Automatically resizes your terminal window to the perfect dimensions and features flawless, single-line extraction progress bars without terminal spam.
* **Drag-and-Drop Interface:** No need to move files to specific folders or type long file paths. Just drag your `.zip` or `.img` directly into the tool.
* **Automated ROM Flashing:** Automatically extracts `payload.bin` (with a live progress percentage), dumps the required boot images, flashes them, and initiates an ADB sideload in one seamless sequence.
* **Holy Trinity Dumper:** Intelligently extracts only `boot`, `recovery`, and `vendor_boot` directly out of a full ROM zip without keeping the massive unpacked files.
* **Integrated Bootloader Unlocking:** Features direct integration with the community Python-based Mi Unlock Tool.

---

## ⚙️ Prerequisites
Before using this tool, ensure you have:
1. A Windows or Linux PC.
2. An unlocked bootloader (required for flashing images and ROMs).
3. **USB Debugging** enabled in your phone's Developer Options.
4. Proper Xiaomi/Android USB drivers installed (Windows) or `udev` rules configured (Linux).
5. **[Python 3](https://www.python.org/downloads/)** installed (Only required if you plan to use the *Mi Unlock Tool* feature).

---

## 🚀 How to Use
1. Download the script (`.bat` for Windows or `.sh` for Linux) to your PC.
2. *(Linux only)*: Make the script executable by running `chmod +x Poco_F7_Essential_Tool.sh`.
3. Run the tool. On the first launch, wait a few seconds while it downloads the required background engines (ADB, Fastboot, Payload Dumper).
4. Connect your phone via USB.
5. Type the number of the action you want to perform and press **Enter**.

---

## 🛠️ Feature Breakdown: What the Tool Does in Action

### 1-3. Power & Reboot Management
Easily bounce between device states without touching your phone's physical buttons.
* **Reboot to System:** Sends commands via both ADB and Fastboot to boot the phone normally.
* **Reboot to Bootloader:** Reboots an active device into Fastboot/Bootloader mode.
* **Reboot to Recovery:** Reboots a Fastboot-connected device straight into Recovery mode.

### 4-6. Individual Image Flashers
Quickly flash specific partitions via Fastboot by dragging and dropping the `.img` file.
* **[4] Flash Boot Image:** Flashes to `boot_ab` (Great for patching custom kernels or Magisk).
* **[5] Flash Recovery Image:** Flashes to `recovery_ab` (Install TWRP, OrangeFox, PBRP).
* **[6] Flash Vendor_Boot Image:** Flashes to `vendor_boot_ab`.

### 7. Extract Boot, Recovery, Vendor_boot
* **What it does:** Extracts only the essential booting images from a massive payload file.
* **In Action:** Drag and drop either a `payload.bin` OR a full custom ROM `.zip`. The tool intelligently unpacks the archive, dumps exactly `boot.img`, `recovery.img`, and `vendor_boot.img` into a dedicated folder, and deletes the leftover gigabytes of junk to save your hard drive.

### 8. Clean Flash Full Custom ROM (The Big One)
* **What it does:** Automates the complex process of installing modern A/B slot Custom ROMs.
* **In Action:** 
  1. You drag and drop the Custom ROM `.zip`.
  2. The tool uses `7-Zip` to extract the `payload.bin` file with a live percentage bar.
  3. It extracts exactly what it needs: `vendor_boot.img` and `recovery.img`.
  4. It flashes those two images to both slots via Fastboot.
  5. It automatically reboots your phone into the newly installed recovery.
  6. It pauses, waiting for you to tap *Apply from ADB* on your phone screen.
  7. Once ready, it automatically triggers `adb sideload` to clean install the full ROM OS.

### 9. Sideload Any .zip
* **What it does:** Pushes modular flashable zips to your device via ADB.
* **In Action:** While your phone is in Recovery mode (Apply from ADB), drag and drop your zip file. Use this for **Dirty Flashing ROM updates**, installing GApps, Custom Kernels, or Magisk.

### 10-12. Fastboot Wiping (Miscellaneous)
* **Erase FRP (10):** Executes `fastboot erase frp` to wipe the Factory Reset Protection partition.
* **Erase Metadata (11):** Executes `fastboot erase metadata` to clear encryption states.
* **Erase Userdata (12):** Executes `fastboot erase userdata` to completely format your internal storage.

### 13. Mi Unlock Tool (Python)
* **What it does:** Bypasses the official Xiaomi unlock app restrictions using the open-source community tool.
* **In Action:** The script checks your PC for Python. If found, it natively installs the latest official branch of [offici5l/MiUnlockTool](https://github.com/offici5l/MiUnlockTool) and launches the GUI interface.

---

## ⚠️ Disclaimer
**Use at your own risk.** Flashing custom firmware, modifying system partitions, and unlocking the bootloader will void your warranty and can potentially brick your device. The creator of this script is not responsible for broken devices, lost data, or thermonuclear war. Always back up your data before wiping `userdata` or flashing a new ROM.

---

## 🤝 Credits
* [Google](https://developer.android.com/studio/releases/platform-tools) for the official ADB and Fastboot Platform Tools.
* [ssut](https://github.com/ssut/payload-dumper-go) for the incredibly fast `payload-dumper-go` engine.
* [offici5l](https://github.com/offici5l/MiUnlockTool) for the Python-based Mi Unlock Tool.
