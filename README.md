# android-niagara-dots

Minimal Niagara Launcher and Android setup instructions, with **Samsung One UI** as the current setup and **GrapheneOS** as an alternative device setup. Most steps are shared; only platform-specific changes belong in their respective guides.

## Shared Android setup

1. Install [Niagara Launcher](https://play.google.com/store/apps/details?id=bitpit.launcher), set it as the default home app, and keep its standard minimal layout.
2. Install [Firefox](https://play.google.com/store/apps/details?id=org.mozilla.firefox) and set it as the default browser.
3. Install any additional essential apps you use; avoid copying every preinstalled app or third-party package from a previous device.
4. Restore a **locally reviewed** Niagara `.nlb` backup only if needed. Check favorite apps, widgets and shortcuts after restoring.

## Choose your device setup

| Device software | Follow these directions |
| --- | --- |
| **Samsung One UI (current)** | Follow [Samsung One UI cleanup](samsung_cleanup.md) for optional notification, privacy, nearby-device and restart controls, plus an optional Shizuku command for Samsung personalization. |
| **GrapheneOS (future)** | Follow [GrapheneOS setup](grapheneos_setup.md) for the few platform-specific setup and compatibility checks. Do **not** apply Samsung-only package commands or settings. |

Only maintain a platform-specific step when it genuinely differs from the shared Android setup. Keep setup instructions practical rather than recording individual device states, preference checklists or troubleshooting history.

## Application list and backups

- [App catalog](apps_installed_list.md) is an older, **unreviewed** list. It should be reduced to essential app installation directions rather than used as an automatic migration checklist.
- Existing Niagara `.nlb` backups are retained unchanged. Review backups for sensitive data before publishing replacements in this public repository.
