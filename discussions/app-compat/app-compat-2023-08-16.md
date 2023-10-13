---
title: "Application Compatibility WG, August 16, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-08-16T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Simon
- RăzvanD
- Teo
- Tianyi
- Ștefan
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

TT: I ran `helloworld` with `fork-glibc` and `fork-musl`.

SK: Glibc uses named version symbols.

### Unikraft as a Static Library

RD: Tiany was thinking about linking the Unikraft object files to the application files.
Object files can be collected as application files.
