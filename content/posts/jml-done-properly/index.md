---
date: '2026-11-02T09:00:00+00:00'
draft: true
title: 'JML Done Properly'
cover:
  image: "jml-done-properly-cover.png"
  alt: "Three flat doors in a row marked with simple arrows for in, across and out, with one access badge still hanging on a hook beside the middle door"
  relative: true
  hiddenInSingle: false
tags: ["ITSM", "ServiceDesk", "Identity", "JML", "DEX"]
---

## 08:50 on someone's first day

It's Monday, 08:50. A new starter is sitting in reception with a visitor badge and a coffee they didn't ask for. Their manager is in a meeting until ten. There's no laptop with their name on it, because the hardware request went in on Thursday. There's an account, but no licence, so Outlook opens and then tells them they can't use it.

The desk gets the call at 09:05. By 11:00 the laptop is built, the licence is assigned and the new starter has met three analysts. Ticket closed, first contact, well inside SLA.

Nobody would call that a good first morning, though. And the cause wasn't on the desk. HR knew this person was starting three weeks ago.

## One start date, many inboxes

Joiners, movers and leavers sound like three processes. On most desks they're one problem: the event happens in one system and the work happens somewhere else.

HR records the start date, the new role or the last day. Then someone has to turn that into tickets. A manager fills in a form, or forgets to. A request lands in the queue with half the fields blank. The desk ends up chasing a hiring manager for a cost centre on the morning the person arrives.

The fix that lasts is simple to say and hard to do. The HR system is the source of truth for who someone is, what they do and when they stop. Tickets carry out that change. They don't decide it. If the desk is the first to hear that someone has left, the process has already gone wrong somewhere upstream.

## Joiners: the first morning is the test

A new starter forms a view of IT before they've opened a single app. If the first morning goes badly, that's the IT department they'll remember.

What helps is boring and early. The account exists before day one, with the right licence and the core groups for the role. The laptop is assigned to a named person, not "one from the cupboard". [The first sign-in has been thought through](/posts/redefining-day-one/), so a new starter isn't stuck trying to set up MFA on a phone they don't have yet. And the manager knows what's ready and what isn't before the person walks in.

I'd rather tell a manager on Friday that the laptop will be a day late than have the new starter find out from reception.

## Movers: the one nobody closes

Joiners get a welcome pack. Leavers get an exit interview. Movers usually get an email from their new manager and a few requests for extra access.

That's the problem. When someone moves from finance to operations, they ask for what the new role needs, and they get it, because the request is reasonable and approved. Nobody asks for the finance access to be taken away. The person won't, because it doesn't stop them working. The old manager doesn't, because they've stopped thinking about that person. The desk can't, because nobody told us which access belonged to the old job.

Do that a few times across a career and you get the long-serving colleague who can see everything. Not because anyone decided they should, but because nothing ever came off.

A move should be treated as a leaver and a joiner on the same day. Grant what the new role needs, then remove what it doesn't, with a short overlap if the handover genuinely needs one. The overlap needs an end date. "Keep it for now" isn't one.

## Leavers: Friday afternoon

It's Friday, 16:30. A manager rings to say someone's last day was today. Could we turn everything off?

So the desk starts working through a list. Disable the account. Sign them out of active sessions. Remove the MFA methods. Collect the laptop, or find out where it is. Decide what happens to the mailbox, and the shared mailboxes they had access to, and the files in their OneDrive that the team still needs. Check the app that isn't connected to single sign-on, the one where somebody added them by hand two years ago.

None of that is hard on its own. It goes wrong when it starts at 16:30 on the day, from a phone call, with nobody sure what the list should be for this person.

A leaver done properly starts when HR records the leaving date. The timing is agreed in advance, and the steps are the same every time. The desk handles the exceptions instead of rebuilding the checklist from memory at the end of a week.

## What auditors pick

If you've been through an audit, you'll know [the sample request](/posts/the-week-the-auditors-arrive/). Give us ten leavers from the last six months. Show us when HR recorded the leaving date, and when each account was disabled.

They'll do the same for joiners (who approved this access?) and, if they're thorough, for movers (why does this person still have access from their last role?).

The gap between those two timestamps is the whole story. If it's a few hours, good. If it's three weeks because the ticket sat in a queue, that's a finding, and it's the desk's name on the ticket. Contractors and vendor accounts get sampled the same way.

## Where the tooling helps

If you're on Microsoft Entra, lifecycle workflows can run joiner, mover and leaver tasks from user attributes, such as a hire date or a change of department. There are built-in tasks for things like generating a Temporary Access Pass and emailing it to the new starter's manager, removing group memberships, disabling the account and revoking sign-in sessions. Access reviews let you ask owners at set intervals whether people still need what they have, which is the safety net for the movers your process missed. Both are licensed under Entra ID Governance or Entra Suite (some access review features work with P2), so check what you've got before you plan around them.

Neither fixes bad data. If the department field in HR is wrong, the automation does the wrong thing faster.

## Try this

Pick five people who left in the last three months. For each one, find the leaving date in HR and the time their account was disabled. Then check one app that isn't behind single sign-on, and see if they're still in it.

Then pick three people who changed role in the last year. List what they can access today and ask their current manager which of it they actually need for the job they have now.

Whatever turns up is your JML backlog. Take it to HR as well as IT, because most of it started with a date that never reached the desk.
