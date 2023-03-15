---
title: "Application Compatibility WG, March 15, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-03-15T12:00:00+02:00
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
- Alex
- ȘtefanJ
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

RD: Priority of app-compat track.
Make as much progress as possible.

RD: Andra is the tech lead for this.
She will work on it and provide support required.

RD: Make sure you submit issue on the issue tracker and report them on Discord.

RD: Ideal steps / mindset:
- Be pro-active. If something doesn't work, jump on another thing.
- Report an issue early on.
  Create issue on issue tracker, open discussion on Discord.
- Do your own debugging.
- Let others know what you're working on (on the `#app-compat` channel).
- Help others.
  Provide documentation / commands you used.

CV: I checkout the PR and now it starts a `hellworld` app as dynamic PIE.
After updates 

CV: Based on the OpenJDK support.
When you issue `pthread_join()` it runs a `wait()` command.

CV: Right now I'm now using the `qemu-guest` script.

SK: `ukmmap` won't work with dynamic executables.
Only `posix-mmap` has to be used.

SK: There is a PR with a `README`: https://github.com/unikraft/app-elfloader/pulls

SK: I'm working on getting rid of the loader (`ld-linux.so`).

CV: I bumped into the issue with the stack not being aligned because of XMM registers.

CV: I'm fixing it in the beginning.

TT: We found the issue related to errno, and there is a PR on GitHub.
I'll check the Python static app.

FP: Regarding the Node porting.
Port it as dynamic library.

FP: Regarding Loupe, I tried using Node on `pr708-wasp`.
I'm having issues with ending processes.

FP: About the static analysis part of Loupe, it depends on the binary you're currently analyzing.

PO: I thought that for dynamic executables, it tries something I don't trust a lot.
It's probably a rough estimate.

PO: Maybe the solution is to disable this by default.

SK: I have patches for socket netlink.

## :wrench: TODOs and Decisions

Ideal steps / mindset:
- Be pro-active. If something doesn't work, jump on another thing.
- Report an issue early on.
  Create issue on issue tracker, open discussion on Discord.
- Do your own debugging.
- Let others know what you're working on (on the `#app-compat` channel).
- Help others.
  Provide documentation / commands you used.

We meet two weeks from now, on Wednesday, March 20, 2023.
We keep in contact via Discord.

AP: Solve https://github.com/unikraft/unikraft/issues/796

CV: Keep investing the futex issue.

CV: Provide instructions on your own way running `app-elfloader`.

CV: Review `README.md`: https://github.com/unikraft/app-elfloader/pull/7

CV: Create issus on stack aligment problem and create PR on the `app-elfloader` repository: https://github.com/unikraft/app-elfloader

TT: Try first Python static PIE.

TT: Try then Python dynamic PIE.

TT: Look into other applications as you make progress.

FP: Try Node as a dynamic PIE.

FP: Look into approaches for killing on 

FP: Disable dynamic analysis on Loupe.
