---
title: "App Compat WG, March 8, 2023"
tags: unikraft, musl-syscall
datetime: 2023-03-08T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- musl-syscall
participants:
- Simon
- RăzvanD
- FlorinP
- Felipe
- Cosmin
- TeoT
- Andra
- ȘtefanJ
- AndreiM
---

## :dart: Agenda

- Current status
- Next steps

## :closed_book: Discussions

TT: When running `app-elfloader`, there is an issue with `posix-mmap`.

SK: It's a double fault part.

TT: I got to this from using Python.
But it not related to the use of Python.

TT: There is another issue with semaphores.

CV: I'm also not able to get the dynamic `app-elfloader` working.

SK: In my setup I was using the CPU emulation mode of QEMU.

SK: There was an issue in my 9pfs that is freezes in the root filesystem.
It seems to be related to the timer interrupt.

TT: Inside `mount` there is the `9pfs_dettach` and `9pfs_attach` call.
If I do `stepi` it works, otherwise it doesn't work.

RD: Cosmin, Teo, when issues are solved, look into running other applications on top of the ELF Loader:
- Run existing ported `static-pie-apps`: https://github.com/unikraft/static-pie-apps
- Run existing ported `static-pie-apps` but build dynamically
- Build and run new dynamic apps listed in issues: https://github.com/unikraft/static-pie-apps/issues

SJ: No updates on my side.

### procfs

AM: I was trying to make the `cmdline` work.
Simon mentioned that I should look into something else.

AM: The branch is more or less working with 0.12.

AM: I read about the stream buffer in order to improve it.

AM: 3 weeks for updating procfs and 0.12, and stream buffer, and caching.

SK: Don't cache too much because the ukstore information should be fresh.

### Loupe

FP: I'm testing NodeJS with Loupe.
It's working on the server I was provided.

FP: The containers were writing log files and fill disk space.
The solution was to just print less lines in the log files.

FP: There was an issue with persistent processes.
I don't know if it will work on parallel mode.

FP: For the moment, the tests are running.

FP: I started porting NodeJS as a library.
And porting with app-elfloader.

## :wrench: TODOs and Decisions

TT: Create issues on the Unikraft repository: https://github.com/unikraft/unikraft/issues

TT/CV: Look into running different applications using the binary compatibility layer.

SK/RD: Look into the issue with `posix-mmap`.

AP: Look into using the `app-elfloader`.

AM: In 3 weeks time:
- Make procfs works with 0.12
- Use streambuf
- Add caching of ukstore data

FP: Provide update to Pierre.

FP: Test with parallel mode.

FP: Port NodeJS as a library on Unikraft.
