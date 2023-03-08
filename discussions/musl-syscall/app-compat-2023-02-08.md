---
datetime: 2023-02-08T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - syscall
participants:
  - Felipe
  - Simon
  - Maria
  - ȘtefanJ
  - RăzvanD
  - Felipe
---

### Agenda

* Current state of ukthread / clone
* Musl integration
* synchronization / futexes

### Discussions

SK: The ELF loader is now able to load from memory.

SK: With dynamic linking, the dynamic linker is the ELF binary.

SK: You have to add the libraries and root filesystem in 9pfs.

SK: With the patches from Marco, you will have a full GDB transparency.

MR: It also gives you page fault information.

RD: Let's do it in two steps:

1. Use the setup to run dynamic PIE apps.

1. Debug using Marco's update.

SK: Only a subset of system calls are decoded.

CV: I looked into the futex syscall issues.

CV: I found a stack alignment issue.

TT: No new updates.

TT: I played with the dynamic PIE.

Use `ldd` to discover the dynamic libraries required.

#### procfs

AM: I'll work on caching ukstore entries.

AM: I also have to give up the Musl dependencies for string.

#### Loupe

FP: I was using the staging branch.
I used nginx.

### TODOs and Decisions

SK: Provide the documentation for using the dynamic ELF loader.

RD/SJ: Remove any references to the old ELF loader use case.

CV: Take another look on the dynamic PIE of Java.

AM: Take a look into streambuf.

RD: Provide `app-elfloader` build script information.

Soft deadline for procfs updates: March 1, 2023
