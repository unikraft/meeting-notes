---
datetime: 2023-07-12T11:00:00+02:00
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

RM: I looked at some courses on the boot system and the build systems.

RM: I went through all the PRs to make commit messages, squash them and improve them.

RM: For the GIC driver, I made a little experiment.
I created a driver in the `make menuconfig`.

MP: You need to have a top-level directory for interrupt controller.
And then you would have a configuration for each interrupt controller.
And then you would have a library that defines the API.

SK: Looking into the Kconfig system, my plan is to come up with a workaround to still use the boolean values.
And at some point you don't select two items.

SK: We have the general purpose libraries.
And we have platform libraries.

SK: For drivers, we imply the availability of headers.
This is deeply ingrained in the drivers.

SK: The plan is to hack this around, so we unblock this.

SK: We need to registers these drivers as libraries.

SK: Those drivers would have platform dependencies.

SK: We may have some drivers that don't rely on platform code, that will make this possible to build.

MP: I have interest in the interrupt drivers, and I would help with that.

MP: For the API library, would we name it `lib/ukintctlr`.
And then you have `drivers/ukintctlr`.

SM: I suggest we name it `ukintctlr`.
It's compatibile with Core Boot naming.

Linux and U-boot are using `irqchip`.

MP: For the CCA, I need to ask Xianjiang to do that for `uart`.

MR: The final design of `ukprint` would be a way of doing printing.
And the actual printing happens depending on the implementation.

MP: For now, we create the `ukconsdev` API that will use the `cin()` / `cout()` operations.
For drivers, we will have the actual implemenation.
In the future, we will rework this with `ukprint`.

MP: There is an issue on naming of the files under `arch`.
I asked to move all the register specific definition under `arch`, named `arch.h`.
I think that apart from `compiler.h`, the rest of the definitions do not need to be in sync.

MP: I Arm, I would put very CPU-generic definitions into `arch.h` and more specific things would have more specific items in drivers (or libraries).

MR: The paging definition is going to be part of the ever-present type of headers.

SK: Definitions would go into arch and lower-level items would go into the corresponding libraries.

### TODOs and Decisions

RM: Make progress on the driver directory hierarchy / configuration for drivers.

SK: Quick fix to the build system to be able to make dependency with 

MP: Talk to Xianjiang on the `ukconsdev` implementation required for Arm CCA.

SM: 
