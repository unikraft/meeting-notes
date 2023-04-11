---
title: "Application Compatibility WG, March 29, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-03-29T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- RăzvanD
- Florin
- CosminV
- Teo
- Pierre
- AndreiM
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

SK: On the filesystem PR, I have a slightly different implementation and I want to publish.

SK: I'm adding support for automatically loading the executable and then figuring out loading the other parts.

AP: I can now run both dynamically and statically linked arguments.

AP: I'm looking into making symbolic links work with app-elfloader.

AP: I'm using the `helloworld` setup.

AP: I've started going through the issues.

SK: You need to find the root cause of having the `0` address.

FP: The `eventfd2` syscall returns EINVAL.

FP: There is an issue with the `clone3()` syscall.
I'll be back with a more detailed discussion on the channel.

SK: There are some missing flags.

PO: The paper is almost ready for submission, mid-April 2023 for ASPLOS.

PO: On the test suite side, the student is finishing their project.

## :wrench: TODOs and Decisions

SK: By tomorrow, provide PR with the `initramfs` support.

CV: Remove the initramfs part from the PR.

AP: Test with `initramfs` to see if symbolic links are an issue there as well.

TT: Create a issue with `clone3` problem.
