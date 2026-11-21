---
date: '2026-02-05T19:56:07Z'
draft: false
title: 'A Better First Day with Autopilot'
cover:
  image: "day-one-header.png"
  alt: "Zero Touch Provisioning vs Legacy Day One"
  relative: true
  hiddenInSingle: false
tags: ["ZeroTouch", "Autopilot", "Intune", "Modern Workplace", "Employee Experience"]
---


## The old first day

Think back to your first day at a new job, five or ten years ago.

Someone from IT turned up with a heavy laptop, a sticky note with a temporary password, and a multi-page printout. You spent the next four hours watching progress bars, mapping network drives, ringing the helpdesk for access to your email, and waiting for the VPN to connect.

Everyone went through it, and it was a poor introduction to a company. If someone spends their first day fighting with technology, the message they take away is that the place is slow, dated, and going to be a struggle.

People now compare their first day with setting up a new phone. Somebody buys a new handset on a Sunday, signs in, and has their life back within minutes. They expect the corporate laptop on Monday to behave the same way.

---

## What zero touch looks like

The approach to aim for is zero-touch provisioning, using Windows Autopilot and Microsoft Intune (or Automated Device Enrollment through Apple Business Manager for Macs). Microsoft is also rolling out Windows Autopilot Device Preparation, sometimes called Autopilot v2. It streamlines the flow further and is worth watching as it matures.

In practice:

- The hardware vendor ships the laptop straight to the employee's home, and IT never touches the box.
- The employee joins their home Wi-Fi and signs in with their work email address.
- The device is recognised, picks up the security baseline, and quietly installs the apps they need.

There are no imaging servers and no USB boot drives. It's identity, hardware and the cloud.

---

## Where teams spoil it

Many teams take the new tooling and bring the old imaging mindset with them.

During Autopilot, users see the Enrollment Status Page (ESP). It holds them at the setup screen until the policies and apps you've marked as required have installed. Too many teams use it to push every application the company owns: a 10GB CAD package, three browsers and a dozen legacy security agents, all over a home broadband connection. The result is a two-hour wait that often ends in a timeout and a failed enrolment. The ESP's default timeout is 60 minutes, so a heavy payload on a slow line is a gamble.

You've taken a good process and loaded it until it breaks.

> **An alternative, if you have the capacity:** pre-provisioned deployment (also called White Glove or Technician Flow), where IT or your OEM does a partial setup before the device ships. That front-loads the heavy work so the user's first boot is nearly finished. It only works if you have the logistics to support it. For most SMBs and remote-first teams, a well-tuned user-driven flow with a lean ESP is still the better bet.

---

## A lean first day

The aim of day one is a secure, usable desktop as quickly as you can get there. A fully loaded workstation can wait.

**Block on the essentials only.** A browser, your zero-trust network access agent so the device is protected, and Microsoft 365. That's the list.

**Let the rest arrive in the background.** Aim to get the user to their desktop within 15 to 20 minutes. One caveat: as of early 2026, Windows devices install the latest monthly security update automatically during OOBE, which can add up to 20 minutes on a fresh device. Build that into your target and tell new starters in advance, so a longer wait doesn't look like a failure. Once they're in, reading welcome emails and joining Teams, Intune can deliver heavier applications such as Adobe or AutoCAD without getting in the way.

**Put everything else in the Company Portal.** Let people choose what they need when they need it. It builds trust and cuts tickets.

---

## Why it matters

If you invited someone to a physical office, you wouldn't ask them to assemble their own chair and wire their own desk before starting. You'd give them a coffee and a ready desk.

A clean Autopilot experience is the digital version of that. It tells the new starter that you value their time and have given them what they need.

---

## Try this

Open your Autopilot Enrollment Status Page configuration in Intune and count the apps marked as required. If the number is above five, you're adding friction. Pick three of the heaviest and move them to background deployment, then time the next new starter's first day and compare.

The device is only half of day one. The account, licence and access behind it are covered in [JML Done Properly](/posts/jml-done-properly/).
