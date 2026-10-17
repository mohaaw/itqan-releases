# ITQAN — The Operations Platform for Serious Teams
# إتقان — منصّة إدارة العمليات للفرق الجدّية

![Release](https://img.shields.io/badge/release-1.8.10-blue)
![Platform](https://img.shields.io/badge/platform-Android%208.0%2B-green)
![Language](https://img.shields.io/badge/lang-English%20%7C%20العربية-purple)
![Quality](https://img.shields.io/badge/build-verified%20release-brightgreen)

> **"Indeed, Allah loves that when someone does a job, they do it with excellence."**
> **«إن الله يحب أن إذا عمل أحدكم عملاً أن يتقنه»**

Built on the meaning of *iḥsān* — doing things with excellence — **Itqan** is a
complete operations platform that turns company work into clear, auditable,
tracked flow. Every request follows an approval path. Every task has an owner.
Every contract has a paper trail. Every number you see you can trust.

مبنية على معنى **الإتقان** — العمل بإنجاز متقن — تعمل **إتقان** على تحويل عمل
الشركة إلى مسارٍ واضحٍ وقابلٍ للمراجعة: كل طلب له مسار موافقات، وكل مهمة لها
مسؤول، وكل عقد له سجل، وكل رقم تراه يمكن الوثوق به.

**Maintainer / المسؤول:** Mohammed Abdulwahab (itqan-dev) · [v1.8.10 release](https://github.com/mohaaw/itqan-releases/releases/tag/v1.8.10)

---

## Table of contents / المحتويات

| # | English | العربيّة |
|---|---------|----------|
| 1 | [What is ITQAN?](#what-is-itqan) | [ما هي إتقان؟](#ما-هي-إتقان) |
| 2 | [Why ITQAN is different](#why-itqan-is-different) | [لماذا إتقان مختلف؟](#لماذا-إتقان-مختلف) |
| 3 | [The core, module by module](#the-core-module-by-module) | [الجوهر: وحدةً وحدة](#الجوهر-وحدةً-وحدة) |
| 4 | [Security & trust](#security--trust) | [الأمان والثقة](#الأمان-والثقة) |
| 5 | [Architecture & quality gates](#architecture--quality-gates) | [المعمارية وبوابات الجودة](#المعمارية-وبوابات-الجودة) |
| 6 | [Release management](#release-management) | [إدارة الإصدارات](#إدارة-الإصدارات) |
| 7 | [Installation](#installation) | [التثبيت](#التثبيت) |
| 8 | [Roadmap](#roadmap) | [خريطة الطريق](#خريطة-الطريق) |
| 9 | [FAQ](#faq) | [أسئلة متكرّرة](#أسئلة-متكرّرة) |
| 10 | [Support & governance](#support--governance) | [الدعم والحوكمة](#الدعم-والحوكمة) |

---

## What is ITQAN?

ITQAN is a **production Flutter application with a hardened cloud backend** used
daily by real teams to run the internal mechanics of a company: requests,
approvals, tasks, contracts, meetings, attendance, dashboards, roles and
notifications — in one coherent system, in **Arabic-first design** with full
RTL support, on low-end and modern Android devices alike.

Most tools give you a chat window and wish you luck. ITQAN gives you an
**operations spine**:

- **A workflow engine** — requests move between defined steps with a recorded
  actor, timestamp and decision at every hop.
- **A permission model** — roles (owner, super admin, manager, supervisor,
  support, employee) with fine-grained capabilities, plus **deputy
  delegation** with exact-match scoping: a deputy gets precisely the
  permissions granted, nothing more.
- **An audit mindset** — the important actions write history. When someone
  approves, changes, or opens a thing, the record exists.

ITQAN is not a prototype, not a demo, and not a re-skinned form builder. It is
operated as a governed, versioned, security-reviewed product with a staged
release pipeline: **analyze → tests → per-ABI build → checksums →
owner-device verification → public release → measured rollout.**

### Who it serves / لمن صُنعت

| Role | What they get |
|------|----------------|
| **Owner / المالك** | Full dashboards: active, pending-review, completed counts; audit visibility; update control |
| **Super admin / مشرف عام** | User lifecycle, permissions, system notifications, release rollout control |
| **Manager / مدير** | Approval queues, team dashboards, meeting and attendance oversight |
| **Supervisor / مراقب** | Monitors team metrics without needing every permission |
| **Support / دعم** | Assists users, limited scope by design |
| **Employee / موظف** | Submits requests, tracks their contracts and tasks, receives deep-linked notifications |

---

## Why ITQAN is different

ITQAN exists because company operations usually collapse into one of three
patterns — and all three fail in the same place:

| Pattern | What actually happens | What ITQAN does instead |
|---------|------------------------|--------------------------|
| **Chat groups + Excel** | Approvals get lost in message walls; "who approved this?" has no answer | Every decision is a recorded step with actor + timestamp |
| **Generic SaaS crates** | Foreign data jurisdictions, English-first UX, pricing per seat per month | Arabic-first, your data stays under your control, no per-seat telemetry |
| **Custom in-house scripts** | One developer's untested project breaks when they leave | Versioned releases, tested pipeline, documented architecture, checksums |

### The five differentiators / الفروق الخمسة

1. **Operational, not social.** ITQAN runs approvals, contracts and customer
   records — not chatter. Notifications deep-link into the exact task,
   request or contract; nothing important lives in a scrollback.
2. **Arabic-first, really.** RTL layouts, Arabic glossary engraved into the
   glossary (فريق العمل، التفويض، لوحة التحكم…) — not a translation layer
   bolted on. English is fully supported; Arabic is the home tongue.
3. **Data you can account for.** Audit trails, recorded workflow hops,
   corruption-resistant storage. If a number appears, its source can be
   traced.
4. **A release process, not hope.** Analyzer-clean builds, a real device test
   before publishing, per-CPU APKs with published checksums, staged
   (non-forced) updates the owner controls.
5. **Owned by the operator.** Roadmap, quality gates and security posture are
   governed by the maintainer (Mohammed Abdulwahab) — feedback goes straight
   to engineering, through the app or this repo.

---

## The core, module by module

### Workflow & approvals

Requests enter with a defined intent and move through a chain of steps. At
each step: who acted, when, and what the decision was. The dashboard rolls
this up into live counters (active · pending review · completed · returned)
and each card deep-links to the underlying queue.

تتحرك الطلبات عبر سلسلة خطواتٍ محدّدة: من فعل، ومتى، وما القرار في كل نقطة،
وتُلخّصها لوحة التحكم في عدّاداتٍ حيّة قابلة للفحص لحظياً.

### Tasks & work tracking

Unit-level work with owners and status. You see what's pending and what's
done, grouped by person or by time. Nothing is "verbally assigned" —
assignment itself is a record.

### Contracts & documents

Requests carry contracts and attachments with structured history. Opening a
mid-process record shows a clean state — not an error screen — while the
content keeps loading in the background.

### Meetings

Structured sessions with agendas and follow-ups — minutes become tasks, not
memories.

### Attendance & presence

Live presence (online-now, active NOW, who's in), attendance records and
reporting. A supervisor can see the day at a glance and correct anomalies
 responsibly.

### Dashboards & insights

- Real counters for active / pending review / completed.
- **The active sessions tile** — who is signed in right now.
- **AI-assisted todo suggestions** — the system surfaces a draft to-do list
  from your incoming work; you approve it, it joins your task list.
- Notification inbox with a live badge and deep links.

### Deputies & delegation

Delegation is **exact-match**: a deputy receives the exact permissions the
grain of the delegation allows — no broad "trust me" cracks. The audit trail
distinguishes the actor from the delegated persona.

### Admin & user lifecycle

Creating and managing users with role-based access, password-change flows,
delegation, and system-level configuration — all behind the platform's
permission model (53 verified permission keys at the time of v1.8.10).

---

## Security & trust

| Practice | What it means for you / بالنسبة لك |
|----------|-------------------------------------|
| Encryption in transit / تشفير أثناء النقل | All backend traffic runs over encrypted connections |
| Fine-grained access / صلاحيات دقيقة | Row-level security: a role sees only what belongs to its scope |
| Full audit trail / سجل تدقيق كامل | The important actions write history that cannot be quietly erased |
| Verified releases / إصدارات موثّقة | Every APK ships with a published sha256 checksum |
| Staged updates / تحديثات مرحّلية | Updates are **not forced** — the owner decides the cadence |
| No telemetry resale / لا بيع بيانات | Your operation records serve your operation — nothing else |

*(For security-review requests, contact the maintainer directly — see
Support below. Security findings are accepted with thanks.)*

---

## Architecture & quality gates

ITQAN is a single **Flutter** codebase compiled natively for Android
(arm64-v8a / armeabi-v7a / x86_64) with a **hardened cloud backend** that
enforces row-level security and a realtime layer for live data.

Every release passes these gates before it reaches your device:

1. **Analyzer clean** — zero errors, zero warnings on the full source tree.
2. **Feature tests** — the touched areas carry executable tests.
3. **Three ABI builds** — split per CPU so devices download only what they need.
4. **Checksums published** — sha256 for every artifact in the release notes.
5. **Real-device verification** — cold start, login, dashboard, notification
   badge and realtime tiles are exercised on a physical phone before publish.
6. **Staged rollout** — update rows are written with gentle (non-forced) flags.

This is a working process, not a marketing slide — every version's history is
documented in this repository's release notes.

---

## Release management

| Version | Date | Theme |
|---------|------|-------|
| **1.8.10 (build 2055)** | 17 Oct 2026 | **Stability & Trust** — 26 crash paths closed; counters fixed; password capture; deep-link precision; hardened connections |
| 1.8.9 (build 2054) | 15 Oct 2026 | Hardening wave — permission model, dynamic forms, dialog fixes |
| 1.8.6 (build 2051) | 27 Sep 2026 | Header metrics + audit fixes |
| 1.8.5 (build 2050) | 21 Sep 2026 | Processing resilience + polish |
| 1.8.4 (build 2049) | 12 Sep 2026 | Approval-flow repairs + dashboards |
| 1.8.3 (build 2048) | 10 Sep 2026 | Stability round 2 |
| 1.8.2 (build 2047) | 8 Sep 2026 | Stability round 1 |
| 1.8.1 (build 2046) | 6 Sep 2026 | Rebuilt lineage |
| 1.8.0 (build 2045) | 27 Aug 2026 | Baseline |

*Full per-version release notes live in the [releases](https://github.com/mohaaw/itqan-releases/releases) section.*

### The release process in one paragraph

The engineering chain runs analyzer and feature tests, produces the three
CPU-split, checksum-verified APKs, then the maintainer installs and exercises
the build on a real device before anything is published. Publishing writes a
public release with rich notes, then updates the rollout rows so existing
users receive the update through the in-app updater — flagged non-mandatory
until the owner explicitly decides otherwise. If anything is uncertain, the
release is held, not shipped. **Stability outranks momentum.**

---

## Installation

Almost always, one of the first two files is what your device needs:

| File | For | Size / الحجم | sha256 |
|------|-----|---------------|---------|
| `itqan-1.8.10+55-new-devices-arm64-v8a.apk` | Modern phones (2016+) / الأجهزة الحديثة | 73.1 MB | `39c64135…cc5346` |
| `itqan-1.8.10+55-old-devices-armeabi-v7a.apk` | Older phones / الأجهزة القديمة | 61.9 MB | `43cc836…cac53` |
| `itqan-1.8.10+55-emulators-x86_64.apk` | Emulators / المحاكيات | 77.7 MB | `ea1f8a3…87174` |

1. Download the APK that matches your device.
2. Allow "install from this source" once (first-time only).
3. Install — your data and settings are preserved (the signature and
   namespace stay the same as previous versions).
4. Open the app; subsequent updates arrive through the safe in-app updater.

**Verify (optional but professional):**
```
39c64135bd76fdd5a9485035fc7aefe78a3868bc415f382349c26c87d6cc5346  itqan-1.8.10+55-new-devices-arm64-v8a.apk
43cc836650c48d7d4fe970ee9a73529348c4280cc411dbacd2596864f02cac53  itqan-1.8.10+55-old-devices-armeabi-v7a.apk
ea1f8a3b4f00c59929181aa54fb273b1d2ecc4a7619169a6193217f714187174  itqan-1.8.10+55-emulators-x86_64.apk
```

---

## Roadmap

The master plan (owner-approved) sequences the platform in tiers:

| Tier | Module | Status |
|------|--------|--------|
| 0 | Client & platform hardening | ✅ Shipped iteratively |
| 1 | **Learning Management (LMS)** | Planned — next |
| 2 | **Chat** | Planned |
| 3 | **HR** | Planned |
| 4 | **CRM** | Planned |
| 5 | **Finance** | Planned |
| 6 | **POS / Inventory** | Planned |
| 7 | **Super-admin analytics** | Planned |

Nothing ships to these tiers while a stability debt exists in the shipped
modules — the platform's promise is **core first, modules second**.

---

## FAQ

**Q: Is my data private? / هل بياناتي خاصة؟**
Yes — your management records serve your operation. There is no telemetry
resale and no third-party analytics marketplace.

**Q: Forced updates? / تحديثات إجبارية؟**
No. Updates are staged and non-forced. The maintainer decides the cadence.

**Q: Which APK do I download? / أي حزمة أختار؟**
If your phone is from roughly 2016 onward: `arm64-v8a`. Older devices:
`armeabi-v7a`. Emulators: `x86_64`. When in doubt, install the arm64 build.

**Q: Will my data be lost if I update? / هل ستفقد بياناتي عند التحديث؟**
No — the update is signed with the same key and namespaces as the previous
version; data and settings are preserved.

**Q: What do I do if I find a bug? / ماذا أفعل إذا واجهت خللاً؟**
Report through the app's support flow or open an issue in this repository.
Stability reports are treated as priority items.

**Q: Is there an iOS version? / هل هناك نسخة آيفون؟**
The current focus is Android 8.0+; the roadmap considers additional
platforms after the planned tiers.

**Q: Where do the checksums come from? / من أين تأتي مجاميع التحقق؟**
From the release build machine, published per version in the release notes —
same values as the ones printed in this document's table.

**Q: Who is behind ITQAN? / من وراء إتقان؟**
The maintainer, Mohammed Abdulwahab (itqan-dev), with direct oversight of
engineering, quality and security discipline.

---

## Support & governance

- **Product owner & maintainer:** Mohammed Abdulwahab (itqan-dev)
- **Public releases:** https://github.com/mohaaw/itqan-releases/releases
- **Security reports:** contact the maintainer directly — coordinated disclosure, no public shaming
- **Business enquiries:** reach out through the app's support channel

> **A note on honesty.** This README describes only what is live today. When
> a module is planned, the table above says "Planned" — not "coming soon"
> with a vague deadline. Trust is earned through truthful releases,
> checksummed artifacts and a tested process — that is the core of the
> platform, and it is what **إتقان** means.

---

## إتقان — نظرة عربية شاملة

**إتقان** منصةٌ تشغيليةٌ لإدارة شؤون الشركات: الطلبات الموافقات، المهام،
العقود، الاجتماعات، الحضور، المؤشرات، الأدوار، والإشعارات — في نظامٍ واحد
مؤسسي، مصمّم عربياً أولاً (RTL كامل) ويعمل على كل أجهزة أندرويد.

### لماذا إتقان؟

- **كل قرار له سجل** — الموقف الموافقات لا يضيع في جدران الرسائل.
- **صلاحيات دقيقة** — أدوار واضحة (مالك، مشرف عام، مدير، مراقب، دعم، موظف)
  بالإضافة إلى **التفويض** القائم على مطابقة تامة.
- **عربي أصيل** — واجهة من اليمين إلى اليسار بنيةً أولية لا بترجمةٍ لاحقة.
- **إصدارات موثّقة** — مجاميع تحقق sha256 لكل حزمة، وتحديثات مرحّلية غير
  إجبارية.
- **هندسة عربية للعمليات** — سير العمل، العقود، الاجتماعات، الحضور،
  المؤشرات الحيّة، والإقترحات الذكية للمهام.

### الوحدات الحيّة / CORE MODULES

| الوحدة | ما تقدّمه |
|--------|-----------|
| سير العمل والموافقات | خطوات مسجّلة: من فعل، ومتى، وما القرار |
| المهام | عمل مؤسسي بمسؤولٍ وحالةٍ وتجميعٍ حسب الشخص أو الوقت |
| العقود والمستندات | سجل منظم للمرفقات وحالات المعالجة |
| الاجتماعات | جداول مع وقائع ومهام متابِعة |
| الحضور | حضور حيّ، سجلات يومية، تقارير |
| لوحة التحكم | عدّادات حيّة: نشط / معلّق للمراجعة / مكتمل + تشاركات الدخول النشطة + اقتراحات AI للمهام |
| التفويض | منح مطابق تماماً وبدون تفضيلات زائدة |
| الإدارة | إنشاء المستخدمين، الأدوار، تغيير كلمات المرور، إعدادات النظام |

### الأمان / SECURITY

يعمل كل الاتصالات مشفّرة، والصلاحيات مُحصّنة على مستوى الصفوف، وكل إجراء
مهّم يُسجل تدقيقاً كاملاً. الإصدارات موثّقة بمجاميع sha256 المطبوعة في صفحة
كل إصدار، والتحديثات مرحّلية وغير إجبارية.

### التثبيت

اختر الحزمة المطابقة لمعمارية جهازك من الجدول أعلاه، اسمح بالتثبيت من
المصدر مرة واحدة، لا التحديثات لاحقة تصل عبر مُحدّث التطبيق الآمن. بياناتك
وإعداداتك محفوظة إذا حدّثت فوقها.

### خريطة الطريق

بعد تثبيت الأساس التشغيلي الحالي، تتوسّع المنصة عبر: إدارة التعلم (LMS)،
ثم الدردشة، ثم الموارد البشرية، ثم إدارة العملاء (CRM)، ثم المالية، ثم
المخازن ونقاط البيع، ثم تحليلات ذكاء الأعمال للمشرف العام.

> **رمز تواضع الحقيقة:** لا نصِف ما لم يُنجز، ولا نُطلق بعِلم خلل. كل
> إصدار يُختبر على جهازٍ حقيقي قبل النشر. الثقة تُبنى بالصدق والقياس،
> وهذا هو معنى **إتقان**.

---

## The v1.8.10 release, in detail

What actually changed, and what it took:

| Change | User-visible effect | Engineering depth |
|--------|---------------------|-------------------|
| 26 crash paths closed | Opening a mid-process request/contract shows a clean state instead of an error screen | Across approval, request and task flows; every empty state designed, none left to luck |
| Dashboard counters fixed | Active / pending-review / completed now match the real work | Filter logic rebuilt and re-verified against live data |
| Password capture fixed | One-tap save from the password manager works reliably | The autofill lifecycle is now finalised at the right moment |
| Deep links precise | Tapping a notification opens the exact task/request/contract | Cold-start race eliminated — the link resolves after, not before, bootstrap |
| Deputation exact | Deputies act with precisely the granted scope | Permission check re-mapped to the granted set, no inheritance surprises |
| Security posture improved | Safer transport, stricter input validation | Backend request throttling tightened; malformed payloads rejected early |

*In addition, this release introduced the rich public release page and this
repository's English-Arabic README — part of the platform's public story.*

## Tech stack & dependencies

| Layer | Choice | Why |
|-------|--------|-----|
| Client | **Flutter** (Dart) | One codebase; native-compiled per CPU; full RTL/Arabic |
| Backend | Managed Postgres-style cloud with **row-level security** | Data integrity enforced at the storage layer, not in the UI |
| Realtime | Live subscriptions (presence, inbox, counters) | The dashboard reflects reality, not a cached snapshot |
| Notifications | Deep-linked push + tray + badge | The right info, at the right screen |
| Packaging | Split per ABI with published sha256 | Only-the-needed download; verifiable artifacts |
| Updates | In-app staged updater (non-forced by default) | Control stays with the operator |

*(External service details and endpoints are deliberately not published here —
public docs describe capabilities, not attack surface.)*

## Deployment model

A production posture, operated as a living system:

- **Single maintained production fleet** — one backend, versioned client apps.
- **Releases are events with history** — every version has notes, checksums
  and a dated record in this repository.
- **Rollback discipline** — every change carries its undo story; publishing
  happened only after the owner-device test says PASS.
- **The release cadence is honest** — small verified steps ship faster than
  a bloated high-risk version.

## Quality metrics, reported per release

Each release carries measurements — not vibes:

| Gate | Standard | v1.8.10 result |
|------|----------|----------------|
| Static analysis | 0 errors / 0 warnings | ✅ |
| Feature tests | Executable tests pass | ✅ |
| Crash paths verified | The fix list is testable | ✅ 26 paths |
| Release packaging | 3 ABIs + checksums | ✅ 73.1 / 61.9 / 77.7 MB |
| Owner-device test | Cold boot, dashboards, realtime, badge — on physical hardware | ✅ Redmi Note 10 Pro, Android 16 |
| Update rollout | Non-forced flags on release rows | ✅ |

## Contributor glossary / معجم المساهمين

| Term | Meaning |
|------|---------|
| Request / طلب | A formal ask (leave, expense, permission, custom) moving through steps |
| Approval hop / نقطة موافقة | One decision point recorded with actor + timestamp |
| Deputation / التفويض | Delegated authority with exact-scoped permissions |
| Presence tile / لوحة الحضور | Who is signed in, now |
| Rollout rows / صفوف التوزيع | Update records that drive the in-app updater |
| Owner-device test / اختبار جهاز المالك | The physical-phone verification before publishing |

## Contributing

This repository is the **release channel** — issues and release questions
belong here; engineering lives in the private source repo.

- Found a bug? Open an issue with what you did, what you expected, and what
  happened. Screenshots help. New versions' crash reports carry extra
  weight if they mention the exact step.
- Have a feature idea? Attach it to the core module it affects (workflows,
  contracts, meetings, attendance) rather than as a standalone tool.
- Security concern? Contact the maintainer directly — coordinated
  disclosure first.

## Acknowledgment / شكر

To the teams who chose to run their operations with **إتقان** — your daily
usage is the platform's real test suite. The meaning of the name is the
standard by which every release is judged: **done, properly, verified.**

---

**Mohammed Abdulwahab** (itqan-dev) · ITQAN — إتقان · *An operations platform that respects the meaning of its name.*


