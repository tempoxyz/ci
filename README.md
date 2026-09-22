# tempoxyz/ci

Common GHA CI workflows.

Use `.github/workflows/deny.yml` for Cargo dependency checks. It configures
Secure Runner, installs a pinned, checksum-verified cargo-deny binary, and runs
the checks on the protected host. Callers must grant `contents: read` and
`id-token: write` to the reusable-workflow job.

The `rust-toolchain` input defaults to `nightly`. The `deny-flags` input defaults
to `--all-features` and accepts whitespace-separated cargo-deny flags (for
example, `--all-features --locked`). Set these inputs on the reusable call
instead of duplicating the installation and check steps in each repository.
Wrappers can also forward `runner` (default `ubuntu-latest`) and
`timeout-minutes` (default `30`) to preserve their existing job configuration.
