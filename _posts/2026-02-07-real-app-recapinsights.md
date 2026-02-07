---
title: "I Built a Real App Without Typing the Code — AI Did the Implementation, I Did the Engineering (and Product)"
date: 2026-02-07
categories: [engineering, ai, architecture, product]
tags: [ai, copilot, codex, claude, guardrails, product-vision, ux, react, typescript, vite, azure, static-web-apps]
---

I recently built a complete, usable web app — **Recap Insights** — and I didn’t implement it the way I normally would.

Instead, I treated AI models as the *implementation engine*. My role was not just technical steering — it was **engineering + product**:

- I owned the **product vision** (what problem the app solves, who it serves, what “useful” looks like).
- I owned the **architecture and guardrails** (how we build it without turning the codebase into spaghetti).
- I owned **verification** (correctness, consistency, maintainability).

The models did the typing, and they helped a lot with usability and UX direction. I did the steering.

This post is my honest take on what worked, why it worked, and where this approach breaks down (especially in brownfield systems).

<!--more-->

## The project: a real product, not a “Hello World”

Recap Insights is a focused product: it helps runners visualize their training progress and generate recap-style views using data from **Strava** and **intervals.icu**. The frontend is **React + TypeScript + Vite**, hosted on **Azure Static Web Apps**, with a backend/API behind it.

Repo:

- https://github.com/svaza/recap-insights



## The surprising part: I didn’t “code” — I orchestrated product + engineering

When I say I didn’t write code, I mean this literally:

- I didn’t sit down and implement components and services line-by-line.
- I didn’t handcraft every function.
- I didn’t build it the “traditional” way.

What I did instead:

- defined the **product direction** (what features matter, what to cut, what “good UX” means)
- established patterns early (project layout, naming, separation of concerns)
- created **guardrails** so the model could operate safely
- reviewed diffs like I would review a strong senior engineer’s PR
- iterated in small slices and kept scope tight

The AI models (mostly Codex + Opus-class models) produced the bulk of the code. My job was to keep the system coherent and the product useful.



## Product vision is the multiplier

Here’s the part most people underestimate:

### Technical steering alone is not enough

If you only bring engineering, you can still end up with a “working” app that nobody wants to use.

With a clear product vision — even a simple one — these models become much more than code generators. Because they’re trained on a massive set of UX and product patterns, they can help with:

- UX flow suggestions (what should be one click vs two clicks)
- UI structure (layout, information hierarchy)
- microcopy (labels, messaging, empty states)
- edge-case thinking (what happens when data is missing, auth fails, slow network)
- visual polish (spacing, responsiveness, consistency)

But there’s a catch:

**They can propose options. They can’t choose the right product.**

You still need a product north star to decide what matters and what doesn’t.



## The key: guardrails (not “prompt magic”)

This didn’t work because I typed a clever prompt once.

It worked because I treated the codebase like a constrained environment and made the model follow the rules.

I did two things up front.

### 1) Established patterns early

Before “autopilot” was possible, I invested time in shaping the skeleton:

- folder structure
- how API calls are made
- how state is managed
- how errors are handled
- how components are composed
- how configuration flows through the app

Once the structure was stable, the model became dramatically more productive and consistent.

### 2) Enforced those patterns with Copilot instructions

I updated Copilot instructions so the model had persistent guardrails, such as:

- use existing patterns, don’t invent new ones
- prefer consistency over novelty
- touch the minimum surface area
- follow the project’s established conventions
- if something is unclear, ask for the intended pattern first

Your instruction file becomes the project’s **coding standards + architecture memory**.

Without it, the model will ship fast… and quietly increase entropy.



## Autopilot, but with a pilot

After the project reached a stable structure, development started feeling like this:

1. I describe the product change I want (user goal first).
2. The model proposes UX + implementation.
3. I verify it against product intent and architecture.
4. I request adjustments until it fits.
5. I merge only when it’s aligned.

This is important:

- It’s not “AI replaces engineering or product.”
- It’s “AI compresses implementation time when product intent and engineering constraints are clear.”

The models are phenomenal at producing code quickly — but they’re not accountable for long-term maintainability or product coherence. You are.



## Why this worked: scope + context

My strongest observation:

### AI is most effective when the product is thin and scoped

If your application is focused, the model can keep more relevant context in a single working window:

- it can reason about the code it “sees”
- it reuses existing conventions
- hallucinations drop because it doesn’t have to guess across a giant surface area

In practice, a thin app can feel like pair programming with a fast engineering + UX team.

### The opposite is also true

If your system is monolithic or sprawling — not just “monolith” in deployment style, but monolith in *responsibility and scope* — the efficiency curve drops quickly:

- too much code to load into context
- too many overlapping abstractions
- inconsistent patterns
- legacy decisions with missing documentation

At that point, the model becomes less reliable because it is forced to guess.



## Brownfield systems: why teams struggle

This is why many brownfield modernization efforts stall when people try to “add AI”:

1. Unstructured codebases are hard for humans.
2. If humans struggle, models struggle more (because they have less context).
3. Missing documentation forces the model into inference mode.
4. Inference mode increases hallucination risk.

For brownfield success, you need a **context + constraint layer**:

- clear `AGENTS.md` / Copilot instructions
- a lightweight architecture overview
- module boundaries documented
- known invariants (“do not break these”)
- a few ADRs capturing decisions that would otherwise be tribal knowledge

If you don’t do this, the model won’t “understand your system.”

It will generate plausible code that slowly drifts away from how your system actually works.



## The honest trade-offs

This approach is powerful, but it’s not free.

### What you gain

- massive speed-up on implementation
- faster iteration cycles
- lower cost of trying ideas
- faster UX iterations (because changes are cheaper)

### What you still must do (non-negotiable)

- product direction and prioritization
- architecture decisions
- security and privacy thinking
- testing strategy
- code review and correctness verification
- refactoring before entropy builds up
- guardrails and documentation

AI makes building faster. It does not make responsibility disappear.



## My takeaway

A person with minimal coding knowledge but strong product direction *can* build a usable product today — if they:

- keep scope tight
- enforce patterns
- use guardrails
- verify outputs like a serious engineer
- make product decisions continuously (what to build, what to avoid)

But “enterprise-grade” doesn’t come from AI.

It comes from discipline: clear product intent, solid engineering standards, structure, and review.

AI can produce a lot of code fast. The real skill is ensuring that code becomes a product and a system you can live with.



## A simple playbook if you want to try this

- start with a thin product slice (one workflow end-to-end)
- define product outcomes first (user goal, success criteria, what “done” means)
- establish conventions early (structure, naming, patterns)
- encode guardrails into instructions (so they persist)
- iterate in small diffs, review aggressively
- add minimal docs/ADRs as the architecture stabilizes
- treat the model like a fast engineer + UX assistant, not a truth oracle
