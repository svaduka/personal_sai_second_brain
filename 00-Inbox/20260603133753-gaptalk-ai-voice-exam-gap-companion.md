---
title: GapTalk — AI Voice Companion for Exam Gap Learning
created: 2026-06-03 13:37:53
modified: 2026-06-03 13:37:53
tags:
  - status/draft
  - type/idea
aliases:
  - GapTalk
  - AI voice learning companion
---

# GapTalk — Learn What You Don't Know

## Context

> Where did this idea come from? What prompted you to capture it?

- **Origin**: Personal insight — evolved from [[report-card-based-personalized-learning-app]]
- **Date captured**: 2026-06-03
- **Why now**: The parent idea (report card learning app) kept growing broader. GapTalk is the focused, actionable product distillation — a daily habit product, not a platform.

## Main Idea

> The core concept in your own words. One atomic idea.

Everyone studies, but nobody studies what they actually got wrong. Exams reveal gaps — and those gaps are ignored. GapTalk is a daily 15-minute AI voice companion that reads your exam paper, finds your specific gaps, and talks to you every single day until those gaps are gone.

## Problem Statement

> What problem is this solving?

Exams reveal exactly where a student or professional is weak. But after the exam, most people either:
1. Move on without addressing the gaps
2. Re-study everything instead of only what they got wrong
3. Have no one to explain the specific thing they missed

The gap becomes permanent. GapTalk closes the gap through daily, personalized, conversational repetition.

## Supporting Details

> How it works — the core flow

```
1. SCAN       → Upload your exam / test paper photo
2. ANALYZE    → AI reads your mistakes and weak areas
3. PLAN       → Builds your personal learning path
4. TALK       → 15 min daily AI voice conversation
5. TRACK      → Shows your progress week by week
```

**Why 15 Minutes:**
- Small enough to do daily without friction
- Large enough to compound meaningfully over weeks
- Feels like a personal tutor, not a classroom

**Who It's For:**
- Students who failed or underperformed in a subject
- Professionals with certification or knowledge gaps
- Anyone who wants to truly understand, not just pass
- Not just kids — everyone

**The Core Vow:**
> *"Every day, 15 minutes. By the end of the month, the gap is gone."*

**Tech Stack (MVP):**
- **Claude** → reads scanned papers, identifies gaps, drives conversation
- **AI Voice** → ElevenLabs or Azure Speech for voice delivery
- **Scheduler** → Power Automate daily trigger
- **Storage** → SharePoint / OneLake

**Week 1 MVP Build:**
- [ ] Upload scanned paper
- [ ] Claude identifies top 3 gaps
- [ ] Generate Day 1 voice conversation script
- [ ] Deliver via automated voice call or audio file

**The Bigger Vision:**
> *Not an app. A daily habit. A companion that knows exactly where you struggle and shows up every single day until you don't struggle anymore.*

## Differences from Parent Idea

> How GapTalk differs from [[report-card-based-personalized-learning-app]]

| Dimension | Learning App (Parent) | GapTalk |
|-----------|----------------------|---------|
| Audience | Kids (primary) | Everyone — students + professionals |
| Delivery | TV-based platform | Daily AI voice conversation |
| Teachers | Creator marketplace | Not needed (AI-driven) |
| Business model | Platform + teacher pay | TBD — subscription? per-gap? |
| Tech | Local specialized LLM | Claude API + voice |
| Scope | Full learning platform | Single focused habit loop |
| MVP timeline | Months | Week 1 prototype possible |

## Connections

- **Evolved from**: [[report-card-based-personalized-learning-app]]
- **Related to**: AI-powered personalized learning
- **Related to**: Habit formation through daily micro-sessions
- **Related to**: Voice as a learning interface

## Questions

> What remains unclear or worth exploring further?

- Business model — subscription per student? Per gap closed? Freemium?
- How does the AI voice conversation actually adapt day-to-day based on progress?
- What subjects/domains to support first? (Math? Language? Certifications?)
- How to handle multiple gaps — prioritize or tackle in parallel?
- What does "gap is gone" mean technically — quiz score threshold? Conversation fluency?
- Is the voice call outbound (system calls student) or inbound (student opens app)?
- Privacy: student exam papers contain personal data — how is this handled?
- Can this work offline or in low-connectivity environments?

## Next Steps

- [ ] Break Week 1 build plan into daily tasks
- [ ] Define what a "gap" looks like as a data structure (topic, question, misconception)
- [ ] Prototype Claude prompt: scan paper → identify top 3 gaps → generate Day 1 script
- [ ] Decide: voice call delivery vs. audio file vs. in-app conversation
- [ ] If pursuing: move to `05-Projects/2026-06-GapTalk/`

---

## Metadata

**Status**: #status/draft
**Type**: Inbox capture (product concept)
**Review Date**: Process during next weekly review
