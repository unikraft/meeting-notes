---
datetime: 2023-07-05T11:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - gsoc
participants:
  - Michalis
  - Simon
  - Rareș
  - RăzvanD
---

### Agenda

Status updates

### Discussions

RM: I moved the OFW driver to `lib/ofw/`.
I tried to librarize it as much as possible.
I didn't make a `Config.uk`.

MP/SK: `Makefile.uk` and `Config.uk` should be part of each library.

RM: I found an error that OFW is double linked.

MP: The best approach to get the issue, rather than go around it.

SK: The OFW needs to go out of KVM.

RM: So I delete the line from KVM and move it to `lib/ofw/`.

RM: I should `Config.uk` for OFW and then add it to the `plat/kvm/` dependency list.

SK: The include path of OFW.
The library should be called `uk_ofw`.
And the include path should `include/uk/`.
And the headers should be called `ofw.h`.

SK: When moving it to a library, we need to namespace it: include folders and file names.

SM: At some point, we would need to remove the function header from the `ofw_gic.h` file.

SM: For `virtio`, you have an `imply` depending on the architecture.

### TODOs and Decisions
