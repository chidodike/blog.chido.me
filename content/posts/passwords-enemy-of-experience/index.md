---
date: '2026-02-11T19:34:28Z'
draft: false
title: 'Why Passwords Are the Enemy of Experience'
cover:
  image: "passwordless-header.png"
  alt: "Passwords vs Biometrics"
  relative: true
  hiddenInSingle: false
tags: ["ZeroTrust", "Passwordless", "EntraID", "Modern Workplace", "Employee Experience"]
---

## Security versus the people it protects

For as long as corporate IT has existed, the security team and the people using the systems have been pulling in opposite directions.

The old belief was that something has to be difficult to be secure. That gave us 90-day password expiry. It gave us rules demanding an uppercase letter, a number and a special character. It gave us VPNs that dropped every time a laptop moved from Wi-Fi to mobile data, and MFA fatigue, where people get prompted so often they tap "Approve" without reading.

The controls were strong, and our own staff struggled to get through them.

People who can't get their work done don't stop working. They email files to a personal Gmail account. They sign up for apps IT has never heard of. High-friction security ends up less secure than it looks on paper, because it breeds workarounds.

---

## Passwordless, in practice

A password is a weak point. It can be guessed, phished, written on a sticky note or reused on a dozen other sites.

There are three main ways to get rid of it:

- **Windows Hello for Business:** the right choice for managed, corporate-joined devices. A face, fingerprint or PIN becomes the credential, tied to the device's TPM chip.
- **FIDO2 security keys:** a physical key (USB or NFC) that gives phishing-resistant sign-in. Good for shared workstations and high-security roles.
- **Passkeys:** the newest option. Microsoft is extending Entra passkey support to Windows so that unmanaged and personal devices, where Windows Hello for Business isn't available, can sign in without a password. Check its current status before you plan around it, because rollout is still early.

For the user, the difference is easy to see. An accountant sits down in a café and opens the lid. The camera recognises her face and she's signed in to Windows. Single sign-on carries her into email, the AWS console and the HR system. She typed no password and her phone didn't buzz once.

---

## Conditional Access does the deciding

The way to make that safe is identity-driven security, and in a Microsoft estate that means Entra ID Conditional Access.

Instead of asking everyone for a password and an MFA code every morning, Conditional Access weighs up signals as each sign-in happens:

- who the user is
- whether the device is compliant in Intune and corporate-managed
- whether the location is familiar
- whether the sign-in carries any unusual risk

If the user is on their usual laptop, signing in with Windows Hello from their normal home office, the answer is simply yes. If the same account turns up on an unmanaged personal iPad in another country at 3am, access is blocked or the user is asked for a phishing-resistant method.

Friction goes where the risk is. Everywhere else it can be left out.

---

## What to aim for

The goal is a zero-trust design that feels like no friction to the person using it. When identity is the perimeter and the device is the key, there's far less reason to make people rotate complicated passwords. The checks happen in the background, and people get back to their jobs.

---

## Check your own prompts

Open the Entra admin centre and look at two reports: **Sign-in logs** and **Authentication Methods Activity**.

How often are users challenged for MFA on their primary managed device? How many password resets did the helpdesk handle this week? If people are being prompted more than once a day on a device they use every day, your Conditional Access policies need tuning. The aim is to have MFA satisfied by the device sign-in itself and not by every individual app.

A sensible next step is a pilot group on Windows Hello for Business. If you have BYOD or unmanaged devices in scope, keep an eye on Entra passkey support as it develops.
