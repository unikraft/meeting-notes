---
title: "Application Compatibility WG, June 21, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-06-21T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- Florin
- Teo
- StefanJ
- Felipe
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

### NodeJS

FP: I managed to get a version of NodeJS that compiles on native mode.
I had to update new libraries and introduce other libraries.

FP: We're not enabling AVX support.
It gets me an abort.
It crashes for some reason.

FP: I managed to run some scripts for testing.

FP: When building an application, use a Docker image from Alpine.

FH: We want to have a registry by the end of July.

FP: Some of the steps on the native port is to make it as configurable as possible.

FP: Some rules in the Makefile are overwritten.

### Redis

TT: I did benchmarking on native and bin-compat Redis.

TT: Without the `LD_PRELOAD` stuff, it's 10-15% slower on bin-compat Redis.

TT: It performance better than Linux.

TT: I get spikes when using Unikraft.

### getdents

SJ: I still have to open the PR for the `getdents` issue.
It's bigger than expected.
I have to do updates on multiple parts.

### LD_PRELOAD + TLS

TL: I discussed issue with implementation with `LD_PRELOAD` with TLS.

TL: I'm doing some extra measurements to see if there are issues with TLS.

TL: VDSO is not yet started.

TL: If the TLS issue persists, we would be required to build a custom glibc.

## :wrench: TODOs and Decisions

FP: Provide a summary of the native NodeJS port and instructions and TODO items.
Also on binary compatible testing.

FP: Post proposal on Alpine-based build rules.

FP: Create an issue on Makefile overwritten.

TT: Provide details on the Redis measurements: binary compat

TT: Provide plots with Redis measurements.

RD: Re-tag Marco with the links to spikes issue on Unikraft Redis.

TT: Upstream latest versions of Redis.

TL: Investigate further the TLS issues with LD_PRELOAD.

TL: Keep discussions open in the public `app-compat` channel.

SJ: Work towards getting `getdents64` system call working.
