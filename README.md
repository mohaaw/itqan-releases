<div align="center">

# إتقان · ITQAN

### The company platform for approvals, tasks, contracts, meetings and attendance — all in one app

**أدوات العمل بتمكّن** — tools that empower the work

[![Latest Release](https://img.shields.io/github/v/release/mohaaw/itqan-releases?include_prereleases=false)](https://github.com/mohaaw/itqan-releases/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Android-blue)](#installation)
[![Architecture](https://img.shields.io/badge/Flutter-full_stack-green)](https://flutter.dev)
[![License](https://img.shields.io/badge/license-proprietary-red)](#license)

</div>

---

## What is ITQAN?

**Itqan** (Arabic: إتقان — *"doing things with excellence"*) is an Arabic-first enterprise operations platform for companies and teams. It replaces scattered chats, paper approvals and manual attendance with a single app that everyone — **owner, manager, supervisor, employee, HR and support** — uses every day.

| Section | What it covers |
|---|---|
| **Approvals & Requests** | Multi-step approval workflows with full history: leave, expenses, permission and custom request types |
| **Tasks** | Unit-of-work tracking between employees and managers |
| **Contracts & Documents** | Organised per request, with secure file access |
| **Meetings** | Structured agendas and follow-ups |
| **Attendance & Shifts** | Time records with supervisor corrections |
| **Dashboards** | Live counters for active / pending review / completed items |
| **Notifications** | Deep links to the exact item, with per-user mute preferences |
| **Delegation (Deputy)** | Exact permission matching so a deputy can act with no more and no less than was granted |
| **Password manager integration** | Save passwords reliably from your phone's credential vault |
| **In-app updater** | Self-updates per CPU architecture with gentle rollout flags |

## Installation

Download the right APK from **[the latest release](https://github.com/mohaaw/itqan-releases/releases/latest)**:

| Your device | Download |
|---|---|
| **Modern phones / tablets (2016+)** | `*-new-devices-arm64-v8a.apk` |
| **Older phones (pre-2016)** | `*-old-devices-armeabi-v7a.apk` |
| **Emulators / Chrome*x** | `*-emulators-x86_64.apk` |

Then: Enable "install from this source" → install → open ITQAN. Data and settings are preserved across updates (same signing key). The in-app updater keeps you current from then on.

## Release channels

| Channel | Purpose | Cadence |
|---|---|---|
| **Stable** | Daily-use channel for all users | As needed |
| (in-repo notes) | Changelog history per release | Every release |

Every release notes its build number, target Android version and per-file sha256 checksums for verification.

## Version history (summary)

| Version | Theme | Status |
|---|---|---|
| **1.8.10** | Stability and trust — 26 crash paths closed, dashboard counters honest, cold-start notifications, deputy exact-matching | ✅ Latest |
| 1.8.9 | Security tightening + crash-guard foundation | ✅ Previous |
| earlier | Iterative feature and deployment releases (1.8.0 → 1.8.8) | 🗄 History |

## Privacy & security model

- **Cloud-hosted backend** with per-role database security (row-level access).
- **Signed releases** — every APK is signed with the same production key; an update from the official channel never loses your identity or data.
- **Per-device updater** that downloads only the right CPU build, silently when gentle flags are on, and only ever with your confirmation on device.

## Contact

For questions or support, use the in-app support route or the repository's private channels — public issues on this repo are for release announcements.

---

<div align="center">

*ITQAN · إتقان · ١.٨.١٠*

</div>
