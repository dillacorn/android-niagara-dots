# Tailscale Auto Rules: network automation

Automatically control the official Tailscale tunnel by network. Requires [Tailscale for Android](https://tailscale.com/docs/install/android) and [Tailscale Auto Rules](https://play.google.com/store/apps/details?id=fr.vbrosseau.tailscaleautorules).

## Configure

1. Sign in to Tailscale; install and open Auto Rules.
2. Complete onboarding. Allow notifications; grant location permission if using Wi-Fi names (SSIDs).
3. Under **Networks**, set explicit rules: tunnel **off** on trusted Wi-Fi only if connectivity is available without it; **on** where needed. Unlisted Wi-Fi follows automatic behavior.
4. Review the **mobile network** rule and optional learning of manual tunnel changes.
5. On Samsung, avoid battery sleep restrictions that interrupt the automation service.

## Check

Switch between a configured Wi-Fi network and mobile data. Verify the **actual tunnel state** in Tailscale and review Auto Rules' history. After reboot, open the app if Android shows a startup reminder.

A persistent notification is required while continuous network monitoring is active.

Reference: [Tailscale Auto Rules documentation](https://github.com/c4software/tailscale-auto-rules).
