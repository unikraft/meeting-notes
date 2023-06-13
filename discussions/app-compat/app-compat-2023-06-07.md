---
title: "Application Compatibility WG, June 7, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-06-07T12:00:00+02:00
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

SJ: I found an issue with mounting 9pfs and scheduling.
It's happening on Aarch64 about half of the time.

The thread doesn't wake up.

SJ: I've checked the `getdents` issue.
The two separate syscalls should

### Redis

TT: Redis both in app-compat and native-mode.

TT: I ran some benchmarks.
There was a memory issue that was solved by Andrei Tatar's PR.

TT: I'm using a standard Redis benchmark.
I've some questions that I posted on the #bench-prof channel.

SK: Is your work handling the TLS problem as well?

TL: Not yet.

### Node

FP: I started ported the coverage tests from the Node repository.

RD: We will create separate repositories for each depending library.

FP: There are forked version of openssl and other libraries that differ from the upstream version.

SK: For starters I would go into including all dependent libraries in the Node repository.

### JVM

CS: I was finally able to get OpenJDK running.

CS: There are issues on `sysinfo` side.

CS: I was looking into tests from JDK.


PO: I will post a link on the #app-compat channel to repository.

## :wrench: TODOs and Decisions

SJ: Investigate more on the mounting / scheduling part for Aarch64.
Post an issue if problem persists.

SK: Take a look into the issue reported by Ștefan.

SJ: Create a draft PR on the getents().

TT: Ping people on Redis bench

TL: Provide draft PR with work on GOT / PLT improvement for TT to use.

TT: Use draft PR work rom TL.

TL: Look into TLS part for the GOT / PLT approach.

FP: 

CS: Look into tests for JDK.
