<!-- markdownlint-disable MD041 -->

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/branding/logo_dark.svg" />
    <img src=".github/branding/logo_light.svg" alt="adguard-home" height="100" />
  </picture>
</p>

[![Super Linter](https://github.com/homelab-alpha/adguard-home/raw/badges/super_linter.svg)](https://github.com/homelab-alpha/adguard-home/actions/workflows/super_linter.yml)
[![CodeQL](https://github.com/homelab-alpha/adguard-home/raw/badges/codeql.svg)](https://github.com/homelab-alpha/adguard-home/actions/workflows/codeql.yml)
[![Last commit](https://github.com/homelab-alpha/adguard-home/raw/badges/last_commit.svg)](https://github.com/homelab-alpha/adguard-home/commits/main/)
[![Repo size](https://github.com/homelab-alpha/adguard-home/raw/badges/repo_size.svg)](https://github.com/homelab-alpha/adguard-home/tree/main)
[![Changelog](https://github.com/homelab-alpha/adguard-home/raw/badges/changelog.svg)](https://github.com/homelab-alpha/adguard-home/blob/main/CHANGELOG.md)
[![Contributor Covenant](https://github.com/homelab-alpha/adguard-home/raw/badges/contributor_covenant.svg)](https://github.com/homelab-alpha/adguard-home/blob/main/CODE_OF_CONDUCT.md)
[![Conventional Commits](https://github.com/homelab-alpha/adguard-home/raw/badges/conventional_commits.svg)](https://conventionalcommits.org)
[![Semantic Versioning](https://github.com/homelab-alpha/adguard-home/raw/badges/semver.svg)](https://semver.org/spec/v2.0.0.html)
[![License](https://github.com/homelab-alpha/adguard-home/raw/badges/license.svg)](https://github.com/homelab-alpha/adguard-home/blob/main/LICENSE)

# AdGuard Home

Filter lists for AdGuard Home to block ads, trackers, phishing, and fraudulent
websites.

<details>
  <summary>Table of Contents (click to expand)</summary>
  <p>

1. [AdGuard Home](#adguard-home)
   1. [Description](#description)
   2. [Features](#features)
      1. [Filter lists](#filter-lists)
   3. [Project Status](#project-status)
   4. [Getting Started](#getting-started)
      1. [Requirements](#requirements)
      2. [Installation](#installation)
   5. [Development](#development)
   6. [Project Structure](#project-structure)
   7. [CI/CD and Automation](#cicd-and-automation)
      1. [Workflows](#workflows)
      2. [Linting](#linting)
      3. [Dependency Management](#dependency-management)
   8. [Policies and Standards](#policies-and-standards)
   9. [Working with Claude](#working-with-claude)
   10. [Known Issues](#known-issues)
       1. [Currently Being Addressed](#currently-being-addressed)
   11. [Contributing](#contributing)
   12. [Support](#support)
   13. [Security](#security)
   14. [Roadmap](#roadmap)
   15. [License](#license)

  </p>
</details>

## Description

**adguard-home** contains custom filter lists for
[AdGuard Home](https://github.com/AdguardTeam/AdGuardHome), the DNS server that
blocks ads and trackers. The lists in `filters/` cover ad and tracker blocking,
phishing and fraud, malicious IP addresses, whole groups of domains, and
allowlists for services that must keep working.

The list of known fraudulent trading parties is updated automatically on a
schedule by the `bekende_malafide_handelspartijen.yml` workflow.

More documentation is on the
[Homelab-Alpha documentation site](https://homelab-alpha.nl/adguard-home/).

## Features

- **19 filter lists** in `filters/`, each with a title and description in its
  header.
- **Automatic update** — The Dutch list of known fraudulent trading parties is
  refreshed several times a day.
- **Allowlists** — Allowlists for authorized domain names, including the
  Microsoft services.

### Filter lists

| File                                   | Title                            | Description                                                                                                                                |
| :------------------------------------- | :------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------- |
| `bekende_malafide_handelspartijen.txt` | Bekende Malafide Handelspartijen | a list of trading parties (sellers and traders) known to the Dutch National Police to be fraudulent                                        |
| `blocklist.txt`                        | Blocklist                        | Filter composed of several other filters and specifically simplified to be more compatible with ad blocking at the DNS level               |
| `blocklist_ip_addresses.txt`           | Blocklist IP Addresses           | Filter composed of several other filters and specifically simplified to be more compatible with ad blocking at the DNS level               |
| `cookies.txt`                          | Cookies                          | a list that blocks ads and ad tracking using cookie filters                                                                                |
| `cosmetic.txt`                         | Cosmetic                         | a list that hide ads, sponsored content, and other unwanted page elements                                                                  |
| `dns_type.txt`                         | DNS type                         | a list that analyzes what type of DNS requests they are and then determines whether they should be locked using a rule in a DNS block list |
| `fraudulent_trading_parties.txt`       | Fraudulent Trading Parties       | a list of trading parties (sellers and traders) known to be fraudulent                                                                     |
| `idns.txt`                             | IDNs                             | a list that blocks Internationalized Domain Names                                                                                          |
| `labhost_phishing_domains.txt`         | LabHost phishing domains         | 41,962 phishing domains. Domains are associated with LabHost, a phishing-as-a-service (PhaaS) platform identified by the FBI               |
| `malicious_ip_addresses.txt`           | Malicious IP Addresses           | a list of known malicious IP addresses. (safeguard your network from potential threats.)                                                   |
| `microsoft_whitelist.txt`              | Microsoft Whitelist              | specific DNS whitelist for Microsoft that allows authorized domain names                                                                   |
| `nlconnect_reference_list.txt`         | NLconnect Reference List         | a list of compliance advice for internet access providers on EU sanctions                                                                  |
| `regex.txt`                            | Regex                            | a list that blocks ads and ad tracking using regular expression syntax                                                                     |
| `slds.txt`                             | SLDs                             | a list that blocks Second-level domains                                                                                                    |
| `sociale_media.txt`                    | Sociale Media                    | a list that blocks social media websites                                                                                                   |
| `third_level_domains.txt`              | Third Level Domains              | a list that blocks Third Level Domains                                                                                                     |
| `tlds.txt`                             | TLDs                             | a list that blocks Top Level Domains                                                                                                       |
| `whitelist.txt`                        | Whitelist                        | a DNS whitelist that allows authorized domain names                                                                                        |
| `wildcard.txt`                         | Wildcard                         | a list that blocks Wildcard DNS records                                                                                                    |

## Project Status

> [!NOTE]
>
> **Status:** Maintained
>
> The repository is maintained and updated through pull requests and automated
> dependency updates. Planned work is listed in [ROADMAP.md](./ROADMAP.md).

## Getting Started

### Requirements

A running AdGuard Home instance.

### Installation

Add a list in the AdGuard Home web interface. For a blocklist, open
**Filters** > **DNS blocklists** > **Add blocklist** > **Add a custom list**.
Use the raw URL of the list:

```text
https://raw.githubusercontent.com/homelab-alpha/adguard-home/main/filters/<file>
```

The allowlists (`whitelist.txt` and `microsoft_whitelist.txt`) go in
**Filters** > **DNS allowlists**.

## Development

Set up the dev tooling on any computer. It needs Node.js 24 (see `engines` in
`package.json`):

```bash
git clone https://github.com/homelab-alpha/adguard-home.git
cd adguard-home
npm ci
npm run lint
```

Linting has two parts. Every pull request runs `npm run lint` (Prettier,
textlint terminology, and merge conflict markers on the changed files), which
you can also run locally. `npm run lint:fix` repairs formatting and terminology
for you. Every push to `main` runs the full Super Linter, which you can run
locally with Docker:

```bash
docker run --rm -e RUN_LOCAL=true -e USE_FIND_ALGORITHM=true \
  -e VALIDATE_ALL_CODEBASE=true --env-file .github/super_linter.env \
  -v "$PWD":/tmp/lint ghcr.io/super-linter/super-linter:v9.0.0
```

For quick formatting of a single file, `npx prettier --write <file>` uses the
same `.prettierrc`.

## Project Structure

```treeview
adguard-home/
├── .claude/                                      # Claude Code project settings
│   └── settings.json                             # Shared permissions for Claude Code
├── .github/                                      # GitHub-specific configuration and automation
│   ├── DISCUSSION_TEMPLATE/                      # GitHub Discussions templates
│   │   ├── announcements.yml                     # Template for announcements
│   │   ├── feature-request.yml                   # Template for feature requests
│   │   ├── feedback.yml                          # Template for feedback
│   │   ├── help-support.yml                      # Template for help and support
│   │   └── q-a.yml                               # Template for Q&A
│   ├── ISSUE_TEMPLATE/                           # GitHub issue templates
│   │   ├── bug_report.yml                        # Template for bug reports
│   │   ├── config.yml                            # Issue template configuration
│   │   ├── i18n_issue.yml                        # Template for translation & localization
│   │   └── security_report.yml                   # Template for security issues
│   ├── branding/                                 # Brand guide, logo, icons, and social preview
│   │   ├── brand_guide.md                        # Brand guide
│   │   ├── favicon.svg                           # Favicon
│   │   ├── icon_dark.svg                         # App icon (dark tile)
│   │   ├── icon_light.svg                        # App icon (light tile)
│   │   ├── logo_dark.svg                         # Logo (dark backgrounds)
│   │   ├── logo_light.svg                        # Logo (light backgrounds)
│   │   ├── logo_tagline_dark.svg                 # Logo with slogan (dark)
│   │   ├── logo_tagline_light.svg                # Logo with slogan (light)
│   │   ├── mark_dark.svg                         # Mark (dark backgrounds)
│   │   ├── mark_light.svg                        # Mark (light backgrounds)
│   │   ├── social_preview.png                    # GitHub social preview (1280x640)
│   │   └── social_preview.svg                    # Source of the social preview
│   ├── docs/                                     # Repository style guide (not project docs)
│   │   ├── code_style_and_standards_guides.md    # Coding standards and style guidelines
│   │   └── .placeholder                          # Placeholder for empty folder
│   ├── linters/                                  # Configuration files for Super Linter
│   │   ├── .checkov.yaml                         # Infrastructure-as-code security rules
│   │   ├── .gitleaks.toml                        # Gitleaks secret scanning configuration
│   │   ├── .markdown-lint.yml                    # Markdown linting rules
│   │   ├── .powershell-psscriptanalyzer.psd1     # PowerShell static analysis rules
│   │   ├── .textlintrc                           # Text/grammar linting configuration
│   │   ├── .yaml-lint.yml                        # YAML linting rules
│   │   └── actionlint.yml                        # GitHub Actions workflow linting rules
│   ├── policies/                                 # Internal policies and documentation
│   │   ├── github_actions.md                     # Workflow standards (ENG-CI-001)
│   │   ├── labels.md                             # Label color strategy and rules
│   │   ├── logs.md                               # Logging policies and practices
│   │   ├── review_process.md                     # Code review process
│   │   ├── security.md                           # Security policy
│   │   └── tests.md                              # Testing policy
│   ├── scripts/                                  # Repository tooling (not project code)
│   │   ├── generate_badges.py                    # Renders the README badges as SVG files
│   │   ├── lint.sh                               # Local lint (Prettier, textlint, conflict markers)
│   │   ├── setup_gpg.sh                          # Configures API or GPG signing for Git operations
│   │   └── verify_signatures.sh                  # Verifies commit and tag signatures
│   ├── workflows/                                # GitHub Actions workflows
│   │   ├── badges.yml                            # Self-hosted README badges
│   │   ├── bekende_malafide_handelspartijen.yml  # Updates the filter list of known fraudulent trading parties
│   │   ├── codeql.yml                            # CodeQL security analysis
│   │   ├── contributors.yml                      # Contributors list generator
│   │   ├── dependency_review.yml                 # Dependency review
│   │   ├── housekeeping.yml                      # Cache and run cleanup
│   │   ├── issues.yml                            # Issue automation
│   │   ├── labels.yml                            # Label synchronization
│   │   ├── lint_pull_request.yml                 # npm linting for pull requests
│   │   ├── merge_conflicts.yml                   # Merge conflict detection
│   │   ├── milestone_manager.yml                 # Milestone automation
│   │   ├── pull_request.yml                      # Pull request automation
│   │   ├── release_manager.yml                   # Release automation
│   │   ├── signing_test.yml                      # Test API-based commit and tag signing
│   │   ├── stale_issues_and_pull_requests.yml    # Stale issue management
│   │   ├── super_linter.yml                      # Super Linter
│   │   └── unreproducible_issues.yml             # Unreproducible issue management
│   ├── CODEOWNERS                                # Code ownership definitions
│   ├── labels.yml                                # Repository label definitions
│   ├── pull_request_template.md                  # Pull request template
│   ├── renovate.json                             # Renovate dependency automation
│   └── super_linter.env                          # Super Linter environment configuration
├── filters/                                      # Filter lists for AdGuard Home
│   ├── bekende_malafide_handelspartijen.txt      # Bekende Malafide Handelspartijen
│   ├── blocklist.txt                             # Blocklist
│   ├── blocklist_ip_addresses.txt                # Blocklist IP Addresses
│   ├── cookies.txt                               # Cookies
│   ├── cosmetic.txt                              # Cosmetic
│   ├── dns_type.txt                              # DNS type
│   ├── fraudulent_trading_parties.txt            # Fraudulent Trading Parties
│   ├── idns.txt                                  # IDNs
│   ├── labhost_phishing_domains.txt              # LabHost phishing domains
│   ├── malicious_ip_addresses.txt                # Malicious IP Addresses
│   ├── microsoft_whitelist.txt                   # Microsoft Whitelist
│   ├── nlconnect_reference_list.txt              # NLconnect Reference List
│   ├── regex.txt                                 # Regex
│   ├── slds.txt                                  # SLDs
│   ├── sociale_media.txt                         # Sociale Media
│   ├── third_level_domains.txt                   # Third Level Domains
│   ├── tlds.txt                                  # TLDs
│   ├── whitelist.txt                             # Whitelist
│   └── wildcard.txt                              # Wildcard
├── .editorconfig                                 # Editor settings (indent, line endings)
├── .gitignore                                    # Git ignore rules
├── .gitleaksignore                               # Gitleaks secret scanning allowlist
├── .npmrc                                        # npm supply-chain hardening
├── .pre-commit-config.yaml                       # Local pre-commit hooks (mirrors CI)
├── .prettierignore                               # Files excluded from Prettier formatting
├── .prettierrc                                   # Prettier configuration file
├── AI_CONTRIBUTION_POLICY.md                     # Rules for contributions made with AI assistance
├── CHANGELOG.md                                  # Project change history
├── CLAUDE.md                                     # Project rules for Claude Code
├── CODE_OF_CONDUCT.md                            # Contributor Covenant Code of Conduct
├── CONTRIBUTING.md                               # Contribution guidelines
├── CONTRIBUTORS.md                               # Auto-generated contributors list
├── GOVERNANCE.md                                 # Project governance model
├── LICENSE                                       # Creative Commons BY-NC-SA 4.0 license
├── MAINTAINERS.md                                # Project maintainer list and process
├── NOTICE                                        # Attribution and license notice
├── package-lock.json                             # Locked versions of the dev tooling
├── package.json                                  # Dev tooling (Prettier, textlint) and lint scripts
├── README.md                                     # Primary repository documentation
├── ROADMAP.md                                    # Planned features and milestones
├── SECURITY.md                                   # Security policy and reporting guidelines
├── SUPPORT.md                                    # Support channels and response times
└── TERMS_OF_SERVICE.md                           # Terms of service
```

## CI/CD and Automation

The repository includes a set of GitHub Actions workflows that run automatically
on push, pull request, and scheduled triggers.

### Workflows

| Workflow                               | Trigger                 | Purpose                                                     |
| :------------------------------------- | :---------------------- | :---------------------------------------------------------- |
| `badges.yml`                           | Workflow run, daily     | Renders the README badges to the `badges` branch            |
| `bekende_malafide_handelspartijen.yml` | Schedule, manual        | Updates the filter list of known fraudulent trading parties |
| `codeql.yml`                           | Push, PR, schedule      | CodeQL static analysis for security vulnerabilities         |
| `contributors.yml`                     | Push to `main`          | Auto-generates `CONTRIBUTORS.md`                            |
| `dependency_review.yml`                | PR                      | Reviews dependency changes for known vulnerabilities        |
| `housekeeping.yml`                     | Weekly schedule, manual | Cleans up old workflow runs and Actions caches              |
| `issues.yml`                           | Issue events            | Automates issue labeling and triage                         |
| `labels.yml`                           | Push, manual            | Synchronizes repository labels from `labels.yml`            |
| `lint_pull_request.yml`                | PR, manual              | Runs `npm run lint` on the changed files                    |
| `merge_conflicts.yml`                  | Push, PR                | Detects merge conflicts in open pull requests               |
| `milestone_manager.yml`                | Manual                  | Automates milestone creation and lifecycle                  |
| `pull_request.yml`                     | PR events               | Pull request automation and validation                      |
| `release_manager.yml`                  | Manual                  | Automates GitHub Releases                                   |
| `signing_test.yml`                     | Manual                  | Tests API-based commit and tag signing                      |
| `stale_issues_and_pull_requests.yml`   | Schedule                | Marks and closes stale issues and pull requests             |
| `super_linter.yml`                     | Push to `main`, manual  | Runs Super Linter across the codebase                       |
| `unreproducible_issues.yml`            | Schedule                | Manages issues that cannot be reproduced                    |

All workflows follow the standards documented in
[`.github/policies/github_actions.md`](./.github/policies/github_actions.md),
including actions pinned to a commit SHA, concurrency controls, timeout limits,
bot filtering, and structured job summaries.

The README badges are not fetched from a third-party service. `badges.yml`
renders them with `.github/scripts/generate_badges.py` (Python standard library
only) and publishes the SVG files to the `badges` branch, which the README links
to through `github.com/<owner>/<repo>/raw/badges/`. The Super Linter and CodeQL
badges show the latest run on the default branch. The workflow does not start on
a push: it starts when Lint Repository or CodeQL finishes (the `workflow_run`
trigger lists their names, so update it when you rename them), and the
`check-workflows` job lets it continue only when both workflows ran and passed
for that commit. A failed, cancelled, or skipped run (the workflows skip bot
commits) leaves the badges as they are, and so does a repository where either
workflow is disabled. The workflow creates the branch on its first run. The
badges follow the colors in
[`.github/branding/brand_guide.md`](./.github/branding/brand_guide.md) and
switch to a dark variant with the system theme.

### Linting

Pull requests are linted with `npm run lint` (`.github/scripts/lint.sh`), which
uses Prettier, textlint, and a merge conflict marker check with the
configuration files below. Pushes to `main` run
[Super Linter](https://github.com/super-linter/super-linter), configured through
`.github/super_linter.env`. The following linters are enabled: Checkov, ENV,
GitHub Actions (actionlint), Gitleaks, Git merge conflict markers, JSON
(Prettier), Markdown (Prettier), Natural Language (textlint), Pre-commit,
Renovate, and YAML (Prettier).

Linter-specific configuration files are stored in `.github/linters/` and include
rules for Checkov, Gitleaks, markdownlint, textlint, yamllint, actionlint, and
PowerShell.

### Dependency Management

Dependency updates are managed by [Renovate](https://github.com/apps/renovate).
The configuration in `.github/renovate.json` pins GitHub Actions to commit SHAs
and npm packages to exact versions, waits 7 days before it proposes a new
release, merges patch, pin, and digest updates automatically with squash, and
prioritizes security updates. Major and minor updates are never merged
automatically. Renovate also keeps a dependency dashboard issue.

## Policies and Standards

The repository includes internal policies that define how the project operates.
These are documented in `.github/policies/` and in root-level files:

| Document                                                                                               | Purpose                                              |
| :----------------------------------------------------------------------------------------------------- | :--------------------------------------------------- |
| [`.github/policies/github_actions.md`](./.github/policies/github_actions.md)                           | Workflow structure, security, and logging standards  |
| [`.github/policies/labels.md`](./.github/policies/labels.md)                                           | Label naming, color strategy, and usage rules        |
| [`.github/policies/logs.md`](./.github/policies/logs.md)                                               | Logging conventions for workflows and scripts        |
| [`.github/policies/review_process.md`](./.github/policies/review_process.md)                           | Code review stages, criteria, and merge strategy     |
| [`.github/policies/security.md`](./.github/policies/security.md)                                       | Security scanning and vulnerability management       |
| [`.github/policies/tests.md`](./.github/policies/tests.md)                                             | Testing standards, structure, and conventions        |
| [`.github/docs/code_style_and_standards_guides.md`](./.github/docs/code_style_and_standards_guides.md) | Coding style guidelines and Prettier configuration   |
| [`AI_CONTRIBUTION_POLICY.md`](./AI_CONTRIBUTION_POLICY.md)                                             | Rules for contributions made with AI assistance      |
| [`GOVERNANCE.md`](./GOVERNANCE.md)                                                                     | Project governance model and decision-making process |
| [`MAINTAINERS.md`](./MAINTAINERS.md)                                                                   | Maintainer roles, responsibilities, and current list |
| [`TERMS_OF_SERVICE.md`](./TERMS_OF_SERVICE.md)                                                         | Terms of use for the repository                      |

## Working with Claude

Project rules and conventions for Claude Code live in
[`CLAUDE.md`](./CLAUDE.md). The shared settings are in
[`.claude/settings.json`](./.claude/settings.json). The code style guide is in
[`.github/docs/code_style_and_standards_guides.md`](./.github/docs/code_style_and_standards_guides.md),
so a session on any computer follows the same rules.

## Known Issues

The maintainers strive to provide a seamless experience. Below are any known
bugs, limitations, or issues you might encounter. This section is updated
regularly.

### Currently Being Addressed

No known issues at this time.

If you discover a bug or experience an issue not listed here, please
[open an issue on GitHub](https://github.com/homelab-alpha/adguard-home/issues/new/choose).

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for
contribution guidelines, branch naming conventions, commit message format, and
the review process. AI-assisted contributions follow
[AI_CONTRIBUTION_POLICY.md](./AI_CONTRIBUTION_POLICY.md).

## Support

For setup questions, troubleshooting, and general help, see
[SUPPORT.md](./SUPPORT.md).

## Security

To report a security vulnerability, please follow the process described in
[SECURITY.md](./SECURITY.md). Do **not** report security issues via public
GitHub issues or discussions.

## Roadmap

Planned features, milestones, and the long-term direction of the project are
documented in [ROADMAP.md](./ROADMAP.md).

## License

This project is licensed under the **Creative Commons
Attribution-NonCommercial-ShareAlike 4.0 International License** (CC BY-NC-SA
4.0). See the [LICENSE](./LICENSE) and [NOTICE](./NOTICE) files for the full
license text and attribution requirements.
