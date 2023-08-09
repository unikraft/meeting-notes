---
datetime: 2023-08-09T11:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - gsoc
participants:
  - Michalis
  - Simon
  - Rareș
  - Sergiu
  - RăzvanD
---

### Agenda

Status updates

### Discussions

RM: I went through Michalis's driver PR.
And on the driver

RM: For the GIC I know we need to place it under `uk/ctrl`.

RM: For the OFW placing it under `lib/`.
These are on top of `libfdt`.

RM: For the virtio, do we still keep the structure: for each driver we keep a directory for each device.

MP: For the GIC driver you will also have to port the interrupt controller API, which is moved into `plat/common/`.

MP: pl031 RTC can be under `ukrtc` subsystem, without requiring an API.
The API will be defined later, after we add other RTC-related devices.

SK: We could provide a skeleton library to have a Config.uk + header.

MP: But the code will still need a function.

#### PIE

SM: Should we use `ukreloc` or `uk_reloc`?

SK: We use `ukreloc` for the library name, `uk_reloc` for code (function, data structures), `__UK_RELOC__` for header guards, `..._UKRELOC_...` for other macros.

### TODOs and Decisions

RM: Friday, August 11: Proposal on compiler-specific data types.

RM: EOD: Complete one of the drivers.

SM: Use `uk_reloc` for code in the PIE implementation.
