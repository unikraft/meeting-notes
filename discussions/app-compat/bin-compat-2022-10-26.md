---
title: "Bin Compat WG, October 26, 2022"
tags: unikraft, musl-syscall
datetime: 2022-10-26T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- musl-syscall
participants:
- Simon
- Pierre
- RăzvanD
---

## :dart: Agenda

- Current status
- Next steps

## :closed_book: Discussions

RD: As part of the Munich hackathon, we ported a bunch of applications and created issues with the problems encountered.

SK: A next step is to provide `execve()`.
It's replacing the address space.
It's also relying on `posix-mmap`.

RD: What would be the best approach for students to tell what they work on?

SK: Some syscalls may require the implementation of a new subsystem.

PO: I can rerun the tool once I have a list of updated system calls.

RD: Applications that we want to support: https://github.com/unikraft/static-pie-apps/issues

SK: We have two types of incomplete system calls:
- One for each we have different flags
- One in which there is a particular value may change the behavior

PO: An idea would be to port the Linux Test Project.

SK: It makes sense to look into LTP both from a research and a suport perspective.

PO: gVisor is using a test suite.

SK: My future provided system calls will likely not show signal-related system calls.

## :wrench: TODOs and Decisions

SK: Generate list of system calls.

SK: Provide binary of ELF loader updated on Unikraft 0.10.

RD: Involve students to start working on system calls.

PO: Provide link on gVisor tests.

Long term: Nice looking graphical / web interface for syscall support status.
