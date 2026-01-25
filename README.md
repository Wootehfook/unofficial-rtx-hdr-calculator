# Unofficial RTX HDR Calculator

A simple, open-source web tool to calculate the optimal **Middle Grey** (Paper White) and **Contrast** settings for the NVIDIA RTX HDR overlay based on your monitor's peak brightness.

**Live Demo** https://wootehfook.github.io/unofficial-rtx-hdr-calculator/

## 🎯 Purpose

NVIDIA's RTX HDR filter uses specific sliders (Middle Grey, Contrast, Saturation) that can be confusing to calibrate. This calculator uses industry-standard math (**ITU-R BT.2408**) to determine the mathematically correct settings for your specific display, ensuring you preserve dynamic range without crushing blacks or blowing out highlights.

## ✨ Features

* **Reference Mode:** Caps Paper White at 203 nits (per ITU standards) to maximize dynamic range on high-end displays.
* **Uncapped Mode:** A "bright room" mode that scales brightness linearly for easier viewing in sunlit environments.
* **Live Updates:** Real-time calculation as you type or adjust settings.
* **Windows 11 Guide:** Includes critical setup tips for Windows 11 (25H2) to prevent double-tone-mapping conflicts.
* **Privacy Focused:** Runs 100% client-side. No user data is stored or transmitted.

## 🚀 Usage

1. Download `index.html` or visit the live demo.
2. Enter your monitor's **Peak Brightness** (e.g., 1000 nits).
3. Select your calculation mode (Reference vs. Uncapped).
4.Copy the resulting values into the NVIDIA App Overlay (`Alt+Z` -> Game Filter -> RTX HDR).

## ⚠️ Important: Windows 11 Configuration

To ensure RTX HDR works correctly without a "washed out" look, you must prevent conflicts with Windows' native features:

* **Disable Auto HDR:** `Settings > System > Display > HDR > Auto HDR [OFF]`
* **Disable ACM:** `Settings > System > Display > Advanced Display > Automatically manage color [OFF]`
* **Note:** The Windows "SDR Content Brightness" slider **does not** affect RTX HDR. If it does, RTX HDR is not active.

## 👏 Credits & Attribution

This tool was built based on the research and mathematical analysis provided by the community.

* **Original Research:** [RTX HDR Paper White & Gamma Reference Settings](https://www.reddit.com/r/nvidia/comments/1b03yfg/rtx_hdr_paper_white_gamma_reference_settings/) by **u/defet_** on r/nvidia.
* **Standards:** Calculations align with **Report ITU-R BT.2408-8 (11/2024)** regarding HDR reference white levels.

## 🤖 AI-Generated Content Notice

This website and calculator were built with the assistance of AI tools. While efforts have been made to ensure accuracy, **please verify calculations and settings independently** before applying them to your RTX HDR settings. The mathematical formulas used are based on industry standards, but edge cases or unusual display configurations may produce unexpected results.

## ⚖️ Legal Disclaimer

**Unofficial Project.** This software is a fan-made tool and is **not** affiliated with, endorsed by, or connected to NVIDIA Corporation.

* "NVIDIA", "GeForce", and "RTX" are trademarks and/or registered trademarks of NVIDIA Corporation.
* All calculations are provided "as is" for educational and calibration purposes.
