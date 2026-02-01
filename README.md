# Unofficial RTX HDR Calculator

A simple, open-source web tool to calculate the optimal **Middle Grey** (Paper White) and **Contrast** settings for the NVIDIA RTX HDR overlay based on your monitor's peak brightness.

**GitHub Repository:** [Wootehfook/unofficial-rtx-hdr-calculator](https://github.com/Wootehfook/unofficial-rtx-hdr-calculator)

**Support:** [Buy me a coffee](https://ko-fi.com/wtfook)

**Live Demo:** https://wootehfook.github.io/unofficial-rtx-hdr-calculator/

## 🎯 Purpose

NVIDIA's RTX HDR filter uses specific sliders (Middle Grey, Contrast, Saturation) that can be confusing to calibrate. This calculator uses industry-standard math (**ITU-R BT.2408**) to determine the mathematically correct settings for your specific display, ensuring you preserve dynamic range without crushing blacks or blowing out highlights.

## ✨ Features

* **Calibration Style:** Choose **Cinema / Reference (BT.2408)** or **Vivid / Daylight (BT.2100 HLG)** based on room lighting.
* **Target Gamma:** Pick Gamma 2.0, 2.2, or 2.4 for your preferred shadow depth.
* **Game Overlay Settings:** Outputs Peak Brightness, Middle Grey, Contrast, and Saturation values.
* **Profile Inspector (HEX):** Shows 32-bit values for NVIDIA Profile Inspector entry.
* **Live Updates:** Real-time calculation as you type or adjust settings.
* **Windows 11 Guide:** Includes critical setup tips for Windows 11 (25H2) to prevent double-tone-mapping conflicts.
* **Privacy Focused:** Runs 100% client-side. No user data is stored or transmitted.

## 🚀 Usage

1. Download `index.html` or visit the live demo.
2. Enter your monitor's **Peak Brightness** (e.g., 1000 nits).
3. Select your **Calibration Style** and **Target Gamma**.
4. Copy the resulting values into the NVIDIA App Overlay (`Alt+Z` -> Game Filter -> RTX HDR).

### NVIDIA Profile Inspector

For users who prefer to configure RTX HDR via NVIDIA Profile Inspector (NPI), the calculator provides pre-converted **32-bit unsigned hexadecimal values**. These values can be copied directly using the clipboard buttons next to each field.

**Important:** The hex values automatically account for NPI's internal +100 offset on the Contrast setting. For example, if the overlay shows 25% contrast, NPI requires a value of 125 (0x0000007D). The calculator handles this conversion automatically—simply copy and paste the displayed hex values.

## ⚠️ Important: Windows 11 Configuration

To ensure RTX HDR works correctly without a "washed out" look, you must prevent conflicts with Windows' native features:

* **Disable Auto HDR:** `Settings > System > Display > HDR > Auto HDR [OFF]`
* **Disable ACM:** `Settings > System > Display > Advanced Display > Automatically manage color [OFF]`
* **Note:** The Windows "SDR Content Brightness" slider **does not** affect RTX HDR. If it does, RTX HDR is not active.

## 📚 Sources

This project is based on community research and established standards. Sources are linked below for transparency and verification.

* **Community Research:** [RTX HDR Paper White & Gamma Reference Settings](https://www.reddit.com/r/nvidia/comments/1b03yfg/rtx_hdr_paper_white_gamma_reference_settings/) by **u/defet_** (r/nvidia).
* **Standards:** 
  * [Report ITU-R BT.2408-8 (11/2024): Guidance for operational practices in HDR television production](https://www.itu.int/dms_pub/itu-r/opb/rep/R-REP-BT.2408-8-2024-PDF-E.pdf) — Determines the "Reference" Paper White level (203 nits) and interpolation logic for lower brightness displays (Cinema mode).
  * [Recommendation ITU-R BT.2100-3 (02/2025): Image parameter values for high dynamic range television for use in production and international programme exchange](https://www.itu.int/dms_pubrec/itu-r/rec/bt/R-REC-BT.2100-3-202502-I!!PDF-E.pdf) — Contains the HLG System Gamma formula (Table 5, Note 2) which scales brightness based on display peak luminance (Vivid mode). *(Note: If unavailable in your region, the previous standard BT.2100-2 (2018) contains the identical gamma formula.)*

## 🤖 AI-Generated Content Notice

This website and calculator were built with the assistance of AI tools. While efforts have been made to ensure accuracy, **please verify calculations and settings independently** before applying them to your RTX HDR settings. The mathematical formulas used are based on industry standards, but edge cases or unusual display configurations may produce unexpected results.

## ⚖️ Legal Disclaimer

**Unofficial Project.** This software is a fan-made tool and is **not** affiliated with, endorsed by, or connected to NVIDIA Corporation.

* "NVIDIA", "GeForce", and "RTX" are trademarks and/or registered trademarks of NVIDIA Corporation.
* All calculations are provided "as is" for educational and calibration purposes.
