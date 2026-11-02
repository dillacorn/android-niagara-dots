# Shizuku and ADB: quick setup

Use these tools only for specific Android configuration steps that need shell-level access. They are **not** required for Niagara Launcher or the other optional utilities.

## Shizuku without a computer (Android 11+)

1. Install [Shizuku](https://shizuku.rikka.app/).
2. On Samsung, open **Settings > About phone > Software information** and tap **Build number** seven times to enable Developer options. For other Android devices, locate **Build number** in device settings.
3. Open **Developer options**, enable **USB debugging** and **Wireless debugging**, and connect to a trusted Wi-Fi network.
4. In Shizuku, select **Pairing**. In **Wireless debugging**, choose **Pair device with pairing code** and enter that code using Shizuku's pairing notification.
5. Back in Shizuku, select **Start via Wireless debugging**. Confirm that Shizuku reports the service **running**.

Pairing normally persists, but **Shizuku must be started again after a reboot** without root. Do not enable old, unencrypted ADB-over-TCP for this procedure.

### Run commands on the phone

1. Install a terminal app such as [Termux](https://termux.dev/), if needed for the documented command.
2. In Shizuku, open **Use Shizuku in terminal apps**, and follow its **rish** setup instructions.
3. In the terminal, verify the shell identity before attempting package-level changes:

```sh
rish -c 'id'
```

Expected: a shell identity (typically `uid=2000(shell)` when Shizuku was started through ADB). If the command fails or Shizuku is not running, stop and correct the setup before issuing changes.

## ADB from a computer (alternative)

1. Install Google's [SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools), and enable **USB debugging** under the phone's Developer options.
2. Connect the intended device by USB, unlock it, and approve its debugging prompt.
3. Check the connected device **before** running any command:

```sh
adb devices -l
adb shell getprop ro.product.model
```

Expected: the intended device is listed as `device`, and the model matches the device you mean to configure. When multiple devices are connected, use `adb -s SERIAL shell ...` to target the exact device.

## Package commands: safe pattern

Check the **exact** package name and whether it is present first. Follow a device-specific guide for the package to change, and keep its matching restore command. As an example, the [optional Samsung Customization Service procedure](../samsung_cleanup.md#4-disable-optional-samsung-customization-service-advanced-reversible) includes the specific package and reversal.

Do not disable arbitrary system packages from generic debloat lists. Avoid granting debugging access to unknown computers or wireless networks. Revoke unnecessary ADB authorizations when finished.

## References

- [Official Shizuku setup](https://shizuku.rikka.app/guide/setup/)
- [Shizuku rish terminal instructions](https://github.com/RikkaApps/Shizuku-API/tree/master/rish)
- [Android Debug Bridge documentation](https://developer.android.com/tools/adb)
