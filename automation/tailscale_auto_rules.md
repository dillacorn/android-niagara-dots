# Tailscale Auto Rules network automation

Optional Android network automation. Include this tool for its specific configuration behavior, not as part of a personal app catalog.

[Tailscale Auto Rules](https://play.google.com/store/apps/details?id=fr.vbrosseau.tailscaleautorules) controls the connection state of the [official Tailscale Android client](https://tailscale.com/docs/install/android) based on the connected network. It does not replace the Tailscale client.

## Configure

1. Install and sign in to the official Tailscale Android client.
2. Install Tailscale Auto Rules from the [Play Store](https://play.google.com/store/apps/details?id=fr.vbrosseau.tailscaleautorules).
3. Open Tailscale Auto Rules and complete its onboarding. Allow notifications for the foreground automation service. If using Wi-Fi network names in rules, grant the requested location permission; Android requires it to read Wi-Fi SSIDs.
4. In the app's **Networks** screen, add networks that need an explicit rule. Set the tunnel **off** for a trusted network only when that network already provides the required connectivity; set it **on** where the tunnel is needed. Unlisted Wi-Fi networks follow the app's automatic behavior.
5. Review the **mobile network** rule and the option to learn manual Tailscale changes. Set these according to the desired behavior, rather than assuming every device needs the same rules.
6. Keep automation enabled when using these rules. On Samsung One UI, review **Settings > Battery > Background usage limits** and avoid putting the automation service into a sleeping state that prevents timely network detection.

## Verify

1. Connect to a Wi-Fi network with a configured rule. Confirm that the Tailscale tunnel reaches the expected state.
2. Switch to a different Wi-Fi network or mobile data, and confirm the rule changes the tunnel as expected.
3. Check the app's status and history for the rule behind each change. A successfully issued command does not necessarily mean the tunnel is already connected, so verify the actual connection state.
4. Reboot the device and confirm that automation resumes. Android may require opening the app from a startup reminder before its location-dependent foreground service can run again.

**Important:** A persistent notification is part of the foreground service needed for continuous network monitoring. Do not disable required notifications or force-stop the service while expecting continuous automation.

## References

- [Tailscale Auto Rules source and documentation](https://github.com/c4software/tailscale-auto-rules)
- [Tailscale Android setup](https://tailscale.com/docs/install/android)
