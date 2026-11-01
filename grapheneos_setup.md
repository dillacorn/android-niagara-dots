# GrapheneOS setup

Use this guide **only on a supported device running GrapheneOS**. The shared launcher and app steps are in [README.md](README.md). This page contains only differences from Samsung One UI; there is no Samsung debloating to reproduce here.

## Install and set up

1. Confirm that your device is supported using the [official GrapheneOS installation guide](https://grapheneos.org/install/). Follow the official installer instructions for the exact device; do not use Samsung firmware or ADB package-disabling instructions.
2. After initial setup, follow the [shared Android setup](README.md#shared-android-setup): Niagara Launcher, Firefox and essential apps. Configure Niagara as your default launcher.
3. Install any apps that do not need Google Play services without adding Play services solely for convenience. For apps that **do** need Play services, review [GrapheneOS's sandboxed Google Play guidance](https://grapheneos.org/usage#sandboxed-google-play). Install it from the GrapheneOS App Store if required.
4. Test notifications, banking/authentication, calling/messaging, NFC/payments, VPN and other essential apps individually before retiring the previous phone. Some apps can impose their own device-integrity or Google certification requirements.
5. Restore a locally reviewed Niagara backup only if desired; manually verify widgets and shortcuts.

## What to skip

- Do **not** apply [Samsung One UI cleanup](samsung_cleanup.md) settings or Samsung package names.
- Do **not** disable GrapheneOS security controls just to recreate Samsung-specific customization or Shizuku workflows.
- Do not copy all apps, packages or settings blindly from an earlier Samsung device.

Consult the [official GrapheneOS usage guide](https://grapheneos.org/usage/) for current device-specific behavior and app compatibility. Add extra steps here only after they are actually needed and verified.
