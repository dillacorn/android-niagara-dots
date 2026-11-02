# Caffeine: keep the screen awake

[Install Caffeine](https://play.google.com/store/apps/details?id=moe.zhs.caffeine) to add a temporary screen-awake toggle to Quick Settings.

## Configure

1. Edit **Quick Settings** and add the **Caffeine** tile.
2. In Caffeine, choose a fixed **Timeout** or **Variable** (tap the tile repeatedly to adjust).
3. Optional: enable **Deactivate automatically** to turn it off when the device locks.

### Samsung One UI

On Android 12+, Samsung needs **Compatibility mode** and a battery-optimization exemption.

- Allow **Change system settings** for Caffeine under **Settings > Apps > Special access**.
- Use Caffeine's **Ignore battery optimization** option (or set its battery usage to **Unrestricted**).

## Check / undo

Activate the tile and confirm the screen stays awake past the normal timeout. Turn it off and confirm the normal timeout returns. If the timeout stays changed, reset **Settings > Display > Screen timeout**. Avoid force-stopping Caffeine while Compatibility mode is active.

Long screen-on periods increase power use and OLED wear.

Sources: [Caffeine configuration](https://lab.zhs.moe/caffeine/guide/config/) · [Samsung compatibility](https://lab.zhs.moe/caffeine/guide/device-compatibility/) · [Troubleshooting](https://lab.zhs.moe/caffeine/guide/troubleshooting/)
