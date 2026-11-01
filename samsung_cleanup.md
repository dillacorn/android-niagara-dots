# Samsung One UI cleanup: Galaxy S24

Research notes, 2026-11-01. This is a **temporary Samsung maintenance guide**, not the planned GrapheneOS configuration. No automatic debloat script is provided.

**Optimization principle:** Preserve functional features. Investigate unwanted consent prompts, optional advertising/personalization, and measured background activity before disabling packages. Package presence or enabled status alone is not evidence of resource consumption. Prefer reversible settings changes; avoid generic mass-debloat lists.

## Selected optional One UI settings (completed; user-confirmed)

**Completed and verified on the Galaxy S24 by the user on 2026-11-01.** These are user-reported confirmations, not independent device-state checks or changes made through GitHub. Exact menu labels can vary by One UI release.

| Setting | Status | Notes |
| --- | --- | --- |
| Galaxy Store / Samsung promotional notifications | **Completed (user-confirmed)** | Promotional categories disabled; important app and security update notifications preserved |
| Optional Samsung diagnostic data | **Completed (user-confirmed)** | Optional diagnostic sharing turned off via Security and privacy settings |
| Nearby device scanning | **Completed (user-confirmed)** | Nearby device scanning turned off; regular Bluetooth functionality retained |
| Light performance profile | **Do not change** | Preserve current CPU/performance behavior |
| Background usage limits | **Accept existing controls; no blanket restrictions** | Protect Tailscale, ntfy, and communications requiring background connectivity; only tune after reviewing current state |
| Auto restart | **Completed (user-confirmed)** | Unattended auto-restart options turned off; system/security update restarts may still occur. Helps preserve the running Shizuku session |

The first, second, third and sixth rows were applied and verified by the user. The Light performance profile and background usage limits were intentionally left unchanged; this is not authorization to deep-sleep specific applications.

## Observed device state

- Device: Galaxy S24 (`SM-S921U`). Exact One UI build/version not audited here.
- Launcher: Niagara (`bitpit.launcher`); preserve its largely stock configuration.
- Termux + Shizuku `rish` works as Android `shell` (UID 2000), including one confirmed mobile-data-only session. After a reboot or Shizuku service stop, starting Shizuku may require Wi-Fi.
- Package inventory: 672 total, of which 179 were reported by `pm list packages -3`. These counts include nonessential system components and are **not** the list of apps to document as essentials.
- **Confirmed modified:** `com.samsung.android.rubin.app` (Customization Service) is `disabled-user` for Android user 0, verified by `pm list packages -d --user 0` on 2026-11-01.
- **Confirmed enabled on 2026-11-01 via `pm list packages -e --user 0`:** `com.facebook.appmanager`. The first Shizuku query reported `Server is not running`; a subsequent query succeeded.
- **AR feature history, 2026-11-01:** `com.samsung.android.ardrawing` and `com.samsung.android.arzone` were temporarily disabled and passed `pm list packages -d --user 0` checks. They were subsequently **re-enabled** and each passed `pm list packages -e --user 0` checks. This preserves functionality; no performance benefit from disabling them was established.
- **Not established:** Whether disabling Customization Service stops recurring Samsung consent/policy dialogs; actual dialogs have not been identified. An enabled package is not proof of a continuously running service.

## Candidate packages and consequences

| Package | Status in supplied inventory | Purpose / cost of disabling | Priority |
| --- | --- | --- | --- |
| `com.samsung.android.rubin.app` | **Confirmed disabled** | Samsung personalization; leave disabled if optional personalized features are unwanted. This is not a mandatory agreement bypass. | Done |
| `com.samsung.android.arzone` | **Confirmed enabled (restored)** | AR Zone hub; keep for AR camera extras, avatars and stickers. | Preserve |
| `com.samsung.android.ardrawing` | **Confirmed enabled (restored)** | AR Doodle; keep for AR camera drawing effects. | Preserve |
| `com.facebook.appmanager` | **Enabled, confirmed** | Meta's preinstalled update helper; disabling can stop that update channel. Normal Play Store updates generally remain available. | Optional trial after confirming preferred update path |
| `com.samsung.android.app.spage` | Not listed among enabled candidates; disabled/absent unknown | Samsung News / former Samsung Free feed; may stop its feed content. Niagara is the active launcher. | Check presence first |
| `com.samsung.android.app.tips` | Not listed among enabled candidates; disabled/absent unknown | Samsung Tips; may generate feature suggestions after setup or updates. | Check presence first; relevant to unwanted prompts |
| `com.samsung.android.voc` | Not listed among enabled candidates; disabled/absent unknown | Samsung Members; loses community, diagnostics and error-report UI. | Check presence first |
| `com.samsung.android.game.gamehome` | Not listed among enabled candidates; disabled/absent unknown | Gaming Hub; affects game library and may affect Game Booster. | Only if unused |

`com.samsung.android.goodlock` and modules such as `com.samsung.android.app.homestar`, `com.samsung.systemui.navillera`, `com.samsung.systemui.lockstar`, `com.samsung.android.app.goodcatch`, `com.samsung.android.qstuner`, and `com.samsung.android.app.cameraassistant` are present. They are **not** part of the default disable list: check actual use before changing them. Bixby/translation language packs are also user-feature dependent.

## Preserve

Keep `com.osp.app.signin` (Samsung Account), `com.samsung.android.mobileservice` (Samsung Experience Service), and `com.sec.android.app.samsungapps` (Galaxy Store). These were confirmed enabled on 2026-11-01. Do not indiscriminately disable telephony/IMS/RCS, Android System UI, permission controller, Knox/Secure Folder, OTA/update, connectivity, camera providers, payment, or authentication services. In particular, arbitrary Samsung debloat lists can break camera functions, profiles, or system components.

## Read-only review on the phone

With Shizuku running, copy this into Termux to check exactly which candidates exist and whether they are enabled. No package states change.

```bash
(
    set -e
    enabled="$(mktemp)"
    disabled="$(mktemp)"
    trap 'rm -f "$enabled" "$disabled"' EXIT
    rish -c 'pm list packages -e --user 0' > "$enabled"
    rish -c 'pm list packages -d --user 0' > "$disabled"
    for pkg in \
        com.samsung.android.rubin.app \
        com.samsung.android.arzone \
        com.samsung.android.ardrawing \
        com.facebook.appmanager \
        com.samsung.android.app.spage \
        com.samsung.android.app.tips \
        com.samsung.android.voc \
        com.samsung.android.game.gamehome; do
        if grep -Fxq "package:$pkg" "$enabled"; then
            printf 'ENABLED  %s\n' "$pkg"
        elif grep -Fxq "package:$pkg" "$disabled"; then
            printf 'DISABLED %s\n' "$pkg"
        else
            printf 'NOT LISTED %s\n' "$pkg"
        fi
    done
)
```

## Change protocol (one package at a time)

1. Prefer the Samsung app's own opt-out / notification controls for marketing, consent and tips. Samsung Account terms can still require acceptance to use account services.
2. Check that a candidate is present and enabled; verify whether the corresponding feature is used.
3. Use `rish -c 'pm disable-user --user 0 PACKAGE'` only for the individually reviewed package, not as part of a broad removal list. Record the exact package and output.
4. Confirm with `rish -c 'pm list packages -d --user 0'`; test relevant UI, camera, calling, messaging, notifications and update paths after the change.
5. Roll back with `rish -c 'pm enable --user 0 PACKAGE'` if anything breaks. **Do not** use `pm uninstall`, `pm clear`, or a mass-disable script for this project.

**No performance improvement is claimed from these changes.** Prefer disabling verified unwanted personalization or promotional behavior and measuring background resource use before attempting additional changes. The AR features were restored explicitly to avoid sacrificing functionality.

## References

- [Samsung: Customization Service privacy controls](https://terms.account.samsung.com/contents/legal/us/en/customizedservicecontent.html)
- [Samsung: opt out of ads](https://www.samsung.com/uk/support/mobile-devices/how-to-remove-ads-from-a-galaxy-smartphone/)
- [Android Developers: ADB package manager commands](https://developer.android.com/tools/adb)
- [Samsung: AR Zone features](https://www.samsung.com/us/support/answer/ANS10002551/)
- [Samsung AR Zone package notes](https://mysystemapp.com/packages/com.samsung.android.arzone/)
- [AR Doodle package notes](https://mysystemapp.com/packages/com.samsung.android.ardrawing/)
- [Meta App Manager package notes](https://mysystemapp.com/packages/com.facebook.appmanager/)
- [Samsung News package notes](https://mysystemapp.com/packages/com.samsung.android.app.spage/)
- [Samsung Tips package notes](https://mysystemapp.com/packages/com.samsung.android.app.tips/)
- [Samsung Members package notes](https://mysystemapp.com/packages/com.samsung.android.voc/)
- [Example of risks from aggressive Samsung debloating](https://github.com/khlam/debloat-samsung-android)
