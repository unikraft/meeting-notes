---
title: "Application Compatibility WG, September 27, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-09-27T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Simon
- RăzvanD
- Marco
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

MS: I would use Dockerfile to grab the executables and the dynamic libraries.

MS: I would work on getting executables and components from Docker running on top of Unikraft.

SK: There would be step-wise items when using multi-process in bincompat mode.

Then we look into `vfork()` and `exec()`.

And then multiple address spaces.
