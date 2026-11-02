# Samsung Customization Service (optional)

Disable Samsung's optional personalization service only if unwanted. Prefer turning it off in **Samsung Account privacy settings**, where available. Package-level disabling may affect personalization; it does not bypass required account terms.

First follow [Shizuku / ADB setup](shizuku_adb.md). Choose **one** method.

## On the phone: Shizuku + rish

Check Shizuku identity and package existence:

```sh
rish -c 'id'
rish -c 'pm path com.samsung.android.rubin.app'
```

Continue only when Shizuku reports the shell user and the package path exists. Disable and verify:

```sh
rish -c 'pm disable-user --user 0 com.samsung.android.rubin.app'
rish -c 'pm list packages -d --user 0' | grep -Fx 'package:com.samsung.android.rubin.app'
```

Restore:

```sh
rish -c 'pm enable --user 0 com.samsung.android.rubin.app'
```

## On a computer: ADB

Verify **one intended device** is connected and the package exists:

```sh
adb devices -l
adb shell getprop ro.product.model
adb shell pm path com.samsung.android.rubin.app
```

Proceed only if the model is correct and a package path is printed. If multiple devices are attached, disconnect the others or use `adb -s SERIAL shell ...` for **every** command.

Disable and verify:

```sh
adb shell pm disable-user --user 0 com.samsung.android.rubin.app
adb shell pm list packages -d --user 0 com.samsung.android.rubin.app
```

Restore:

```sh
adb shell pm enable --user 0 com.samsung.android.rubin.app
```

Expected after disabling: `disabled-user` and the exact package in the disabled list. Recheck the target device before restoring.

Reference: [Android package manager via ADB](https://developer.android.com/tools/adb).
