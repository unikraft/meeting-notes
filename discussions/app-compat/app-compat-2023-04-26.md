---
title: "Application Compatibility WG, March 15, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-03-15T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- Florin
- CosminV
- Teo
- Pierre
- AndreiM
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

SK: You can now pack the executable and libraries into the filesystem for the guest and that point it to the application.

SK: You can now package the entire application as a CPIO archive or with a 9pfs filesystem without.

### JDK

CV: Worked on PRs.

CV: Gets past the `getcpu` system calls.

CV: Some variables are initialized to `0`.
The variable is written in Java code.

CV: I'm using GDB to see what the native process does this to that variable.

FP: One issue with Node with Musl is fixed.

FP: The other issue with Node is related to `pthread_rwlock_lock`.

FP: The problem is solved by disabling `ukvmem`.

This is similar to the issue that Teo encountered.

TT: I submited a PR.

TT: I also submitted a PR on lwip on a wrong TCP option.

TT: With Marc's `accept` patch.

TT: With regards with Nginx.

## :wrench: TODOs and Decisions

SK: Submit PR with native support for dynamic loaders.

CV/RD: Review for native support.

FP: Open issue with `clone`.

FP: Work on dynamic NodeJS.
