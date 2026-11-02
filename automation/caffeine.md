# Caffeine: keep the screen awake

Optional Quick Settings utility for temporarily preventing the display from turning off. It is not a general app-installation recommendation.

## Set up

1. Install [Caffeine - Keep Screen On](https://play.google.com/store/apps/details?id=moe.zhs.caffeine).
2. Pull down **Quick Settings**, choose **Edit**, and add the **Caffeine** tile.
3. Open Caffeine settings. Choose a **Timeout** for timed use, or **Variable** to change the duration by tapping the tile repeatedly.
4. Optionally enable **Deactivate automatically** so locking the phone turns Caffeine off.

### Samsung One UI

On Samsung devices running Android 12+, the developer says Caffeine uses **Compatibility mode**, which needs permission to modify system settings.

1. Open **Settings > Apps > Special access > Change system settings** and allow **Caffeine** if its compatibility mode requires it.
2. Open **Settings > Apps > Caffeine > Battery** and select **Unrestricted** (or use the app's **Ignore battery optimization** option). The developer identifies a battery-optimization exemption as necessary for Samsung and Android 14+.
3. Return to the Caffeine tile and confirm that it works. Menu paths can differ by One UI version.

## Verify and restore

- Turn on Caffeine from Quick Settings and wait longer than the phone's usual screen timeout. The screen should remain awake.
- Turn it off or lock the device if **Deactivate automatically** is enabled. Verify the usual timeout returns.
- If the screen stays awake after Caffeine is disabled, restore the preferred timeout under **Settings > Display > Screen timeout**. Do not force-stop Caffeine while compatibility mode is active; the developer warns that this can leave the modified timeout in place.

Keeping the screen on indefinitely uses power and may increase burn-in risk on OLED displays. Use the shortest useful duration.

## Sources

- [Caffeine: getting started](https://lab.zhs.moe/caffeine/guide/)
- [Caffeine: configuration options](https://lab.zhs.moe/caffeine/guide/config/)
- [Caffeine: device compatibility](https://lab.zhs.moe/caffeine/guide/device-compatibility/)
- [Caffeine: troubleshooting](https://lab.zhs.moe/caffeine/guide/troubleshooting/)
