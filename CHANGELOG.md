# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Add a link to the documentation site to `README.md`
- Add a brand guide and branding files in `.github/branding/` (logo, icons,
  favicon, and social preview), and show the logo at the top of `README.md`
- Add the `badges.yml` workflow and `.github/scripts/generate_badges.py` to render the
  README badges, including Super Linter and CodeQL, as SVG files on the `badges`
  branch
- feat(workflows): add bekende malafide handelspartijen update workflow [5bbb89b](https://github.com/homelab-alpha/adguard-home/commit/5bbb89b2163f51026de11e6170a2c01ae81d8080) by [@homelab-alpha](https://github.com/homelab-alpha)
- feat(metadata): synchronize version with AdGuard Home main version [1f36d2a](https://github.com/homelab-alpha/adguard-home/commit/1f36d2ae52f68523ca3d85dc93f136b1df397bce) by [@homelab-alpha](https://github.com/homelab-alpha)

### Changed

- Move the repository tooling (`lint.sh`, `generate_badges.py`, `setup_gpg.sh`,
  and `verify_signatures.sh`) from `scripts/` to `.github/scripts/`, the
  branding from `assets/branding/` to `.github/branding/`, and the code style
  guide from `docs/` to `.github/docs/`
- Add a 20 px protective border to the logo SVGs and show the logo in
  `README.md` at a fixed height of 100 px
- Update the badges only after Lint Repository and CodeQL ran and passed for the
  same commit: remove the `push` trigger from `badges.yml` and add the
  `check-workflows` job
- Replace the `img.shields.io` badges in `README.md` with the self-hosted
  badges
- Enable Bash and Bash Exec validation in `.github/super_linter.env`
- Explain in `codeql.yml` when to add a language
- Ignore `notes.md`, `super_linter.log`, and Python cache files in `.gitignore`
- Run the known malicious trading parties workflow every 8 hours instead of
  every 3 hours
- Replace the deprecated `deny-licenses` option in `dependency_review.yml` with
  an `allow-licenses` list of permissive licenses and CC BY-NC-SA 4.0, so GPL
  and LGPL stay blocked
- Check development dependencies too in `dependency_review.yml`, by setting
  `fail-on-scopes` to `runtime, development`
- chore: adopt the blueprint template as the repository standard [870e37b](https://github.com/homelab-alpha/adguard-home/commit/870e37ba05de7e617aa529e31122231f3c816431) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(deps): comment on the pull request only when the dependency review fails [03f7bf9](https://github.com/homelab-alpha/adguard-home/commit/03f7bf981dfe66d1191b90b5fa6ca958a34d12de) by [@homelab-alpha](https://github.com/homelab-alpha)
- docs: add CLAUDE.md with the project rules for Claude Code [249ac56](https://github.com/homelab-alpha/adguard-home/commit/249ac564bc28361ada693406173628323335dac9) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(workflows): run the filter update every 8h [6c084fa](https://github.com/homelab-alpha/adguard-home/commit/6c084fa41b0721a7968682bc566fc939dc67fda7) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(repo): adopt the current blueprint standard [8732435](https://github.com/homelab-alpha/adguard-home/commit/873243574a74b0137ec2dce61518bc2f0b2640d7) by [@homelab-alpha](https://github.com/homelab-alpha)
- docs(readme): add the documentation site link [5d89b9b](https://github.com/homelab-alpha/adguard-home/commit/5d89b9b4be3d161afda294f59ec35913bd05bdc1) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(repo): sync the latest blueprint updates [3aacac9](https://github.com/homelab-alpha/adguard-home/commit/3aacac95329dc4006c33d2fa6518f4d372897978) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(workflows): replace deny-licenses with allow-licenses [fb7ac5e](https://github.com/homelab-alpha/adguard-home/commit/fb7ac5ed36875f940a11d4871e98377839874454) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(cosmetic): update list [41646c4](https://github.com/homelab-alpha/adguard-home/commit/41646c47771be41616308c85f45b211772d259cb) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(cosmetic): update list [ee148bc](https://github.com/homelab-alpha/adguard-home/commit/ee148bcc570dd28a985ce1f5990297b457fc2e49) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(blocklist): update list [82cc552](https://github.com/homelab-alpha/adguard-home/commit/82cc55261ff60e3f1c442227bb85e78ce69a3f3f) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(blueprint): sync with the blueprint [589797e](https://github.com/homelab-alpha/adguard-home/commit/589797e693ab7564429eac83c3b1041d20500420) by [@homelab-alpha](https://github.com/homelab-alpha)
- ci(workflows): use pull_request_body.py [ad7f95b](https://github.com/homelab-alpha/adguard-home/commit/ad7f95b9bcd221acab3ff5a4d3871d984e083ea1) by [@homelab-alpha](https://github.com/homelab-alpha)
- ci(workflows): request a reviewer on bot PRs [8e89bb1](https://github.com/homelab-alpha/adguard-home/commit/8e89bb1ecc7632b15d2912a107e8873b86da8939) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(github): sync Hugo and Dart Sass rules [0f746c8](https://github.com/homelab-alpha/adguard-home/commit/0f746c843f2ae15875d1db22f089a1f21226e20e) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(github): sync runners, Renovate, and linters [d4ba0dc](https://github.com/homelab-alpha/adguard-home/commit/d4ba0dca93e75d7af4f4f2ffd4d804851cea6c78) by [@homelab-alpha](https://github.com/homelab-alpha)
- ci(workflows): run workflows for bots [e206338](https://github.com/homelab-alpha/adguard-home/commit/e206338d482f2659e184fbaa10dee0d251aeccb0) by [@homelab-alpha](https://github.com/homelab-alpha)
- ci(workflows): allow BlueOak-1.0.0 license [659326d](https://github.com/homelab-alpha/adguard-home/commit/659326dad9a9a0db491e30ffe47c2b435fe058b8) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(labels): add dependency update labels [e58cc67](https://github.com/homelab-alpha/adguard-home/commit/e58cc67e7069895fa5c457e402c3682d109f13c8) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(renovate): remove default assignees [feb5017](https://github.com/homelab-alpha/adguard-home/commit/feb5017ab5b563c35fbb20893dc4f19f0b3afb2a) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(renovate): group and automerge updates [387f114](https://github.com/homelab-alpha/adguard-home/commit/387f114d173577bdd4a3f3714755ec8735e0882c) by [@homelab-alpha](https://github.com/homelab-alpha)
- chore(sync): sync shared files with blueprint [65b8425](https://github.com/homelab-alpha/adguard-home/commit/65b84250c7be9af1dd388f0f509378303a39114f) by [@homelab-alpha](https://github.com/homelab-alpha)

### Deprecated

### Removed

### Fixed

- Fix the GitHub link in `NOTICE`, which pointed to `github.com/adguard-home`
  instead of `github.com/homelab-alpha`
- Fix the table of contents link of `CONTRIBUTING.md` to its first heading
- fix(renovate): fix invalid automergeType and vulnerability rule [33f9459](https://github.com/homelab-alpha/adguard-home/commit/33f94596376d367e048768c21e3423e23b37e95a) by [@homelab-alpha](https://github.com/homelab-alpha)
- fix(labels): skip unchanged labels and retry failed writes [8f9c742](https://github.com/homelab-alpha/adguard-home/commit/8f9c742ac7d260c7a4b9685ce736f2edc5f60a00) by [@homelab-alpha](https://github.com/homelab-alpha)
- fix(docs): fix the TOC link to the first heading [0c88e24](https://github.com/homelab-alpha/adguard-home/commit/0c88e245e976264c632afebae116132548cda412) by [@homelab-alpha](https://github.com/homelab-alpha)
- fix(changelog): remove the date from Unreleased [dfea888](https://github.com/homelab-alpha/adguard-home/commit/dfea888125ea7d779ed9c1cd4a726586deeb28f6) by [@homelab-alpha](https://github.com/homelab-alpha)
- fix(changelog): remove the Unreleased link [813e7d1](https://github.com/homelab-alpha/adguard-home/commit/813e7d18173f165f790f568cb550fb1bce5597c8) by [@homelab-alpha](https://github.com/homelab-alpha)
- fix(workflow): do not draft Renovate PRs [3b34729](https://github.com/homelab-alpha/adguard-home/commit/3b3472971a0e90f51297e55715273a9715b7b946) by [@homelab-alpha](https://github.com/homelab-alpha)

### Security

- Override the transitive dev dependencies `glob` (14.0.3) and `minimatch`
  (11.0.3) to fix Dependabot alerts, which textlint pulls in
