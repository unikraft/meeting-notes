---
title: "Application Compatibility WG, April 19, 2023"
tags: unikraft, musl, app-compat
datetime: 2023-04-19T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- musl-syscall
participants:
- Andra
- Andrei
- Cosmin
- Florin
- Marc
- Simon
- Teodor
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

Apps status - tracking doc:

- https://docs.google.com/spreadsheets/d/1cu7wecQmuYhdwf-D2_irbm8l97UEA74Vs3dFJRYxsZg/edit

Helper scripts and demo for running and debugging apps using the app-elfloader:

- https://github.com/unikraft/run-app-elfloader
- https://github.com/unikraft/static-pie-apps
- https://github.com/unikraft/dynamic-apps
- https://youtu.be/6JCvm_m_kC8

GitHub project for the application compatibility track:

- https://github.com/orgs/unikraft/projects/31

Community meeting notes:

- https://github.com/unikraft/meeting-notes/tree/staging/discussions/app-compat
- https://hackmd.io/@unikraft?tags=%5B%22+app-compat%22%5D

AP:

- Checked the fix for the following issue [Cannot handle multiple user space heaps](https://github.com/unikraft/unikraft/issues/611), using the dynamically linked hello world app. Will create a PR as next step.
- [9pfs, vfscore: Fix symlink support for 9pfs](https://github.com/unikraft/unikraft/pull/830)

AM:

- procfs roadmap - https://hackmd.io/oiCVerQRTgytSKjcacKu8g
- What we discussed previously is included in the doc.
- Need to decide how to move forward for the prioritization.

SK:

- Publish a small version with the initial entries e.g. cmdline, uptime, as soon as possible.
- Would prioritize to add the main entries in separate files and have a registration logic for the entries.
- Should be done at compile time, adding the entries.
- It's more important to have the reorg of the code, than adding more procfs entries.

AM:

- Is it mandatory to have a tree structure, to not have differences betweem static / dynamic entries?

MR:

- It would be nice if the entries would have a registration function, not a one large if.
- Can have different .c files for the procfs entries.
- Could use a list, not necessary a tree for the entries.
- There is the procfs mount function, would have some register function that would call the create entry logic.
- Iterate over the list of entries for the procfs files; can build it similar to the constructor table, for example.
- Found a memory leak in the procfs read function.
- I'll leave a comment to get it fixed.

AM:

- How to remove the musl dependency? Given that ukstore is dependent.

SK:

- ukstore depending on musl is a bug, needs to be fixed and work with nolibc.
- ukstore should work with both musl and nolibc.

CV:

- Not much other updates than the open PRs.
    - [Align the stack pointer at a 16-byte boundary at function calls](https://github.com/unikraft/app-elfloader/pull/9)
    - [Fix argv parsing](https://github.com/unikraft/app-elfloader/pull/13)
- I'm looking into the feedback for the memory related PR, [lib/ukvmem: Allow non-writable shared file mappings](https://github.com/unikraft/unikraft/pull/832).

SK:

- As the first PR (stack alignment) is merged, a rebase is needed, then I will approve the second PR (args parsing).

FP:

- Checked out the symlinks PR.
- The Unikraft codebase is setting the errno code different than Linux.
- Will create an issue for the errno code setup.

SK

- The error code might not specifically match the Linux codebase.
- It should return errors similar to the ones in the man pages.
- Should open an issue and provide a fix.

FP:

- Need to check out the Node.js statically linked, crashing at clone.
- Then I'll move to the dynamically linked one.
- At init, when trying to map the statically linked executable into elfloader, it says the heap is too small.
- It might the app that does too many allocations.

SK:

- Should increase the heap and look through syscalls traces for brk, mmap calls.
- Should have a proper implementation for brk, if needed for the apps.

MR:

- Could look through data segment and expand that for the statically linked.

SK:

- For the dynamically linked one, would be the brk logic from the app-elfloader so far.
- When getting to increase the heap, should append the memory pages contiguously for the brk logic.

MR:

- Opened PRs for app compat fixes and syscall traces.
    - [Various fixes for application compatibility](https://github.com/unikraft/unikraft/pull/834)
    - [lib/syscall_shim: Extend prsyscall (print structs, ...)](https://github.com/unikraft/unikraft/pull/836)
- Additional fix for a problem in musl and in nolibc.
- Working on HAProxy dynamically linked.
- [Fix file flags for O_NONBLOCK and O_ASYNC](https://github.com/unikraft/unikraft/pull/850)
- Discovered the static Go app doesn't work without a rebuild, having a newer version of Go.
- Depending on vdso with an older version of Go, any plan to implement that?

SK:

- Seen also e.g. in alpine, the musl syscall definition doesn't match the Linux definition.
- At some point it makes sense to have a vdso when using elfloader.
- Had issues with unmap functionality, updated to the latest unikraft including the fix.
- Finishing the last things for choosing how to load the app, the args passing.
- Auto retrieve the loader for the dynamically linked app, parsing the headers.
- Reviewed PRs for stack alignment and args parsing.
- Created the following PRs:
    - [Re-introduce elf_open(), elf_openmemory()](https://github.com/unikraft/lib-libelf/pull/1)
    - [lib/nolibc: Prototypes for pread and pwrite](https://github.com/unikraft/unikraft/pull/846)
- Adding config option for specifying the stack size and the env variables.

TT:

- pthread falls back to regular clone if clone3 doesn't exist.
- The Linux kernel puts the registers in the task struct.
- Looked into Redis, statically linked, managed to patch the lwip.
- Having an issue getting stuck in an accept function.

MR:

- Maybe is the same issue as for the HAProxy.
- Should wait for the fix for this.
    - [Fix file flags for O_NONBLOCK and O_ASYNC](https://github.com/unikraft/unikraft/pull/850)

SK:

- Should create a PR to remove the clone3.
- Create an issue with the finding about the registers on Linux.

## :wrench: TODOs and Decisions

AP:

- Create PR for the following issue [Cannot handle multiple user space heaps](https://github.com/unikraft/unikraft/issues/611).

AM:

- Develop an initial solution for procfs. Focus on the reorganzation of the codabase e.g. separate .c file per entry, and add support for the current procfs main entries e.g. cmdline, uptime.
- Check the musl depedency for ukstore, it should work with nolibc as well. Needs to be fixed, if not working with nolibc.

CV:

- Continue to work on the open PRs.

FP:

- Create an issue for the errno setup in vfscore.
    - [lib/vfscore: ERRNO gets wrongly set](https://github.com/unikraft/unikraft/issues/849)
- Identify why there is an issue with the heap being too small / memory allocations, when trying out statically linked Node.js.

SK:

- Publish the remaining PRs for elfloader e.g. app loading, environment vars.

TT:

- Create a PR to remove clone3.
    - [lib/posix-process: remove clone3 syscall](https://github.com/unikraft/unikraft/pull/847)
- Check the fix from Marc for the "accept" issue.
- Create an issue with the findings about the Linux kernel adding the registers in the task struct.
