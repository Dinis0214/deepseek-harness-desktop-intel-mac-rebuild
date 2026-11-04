# DeepSeek Harness Desktop for Intel macOS (Unofficial)

[![Build Intel macOS desktop release](https://github.com/Dinis0214/deepseek-harness-desktop-intel-mac-rebuild/actions/workflows/build-intel-macos-release.yml/badge.svg)](https://github.com/Dinis0214/deepseek-harness-desktop-intel-mac-rebuild/actions/workflows/build-intel-macos-release.yml)

Community-built Intel (`x86_64`) macOS desktop packages for [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness).

> **Disclaimer**: This repository is not officially affiliated with DeepSeek AI. Packages are built from official stable Release tags, but are neither signed nor notarized by Apple.

---

## 📥 Download

Download the newest DMG or ZIP from the **[Latest Release](../../releases/latest)**.

Each release includes:
- `deepseek-harness-<version>-mac-x64.dmg`
- `deepseek-harness-<version>-mac-x64.zip`
- `SHA256SUMS.txt`

---

## 💻 Compatibility

- **Architecture**: Intel Mac (`x86_64`)
- **Supported macOS**: macOS 12 (Monterey) or later
- Automated builds run on GitHub's `macos-15-intel` virtual machines.

---

## 🛡️ Gatekeeper Notice

These community packages are **not signed or notarized by Apple**, so macOS may block the first launch.

1. Right-click `DeepSeek Harness.app`, choose **Open**, and confirm the prompt.
2. Alternatively, run the following command in Terminal:
   ```bash
   xattr -dr com.apple.quarantine "/Applications/DeepSeek Harness.app"
   ```

Verify the download against `SHA256SUMS.txt` before launching.

---

## 🔧 Stability Enhancements Included

To provide dependable long-term execution on Intel macOS environments, this rebuild automatically incorporates non-intrusive runtime stability guards:

1. **Plugin Ecosystem Compatibility**: Restores legacy icon aliases and `settingsScope` backward compatibility to prevent third-party plugins from triggering React runtime errors.
2. **Lifecycle & Process Protection**: Guards RPC host registrations against lifecycle race conditions and prevents orphaned background services on exit.
3. **GPU & Memory Guard**: Throttles background occluded rendering to prevent excessive memory/CPU footprint on Intel graphics.
4. **Isolated Updater**: Disables official auto-updating channels to protect your installation from accidental architecture overwrites.
5. **Session Continuity**: Backward-compatible normalization for multi-agent legacy session descriptors.

---

## ⚙️ How Releases Are Built

The GitHub Actions workflow checks every six hours for the latest upstream [DeepSeek Harness Release](https://github.com/deepseek-ai/deepseek-harness/releases). When a new version is detected, it:

1. Checks out the exact official Release tag from `deepseek-ai/deepseek-harness`.
2. Applies the non-intrusive stability patches.
3. Builds the Electron desktop app for `x86_64` on a native Intel macOS runner.
4. Validates that all packaged executables are verified `x86_64` binaries.
5. Verifies the DMG image with `hdiutil verify` and publishes versioned release assets with SHA-256 checksums.

---

## 📜 License

DeepSeek Harness is distributed under the [MIT License](LICENSE).
