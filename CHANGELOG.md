# Changelog

All notable changes to the **Unofficial RTX HDR Calculator** project will be documented in this file.

## [v1.4.2] - 2026-01-30
### Added
- **Source Documentation:** Added direct PDF links to ITU-R BT.2100-3 (02/2025) alongside existing BT.2408-8 reference.
- **Standards Clarity:** Updated sources section in README and index.html to explicitly document which standard supports each calibration mode (Cinema vs. Vivid).

## [v1.4.1] - 2026-01-30
### Fixed
- **NPI Labels:** Updated Nvidia Profile Inspector field names to match the common "TrueHDR" XML configuration (e.g., `TrueHDR - Peak Brightness`).
- **Hex IDs:** Added specific Hex IDs (e.g., `0x10D17E79`) to the UI to assist users without custom XML definitions.

## [v1.4.0] - 2026-01-30
### Added
- **Clipboard Support:** Added one-click "Copy" icon buttons next to all NPI Hex values.
- **Visual Feedback:** Icons momentarily change to green checkmarks upon successful copy.
- **Legacy Fallback:** Added fallback copy method for non-secure contexts (local file usage).

## [v1.3.1] - 2026-01-30
### Changed
- **UI Redesign:** Moved Nvidia Profile Inspector (NPI) values from a hidden toggle to a distinct, always-visible secondary card for better discoverability.

## [v1.3.0] - 2026-01-30
### Added
- **Nvidia Profile Inspector Support:** Added automatic conversion of standard slider values into 32-bit unsigned Hexadecimal strings (e.g., `0xFFFFFFE7`) for power users configuring RTX HDR via Inspector.

## [v1.2.2] - 2026-01-30
### Verified
- **Standards Compliance:** Audited math against **ITU-R BT.2100-2** and **BT.2408-8**. Verified the 75% HLG constant (`0.26496`) aligns with the 1000-nit reference anchor.

## [v1.2.0] - 2026-01-30
### Added
- **Hybrid Calculation Engine:** Introduced a mode selector allowing users to choose between two industry standards:
  - **Cinema / Reference (BT.2408):** Caps Paper White at 203 nits (Best for dim rooms/eye safety).
  - **Vivid / Daylight (BT.2100 HLG):** Scales Paper White using System Gamma (Best for bright rooms/high impact).
- **Tooltips:** Added dynamic explanatory text explaining the visual difference between the two modes.

## [v1.1.0] - 2026-01-30
### Changed
- **Calculation Logic:** Replaced legacy linear interpolation (100->203 nits) with the mathematically accurate **HLG System Gamma** formula (`1.2 + 0.42 * Log10(Lw/1000)`) for high-brightness displays.

## [v1.0.0] - 2026-01-30
### Initial Release
- **Core Calculator:** Implemented "Middle Grey" and "Contrast" logic based on r/nvidia community research.
- **Live Updates:** Removed "Calculate" button in favor of real-time input listeners.
- **Safety:** Added legal disclaimers and "Unofficial" branding to avoid trademark infringement.
- **Windows 11 Guide:** Added critical setup tips for Windows 11 25H2 (disabling ACM and Auto HDR).