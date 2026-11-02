# Samsung Customization Service (optional)

Prefer Samsung Account privacy settings if available. Package disabling affects personalization.

Requires [Shizuku / ADB setup](shizuku_adb.md). Choose one method.

## Shizuku + rish (phone)

**Check** — continue only if `uid=2000(shell)` and a package path appears:

```sh
rish -c 'id'
rish -c 'pm path com.samsung.android.rubin.app'
```

**Disable / verify:**

```sh
rish -c 'pm disable-user --user 0 com.samsung.android.rubin.app'
rish -c 'pm list packages -d --user 0' | grep -Fx 'package:com.samsung.android.rubin.app'
```

**Restore:**

```sh
rish -c 'pm enable --user 0 com.samsung.android.rubin.app'
```

## ADB (computer)

**Check** — confirm exactly one intended device and the package path. Disconnect other devices first.

```sh
adb devices -l
adb shell getprop ro.product.model
adb shell pm path com.samsung.android.rubin.app
```

**Disable / verify:**

```sh
adb shell pm disable-user --user 0 com.samsung.android.rubin.app
adb shell pm list packages -d --user 0 com.samsung.android.rubin.app
```

**Restore:**

```sh
adb shell pm enable --user 0 com.samsung.android.rubin.app
```

Expected after disabling: `disabled-user` and the exact package in the disabled list.
