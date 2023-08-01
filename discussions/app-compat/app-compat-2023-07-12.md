---
title: "Application Compatibility WG, July 5, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-07-05T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- Florin
- Teo
- Felipe
- ȘtefanJ
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

### JDK

CV: The Unikraft PR fixes the `sysconf()` syscall.

Regarding the tests, I made progress with the automation.

Next priority after 

### getdents64

SJ: Update on the getdents64 PR based on SK's review.

### Redis

Open up issues on Redis and then work on variations of the benchmarking.

### VDSO

I completed the code refactoring.
Only one unified interface remaining for syscalls.
This new approach is 10% slower than before.
Implementation is more efficient.

With Simon's suggestions, I would be able to complete these work.

There are now patched versions of glibc and Musl.

SK: We can have a per-architecture VDSO.

## :wrench: TODOs and Decisions

CV: Continue testing with JDK.

CV: Create PR with the binary compat part on the `dynamic-apps` repository.

Next steps would be top-level 5 JDK apps: Kafka, Springboot or others.

RD: We will test the binary compatibility with applicatins already in the `dynamic-apps` repository.

All: We can upstream the version of the VDSO.
Changes are small.

RD: Talk to Răzvan Vîrtan about Aarch64 bincompat support.
