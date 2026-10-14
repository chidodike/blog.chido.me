---
date: '2026-10-19T09:00:00+01:00'
draft: true
title: 'When the VPN Is the Ticket'
cover:
  image: "vpn-is-the-ticket-cover.png"
  alt: "A laptop on a hotel desk showing a connected badge, with a broken padlock beside it"
  relative: true
  hiddenInSingle: false
tags: ["ITSM", "ServiceDesk", "RemoteAccess", "ZeroTrust", "DEX"]
---

Picture 07:50 on a Monday. An engineer is on a client site with a job starting at 08:30. The VPN client says "connected" in green. Nothing resolves. The ticket portal sits behind the same VPN, so they can't raise a ticket there, and they ring the desk instead. The analyst picks up and goes to look at the device. The remote tool is also behind the VPN, so the analyst can't see it either.

Both people are stuck behind the same broken thing. This post is about what a desk can do so the fix doesn't depend on it.

## Why VPN tickets are different

Most tickets are solved with tools the desk already has: the admin console for a password reset, the remote tool and device record for a slow laptop. A VPN ticket can take those tools away at the same moment it takes the user's access away. The diagnostic path sits behind the thing being diagnosed.

The second difference is the word "connected". The client reports that a tunnel exists. The user wants to open the ticket portal and the file they need at 08:30. Those are different states, and the client only tells you about the first. A desk that accepts "connected" as the answer ends up asking the user to read error messages down the phone.

## What users actually experience

From the user's side it rarely looks like an outage. It looks like oddities they've learned to work around.

Split tunnelling is one. Some traffic goes down the tunnel and some goes straight out, and the user can't tell which is which. Teams works, the internal wiki doesn't, and the browser gives no clue why.

DNS is another. A name that resolves in the office may not resolve at home or in a hotel, because the resolver the laptop is asking isn't the one the name lives on. Public sites all work, so the user concludes that one internal site is broken.

Then there's the reconnect dance. The laptop moves from hotel wifi to a phone hotspot, the tunnel comes back half-formed, and the user disconnects and reconnects until something changes. The desk never sees any of those attempts.

## A mesh network as a worked example

I'll use Tailscale to make this concrete, with a clear caveat. I run it at home to reach Linux boxes on a VMware ESXi host and some Windows machines, all in my home lab. That's a home-lab setup. It isn't an enterprise rollout, and I'm not claiming enterprise deployment experience with it. What follows is based on Tailscale's documentation.

In a mesh network, devices connect to each other, and `tailscale status` shows whether a given connection is direct or going through a relay. There's no single gateway that every packet has to pass through.

Access is written as named rules. The default is deny, and a grant allows a source to reach a destination. Sources and destinations can be users, groups, or tags that describe what a device is for, such as a database or a file server. An analyst can read "engineering can reach the build servers" and check it against a ticket.

Sign-in goes through your identity provider. Microsoft Entra ID is a supported provider, and the documentation says MFA enabled in the provider applies to Tailscale. The identity side of a remote-access ticket is then the same one the desk knows from every other sign-in problem.

When a ticket arrives, you can read what a device should be able to reach before you speak to the user. Tailscale's troubleshooting guide for devices that can't connect works through client version, `tailscale status`, `tailscale ping`, firewalls, access control policy, then authentication and key expiry. The admin console has a Preview rules tab showing what the policy allows.

## What the desk needs to see

An analyst should be able to answer five things without ringing the user.

- Is the device online, and when was it last seen?
- Is its sign-in still valid? Tailscale keys expire, with a default of 180 days that an admin can change between 1 and 180, and once a key lapses its connections stop.
- Does a rule allow this user or device to reach the thing they say is broken?
- If a rule blocks it, which one?
- Does DNS resolve the name the user is trying to open?

The fourth is the hardest. Tailscale's network flow logs are on the Premium and Enterprise plans, and the documentation says they record successful connections only, so a denied attempt isn't logged there. The troubleshooting guide points to the receiving device's logs and the Preview rules tab instead. Whatever tool you adopt, find out early what it shows for a blocked connection.

A first-five-minutes checklist for the analyst:

1. Find the device record and check last seen and sign-in state.
2. Check whether the user's sign-in has expired or been interrupted.
3. Read the rules that apply to this user and the destination they named.
4. Test name resolution for the destination, then reachability by address.
5. Only then call the user, with a specific question.

## Where it still goes wrong

Over-broad rules come first. A rule added to close one ticket slowly becomes "everyone can reach everything", and the list stops being readable.

Forgotten devices come second. Tagged devices, such as servers, have key expiry off by default in Tailscale, so they can stay in the list long after anyone remembers why. A trusted device with no owner is a leaver problem that nobody has picked up.

The third is the one this post started with. If sign-in itself is the problem, the user can't use the network to fix it. Tailscale's documentation covers one fallback: for a remote device you can't otherwise reach, an admin can extend an expired key by 30 minutes so the owner can sign in again. Decide in advance who on your side can authorise that, and how the user reaches them by phone.

## Try this

Take the last ten remote-access tickets from your queue. For each one, mark whether the analyst could see the cause from their own tools without calling the user. Count how many had the answer in a device record, a rule or a log, and how many only came out on the phone.

The ones that needed the phone show where the desk is blind. Pick the most common one, name an owner, and set a date for making that fact visible to the analyst.
