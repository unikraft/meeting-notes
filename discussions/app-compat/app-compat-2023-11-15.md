---
title: "Application Compatibility WG, November 15, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-11-15T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- RăzvanD
- ȘtefanJ
- MihneaP
- CosminV
- AlexJ
---

## :dart: Agenda

- App catalog
- Lingering issues for app compat
- Bin compat on ARM64
- Others

## :closed_book: Discussions

### Catalog

We will move all application repository to the catalog repository:

We will have an maintainers / system devs, testers catalog repository: 

The main catalog is KraftKit-centric, the other will be used with Make-based and QEMU / Firecracker basic runs.

### App Compat Work

CV: Java should work out of the box.

CV: Next step would be to do testing with Java.

RD: Consider a framework or practical applications using Java.

RD: C# could be a next option.

SJ: C# has been worked by Tianyi.

RD: To my understanding he did a hybrid build approach.

### Lingering Issues

MP: Rust applications don't work with 9pfs.

I get poor performance both on native and on bincompat.

RD: Try out with forked library versions:
- https://github.com/unikraft/fork-glibc
- https://github.com/unikraft/fork-musl

## :wrench: TODOs and Decisions

RD: Complete moving of all repositories and apps to catalog.
Test JDK.

CV: Add tests to JDK

RD: Schedule Rust meeting.

MP: Try out forked library version.
