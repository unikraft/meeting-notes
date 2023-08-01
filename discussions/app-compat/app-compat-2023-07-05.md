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

### Redis

There are some benchmarking variation.

If I connect with more than 60 clients, I get an error on `virtio`.

For 100 clients or more, a maximum number of items is reached.

### NodeJS

I'm working on the AVX-enabling problem.

I'm working on `lib-intel-intrinsics` to get AVX going.

On the group chat, I've asked some questions on NodeJS native port.

About the benchmarking issue with the missing shutdown feature.

You could sleep and measure the response time, so there is no harm done, no performance penalty.

FP: In your case it would be nice to measure image size, memory consumption, bootup time.

### Tiany Liu

TL: I've been refactoring the interface based on the feedback from Simon.

TL: We don't use LD_PRELOAD anymore, we turned to VDSO.

TL: There are some linking errors with the VDSO linking to the kernel.

SK: Because of the TLS setup, because of the VDSO work, we would need a separate VDSO entry.
And a patched Glibc / Musl to make direct calls to the kernel.
That would look for the VDSO and use that if it's available.
If not available, it will fallback to the classical syscall interface.

### `getdents64`

SJ: Simon reviewed the PR, I will review it.

FH: Add languages on the agenda of next meeting.

Next item is WAMR.

The goal is to get minimal functionality.
And the improve that.

## :wrench: TODOs and Decisions

RD: Merge the `lib-redis` PR for version 7.0.11 of Redis.

TT: Add an issue on `lib-redis` fork() for background saves.

TT: Keep the discussion going for benchmark variations.

TT: Open up two issues.

RD: Figure out future steps.

FP: Talk to Andrei Tătar about `lib-intel-intrinsics` and AVX support.

FP: Create a screenshot with the NodeJS name to prove it running.

RD: Integrate the nodejs binary-compat PR.

FP: Update the binary-compat PR to only feature the NodeJS 18 version.

SJ: Go through `getdents64` for 
