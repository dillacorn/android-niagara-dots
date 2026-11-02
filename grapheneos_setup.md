# GrapheneOS setup

Use this guide **only on a supported device running GrapheneOS**. The shared launcher settings are in [README.md](README.md). This page contains only differences from Samsung One UI; there is no Samsung debloating to reproduce here.

## Install and set up

1. Confirm that your device is supported using the [official GrapheneOS installation guide](https://grapheneos.org/install/). Follow the official installer instructions for the exact device; do not use Samsung firmware or ADB package-disabling instructions.
2. After initial setup, follow the [shared Android setup](README.md#shared-android-setup) to configure Niagara as your default launcher.
3. If a required function depends on Google Play services, review [GrapheneOS's sandboxed Google Play guidance](https://grapheneos.org/usage#sandboxed-google-play). Configure sandboxed Google Play only when needed for that function.
4. Test device functions that matter to the setup, such as notifications, calls, messaging, and NFC. Where relevant, verify compatibility requirements before retiring a previous device.
5. Restore a locally reviewed Niagara backup only if desired; manually verify widgets and shortcuts.

## What to skip

- Do **not** apply [Samsung One UI cleanup](samsung_cleanup.md) settings or Samsung package names.
- Do **not** disable GrapheneOS security controls just to recreate Samsung-specific customization or Shizuku workflows.
- Do not copy packages or device settings blindly from an earlier Samsung device.

Consult the [official GrapheneOS usage guide](https://grapheneos.org/usage/) for current device-specific behavior and app compatibility. Add extra steps here only after they are actually needed and verified.
