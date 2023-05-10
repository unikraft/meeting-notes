---
title: "Application Compatibility WG, May: 10, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-05-10T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- Teo
- Florin
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

TT: I investigated the redis app, a thread gets stuck in a futex wait call, program freezes

SK: I have the same issue on another app, Envoy, need to investigate further.

TT: Created the PR on dynamic apps. lib-redis does not connect to network, solutions proposed on the lib-redis channel did not work.

AP: I managed to reproduce the 9pfs issue, have a fix. Managed to run the latest staging with changes from PRs.

AP: Continuous checking of code and apps partially done.

SK: Waiting for review and approval, applied changes from Marc.

FP: Dynamic node.js, failed read-write lock, possible solution find. Fields are initialized with 0, read-write lock checks thread-id against empty structure and returns EDEADLOCK. Change find_free_tid prev variable to 1.

FP: Output obtained, command input does not work.

FP: SK, do you know how to list unikraft threads in GDB?

SK: There is a debugging function in uksched, will check.

FP: node.js epoll_wait for command input.

SK: Debug function noted in app-compat channel.

SK: Is an interactive shell necessary in node.js, or can it run scripts without one?

FP: Maybe it can be done.

SK: Is it a musl issue?

FP: It is a glibc structure, with a node.js wrapper. It is part of the application.

SK: Configurable, or hardcoded? Internally, there is a bitmap for thread ids. In linux, init has a 0 id, application assumes it never gets a 0 id. Maybe make the syscall never return 0.

FP: It should be never 0 if working in app-compat.

SK: Does it harm programs if it never returns 0? I think most apps can live without id 0.

SK: It should increment any thread id outputted, and decrement any thread ids received as input.

SK: Check the linux kernel implementation.

## :wrench: TODOs and Decisions

SK: Investigate futex wait problem.

TT: Try to get redis-lib to work.

AP: Send PR with 9pfs fix.

FP: Get node.js to run script directly, without interactive shell.

FP: Check thread id allocation in the linux kernel, if it ever returns 0.
