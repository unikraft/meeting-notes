---
title: "Application Compatibility WG, April 5, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-04-05T12:00:00+02:00
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

### Loupe

PO: Not much to say about Loupe.
I'm now working on the paper.

PO: These are tests from LTP (Linux Test Project) on top of Unikraft.

PO: Student is now finishing his work.
This work could be made open source.

PO: Pretty sure he's using the ELF Loader to run executables with Unikraft.

PO: For Loupe we could find the most common flags and use them for testing.
Very likely these are just corner cases.

### Binary Compatibility

#### Cosmin

CV: I made updates to PRs.
I changed the alignment PR.

CV: I moved the commits with arg parsing to another PR, as there is work already done by Simon.

SK: I will provide an update for supporting dynamically linked applications.

CV: Teo found the `clone3` bug.
It was something I bumped into also in JDK.

CV: I built JDK on an older libc and it passed that point.

CV: Java tries to find out the executable name.
It first tries to use `/proc/self/exe`.

#### Teo

TT: Investigate the `clone3` system calls.

TT: Figure out the issue with `clone3`.
They use the same underlying syscall.
The only difference is in how the arguments are used by `clone` and `clone3`.

TT: When the syscall returns, it returns into the `clearregs` function.

TT: Does open cause a system call?

RD: Yes, because it makes a call to disk, that may put the current thread to sleep.

#### Andra

AP: I've been through the code base of `vfscore` regarding the symlink file type issue.
I was able to replicate the matter on a native build.

AP: For now, I think the issue is part of 9pfs.

AP: I get another error on the different version of 9pfs.

#### Simon

SK: Need to push my work on environment, argument parsing and initial ramfs support.

## :wrench: TODOs and Decisions

SK: To review the alignment PR from Cosmin.

SK: Provide the initramfs PR.

SK: To provide other items: environment variables, native loader, argument parsing.

AP: Investigate the symlink issue further.
Fix it as soon as possible then move to other issues.

TT: Investigate the `clone3` system call issue.

TT: Build Redis on an older libc.

CV: Investigate `stat` / `mode` issue when testing JDK.

CV: Keep contact with Simon on the open PRs.

RD: Review documentation on app-elfloader.
