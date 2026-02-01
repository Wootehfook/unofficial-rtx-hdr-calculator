# Pull Request: Fix NPI Contrast Offset (v1.5.0)

## 🎯 Summary
This PR fixes a critical calculation error in the NVIDIA Profile Inspector (NPI) hex values for the Contrast setting. NPI uses a base-100 offset system that wasn't previously accounted for, causing users who copied hex values directly into Profile Inspector to get incorrect results.

## 🔧 Changes Made

### Code Changes
- **index.html (Line 611)**: Updated contrast hex calculation to add +100 offset
  ```javascript
  // Before: toHex(contrast)
  // After: toHex(contrast + 100)
  ```
- Added explanatory comment documenting NPI's base-100 system

### Documentation Updates
- **CHANGELOG.md**: Added v1.5.0 release entry documenting the fix
- **README.md**: Added new "NVIDIA Profile Inspector" subsection under Usage
  - Explains the automatic offset handling
  - Provides example (25% contrast = 125 in NPI = 0x0000007D)
  - Clarifies users can copy/paste hex values directly
- **index.html**: Updated version tag from v1.4.3 to v1.5.0

## 🐛 Problem Being Fixed

### Before
When users copied hex values for Contrast from the calculator into NPI:
- Overlay shows: 25% contrast
- Calculator output: `0x00000019` (decimal 25)
- **Problem**: NPI interprets this as -75% contrast (base-100 system: 25 - 100 = -75)

### After
With this fix:
- Overlay shows: 25% contrast  
- Calculator output: `0x0000007D` (decimal 125)
- **Result**: NPI correctly interprets as 25% contrast (base-100 system: 125 - 100 = 25)

## 🧪 Testing Recommendations
1. Enter peak brightness (e.g., 1000 nits)
2. Verify hex contrast values:
   - Gamma 2.0 (0% contrast) → `0x00000064` (100 in hex)
   - Gamma 2.2 (25% contrast) → `0x0000007D` (125 in hex)
   - Gamma 2.4 (50% contrast) → `0x00000096` (150 in hex)
3. Confirm other hex values (Peak, Middle Grey, Saturation) remain unchanged

## 📊 Impact
- **Affected Users**: Anyone using NVIDIA Profile Inspector instead of the in-game overlay
- **Severity**: High (incorrect values produce wrong visual results)
- **Breaking Changes**: None (this is a bug fix, not a feature change)

## ✅ Checklist
- [x] Code updated with +100 offset
- [x] CHANGELOG.md updated with v1.5.0 entry
- [x] README.md updated with NPI guidance
- [x] Version tag updated in index.html
- [x] Commit message follows conventional format
- [x] No breaking changes introduced

## 🔗 Related Issues
Fixes incorrect contrast values when using NVIDIA Profile Inspector hex input.
