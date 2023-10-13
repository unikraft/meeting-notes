---
datetime: 2023-08-30T11:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
  - gsoc
participants:
  - Michalis
  - Rareș
  - Marc
  - RăzvanD
  - Marc
  - Simon
---

### Agenda

Status updates

### Discussions

RM: I get an error for virtio driver.

MP: We'll need to update that, according to a discussion we had yesterday.

RM: The error is part of `ukbus`.

MP: This depends on `virtio-pci`.

RM: There are some other PRs:

- data types PR: this could be reviewed and merged
- register definitions
  - Sergiu moved things around
- `compiler.h` migrations: this one could also be reviewed

MP: Especially after yesterday's discussion on how commits should be formulated, it's time to get them merged.

With RTC we would have merged everything related to KVM.

MP: As a summary from yesterday's discussion:

- Structuring commits
- Configuration

Decisions:

- Changes on different libraries should be on different commits.
  - For plat re-arch, it may be problematic, so there would be exceptions.
- Regarding bisecting, we will relax the requirements.
  - A workaround is to use a script that does bisecting at PR level.

For the PR, we will make the `VIRTIO_BUS` config visibile, after a discussion with Simon.

MP: Related to virtio, we will make a change to ukbus.

MP: Before we rework virtio, we would complete PCI.

### TODOs and Decisions

RM: After virtio, the next item is RTC.

SM+RM: Review PR: https://github.com/unikraft/unikraft/pull/1024

SK: Approve PR: https://github.com/unikraft/unikraft/pull/1024
