# SharpTS Homebrew tap

This tap is being prepared for the SharpTS TypeScript interpreter and compiler on Apple Silicon
Macs. **No installable casks have been published yet.**

The planned casks are:

| Cask | Distribution |
| --- | --- |
| `sharpts` | Self-contained managed CLI with the full feature set. |
| `sharpts-native` | Native AOT CLI with a closed .NET interop catalog. |

Both will expose the `sharpts` command and conflict with each other. Intel Macs are unsupported.
Basic CLI use needs no separate .NET installation; running emitted managed DLLs requires a
compatible .NET host. Native AOT excludes arbitrary DLL/NuGet references, `--verify`, `--gen-decl`
and compiled `child_process.fork`; those operations require the managed SKU. See the upstream
[Native AOT contract](https://github.com/nickna/SharpTS/blob/main/docs/native-aot.md).

## Publication status

Initial casks await a selected stable SharpTS release with Developer ID signed and notarized
macOS ARM64 archives. Both exact released executables must pass online Gatekeeper assessment,
and both casks must pass actual audit, installation, runtime, conflict and uninstall checks.
Installation and switching commands will be added only after that acceptance. A second signed
release is needed to verify upgrades. No Gatekeeper workaround is part of installation, and a
bare CLI executable has no stapled offline-install ticket.

The `Cask CI` workflow explicitly reports pending acceptance while this repository has no casks.
It rejects a partial cask pair or removal of a previously published pair. Once both real casks
are present, its `Apple Silicon (sharpts)` and `Apple Silicon (sharpts-native)` jobs run the
upstream prepared acceptance steps. A bootstrap skip is not a passed installation or signing
check. `Tap syntax` retains Homebrew's tap syntax maintenance; Dependabot maintains pinned
GitHub Actions. Formula bottle publication/autobumping is not used for these casks.

Future stable updates are prepared in the upstream
[Homebrew workflow](https://github.com/nickna/SharpTS/blob/main/.github/workflows/homebrew.yml).
Enable that path only after initial casks pass and both Apple Silicon jobs are required checks.
It validates the published signed archives, opens an update PR with restricted tap credentials,
and waits for required checks before requesting auto-merge.

Follow [#1357](https://github.com/nickna/SharpTS/issues/1357) for progress and the upstream
[distribution guide](https://github.com/nickna/SharpTS/blob/main/docs/homebrew-distribution.md)
for release, credential and validation procedures. Report CLI defects to
[SharpTS](https://github.com/nickna/SharpTS/issues) and cask installation problems to this tap.
