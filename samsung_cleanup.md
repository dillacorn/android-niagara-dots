# Samsung One UI cleanup

Optional, reversible steps for reducing unwanted Samsung notifications, background integrations and interruptions on a Samsung Galaxy phone. **Preserve normal camera, communications, security, update and gaming features.** Menu labels may differ by One UI version.

## 1. Remove promotional notifications

1. Open **Settings > Notifications > Advanced settings**.
2. Enable **Manage notification categories for each app**, if available.
3. Open **Settings > Apps > Galaxy Store > Notifications > Notification categories** (or open Galaxy Store's notification settings).
4. Turn off **Offers and events** and other promotional categories. **Keep app-update and important service notifications enabled.**
5. Repeat for **Samsung Members** or other Samsung apps that send unwanted marketing notifications.

## Optional: review Samsung diagnostic data collection

1. Open **Settings > Security and privacy > More privacy settings > Send diagnostic data**.
2. Read the description and linked privacy notice for the device's software version.
3. Choose whether to leave optional diagnostic sharing **on or off**. It is not required for this cleanup.

Samsung says diagnostic data can help improve Galaxy services, reliability and support. **Do not assume this data is fully anonymous.** Samsung's broader US privacy policy also describes collecting device identifiers, diagnostic logs and usage details; it does not establish that all data sent through this toggle is anonymous. Sharing a pseudonymous identifier is not the same as sharing anonymized data. This guide does not prescribe a setting or disable general advertising and analytics collection.

## 2. Turn off nearby device scanning

1. Open **Settings > Connections > More connection settings**.
2. Turn off **Nearby device scanning**.

This reduces unsolicited nearby-device discovery prompts. Manual Bluetooth pairing remains available.

## 3. Stop unattended maintenance restarts

1. Open **Settings > Device care > Auto optimization > Auto restart**.
2. Turn off **Restart when needed** and **Restart on schedule** where available.

System and security updates can still require a reboot. Do not disable updates to prevent restarts.

## 4. Disable optional Samsung Customization Service (advanced, reversible)

If you don't use Samsung's **Customization Service**, first disable it from Samsung Account privacy settings if that option is available. For a package-level alternative, use **Termux with a running Shizuku server**. This affects personalization functionality; it does **not** bypass required Samsung Account terms.

Run:

```bash
rish -c 'pm disable-user --user 0 com.samsung.android.rubin.app'
rish -c 'pm list packages -d --user 0' | grep -Fx 'package:com.samsung.android.rubin.app'
```

Expected: the command reports `disabled-user`, and the last line prints the exact package.

To restore the service:

```bash
rish -c 'pm enable --user 0 com.samsung.android.rubin.app'
```

If Shizuku reports **Server is not running**, start it from the Shizuku app first. Non-root startup may need Wi-Fi, especially after rebooting. Do not enable unencrypted legacy ADB TCP mode just for this guide.

## Preserve features and background connectivity

- Leave **AR Zone**, **AR Doodle**, camera components, **Good Lock**, Galaxy Store, Samsung Account, security services, and system updates enabled unless a specific unwanted behavior has been identified.
- Avoid disabling apps solely because they appear on a debloat list. Installed or enabled packages are not automatically running or consuming meaningful battery.
- Review **Settings > Battery > Background usage limits**, but avoid blanket deep-sleep rules for functions that depend on continuous background operation.
- Leave performance profiles unchanged unless testing demonstrates a benefit. Do not assume disabling features improves performance.
- If policy prompts continue, capture the actual dialog and identify its source before disabling additional system packages.

## Sources

- [Samsung: Security and privacy settings](https://www.samsung.com/us/support/answer/ANS10002544/)
- [Samsung: Diagnostic data setting and its purpose](https://www.samsung.com/us/support/answer/ANS10002544/)
- [Samsung: Mobile terms and diagnostic data](https://www.samsung.com/us/support/legal/LGL10000282/)
- [Samsung: US privacy policy](https://www.samsung.com/us/account/privacy-policy/)
- [Android: ADB package manager commands](https://developer.android.com/tools/adb)
