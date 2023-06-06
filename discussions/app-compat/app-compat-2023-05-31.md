---
title: "Application Compatibility WG, May 31, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-05-31T12:00:00+02:00
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

App-compat hackathon

TT: Redis uses `rename()`.
Inside the `rename()` implementation.

SK: Should we give up 9PFS 9000L version or should we fix on both versions?

TT: There were about 10-12 tests and everything works.

TT: I tested on 7.0.11.

CV: JDK: I did a detour and looked at the default builds from Oracle.

SJ: Is there a `getdents64` syscall on ARM.

## :wrench: TODOs and Decisions

RD: Contact Cristi Banu about 9000L support for `rename()`.

TT: Test with Ubuntu / Debian Redis binary-compat packages.

TT: Run benchmarking: req/s, 

TT: Build and run a native case.
Update it to a newer version.
Look for the `lib-redis` repo.
Use `make`-based approach.

CV: Look into JDK issue for heap initialization.
