# Changelog

All notable changes to the **Poco F7 (ONYX) Essential Tool** will be documented in this file.

## [1.2.1] - 2026-05-12

### Fixed
- **Empty Input Crash:** Fixed a fatal syntax error in the Windows Batch script where pressing 'Enter' without dragging a file (or dropping a file with trailing spaces) would instantly crash and close the window. Implemented bulletproof input validation (`if "!INPUT!"==""`) and delayed expansion quote stripping across all menu options.

### Changed
- **Option 7 Workflow:** Changed Option 7 back to an automated **Extract Boot, Recovery, Vendor_Boot** tool. Dragging a ROM `.zip` or `payload.bin` now automatically extracts the "Holy Trinity" of boot images with a perfectly clean, single-line live progress bar, bypassing the need for manual partition selection.

## [1.2.0] - 2026-05-11

### Added
- **Flash Boot Image (Option 4):** Added dedicated 1-click flashing for `boot.img` files to active slots.
- **Flash Vendor_Boot Image (Option 6):** Added dedicated 1-click flashing for `vendor_boot.img` files to active slots.
- **Auto-Resize Window Function:** The script now automatically forces the terminal window to a clean 120-column by 45-line size upon launching to fit the expanded 14-option menu without vertical scrollbars.
  - On Windows: Uses `mode con`.
  - On Linux: Uses native ANSI escape sequences (`\e[8;45;120t`).

### Changed
- **Menu Expansion:** The main menu has been expanded to 14 total options.
- **Option Renames:** 
  - Renamed "Flash Custom Recovery Only" to **Flash Recovery Image (.img)**.
  - Renamed the Sideload option to **Sideload Any .zip (Dirty Flash ROM, GApps, Kernel, Magisk)** with mathematical word-wrap to ensure the UI borders remain pixel-perfect.
  - Renamed Full Custom ROM option to **Clean Flash Full Custom ROM**.

### Fixed
- **Progress Bar Line Spam:** Fixed an annoying bug where `payload-dumper-go` would spam the terminal with hundreds of new lines during extraction. The tool now temporarily disables terminal line-wrapping during extraction and forces a single-thread (`-c 1`) worker, keeping the live progress bar completely flat and clean on a single line.
- **Mathematical Border Alignment:** Recalculated spacing across all menus and sub-menus to ensure the right-side border never breaks, regardless of text length.

## [1.1.1] - 2026-05-11

### Fixed
- **UI Alignment Bug:** Fixed a visual bug where the right-side border in the main menu was misaligned due to batch escape characters (`^`) being counted in the invisible string length. 

## [1.1.0] - 2026-05-11

### Added
- **Extract & Flash Support:** Added drag-and-drop support for both `payload.bin` files AND full custom ROM `.zip` files for direct boot image flashing.

### Changed
- Expanded the Main Menu options to accommodate new flashing targets.

## [1.0.0] - 2026-05-11

### Added
- Initial Release.
- Zero-Setup Environment (Auto-downloads Platform Tools, payload-dumper-go, and 7-Zip).
- Sleek Terminal UI with 65-character fixed-width box drawing.
- Advanced Power Menu (System, Bootloader, Recovery).
- Automated Custom ROM Installer with live extraction progress.
- Universal Sideload Utility.
- 1-click Fastboot wiping for FRP, Metadata, and Userdata.
- Integrated Python-based Mi Unlock Tool.
