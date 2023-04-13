---
title: "Application Compatibility WG, April 12, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-04-12T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- CosminV
- Teo
- AndreiM
- ȘtefanJ
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

CV: I looked into the issue with `stat()`.
There was a type alignment.

CV: I went to OpenJDK.
I encoutered the `mmap` call with `MAP_SHARED`.
I created a PR that works around `MAP_SHARED` as long as `PAGE_WRITE` is absent.

CV: The next problem is `getcpu()`.
The syscall is absent.

AP: I opened a PR for the symlink.
Teo, Florin have looked into it.
I had feedback that is now fixed.

AP: I want to get through the PRs.
I'm looking at the "multiple heaps" issue.

SK: I would keep the poor man's implementation.

TT: I looked into the `clone3` issue.
The `clone3` doesn't save and restore the function address and the argument on the child stack.

TT: If we can get the registers inside the call, we can do a push and then do a pop.

SK: You don't know when the child is scheduled.
You need to store somewhere for the child.
Leaving out the registers with a new `clear_register` function.

TT: The child stack is part of `cl_args`.

TT: I found some other issues.
LWIP is complaining with an issue about a protocol.

TT: There's another issue with binding to address `0.0.0.0`.

SK: The value of the `R8` register is saved.

MR: I'm thinking of a system where you would have more a registration function.
And a function where you could register new filenames.

MR: You would have a single C file for a filename.
That function would provide an init, read functions in each of these files.

SK: One solution could be to use the `inittab` to register each entry.
That will also make the code organization easier to maintain.

MR: For performance, I would generate some data structure at linktime.
I think this is more flexible.

AM: I think we only have static entries, based on static ukstore.

SK: The purpose is to have a static version (first phase).

SK: The TODO item is on code organization for the first phase.

## :wrench: TODOs and Decisions

SK: Do a tour of Cosmin's PRs.

AP: Look into multiple heaps issue.

RD: A quick tour script of running all supported applications.

TT: Return `-ENOSYS` with `clone3`.

AM: Create a draft plan on next steps regarding `procfs`.
