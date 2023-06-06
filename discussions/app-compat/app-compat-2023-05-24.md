---
title: "Application Compatibility WG, May 24, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-05-24T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Simon
- RăzvanD
- Florin
- Tiany
- Marc
- Felipe
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

### NodeJS

FP: NodeJS bincompat works.

FP: I'm now looking into the eventfd PR.

SK: Slides 18-21: https://wiki.xenproject.org/images/2/23/Unikraft-buildsystem-compressed.pdf

### lib-libc-tests

TL: I created a CI/CD action for 

https://github.com/unikraft/static-pie-apps/pull/85

https://github.com/i-Pear/unikraft/pull/2

https://github.com/i-Pear/unikraft/actions/runs/5067213432/jobs/9097989312

FP: Regarding Musl, some tests were left out, because they were not working.

FP: There are a lot of patches when porting `lib-libc-test`.

SK: It would be great to provide the scripts you used for this.

FP: There is compile option to change the symbol name.

TL: I enabled all the tests.

## :wrench: TODOs and Decisions

FP: Add an issue with the Musl-based build of NodeJS.

FP: Port more complicated applications on bincompat NodeJS.

FP: Natively port NodeJS with Unikraft.

RD: Talk to Alex about CI/CD integration.

RD: Add small apps to the binary compat hackathon on Saturday.
