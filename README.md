# android-niagara-dots

Repeatable Android setup directions using Niagara Launcher. Follow the shared steps first, then the instructions for the device's operating system. Samsung One UI has additional manual cleanup steps; GrapheneOS needs only the steps that differ from standard Android.

## Shared Android setup

1. Install [Niagara Launcher](https://play.google.com/store/apps/details?id=bitpit.launcher) and set it as the default home app.
2. Configure the launcher layout and restore a **locally reviewed** Niagara `.nlb` backup only if needed. Verify favorites, widgets and shortcuts after restoring.

## Device-specific directions

| Operating system | Follow these directions |
| --- | --- |
| **Samsung One UI** | Follow [Samsung One UI cleanup](samsung_cleanup.md) for optional notification, nearby-device and restart controls, plus a reversible Shizuku command for an unwanted Samsung service. |
| **GrapheneOS** | Follow [GrapheneOS setup](grapheneos_setup.md) for platform-specific setup and compatibility checks. Do **not** apply Samsung-only package commands or settings. |

Keep shared Android settings here and platform-specific steps in their respective guides. Include named applications only when they are essential to a documented configuration or automation procedure, and document their exact role. Do not maintain a list of personal applications, browsers, VPNs or other installed software.

## Optional configuration automations

- [Tailscale Auto Rules](automation/tailscale_auto_rules.md): Configure network-dependent Tailscale tunnel behavior, permissions, and background operation. This is a targeted automation guide, not a general VPN app recommendation.

## Niagara backups

- Existing `.nlb` backups are optional restore files, not application recommendations or a record of a device's expected configuration.
- Review backups locally for personal data, installed-app references, widgets, shortcuts and account details before publishing updated copies in this public repository.
