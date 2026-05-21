---
title: Public Domain Software Licenses
tags:
  - zapps
  - licensing
---

The standard reflex for an open-source release is to slap on an MIT or Apache 2.0 license. That's fine for most situations, but it's not actually "do whatever you want, no strings attached" — both require preserving the copyright notice in copies and derivatives. For someone who genuinely wants their code to be a public good with **no attribution required**, those licenses still impose friction.

The truly friction-free options are public-domain dedications.

## The licenses ranked by "no strings attached"

### CC0 1.0 Universal — the cleanest public-domain dedication

**Creative Commons Zero** is a legal instrument that waives all copyright and related rights worldwide, as far as the law allows. Anyone can copy, modify, distribute, perform, and use the work — even commercially — without permission and **without giving credit**.

Originally written for general creative works, but it works fine for software. Recognised by SPDX (`CC0-1.0`).

The trade-off: CC0 includes a "patent waiver" disclaimer that some lawyers find ambiguous for software. For pure software releases, The Unlicense is sometimes preferred.

### The Unlicense — software-specific public-domain dedication

A short license specifically written for software, explicitly placing code in the public domain. The core text reads:

> Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software... for any purpose... without restriction.

Recognised by SPDX (`Unlicense`), recommended by some lawyers for software because it was drafted with software in mind.

Functionally equivalent to CC0 for almost all purposes.

### MIT — popular but not "no strings"

Common reflex license. People assume it means "do whatever you want," but the fine print requires that **the copyright notice and the permission notice be included in all copies or substantial portions of the software.**

That's a real attribution requirement. For a serious commercial fork, the attribution is fine. For a one-line library someone copy-pastes into their codebase, the requirement adds friction.

### Apache 2.0

More elaborate than MIT. Adds explicit patent grants and contributor terms. Stronger legal protection for both creator and user. Same attribution-required category as MIT.

### GPL, AGPL — copyleft

Forces derivative works to also be open-source. Strong philosophical statement, but it's *more* friction for forks, not less. If the goal is "anyone, anywhere, can do anything with this," copyleft is the wrong direction.

## How to choose

If the goal is "I am throwing this into the universe, do whatever you want, don't even thank me":

- **CC0** — for general use, including assets and content alongside code
- **The Unlicense** — for pure software releases

If the goal is "use freely, but credit me":

- **MIT** — the standard, minimal-restriction license
- **Apache 2.0** — when patent grants matter

If the goal is "anyone who uses this must also share their changes":

- **GPL / AGPL** — copyleft

## How to apply CC0 or Unlicense

GitHub's "Choose a license" search recognises both. For Unlicense, type "unlicense" into the license search; for CC0, type "CC0" or "Creative Commons Zero". Both will generate the appropriate `LICENSE` file in the repository.

You can also use GitHub's web UI: when creating a new repo, pick the license from the dropdown. It will not appear in the most-common shortlist; you have to type the name.

## Why this matters for Zapps

A [[Zapp Manifesto|Zapp]] is meant to be a gift to the internet. The [[Forking Over Modding|forking pattern]] depends on people being legally free to take, modify, and republish without worrying about attribution chains.

Public-domain dedications remove the legal friction completely. Someone can take a Zapp, turn it into a paid enterprise tool, never credit the original author, and that's fine — the original Zapp remains free for anyone who wants it.

## See also

- [[Zapp Manifesto]]
- [[Forking Over Modding]]
