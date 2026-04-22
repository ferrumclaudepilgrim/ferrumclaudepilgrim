<div align="center">
  <img src="https://ferrumfluxfenice.com/logo.png" width="180" alt="Ferrum Flux Fenice / Pilgrim" />

  # Hi, I'm Erin

  *40 years old. A GED. 25 years serving others. One AI chat lit something*
  *that hasn't gone out. I'm not special. I won't quit. Watch me figure it*
  *out... or not.*

  **BUILDER · WRITER · AI INFRASTRUCTURE**

  [![Main site](https://img.shields.io/badge/site-ferrumfluxfenice.com-F4622A?style=flat&labelColor=0A0B0E)](https://ferrumfluxfenice.com)
  [![Dev site](https://img.shields.io/badge/dev-ferrumclaudepilgrim.com-F4622A?style=flat&labelColor=0A0B0E)](https://ferrumclaudepilgrim.com)
  [![Email](https://img.shields.io/badge/email-ferrumfluxfenice%40gmail.com-5AABFF?style=flat&labelColor=0A0B0E)](mailto:ferrumfluxfenice@gmail.com)
  [![Main account](https://img.shields.io/badge/main_account-%40FerrumFluxFenice-5AABFF?style=flat&labelColor=0A0B0E)](https://github.com/FerrumFluxFenice)
</div>

---

This is my mobile dev account. Most of my open-source work lives here,
done from a Samsung Galaxy S26 Ultra running Termux. After the AI chat
that started it, I built my own PC, took Anthropic's AI Fluency and
Google's AI Essentials, killed a vibe-coded hex puzzle game, and have
been getting less wrong since.

I run a six-device home lab connected over Tailscale: two Android phones
(a Samsung Galaxy S26 Ultra and a Google Pixel 10 Pro on Android 17 Beta,
paired so I can test cross-vendor on every Android change), a Windows
desktop with an RTX 5070 for inference and Docker builds, a Windows
laptop for mobile work, an Ubuntu VPS for persistent services, and a
Chromebook running Debian inside Crostini.

On the Samsung phone, I run a Claude Code setup with multiple specialist
agent roles for different concerns. One plans, one writes code, one
documents, one keeps the repo clean, one researches, one handles
audience-facing work. Session hooks enforce safety rules before any
git commit or push. Every non-trivial call I make gets written down,
both the wins and the bail decisions, so I can check my own reasoning
later and so anyone reading along can follow how I got there.

The recovery infrastructure was proven for real a couple weeks ago when
an agent script wiped my Android home directory by mistake. Everything
that mattered was already tracked in git, every device knew about every
other device, and the whole system could be reproduced from a fresh
phone with a clone and an install script. Total recovery time was under
a day. I'd built the infrastructure before I needed it.

That's the kind of work I do. AI-assisted, fully disclosed, choices and
on-device verification mine.

---

## Selected upstream contributions

### `termux-packages` · 3 PRs · 1 merged · 2 approved-open

#### [PR #29123](https://github.com/termux/termux-packages/pull/29123) · `fix(main/cups)` · MERGED

Web UI permissions and missing runtime dirs for CUPS printing on Termux.

> Merged by maintainer **TomJo2000** on 2026-03-28.

#### [PR #29074](https://github.com/termux/termux-packages/pull/29074) · `enhance(main/pulseaudio)` · APPROVED

AAudio source module for microphone input. Enables real-time audio recording on Android via PulseAudio.

> "Audio quality very good." — maintainer **robertkirkman**, after on-device tests on Android 8 and Android 13.

#### [PR #29319](https://github.com/termux/termux-packages/pull/29319) · `addpkg(main/oboe) + openal-soft + pulseaudio` · APPROVED

3 commits, 1052+/5−. First time Google's Oboe library has been packaged for a Linux-style package manager outside Android Studio. Adds Oboe backend in openal-soft and PulseAudio Oboe sink/source modules.

> "This works for me and it fixes the problem with openal-soft on certain devices." — maintainer **robertkirkman**.

### Investigative comments

| Thread | What I did |
|---|---|
| [termux-packages#29336](https://github.com/termux/termux-packages/issues/29336#issuecomment-4274862785) | Identified upstream Neovim regression commit `142f914089` via source-trace bisection. Verified by maintainer within 4 hours. |
| [termux-app#5086](https://github.com/termux/termux-app/issues/5086#issuecomment-4294194568) | Paired-device A/B (Pixel 10 Pro stock vs S26 Ultra OneUI) isolating Samsung's policy as root cause. Followed up with a test APK that quantified the only viable elevation pattern at exactly **1.50× CPU throughput** under load. |
| [termux-packages#28898](https://github.com/termux/termux-packages/issues/28898#issuecomment-4148528200) | First reproducible workaround for a multi-year cluster of Samsung sleep issues. Two-command ADB fix with full mechanism trace through AOSP `WifiStateMachine` plus Doze eBPF cgroup filters. |
| [tailscale#12090](https://github.com/tailscale/tailscale/issues/12090) | Four cold-boot tests on the Chromebook above, captured strace of the cros-garcon NULL-deref after NETLINK enumeration, disproved two in-thread workarounds. Followed up with feature-request issue [tailscale#19488](https://github.com/tailscale/tailscale/issues/19488). |

### Public repo · `claude-code-android` · ★30

[`ferrumclaudepilgrim/claude-code-android`](https://github.com/ferrumclaudepilgrim/claude-code-android). Native Termux installation guide and Claude Code recovery infrastructure. When upstream Claude Code v2.1.113 broke every Termux user, shipped v2.7.0 emergency pin within 8 hours. Repo absorbed ~20× baseline clone traffic during the break.

---

## How and why I work this way

The lab, the agent system, and the habit of writing down my reasoning
aren't a flex. They're the conditions that make contributing possible
from where I'm starting. Cross-vendor testing only exists because the
lab exists. Honest comments only exist because the written record holds
me accountable to my own thinking. The recovery infrastructure exists
because I broke things on the way here and am going to break things again.

A few examples of how this plays out, since process language without
specifics is just process language:

- I bailed cleanly on a frida investigation last week when an internal
  audit showed the real time budget was 6 to 13 hours instead of the 1
  or 2 I had estimated. The work was captured for future reference, not
  abandoned.
- I held scope on the AAudio PR when a maintainer offered to expand it
  to upstream PulseAudio. Merge risk on the already-approved PR wasn't
  worth the new ground. The expansion got its own future-workstream entry.
- I caught a four-year framing error in my own PipeWire prep plan before
  opening the workstream, by running a basic "what's already in the tree"
  check before doing the activity-signal research that had been the plan.

AI assistance is the tool I use everywhere. The choices, the on-device
verification, and the corrections are mine. When I get something wrong
(and I do), the correction is in the same thread.

---

## Where I'm still learning

The OSS work is one face of a larger thing. Actively building skills
across the territory I'll need for the next chapter.

- **Coursework completed:** Anthropic AI Fluency, Google AI Essentials,
  100+ hours of Coursera across AI/ML and adjacent topics
- **Currently studying:** CompTIA Security+ (cert prep, active)
- **Daily scripting practice** in PowerShell, bash, and Python. AI-assisted,
  but the AI is the tutor as much as the tool. Every script I write, I
  ask why each piece works the way it does, then read the docs to
  confirm. Goal is to write scripts I can defend without consulting the
  AI afterward.
- **Writing down the reasoning behind every non-trivial call I make** is
  itself a learning practice. Forcing the articulation surfaces the gaps
  in my understanding before they ship.

I am not a developer. I am someone who is learning to do the work, using
every tool that helps without pretending the help isn't there.

---

## Why I publish all this

Two reasons.

One, I'm learning out loud. The notes I keep and the public comments I
post are notes I write to my future self, but they're also notes anyone
else can read. Someone going through the same path I went through (no
CS degree, learned AI from scratch in the last year and a half, trying
to ship real work) might find the trail useful.

Two, I want to be wrong publicly so I can stop being wrong faster. The
honest AI-disclosure pattern, the bail decisions, the "happy to be
wrong" framings exist because someone catching me means I get to learn
something. If you read something I posted that's mistaken, please tell
me.

---

<div align="center">

**Building in public. Pensacola, FL.**

</div>
