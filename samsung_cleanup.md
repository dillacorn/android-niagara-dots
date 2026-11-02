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

If you don't use Samsung's **Customization Service**, first turn it off from Samsung Account privacy settings if the option is available. The following package-level alternative changes personalization functionality; it does **not** bypass required Samsung Account terms.

Follow [Shizuku and ADB setup](guides/shizuku_adb.md) first. **Check the exact package and target device before any changes.** Use only one method.

**On the phone (Termux + Shizuku/rish):**

Check the package:

```sh
rish -c 'pm path com.samsung.android.rubin.app'
```

If that prints an installed package path, disable and verify:

```sh
rish -c 'pm disable-user --user 0 com.samsung.android.rubin.app'
rish -c 'pm list packages -d --user 0' | grep -Fx 'package:com.samsung.android.rubin.app'
```

**From a computer (ADB alternative):**

Check the device identity and package first:

```sh
adb devices -l
adb shell getprop ro.product.model
adb shell pm path com.samsung.android.rubin.app
```

Proceed only if the model and package match the intended target. For multiple connected devices, specify the exact serial with `adb -s SERIAL shell ...`:

```sh
adb shell pm disable-user --user 0 com.samsung.android.rubin.app
adb shell pm list packages -d --user 0 com.samsung.android.rubin.app
```

Expected after either method: `disabled-user`, and the exact package in the disabled list.

**Restore:** Use the same method used to disable the service, after checking the intended device again:

```sh
rish -c 'pm enable --user 0 com.samsung.android.rubin.app'
```

Or from a computer:

```sh
adb shell pm enable --user 0 com.samsung.android.rubin.app
```

If Shizuku reports **Server is not running**, restart it as described in the [setup guide](guides/shizuku_adb.md). Do not enable unencrypted legacy ADB TCP mode for this guide.

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
