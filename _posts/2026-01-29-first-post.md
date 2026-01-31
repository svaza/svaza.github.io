---
layout: post
title: "My default Azure architecture decision checklist"
categories: [azure, architecture]
---

When I’m unsure, I want a checklist, not vibes. Here’s my baseline.

<!--more-->

## 1) Clarify the “blast radius”
- Single app? Multi-tenant platform?
- Data isolation requirements?

## 2) Define non-negotiables
- RPO/RTO
- Security boundaries (private endpoints, identity, secrets)
- Cost ceiling

## 3) Pick the simplest deployment that meets constraints
Start with boring. Add complexity only when requirements force it.
