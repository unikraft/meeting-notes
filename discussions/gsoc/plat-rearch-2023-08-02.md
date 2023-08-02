---
datetime: 2023-08-02T11:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - gsoc
participants:
  - Michalis
  - Simon
  - Rareș
  - Marc
  - RăzvanD
---

### Agenda

Status updates

### Discussions

RM: The compiler definitions and the essentials PRs are now ready to be upstream.

MP: We need some of them.
They are required for the `ukconsole` part of the CCA.

RM: I've done a design for the driver configuration menu.
I've been searching the entire program to see why the menu isn't shown.

MP: I will make a PR that will let you drop drivers in the `drivers/` directory.

SK: I have an update to the macOS that also update the PIE support.

RM: What should I do in the meantime?

MP: `include/uk/arch/define_types.h` defines types.
This task is about how we define Unikraft native types.

Currently `unsigned long` is defined as `__u64`.
Define native GCC types to Unikraft native types.
Consider Clang as well.

RM: Will some data types fit in the `types.h` header or in the arch-specific header.

MP: This will be based on the conclusion that you reach.

### TODOs and Decisions

RD/MP: Review Rareș's 3 PRs:
* https://github.com/unikraft/unikraft/pull/960
* https://github.com/unikraft/unikraft/pull/954
* https://github.com/unikraft/unikraft/pull/937

RD: Review Sergiu's PR.

MP: Create skeleton PR for drivers.
Take a look into Simon's branch for macOS.

RM: There is a task to look into GCC data types that can be used native Unikraft types.
It's task #3 on the board.
Also consider Clang.
Come back with a proposal on Discord.
Have a look at LP64 at the "64-bit data models" section in  https://en.wikipedia.org/wiki/64-bit_computing (and elsewhere)
