# Pull Request: Fix NPI Saturation Offset (v1.6.0)

## 🎯 Summary

This PR fixes a critical calculation error in the NVIDIA Profile Inspector (NPI) hex values for both the Contrast and Saturation settings. NPI uses a base-100 offset system for these fields that wasn't fully implemented, causing users who copied hex values directly into Profile Inspector to get incorrect results for Saturation.

## 🔧 Changes Made

### Code Changes

- **index.html**: Implemented `toNvidiaHex()` function with +100 offset logic and clamping for Contrast and Saturation
- **index.html**: Added `clamp()` helper to ensure input values stay within -100 to 100 range
- **index.html**: Updated Saturation hex calculation to use the offset conversion (matching Contrast behavior)
- **index.html**: Moved inline CSS styles to external classes for better maintainability

  ```javascript
  // Before: toHex(saturation)  // Would output 0xFFFFFFE7 for -25
  // After: toNvidiaHex(saturation, true)  // Outputs 0x0000004B (75 in decimal)
  ```

### Documentation Updates

- **CHANGELOG.md**: Added v1.6.0 release entry documenting the Saturation offset fix and automated testing
- **README.md**: Updated NPI section to clarify that both Contrast and Saturation use the +100 offset, with examples for both
- **PR_SUMMARY.md**: Updated to reflect Saturation offset fix alongside existing Contrast documentation
- **index.html**: Updated version tag from v1.5.1 to v1.6.0

### Testing

- **Playwright Suite**: Added comprehensive automated tests validating:
  - Hex conversion with +100 offset for Saturation and Contrast
  - Cinema vs Vivid calculation differences
  - Edge cases (low/high peak brightness, empty inputs)
  - Gamma 2.0, 2.2, and 2.4 validation

## 🐛 Problem Being Fixed

### Before

When users copied hex values for Saturation from the calculator into NPI:

- Overlay shows: -25% saturation
- Calculator output: `0xFFFFFFE7` (signed two's complement for -25)
- **Problem**: NPI doesn't use standard two's complement; it expects base-100 offset (75 in this case)

### After

With this fix:

- Overlay shows: -25% saturation
- Calculator output: `0x0000004B` (decimal 75)
- **Result**: NPI correctly interprets as -25% saturation (base-100 system: 75 - 100 = -25)

## 🧪 Testing Recommendations

- Enter peak brightness (e.g., 1000 nits)
- Verify hex values:
- Saturation -25% → `0x0000004B` (75 in hex)
- Contrast 0% (Gamma 2.0) → `0x00000064` (100 in hex)
- Contrast 25% (Gamma 2.2) → `0x0000007D` (125 in hex)
- Contrast 50% (Gamma 2.4) → `0x00000096` (150 in hex)
- Cinema vs Vivid calculations differ at mid-range brightness (e.g., 600 nits)
- Empty peak brightness disables results area

## 📊 Impact

- **Affected Users**: Anyone using NVIDIA Profile Inspector instead of the in-game overlay
- **Severity**: High (incorrect Saturation values produce wrong visual results)
- **Breaking Changes**: None (this is a bug fix completing the v1.5.0 offset implementation)

## ✅ Checklist

- [x] Code updated with +100 offset for Saturation
- [x] Added input clamping to prevent invalid hex outputs
- [x] CHANGELOG.md updated with v1.6.0 entry
- [x] README.md updated with Saturation offset guidance
- [x] Version tag updated in index.html
- [x] Playwright test suite validates all hex conversions
- [x] All markdown and HTML lint issues resolved
- [x] No breaking changes introduced

## 🔗 Related Issues

Fixes incorrect Saturation values when using NVIDIA Profile Inspector hex input. Completes the NPI offset implementation started in v1.5.0.
