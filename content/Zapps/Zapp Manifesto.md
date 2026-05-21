---
title: Zapp Manifesto
tags:
  - zapps
---

## The current situation

Making software tools used to be expensive. Servers, infrastructure, operations, and ongoing maintenance all cost real money. Because of that cost, most tools ended up following one of two paths:

1. **Free tools as services.** Give the tool away, but turn it into a service: require accounts, track behavior, collect data, sell insights or attention to someone else.
2. **Paid SaaS tools.** Charge users continuously: lock data into proprietary systems, make leaving painful, keep adding features to justify rent.

In both cases the tool stopped being just a tool. It became a relationship, an obligation, a dependency. This wasn't malicious. For decades it was often the only way to survive.

## Where this trend leads

The justifications for these patterns are weakening fast. With AI dramatically reducing the cost of building software, distribution effectively free, and modern static hosting (GitHub Pages, Cloudflare Pages) absorbing the long-tail of serving cost:

- Harvesting user data is no longer necessary to subsidise development
- Forcing accounts is no longer needed to recoup infrastructure costs
- Charging ongoing rent for a finished tool is no longer the only way to recover development effort

But most tools still default to these patterns, because the patterns are familiar. Without a deliberate shift, the trajectory is more services pretending to be tools, more data collection with less justification, more user lock-in by default.

## The idea behind Zero Apps

**Zero Apps**, or **Zapps**, start from a simple question:

> What would a software tool look like if it imposed zero ongoing obligations on the user?

A Zapp is not anti-cloud, anti-business, or anti-modern. It is software that refuses to create dependency where none is required.

## Core idea

A Zapp is a tool, not a service.

It is:

- Complete at install time
- Usable without permission
- Blind to its users

The app may have state. The user may have identity. But the maker has **zero knowledge** of either.

## The Six Zeros

These aren't features. They are design constraints.

1. **Zero accounts** — No sign-up, no login, no identity known to the maker.
2. **Zero observation** — No tracking, analytics, telemetry, crash reporting, or behavior logging.
3. **Zero backend dependency** — No required servers to function.
4. **Zero network dependence** — Works fully offline after install.
5. **Zero rent** — No ads, no subscriptions, no attention extraction. Voluntary donations only.
6. **Zero lock-in** — Data is exportable to open, human-readable formats. Users own their state.

If removing the developer's servers breaks the app, it is not a Zapp.

## Why these constraints matter

Constraints force better design.

- When accounts are removed, identity must be rethought.
- When servers are removed, state must become explicit.
- When tracking is removed, incentives become honest.

The question shifts from "how do we keep users and monetize attention?" to "how do we make a good tool?"

## What Zapps are not

- Not minimal for the sake of minimalism
- Not toys or demos
- Not anti-updates or anti-payments
- Not anti-identity (Zapps are *maker-blind*, not user-less)

A Zapp can be sophisticated, beautiful, and feature-rich. It just refuses to require a relationship after install.

## Why this matters now

As the cost of building software approaches zero, the cost that remains is increasingly imposed on the user: through surveillance, lock-in, and rent-seeking. Zapps argue that this cost is no longer inevitable.

We can build tools that:

- Respect users by default
- End cleanly when the user is done
- Work without permission
- Remain useful even if the maker disappears

Not everything needs to be a service. Some things can just be tools again.

## A simple test

If the app:

- Needs to know who the user is
- Needs to watch how it's used
- Needs a server to stay alive

It is not a Zapp.

If it works, silently, on its own — it probably is.

## See also

- [[Zapp Architecture Patterns]]
- [[Zapp Data Formats]]
- [[Why Buy Once Software Died]]
- [[Forking Over Modding]]
- [[Public Domain Software Licenses]]
- [[Zapp Cursor Rules]]
- [[Local-First Philosophy]]
