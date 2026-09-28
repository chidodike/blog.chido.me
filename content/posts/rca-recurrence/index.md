---
date: '2026-10-05T09:00:00+01:00'
draft: true
title: 'RCA That Actually Cuts Recurrence'
cover:
  image: "rca-recurrence-header.png"
  alt: "Same ticket category reopening beside a root-cause board with a named owner and a closed loop"
  relative: true
  hiddenInSingle: false
tags: ["ITSM", "ServiceDesk", "RCA", "IncidentManagement", "Leadership", "DEX"]
---

## The Ticket That Came Back With a New Number

Picture this. It is Tuesday, 11:40. The major-incident bridge closed yesterday with a clean timeline, a polite “thanks everyone,” and a promise that root cause would follow. Today the same symptom is back — different ticket number, same category, same angry colleague who already told the story once.

Your queue looks busy in the right way. Your problem record looks complete in the wrong way. There is a five-whys slide, a parking-lot action that says “engage vendor,” and no owner with a date when the Monday morning version of this failure stops.

This is not missing RCA. This is **RCA theatre**.

## RCA Is Leadership Practice, Not a Ritual

I have led IT Service Desk work across EMEA and APAC where follow-the-sun handoffs, vendor bridges, and recurring noise are part of the week. Root cause analysis is not a compliance checkbox after Severity 1. It is how you decide whether next month’s desk is quieter than this month’s — or only better at writing post-mortems.

A closed problem with no change is still an open wound. The clock on the major can look green. The colleague who cannot work still lives with the same failure under a new ticket ID.

We already know green SLAs can hide angry Mondays. Recurrence is how that lie compounds: every reopen, every “explained twice,” every VIP side channel that starts because the main path failed the same way last week. If VIP support without a named path creates a shadow helpdesk, RCA without an owner creates a **shadow backlog** — issues everyone remembers and nobody is paid to finish.

In one of the environments I have led, partnering across Network, Security and Engineering on root cause cut recurring incidents on the order of a third. The number is not the point. The practice is: treat RCA as work that changes the estate, not as a meeting that closes a problem record.

## What Good Looks Like

A healthy RCA model is unglamorous. It fits inside Jira Service Management (or whichever ITSM you use) the same way a VIP path does — visible, owned, measurable.

What good looks like in practice:

- **One named owner.** Not a team name. A person who can say yes or no to the fix, with a date. If ownership is “the platform team,” it is nobody until Monday.
- **A cause you can falsify.** “Intermittent network” is a shrug. “DHCP lease race on VLAN X after change Y” is something you can prove wrong — or fix.
- **A change that ships.** Patch, policy, Intune profile, runbook, vendor config, capacity. If the only output is a slide, you held a retrospective, not an RCA.
- **Knowledge back to the desk.** Known error, article, or a one-line handoff note for follow-the-sun: what it looks like, what not to try again, when to escalate. Privilege that never teaches the desk is expensive silence; RCA that never teaches the desk is expensive memory.
- **A stop-the-bleed metric.** Recurrence rate for that category, reopen rate, or “same user, new ticket within seven days.” Pair it with one experience check — time to useful work or “explained twice” — so green problem closures do not become another watermelon chart.

Tickets can have priorities. Recurring pain needs a **contract**: owner, falsifiable cause, change, knowledge, measure.

## The Parking-Lot Trap

Here is the practical nuance most teams miss.

You can run every major through a textbook RCA template and still teach the organisation that the real work ends when the bridge ends. Analysts learn to capture timelines. Managers learn to defend “we did RCA.” Vendors learn that “under investigation” is an acceptable forever state.

That is the **Parking-Lot** trap. Not laziness. Ritual without a finish line. The cousin of Zero Trust still applies: trust nothing that is not verified — including the assumption that a completed RCA form means recurrence will fall. Then get out of the way: Zero Friction for the colleague who just wants the failure to stop repeating.

The other trap is treating every ticket as unique. Volume reporting that ignores same-category clusters will keep your major-incident count tidy and your week noisy. Users do not experience your problem workflow. They experience whether the same Monday returns.

Shadow RCA burns your best people twice: once on the bridge, again on the encore. Designed RCA survives the rota because the estate changed, not because the same hero remembered the workaround.

## This Week’s Challenge: Finish One Open Wound

My challenge to you this week is simple. Do not start with a new RCA tool. Start with honesty about one problem that already exists.

Pick **one** category that reopened or recurred in the last thirty days — same symptom, new tickets.

Ask:

1. Is there a named owner with a date — or only a team and a parking lot?
2. Did the last “RCA” produce a change that shipped — or only a timeline slide?
3. Can a follow-the-sun analyst inherit the story without calling the person who lived the bridge?

If any answer unsettles you, that is theatre.

Then finish **one** loop for that category: owner, falsifiable cause, change with a ship date, knowledge article or known error, and one recurrence metric on next week’s leadership pack. Coach it live with the desk and the engineering partner who can actually move the estate.

When RCA cuts recurrence instead of decorating it, the queue gets quieter for the right reason — and Monday morning stops meeting last month’s failure under a new number.

That is when incident management, Modern Workplace, and service leadership stop competing — and start compounding.

Thanks for reading. See you next week.
