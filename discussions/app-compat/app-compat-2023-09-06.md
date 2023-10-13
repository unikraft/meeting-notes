---
title: "Application Compatibility WG, September 6, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-09-06T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Simon
- RăzvanD
- ȘtefanJ
- Pierre
- Tianyi
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

SK: We are using VDSO for the binary compatibility layer.

Binary compatibility is becoming the default way to run applications with Unikraft.

When you link with Unikraft.

TL: I'm interested in the multi-process support.
What happens when you do a fork.

SK: Another problem interesting to look at is if you have different applications.
You compile everything together and you have two `main()` function calls.

TL: I was looking into a paper that uses MPK for isolation.

PO: You need to provide a PIE approach.

PO: You can assume you are going to drop the security a bit for performance gain.

OSv has some support of multi-process support, some spawn feature.

TL: If you are using the external linking.
You have to manually write the commmand to get the final image.

## :wrench: TODOs and Decisions

TL: Do a write-up of the proposal for multi-process support.
