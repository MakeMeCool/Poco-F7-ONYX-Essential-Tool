# Changelog

All notable changes to the **Poco F7 (ONYX) Essential Tool** will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-05-11

### Added
- **Zero-Setup Environment:** Script automatically checks for and downloads required dependencies on first launch (Google Platform Tools, `payload-dumper-go`).
- **Sleek Terminal UI:** Mathematically aligned, 65-character fixed-width interface with UTF-8 box drawing and ANSI color coding.
- **Advanced Power Menu:** 1-click commands to reboot the device to System, Bootloader (Fastboot), or Recovery from ADB/Fastboot states.
- **Custom Recovery Flasher:** Drag-and-drop support for flashing custom recovery `.img` files (TWRP, OrangeFox, PBRP) directly to the `recovery_ab` slot.
- **Automated Custom ROM Installer:** 
  - Drag-and-drop `.zip` support.
  - Automatically extracts `payload.bin` using native Windows `tar`.
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
