---
title: "Binary Compat WG, October 19, 2022"
tags: unikraft, syscall, bincompat
datetime: 2022-10-19T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- bincompat, syscall, musl
participants:
- Felipe
- Pierre
- Simon
- RazvanD
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

PO: I collected a list of tools from Felipe.
And I'm running Loupe on those: https://github.com/unikraft/loupedb

PO: We have results that shows us what syscalls are required for supporting these applications.

SK: This is dynamic analyis.

SK: Another next steps is to increase this.

SK: Just a helloworld for the application is good news.

PO: There are things we can do: write tests for applications.
The precision of the test is useful for the app.

FH: Alex mentioned there was a framework to test applications.

PO: Debian integrates some make check for packages.

SK: As a developer tool, you want to know what's missing.

FH: The analysis of individual clone is done manually.

## :wrench: TODOs and Decisions

RD: Assign students to work on syscall implementation and features missing in syscalls.

SK: Generate list of supported system calls.

SK: Provide updated ELF Loader.
