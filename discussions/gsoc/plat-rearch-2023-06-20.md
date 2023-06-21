---
datetime: 2023-06-20T10:30:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
    - gsoc
participants:
    - Michalis
    - Marc
    - Edi
    - Rareș
    - Sergiu
---
    
### Agenda

Status updates

### Discussions

MP: Types must have no `libc` dependencies.

MP: For `/lib`, it's ok for some files to be dependent to external libraries.

RM: Should I make separate commits for each category of files?

MR: Yes, commits need to be more explicit.

EM: Should we stick with the proposed design?

MP: You should move the header to the library.

MR: `spinlock.h` could be deleted.

EM: All definitions go into the header.

### TODOs and Decisions

RM: Create PR with the work already done and continue it.

EM: Create PRs with every step made.