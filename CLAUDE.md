# HyperTranslator Project Notes

## Hard rules

- This repository is release-facing only. Do not add source code, Rust project files, assets, debug output, or build directories to `main` unless the user explicitly changes the repository policy.
- `main` should track only:
  - `.github/workflows/release.yml`
  - `.gitignore`
  - `.gitmessage`
  - `CLAUDE.md`
  - `CHANGELOG.md`
  - `README.md`
  - `LICENSE`
- Do not commit `dist/`, `target/`, root release binaries, `Cargo.toml`, `Cargo.lock`, `src/`, `assets/`, or `build.rs` to `main`.
- Build complete client outputs under `dist/debug/` or `dist/release/`; do not split them into frontend/backend directories.
- Release binaries are distributed through GitHub Releases only, not through the repository Code view.
- Use Angular/Conventional Commit style for commits, e.g. `ci(release): scope notes to current version`, `docs: update README usage`, `chore(repo): track release metadata`.
- Current repository-local Git author must remain:
  - `user.name = hdewai`
  - `user.email = hdewai@proton.me`
- SSH identity/remote host controls push authentication only; commit authorship comes from `git config user.name` and `git config user.email`.

## Release version flow

1. Bump the top release entry in `CHANGELOG.md` to the new SemVer version, e.g. `## [0.1.1] - 2026-07-31`.
2. Update release links in `CHANGELOG.md`, e.g. `[0.1.1]: https://github.com/hdewai/HyperTranslator/releases/tag/v0.1.1`.
3. Update the README release badge target if it points to a concrete tag.
4. Commit and push `main`.
5. The workflow runs on `main` and creates/updates the GitHub Release for the version parsed from the top `CHANGELOG.md` entry.
6. The `main` workflow only publishes Release notes; it must not upload a binary.

## Release notes rule

- GitHub Release notes must contain only the current version section from `CHANGELOG.md`.
- Do not pass the whole `CHANGELOG.md` directly to `gh release create/edit`.
- The workflow should generate `release-notes.md` by extracting only the first `## [x.y.z]` section up to, but not including, the next `## [x.y.z]` section.
- This avoids putting old release notes such as `v0.1.0` into a newer release such as `v0.1.1`.

## Binary release flow

Use a temporary release branch only when uploading the executable asset:

1. Keep `main` clean and synchronized with `origin/main`.
2. Ensure the release binary exists locally at `dist/release/hyper-translator.exe`.
3. Ensure any installer deliverables remain under `dist/release/bundle/`.
4. Create a temporary branch named exactly for the current version:
   - `hyper-translator-vX.Y.Z`
   - Example: `hyper-translator-v0.1.1`
5. Copy the binary to `dist/release/hyper-translator.exe` on the temporary branch.
6. Force-add and commit only that release asset on the temporary branch:
   - `git add -f dist/release/hyper-translator.exe`
   - `git commit -m "release: publish vX.Y.Z binary"`
7. Push the temporary branch:
   - `git push origin HEAD:refs/heads/hyper-translator-vX.Y.Z`
8. The workflow validates that the temporary branch name matches the top `CHANGELOG.md` version.
9. The workflow reads `dist/release/hyper-translator.exe` and uploads it as `hyper-translator.exe` to the matching GitHub Release.
10. The workflow deletes the temporary remote branch after success.
11. Switch back to `main` and delete the local temporary branch.
12. Confirm `main` still does not track `hyper-translator.exe`, `dist/`, or any Cargo target directory.

## Workflow behavior

`.github/workflows/release.yml` should keep this split behavior:

- On `main` push:
  - Parse the top version from `CHANGELOG.md`.
  - Build current-version-only `release-notes.md`.
  - Create or edit the matching GitHub Release.
  - Do not upload a binary.
- On `hyper-translator-v*` push:
  - Validate the branch name matches the top `CHANGELOG.md` version.
  - Build current-version-only `release-notes.md`.
  - Create or edit the matching GitHub Release.
  - Read `dist/release/hyper-translator.exe` and upload it as the `hyper-translator.exe` release asset.
  - Delete the temporary release branch.

## Verification checklist

Before finishing release-related work:

- `git status --short --branch` should show `main...origin/main` or only intentional pending changes.
- `git ls-files` on `main` should list only the release-facing metadata files documented above.
- Check that the latest release tag matches the top `CHANGELOG.md` entry.
- Check that the GitHub Release body only contains the current version section.
- Check that the binary asset exists on the GitHub Release when a binary release was requested.
- If pushing over SSH port 22 fails with `kex_exchange_identification`, use GitHub SSH over port 443 for the push rather than changing repository data.
