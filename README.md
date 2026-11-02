# android-niagara-dots

Short, practical guides for Android settings, Samsung cleanup, Niagara Launcher, and useful configuration utilities. Application guides appear only when a tool changes or automates device behavior.

## Start with Niagara

1. Install [Niagara Launcher](https://play.google.com/store/apps/details?id=bitpit.launcher) and set it as the default home app.
2. Configure the layout. Optionally restore a locally reviewed Niagara `.nlb` backup, then check favorites, widgets and shortcuts.

## Choose the operating system

- **Samsung One UI:** [Silence promotional notifications, adjust optional settings and disable unwanted services](samsung_cleanup.md).
- **GrapheneOS:** [Set up device-specific behavior and check compatibility](grapheneos_setup.md). Do not apply Samsung-only package commands.

## Optional configuration tools

- [Caffeine: keep the display awake](automation/caffeine.md) — Quick Settings toggle, timeouts and Samsung compatibility.
- [Tailscale Auto Rules: automatic network switching](automation/tailscale_auto_rules.md) — Connection behavior based on network rules, including requirements for its parent Tailscale app.

## Advanced setup

- [Shizuku and ADB](guides/shizuku_adb.md) — Pair a device, run a shell safely, and check the target before changing Android settings.

## Niagara backups

Existing `.nlb` files are optional launcher restore points. Review backups locally for personal data, accounts, app references, widgets and shortcuts before publishing replacements.
