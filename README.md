# SharpTS Homebrew tap

This tap is being prepared for the SharpTS TypeScript interpreter and compiler on Apple Silicon Macs.

The planned casks are `sharpts` for the self-contained managed CLI and `sharpts-native` for the Native AOT CLI. Both will expose the `sharpts` command and will be mutually exclusive.

Initial cask publication awaits a stable SharpTS release with Developer ID signed and notarized macOS ARM64 archives and successful installation checks. Casks and installation commands will be added after those release gates pass. Intel macOS is outside this tap's supported architecture.

Follow the [Homebrew distribution issue](https://github.com/nickna/SharpTS/issues/1357) for publication and validation progress. Report compiler and runtime defects to [SharpTS](https://github.com/nickna/SharpTS/issues).
