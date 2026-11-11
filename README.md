<!--
  Public profile README for https://github.com/Backupino/Backupino
  Audience: site owners, agencies and developers evaluating Backupino.

  IMAGE HOSTING NOTE: every remote image is served from a host that works from Iran and is not
  on *.vercel.app. capsule-render, github-readme-stats, github-readme-activity-graph and
  github-profile-trophy were removed on purpose — they live on vercel.app and render as broken
  placeholders. In use: shields.io · komarev.com · skillicons.dev · readme-typing-svg.demolab.com
  · ghchart.rshah.org · contrib.rocks · github.com (avatars).

  LICENSE BADGE NOTE: /github/license/Backupino/plugin returns "NOASSERTION" because GitHub's
  licensee cannot machine-detect the LICENSE file, so that badge renders as garbage. The license
  is GPL-2.0-or-later (free/backupino.php header + free/readme.txt "License: GPLv2 or later"),
  therefore the license badge is intentionally static. Fixing the LICENSE file would let the
  dynamic badge work again.

  DOWNLOAD LINK NOTE: every download button points at
  https://github.com/Backupino/plugin/releases/latest/download/backupino.zip
  which is GitHub's "latest release asset" redirect — it always serves the newest `backupino.zip`
  (v1.0.4 → 180,215 bytes ≈ 176 KB) without any edit to this page.

  SIZE NOTE: GitHub's repo size (≈583 KiB) counts the whole repository; the shipped plugin package
  is the release asset (176 KiB). Both are shown, clearly labelled.

  DYNAMIC-VALUES NOTE: stars, forks, watchers, followers, releases, release date, last commit,
  repo size, issues, PRs, contributors, commit activity, downloads and the language badges are all
  fetched live by shields.io. Only the plugin package size and the version pinned inside the text
  are static.

  Facts and their sources (all public):
    - Version 1.0.4, WP 6.0–7.1, PHP 7.4–8.4, GPL-2.0-or-later → free/backupino.php, free/readme.txt
    - Features → free/readme.txt · Pipeline/installer → docs/Dev/SPEC.md
    - Release asset backupino.zip = 180,215 B → GitHub Releases API (v1.0.4)
    - Pro capabilities → pro/README.md, docs/Dev/PRODUCT-PLANS.md

  Design: theme `nord`, BG 0D1117, accent 88C0D0, secondary 81A1C1, alert BF616A, label 2E3440.
-->

<!-- SECTION: Header -->
<h1 align="center">Backupino</h1>

<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=24&duration=3000&pause=800&color=88C0D0&center=true&vCenter=true&width=820&lines=Fast%2C+resumable+WordPress+backup+%26+migration;Files+%2B+database+in+one+recoverable+package;Restore+on+an+empty+server+with+installer.php)](https://github.com/Backupino/plugin)

![Profile Views](https://komarev.com/ghpvc/?username=Backupino&label=Profile%20Views&color=88C0D0&style=for-the-badge)
![Version](https://img.shields.io/github/v/release/Backupino/plugin?style=for-the-badge&color=88C0D0&labelColor=2E3440&label=stable)
![WordPress](https://img.shields.io/badge/WordPress-6.0%20%E2%80%93%207.1-21759B?style=for-the-badge&logo=wordpress&logoColor=white&labelColor=2E3440)
![PHP](https://img.shields.io/badge/PHP-7.4%20%E2%80%93%208.4-777BB4?style=for-the-badge&logo=php&logoColor=white&labelColor=2E3440)
![License](https://img.shields.io/badge/License-GPL--2.0--or--later-A3BE8C?style=for-the-badge&labelColor=2E3440)

</div>

---

<!-- SECTION: About -->
<h2 align="center">📖 About</h2>

**Backupino** is a WordPress backup, cloning and migration plugin engineered for real shared hosting —
not for idealised servers. It was built around three jobs that normally need three products:

| Job | Entry point | Output |
|---|---|---|
| **Migrate / clone** a site | Admin button or WP-CLI | `site.zip` + `installer.php` |
| **Scheduled backup** | WP-Cron (monthly, Jalali-aware) | The same package, stored locally |
| **Disaster restore** | Upload `installer.php` to an empty server | A working WordPress site |

Three problems it solves concretely:

- **Timeouts.** Every step is split into small, resumable slices with persisted checkpoints. A 30-second
  FastCGI limit is no longer a failed backup — it is simply one more tick.
- **No shell access.** The database is streamed through native PDO/MySQLi with keyset pagination, so no
  `mysqldump`, `exec()` or SSH is required.
- **Restore paywalls.** Restoring a backup you already own is never locked behind a paid tier. The
  installer is free, self-contained and ships with every package.

**Offline-first by design:** zero CDNs, zero remote fonts, zero telemetry. It works on intranets and
isolated networks, and notifies you through your own Telegram or Bale bot.

<div align="center">

[![Download](https://img.shields.io/badge/Download_Plugin-backupino.zip-88C0D0?style=for-the-badge&logo=github&logoColor=0D1117)](https://github.com/Backupino/plugin/releases/latest/download/backupino.zip)
[![Documentation](https://img.shields.io/badge/Documentation-EN_%2B_FA-5E81AC?style=for-the-badge&logo=readthedocs&logoColor=white)](https://github.com/Backupino/documents)
[![Architecture](https://img.shields.io/badge/Architecture-Deep_Dive-81A1C1?style=for-the-badge&logo=diagramsdotnet&logoColor=white)](https://github.com/Backupino/documents/blob/main/en/01-getting-started/02-architecture.md)

</div>

---

<!-- SECTION: Features -->
<h2 align="center">✨ Features</h2>

<div align="center">

| | Feature | Why it matters |
|---|---|---|
| 🔁 | **Resumable chunk engine** | Backup is sliced into `scan → files → database → finalize`. Every slice is checkpointed in the database, so a timeout, a closed browser or a PHP fatal resumes at the last committed byte. |
| 🗃️ | **Pure PHP SQL dumper** | `SHOW CREATE TABLE` + keyset-paginated data, binary columns as `0x…`, `DEFINER` stripped. No `mysqldump`, no `exec()`, no shell. |
| ⚙️ | **Standalone installer (~72 KB)** | One generated file rebuilds the site on an empty server in 7 guided steps. It never needs WordPress to be installed first. |
| 🔗 | **Deep URL search & replace** | A recursive-descent parser for PHP `serialize()` rewrites nested arrays and objects, JSON strings, Elementor dynamic tags and UTF-8 Persian slugs without corruption. |
| ♾️ | **Permanent latest-backup link** | A non-expiring URL that always resolves to the newest package, protected by `manage_options` or a 32-byte secret key — perfect for cron-driven off-site copies. |
| 📅 | **Scheduled monthly backup** | Runs on the first day of each month with native **Jalali** calculation for `fa_IR` and Gregorian elsewhere. |
| 🧹 | **Retention management** | Keeps the latest N packages (default 3) and prunes the rest to protect disk quota. |
| 🔔 | **Telegram & Bale alerts** | Completion report with scope, size, date and download link, with an automatic 3-attempt retry queue. |
| 📦 | **Full, files-only or DB-only** | Choose the scope, exclude paths with glob rules (`*`, `**`, `?`, `cache/`, `*.log`). |
| 🛡️ | **Safe restore by default** | `wp-config.php` is never copied; the installer writes a fresh one with new salts, quarantines server configs and refuses a mismatched archive (SHA-256 pairing). |
| 💻 | **WP-CLI** | `wp backupino create`, `create --db-only`, `status`, `jobs` — scriptable for sysadmins and agencies. |
| 🌐 | **100% offline-first** | All CSS/JS/fonts served locally. Works on isolated networks; no external service is contacted unless you enable it. |

</div>

---

<!-- SECTION: How it works -->
<h2 align="center">⚡ How It Works</h2>

**Build pipeline** — time-boxed to ~20 s per request by default, every stage resumable:

| # | Stage | Share | Resume mechanism |
|---|---|---|---|
| 1 | `scan` | 8 % | Directory stack persisted in the job payload |
| 2 | `files` | 50 % | Byte offset into the manifest; ZIP reopened and appended per tick |
| 3 | `database` | 32 % | Per-table `(index, phase, cursor, offset, bytes)` |
| 4 | `finalize` | 10 % | Explicit sub-steps: seal → hash → installer → publish |

```text
queued ──► running ──► completed
              ├──► failed      (exception → message, never a half-written status)
              └──► cancelled   (user action)

Package:  site.zip  +  database.sql  +  backupino-manifest.ndjson  +  backupino-package.json
Output:   site.zip  +  installer.php
```

**Restore** — seven AJAX-isolated steps, so no single step can time out:

`1` Environment check → `2` Database connection → `3` Extract (300 entries/slice, zip-slip protected)
→ `4` Streaming SQL import (packet auto-splitting, orphaned-tablespace recovery) → `5` Deep URL rewrite
→ `6` Fresh `wp-config.php` + salts + `.htaccess` → `7` Self-cleanup.

**Measured footprint of the stable release:** a 92-file plugin, a 180,215-byte installable zip and a
~75 KB standalone installer — verified by 153 automated tests on PHP 7.4, 8.0, 8.1, 8.2, 8.3 and 8.4.

---

<!-- SECTION: Free vs Pro -->
<h2 align="center">🆚 Free vs Pro</h2>

The free plugin is complete on its own — it is not a demo. Pro is an **optional addon** that attaches to
the free core through standard WordPress filters; no functionality is removed from the free version.

| Capability | Free | Pro |
|---|:---:|:---:|
| Full backup — files **+** database, no size cap | ✅ | ✅ |
| Database-only / files-only packages | ✅ | ✅ |
| Standalone installer + URL rewrite | ✅ | ✅ |
| Local storage, unlimited packages (retention configurable) | ✅ | ✅ |
| Permanent latest-backup link | ✅ | ✅ |
| Telegram & Bale notifications | ✅ | ✅ |
| Automated backup — monthly schedule | ✅ | ✅ |
| Custom intervals — hourly / daily / weekly / custom | — | ✅ |
| S3-compatible cloud destinations | — | ✅ |
| Google Drive & Dropbox (OAuth 2.0) | — | ✅ |
| Client-side AES-256 encryption | — | ✅ |
| Multisite network support | — | ✅ |
| Incremental packages | — | ✅ |
| In-place restore + rollback | — | ✅ |
| Central bot & portal-driven manual backup | — | ✅ |
| Licensed auto-updates from the official portal | — | ✅ |

> **Rule we do not break:** restoring a backup you already own is never paywalled.

<br/>

**Pro in detail** — an addon plugin (`backupino-pro`) that requires the free core:

- **Cloud destinations** — native Amazon S3 protocol with **AWS SigV4** signing, compatible with
  ArvanCloud S3, MinIO, DigitalOcean Spaces, Wasabi and Cloudflare R2; Google Drive and Dropbox over OAuth 2.0.
- **Advanced scheduling** — hourly, daily, weekly or custom windows, plus a chained pipeline:
  *backup → upload to cloud → purge the local copy*.
- **Encryption** — packages are sealed with **AES-256** before they leave the server.
- **Multisite** — extract or clone one sub-site of a network into an independent single site.
- **In-place restore & rollback** — two-phase `Shadow → Confirm → Commit → Rollback` restore over a live
  site, executed without booting WordPress, restricted to the license owner with 2FA.
- **Licensing & updates** — **Ed25519**-signed license documents validated offline with a 7-day grace
  period; automatic updates delivered from the customer portal.
- **Hooks, not forks** — Pro plugs into `backupino_storage_drivers`, `backupino_stages`,
  `backupino_schedule_intervals` and `backupino_limits`. The free core never references Pro code.

---

<!-- SECTION: Tech Stack -->
<h2 align="center">🛠️ Tech Stack</h2>

<div align="center">

<img src="https://skillicons.dev/icons?i=php,wordpress,mysql,js,html,css,npm,git,github,githubactions,bash&theme=dark&perline=11" alt="PHP, WordPress, MySQL, JavaScript, HTML, CSS, npm, Git, GitHub, GitHub Actions, Bash" />

</div>

<h3 align="center">Languages used</h3>

<div align="center">

![PHP](https://img.shields.io/github/languages/top/Backupino/plugin?style=for-the-badge&color=777BB4&labelColor=2E3440&logo=php&logoColor=white)
![Languages](https://img.shields.io/github/languages/count/Backupino/plugin?style=for-the-badge&color=88C0D0&labelColor=2E3440)
![Code size](https://img.shields.io/github/languages/code-size/Backupino/plugin?style=for-the-badge&color=81A1C1&labelColor=2E3440)

</div>

| Language | Share | Where it lives |
|---|---:|---|
| **PHP** | ~90 % | Plugin core, backup engine, installer, admin UI, REST endpoints, WP-CLI |
| **JavaScript** | ~5 % | Admin dashboard, installer wizard, public download page (vanilla, no framework) |
| **CSS** | ~4 % | Admin, installer and download-page styles (design tokens, no CDN) |
| **HTML** | <1 % | Templates, installer layout, `readme.txt` markup |

*Shares recalculated from the GitHub language breakdown; the badges above are live.*

<h3 align="center">What is actually used</h3>

| Layer | Technologies |
|---|---|
| **Language & std** | PHP 7.4 → 8.4, `declare(strict_types=1)`, PSR-style autoloader, no runtime PHP dependencies |
| **Platform** | WordPress hooks, REST API, WP-Cron, WP-CLI, `$wpdb` behind an adapter class |
| **Data** | MySQL / MariaDB via PDO **and** MySQLi, keyset pagination, `ZipArchive` (libzip, Zip64-aware) |
| **Frontend** | Vanilla JavaScript, CSS custom properties (design tokens), SVG assets — all self-hosted |
| **Crypto** | SHA-256 archive pairing, `hash_equals` token comparison, Ed25519 (`ext-sodium`) for licensing |
| **Security** | Nonces, capability checks, strict table-prefix regex, zip-slip protection, secret redaction from `wp-config.php` |
| **Testing** | Custom dependency-free harness — 153 tests (unit, integration, installer build) |
| **Build & CI** | Composer (dev toolchain) + npm (test harness only), PHPCS with WordPress Coding Standards, GitHub Actions matrix PHP 7.4–8.4 |
| **Integrations** | Telegram Bot API, Bale (`tapi.bale.ai`), optional WooCommerce-powered license portal |

---

<!-- SECTION: Developers -->
<h2 align="center">👩‍💻 Developers</h2>

<div align="center">

**All contributors** — this list, the count and the avatars below update themselves:

![Contributors](https://img.shields.io/github/contributors/Backupino/plugin?style=for-the-badge&color=88C0D0&labelColor=2E3440&logo=github)
![Commit activity](https://img.shields.io/github/commit-activity/m/Backupino/plugin?style=for-the-badge&color=81A1C1&labelColor=2E3440&logo=git)

<img src="https://contrib.rocks/image?repo=Backupino/plugin&max=40" alt="Contributors of Backupino/plugin" />

<sub>Contributions welcome under GPL-2.0-or-later —
<a href="https://github.com/Backupino/plugin/issues">open an issue</a> ·
<a href="https://github.com/Backupino/plugin/pulls">send a pull request</a></sub>

</div>

---

<!-- SECTION: Project Stats -->
<h2 align="center">📊 Project Stats</h2>

<div align="center">

![Stars](https://img.shields.io/github/stars/Backupino/plugin?style=for-the-badge&color=88C0D0&labelColor=2E3440&logo=github)
![Forks](https://img.shields.io/github/forks/Backupino/plugin?style=for-the-badge&color=81A1C1&labelColor=2E3440&logo=github)
![Watchers](https://img.shields.io/github/watchers/Backupino/plugin?style=for-the-badge&color=8FBCBB&labelColor=2E3440&logo=github)
![Followers](https://img.shields.io/github/followers/Backupino?style=for-the-badge&color=BF616A&labelColor=2E3440&logo=github)

![Release](https://img.shields.io/github/v/release/Backupino/plugin?style=for-the-badge&color=A3BE8C&labelColor=2E3440&logo=github)
![Release date](https://img.shields.io/github/release-date/Backupino/plugin?style=for-the-badge&color=A3BE8C&labelColor=2E3440)
![Last commit](https://img.shields.io/github/last-commit/Backupino/plugin?style=for-the-badge&color=8FBCBB&labelColor=2E3440&logo=git)
![Downloads](https://img.shields.io/github/downloads/Backupino/plugin/total?style=for-the-badge&color=5E81AC&labelColor=2E3440&logo=github)

![Plugin package](https://img.shields.io/badge/plugin_package-176_KB-88C0D0?style=for-the-badge&labelColor=2E3440&logo=files)
![Repo size](https://img.shields.io/github/repo-size/Backupino/plugin?style=for-the-badge&color=4C566A&labelColor=2E3440&logo=git)

![Issues](https://img.shields.io/github/issues/Backupino/plugin?style=for-the-badge&color=BF616A&labelColor=2E3440&logo=github)
![Closed issues](https://img.shields.io/github/issues-closed/Backupino/plugin?style=for-the-badge&color=A3BE8C&labelColor=2E3440&logo=github)
![PRs](https://img.shields.io/github/issues-pr/Backupino/plugin?style=for-the-badge&color=81A1C1&labelColor=2E3440&logo=github)

<sub><b>plugin package</b> = the downloadable <code>backupino.zip</code> release asset (180,215 bytes) ·
<b>repo size</b> = the whole source repository, as reported by GitHub</sub>

</div>

---

<!-- SECTION: Contribution Activity -->
<h2 align="center">📈 Contribution Activity</h2>

<div align="center">

**Lead developer** — [`im-JvD`](https://github.com/im-JvD)

[![im-JvD contributions](https://ghchart.rshah.org/81A1C1/im-JvD)](https://github.com/im-JvD)

<sub>Backupino is developed from individual accounts, so the calendar of the lead developer is shown.
To add a maintainer, copy one chart line with their username — the rest of the page
(contributor count, avatars, activity badges) updates automatically.</sub>

</div>

---

<!-- SECTION: Connect -->
<h2 align="center">🤝 Connect</h2>

<div align="center">

[![Download](https://img.shields.io/badge/Download-backupino.zip-88C0D0?style=for-the-badge&logo=github&logoColor=0D1117)](https://github.com/Backupino/plugin/releases/latest/download/backupino.zip)
[![Plugin Source](https://img.shields.io/badge/Source-plugin-BF616A?style=for-the-badge&logo=php&logoColor=white)](https://github.com/Backupino/plugin)
[![Documentation](https://img.shields.io/badge/Docs-documents-5E81AC?style=for-the-badge&logo=readthedocs&logoColor=white)](https://github.com/Backupino/documents)
[![WordPress.org](https://img.shields.io/badge/WordPress.org-backupino-21759B?style=for-the-badge&logo=wordpress&logoColor=white)](https://profiles.wordpress.org/backupino/)
[![License](https://img.shields.io/badge/License-GPL--2.0--or--later-A3BE8C?style=for-the-badge)](https://www.gnu.org/licenses/gpl-2.0.html)

<sub>Bugs and feature requests: <a href="https://github.com/Backupino/plugin/issues">github.com/Backupino/plugin/issues</a></sub>

</div>

---

<!-- SECTION: Footer -->
<div align="center">

![Footer](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=16&duration=4000&pause=1200&color=81A1C1&center=true&vCenter=true&width=620&lines=Back+up+once.+Restore+anywhere.+%C2%B7+GPL-2.0-or-later;WordPress+6.0%2B+%C2%B7+PHP+7.4+%E2%80%93+8.4+%C2%B7+made+for+real+shared+hosting)

</div>
