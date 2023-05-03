---
title: "Application Compatibility WG, May 3, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-05-03T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- Teo
- AndreiT
- ȘtefanJ
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

SJ: I did an overall script to test Musl-based builds.

TT: I tested the latest 7.X Redis PR.

TT: It freezes when you save and after the `fork()`.

TT: This happens when using the Redis benchmark app.

TT: For the static part, everything works, but the `fork()` causes the save not to work (but with no crash or freeze).

TT: I found a `fork()` for the 6.X and 7.X version.

TT: From what is says here, Redis relies on `fork()` in order to save.

AP: I added a PR for bzip2.

SK: I have an issue with 9pfs on the `app-elfloader` update that I did.

AT: Should I be worried if Xen auto-builds don't work?

RD: Don't worry at this point.

AT: I looked into the FS/GS issue and the selection between inline assembly and using intrinsics.

SK: For now use builtins and figure out later ways to make this clean.

SK: Submitted env and param library updates.

SK: The native support for loading the dynamic loader.

SK: There are two issues: one with 9pfs.
Another one with memory corruption Musl / mmap.

SK: On the plate:
- netlink support
- the `wait()` system call
- the shutdown feature

## :wrench: TODOs and Decisions

TT: Investigate freeze of dynamic-app Redis.

TT: Create a PR with dynamic Redis in the `dynamic-apps` repository.

TT: Look into `lib-redis` 5.0.6 in the Unikraft GitHub organization (https://github.com/unikraft/lib-redis).

AP: Look into the 9pfs issue with `app-elfloader`.

AP/RD: Do continuous of `app-elfloader`.

SK: Please provide a description of the issue and set of steps for Andra to replicate.

RD: Approve PR for bzip2.

SK: Be on the lookout with updates to the PR you created.

SJ: Use `make-based` script to test Musl builds for 0.13 release.

AT: Use builtin for the FS/GS issue.
