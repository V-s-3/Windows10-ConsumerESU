# Windows 10 Consumer ESU Activation

One-click activation of **Extended Security Updates (ESU)** for Windows 10 22H2.

After October 14, 2025, Windows 10 no longer receives security updates. This script enrolls your PC into the **Consumer ESU** program, extending security update support until **October 2028**.

## Features

- **Single file** - one `.cmd` file, no dependencies
- **Auto-elevation** - automatically requests administrator privileges
- **Region bypass** - works in embargoed regions (Russia, etc.) by temporarily switching GeoId to US
- **Step-by-step output** - shows progress at each stage
- **Auto-restore** - restores original region settings after enrollment

## Requirements

- **Windows 10 22H2** (build 19045)
- **KB5061087** (June 2025) or later update installed - this provides `ConsumerESUMgr.dll`
- **Microsoft Account** signed into Windows (for token acquisition)
- **Internet connection** (for enrollment with Microsoft servers)

## Usage

1. Download `Activate_ESU.cmd`
2. Double-click to run (UAC prompt will appear)
3. Wait for enrollment to complete
4. Done - your PC will receive ESU security updates

## How it works

1. **Region check** - detects embargoed regions and temporarily bypasses (GeoId -> US)
2. **Feature activation** - enables Consumer ESU feature flag via Windows Feature Configuration API
3. **Eligibility check** - evaluates ESU eligibility via `ConsumerESUMgr.dll`
4. **Token acquisition** - obtains MSA authorization token (user -> store -> local fallback)
5. **Enrollment** - registers the device for Consumer ESU via `EnrollUsingBackupV1`
6. **Verification** - re-checks eligibility status to confirm enrollment
7. **Region restore** - restores original region settings

## ESU Timeline

| Period | Coverage |
|--------|----------|
| Year 1 | October 2025 - October 2026 |
| Year 2 | October 2026 - October 2027 |
| Year 3 | October 2027 - October 2028 |

## Credits

Based on [ConsumerESU](https://github.com/abbodi1406/ConsumerESU) by abbodi1406.

Modified with region bypass for embargoed countries and single-file packaging.

## License

MIT License - see original project for details.
