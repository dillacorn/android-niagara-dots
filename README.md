# android-niagara-dots

Repeatable Android setup directions using Niagara Launcher. Follow the shared steps first, then the instructions for the device's operating system. Samsung One UI has additional manual cleanup steps; GrapheneOS needs only the steps that differ from standard Android.

## Shared Android setup

1. Install [Niagara Launcher](https://play.google.com/store/apps/details?id=bitpit.launcher), set it as the default home app, and use its standard minimal layout.
2. Install [Firefox](https://play.google.com/store/apps/details?id=org.mozilla.firefox) and set it as the default browser.
3. Set up only the applications needed for the device's intended use. Follow the [app setup checks](apps_installed_list.md) rather than reinstalling an entire app list from an older phone.
4. Restore a **locally reviewed** Niagara `.nlb` backup only if needed. Verify favorites, widgets and shortcuts after restoring.

## Device-specific directions

| Operating system | Follow these directions |
| --- | --- |
| **Samsung One UI** | Follow [Samsung One UI cleanup](samsung_cleanup.md) for optional notification, nearby-device and restart controls, plus a reversible Shizuku command for an unwanted Samsung service. |
| **GrapheneOS** | Follow [GrapheneOS setup](grapheneos_setup.md) for platform-specific setup and compatibility checks. Do **not** apply Samsung-only package commands or settings. |

Keep shared Android steps here. Document platform-specific steps only when they actually differ. Describe what to do and how to verify it, not the state of one person's phone.

## Niagara backups

- Existing `.nlb` backups are optional restore files, not application recommendations or a record of a device's expected configuration.
- Review backups locally for personal data, installed-app references, widgets, shortcuts and account details before publishing updated copies in this public repository.
