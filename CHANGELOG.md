# Changelog

All notable changes to the **Poco F7 (ONYX) Essential Tool** will be documented in this file.

## [1.1.0] - 2026-05-11

### Fixed
- **UI Alignment Bug:** Fixed a visual bug where the right-side border in the main menu and Option 5 sub-menu was misaligned. This was caused by the batch escape character (`^`) used in "Extract ^& Flash" being counted in the invisible string length. Recalculated spacing ensures 100% perfect mathematical alignment.

### Added
- **Extract & Flash Recovery + Vendor_Boot (Option 5):** Added a new dedicated feature to instantly extract and flash boot-critical images without running the full ROM flashing sequence.
  - Supports drag-and-drop for both `payload.bin` files AND full custom ROM `.zip` files.
  - Leverages `payload-dumper-go`'s hidden ability to directly extract only `recovery.img` and `vendor_boot.img` straight from the archive, bypassing the need to unpack the entire payload first.
  - Automatically flashes both images to the active A/B slots (`fastboot flash recovery_ab` and `fastboot flash vendor_boot_ab`).
  - Auto-cleans up the extracted images immediately after flashing.

### Changed
- Reordered the Main Menu to accommodate the new feature (Full Custom ROM flashing is now Option 6, and all subsequent options shifted down by one, expanding the menu to 12 total options).

## [1.0.0] - 2026-05-11

### Added
- **Zero-Setup Environment:** Script automatically checks for and downloads required dependencies on first launch (Google Platform Tools, `payload-dumper-go`, and `7z`).
- **Sleek Terminal UI:** Mathematically aligned, 65-character fixed-width interface with UTF-8 box drawing and ANSI color coding.
- **Advanced Power Menu:** 1-click commands to reboot the device to System, Bootloader (Fastboot), or Recovery from ADB/Fastboot states.
- **Custom Recovery Flasher:** Drag-and-drop support for flashing custom recovery `.img` files (TWRP, OrangeFox, PBRP) directly to the `recovery_ab` slot.
- **Automated Custom ROM Installer:** 
  - Drag-and-drop `.zip` support.
  - Automatically extracts `payload.bin` using `7z` with a live, real-time percentage progress bar.
  - Automatically dumps `vendor_boot` and `recovery` images using `payload-dumper-go`.
  - Flashes boot images to both A/B slots.
  - Auto-reboots the device to recovery and initiates an ADB Sideload sequence for the OS.
  - Auto-cleans up extracted payload files to save disk space.
- **Universal Sideload Utility:** Drag-and-drop support to easily sideload modular `.zip` files (GApps, Magisk, KernelSU, Custom Kernels).
- **Partition Wiping Utilities:** 1-click fastboot commands to safely erase `frp`, `metadata`, and `userdata` partitions.
- **Integrated Mi Unlock Tool:** 
  - Direct integration with the community Python-based Xiaomi bootloader unlocker.
  - Automatically verifies Python 3 installation.
  - Auto-installs/updates required dependencies directly from the official GitHub repository via `pip`.

### Changed
- **Menu Optimization:** Removed background polling for device connection status to completely eliminate terminal screen flickering. The main menu now loads instantly with zero lag.
- **Streamlined Workflow:** Removed the redundant Stock Fastboot ROM flasher to focus the tool specifically on Custom ROM and Recovery management. 
- **Script Execution:** Suppressed initial ADB daemon startup logs (`adb start-server`) to prevent UI breakage upon opening the tool.
