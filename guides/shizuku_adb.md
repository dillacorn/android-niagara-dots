# Shizuku / ADB

Shell access for optional Android configuration. No root required.

## Shizuku on the phone (Android 11+)

1. Install [Shizuku](https://shizuku.rikka.app/).
2. Enable **Developer options** (Samsung: **Settings > About phone > Software information > Build number**, tap seven times).
3. Enable **USB debugging** and **Wireless debugging**, then connect to trusted Wi-Fi.
4. In Shizuku choose **Pairing**; under **Wireless debugging**, choose **Pair device with pairing code** and enter the code in Shizuku.
5. Tap **Start via Wireless debugging**. Check that Shizuku says **Running**.

Shizuku must be restarted after each reboot.

### Terminal commands (rish)

In Shizuku, follow **Use Shizuku in terminal apps** to set up `rish` in a terminal such as Termux. Check shell privileges:

```sh
rish -c 'id'
```

Expected with ADB startup: `uid=2000(shell)`. Stop if Shizuku is not running or identity differs.

## ADB from a computer

Install [Android SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools), enable **USB debugging**, connect by USB and approve the phone's prompt.

Check the target:

```sh
adb devices -l
adb shell getprop ro.product.model
```

Proceed only when the intended device is listed as `device` and the model matches. If multiple devices are connected, target one explicitly with `adb -s SERIAL shell ...` or disconnect the others.

For a package-level example with verification and rollback, see [Samsung Customization Service](samsung_customization_service.md).

Do not enable unsecured legacy ADB TCP. Revoke unneeded debugging authorizations after use.

Sources: [Shizuku setup](https://shizuku.rikka.app/guide/setup/) · [ADB](https://developer.android.com/tools/adb)
