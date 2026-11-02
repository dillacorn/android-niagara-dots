# Samsung One UI cleanup

Optional settings. Menu paths vary by One UI version.

## Promotional notifications

1. **Settings > Notifications > Advanced settings:** enable **Manage notification categories for each app**.
2. **Settings > Apps > Galaxy Store > Notifications > Notification categories:** turn off **Offers and events**. Keep update/service alerts.
3. Repeat for **Samsung Members** if it sends unwanted promotions.

## Nearby scanning

**Settings > Connections > More connection settings:** turn off **Nearby device scanning** if unused. Manual Bluetooth pairing remains available.

## Automatic restarts

**Settings > Device care > Auto optimization > Auto restart:** turn off **Restart when needed** and **Restart on schedule**, if present. Continue installing system updates.

## Animations (optional)

1. **Settings > Accessibility > Vision enhancements:** enable **Reduce animations**.
2. **Settings > Developer options:** set **Window animation scale**, **Transition animation scale**, and **Animator duration scale** to **Animation off**.

To reveal Developer options, tap **Build number** seven times under **About phone > Software information**. Undo: turn off **Reduce animations** and restore the scales to **1x**. If One UI 7 Camera has problems, try disabling **Reduce animations**.

## Diagnostic sharing (optional)

**Settings > Security and privacy > More privacy settings > Send diagnostic data:** review and choose on/off. Diagnostic information may contain identifiers and logs; do not assume it is anonymous.

## Customization Service (advanced, optional)

For unwanted Samsung personalization, first check Samsung Account privacy settings. Alternatively, follow the [reversible Shizuku/ADB procedure](guides/samsung_customization_service.md).

## Preserve system functions

- Do not disable camera, security, updates, or other system packages based only on generic debloat lists.
- Under **Settings > Battery > Background usage limits**, avoid sleeping services that must stay connected.

## Sources

- [Samsung: Reduce animations and Camera compatibility](https://www.samsung.com/us/support/troubleshoot/TSG10005233/)
- [Samsung: Privacy policy](https://www.samsung.com/us/account/privacy-policy/)
