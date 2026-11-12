# AGENTS.md

Guidance for agents editing `android-niagara-dots`.

## Scope

This is a **short Android settings and configuration guide**, not an inventory of the maintainer's phone.

- Primary coverage: Niagara Launcher, optional Omalauncher/Omagara, Samsung One UI cleanup, ADB/Shizuku, and useful optional configuration/automation tools.
- Keep GrapheneOS-specific differences in `grapheneos_setup.md`; never apply Samsung package commands to GrapheneOS.
- Name an application only when explaining a concrete configuration tool or its necessary companion. Do not document personal browsers, media, shopping, messaging, VPN catalogs, or which apps the maintainer uses.
- Do not record personal usage, accounts, device identifiers, networks, or private settings. One concise current-launcher note is allowed; usage does not imply a recommendation. Examples must otherwise be generic.
- Keep `niagra_backup/` binary files untouched unless specifically asked. Existing backup content has not been privacy-audited.

## Documentation style

- Keep `README.md` a small link index; detailed steps belong in focused pages.
- Format user-facing directions as **Setting path → value** or **Check → command → verify → restore**. No prose introductions, changelog/release-note narration, personal rationale, or explanatory paragraphs unless necessary to use the procedure safely.
- Explain **what to change**, not the maintainer's current settings or why a preference is popular.
- Label optional/advanced steps. Include a concise check and reversal wherever a change can affect system behavior.
- Do not repeat warnings, introductions, sources, or the same setup procedure across pages. Link to the owner page instead.
- Preserve useful compatibility warnings and safeguards when trimming prose; brevity never overrides correctness.
- No speculative performance, security, privacy, or battery benefits. Verify changing menu paths, app behavior and commands against current vendor or project documentation.

## Page ownership

- `guides/omalauncher_omagara.md`: launcher installation, Omagara face, home-page setting and known limitations.
- `samsung_cleanup.md`: quick One UI switches and links to advanced procedures.
- `grapheneos_setup.md`: only GrapheneOS-specific setup differences.
- `guides/shizuku_adb.md`: debugging, pairing, identity checks and terminal setup.
- `guides/samsung_customization_service.md`: optional, reversible Samsung package-level change.
- `automation/`: focused configuration recipes, not application recommendations.

## Safety

- Inspect the exact repository, branch, current file, and applicable instructions before editing.
- For ADB: verify the intended device; if multiple devices are attached, require a serial-specific command. For Shizuku: verify `rish` shell identity.
- Check exact package existence before modification. Never propose generic debloat lists or disabling security, updates, camera or essential services without evidence and an explicit request.
- Keep read-only checks separate from state-changing commands. Pair each reversible change with its restore command.
- Never assume a user has applied a documented option or that static documentation checks prove phone behavior.

## Delivery and validation

- Editing and validating does **not** authorize merging or pushing to `main`. Do so only when explicitly requested.
- Preserve unrelated files and branch work. Do not rewrite Git history or delete backups.
- Re-read edited files. Validate local links/anchors, fenced command blocks, command targets, removed references, and any changed procedures before delivery.
- Report branch, changed files, checks passed/failed, and any device-level verification still needed.
