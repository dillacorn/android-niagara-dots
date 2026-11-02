# Shizuku / ADB

## Shizuku (Android 11+)

1. Install [Shizuku](https://shizuku.rikka.app/).
2. Enable **Developer options** (Samsung: **About phone > Software information > Build number**, tap 7 times).
3. Enable **USB debugging** and **Wireless debugging**; connect to trusted Wi-Fi.
4. **Shizuku > Pairing** → **Wireless debugging > Pair device with pairing code** → enter code in Shizuku.
5. **Shizuku > Start via Wireless debugging** → Confirm **Running**.

Restart Shizuku after rebooting.

### Terminal (rish)

Follow **Shizuku > Use Shizuku in terminal apps** for setup in Termux. Check:

```sh
rish -c 'id'
```

Expected: `uid=2000(shell)`. Stop if different.

## ADB (computer)

Install [Android Platform Tools](https://developer.android.com/tools/releases/platform-tools), enable USB debugging, connect by USB and approve the prompt.

**Check the device before any changes:**

```sh
adb devices -l
adb shell getprop ro.product.model
```

Confirm exactly one intended device listed as `device` and the correct model. Disconnect others or use `adb -s SERIAL shell ...` for every command.

Example: [Samsung Customization Service disable / restore](samsung_customization_service.md).

Do not enable unsecured ADB TCP. Revoke unneeded debugging authorizations.

References: [Shizuku](https://shizuku.rikka.app/guide/setup/) · [ADB](https://developer.android.com/tools/adb)
