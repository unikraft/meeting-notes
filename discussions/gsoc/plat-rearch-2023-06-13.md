---
datetime: 2023-06-13T10:30:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - gsoc
participants:
  - Michalis
  - Marc
  - Edi
  - Rareș
  - RăzvanD
---

### Agenda

Status updates

### Discussions

RM: I think I did what's required: https://github.com/unikraft/unikraft/pull/937

MP: I would add a Kconfig option and then I would use `-foptimize`, an optimization configuration.

MR: Where would you put the generic definitions?

MP: In the top header, that will be included by everything.

If it's x86, only create arch/x86.

Otherwise, only use the built-ins in the generic header.

The library name would be `ukatomic`.

The name would be `uk_ffs` instead of `ukarch_ffs`.

### TODOs and Decisions

RM: Continue with the definitions under `plat/common`.

EM: Try two approaches for `ukdynamic`.
Let's then see which works best.
