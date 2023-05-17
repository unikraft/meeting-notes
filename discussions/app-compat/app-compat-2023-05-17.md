---
title: "Application Compatibility WG, May: 17, 2023"
tags: unikraft, app-compat, bincompat, syscall
datetime: 2023-05-17T12:00:00+02:00
location: Online, Discord (https://bit.ly/UnikraftDiscord), the `#monkey-business` voice channel
teams:
- app-compat, syscall, bincompat
participants:
- Andra
- Simon
- Teo
- Florin
- Cosmin
---

## :dart: Agenda

- Status update
- Next steps

## :closed_book: Discussions

AP: I published the 9pfs fix and it got merged.

SK: It is cool that it can just run hostfs.

AP: Previously, some paths were not working correctly. We might encounter more path related bugs in the future.

CV: I was able to get a stack trace on the host machine, will compare with app-elfloader run.

SK: Was OpenJDK affected by the futex wait issue?

CV: Yes, but I fixed it with Marco's fix. It should be upstreamed.

CV: PR 758.

SK: I likely have a different problem, will double check.

FP: I did the tid number PR, was merged, the crash is solved. Read-write locks from glibc now work.

SK: I will create a PR which instruments some lines of code and outputs more information. I used to investigate the futex wait issue.

SK: Fix for posix-event eventfd. When you create a nonblock fd, you run in an assertion, caused by a fcntl PR. Will create a PR.

FP: Should the assertion be erased?

SK: Yes.

SK: Doing work on posix-netlink for Envoy. Used as a networking interface.

TT: Compared native lib-redis with binary compatible, same behaviour, except for the futex wait issue.

SK: Possible cause for the EINVAL?

TT: Will work on that.

SK: The BGSAVE will not work due to the fork, should document.

FP: I tried running a script in app-compat. I encountered the nonblock issue. I commented the assert. There are issues with the file descriptors, they get blocked, after a while only idle_thread gets executed. From another thread, there is a write call on a file descriptor, but it does not appear to ever happen. There is an ioctl with a flag which returns EINVAL.

SK: I patched this, and the flag is handled correctly. You might have another issue. Where do you block?

FP: I block on a read. It tries to read the data which does not exist because the write did not happen. After the yield, it just sleeps.

SK: Maybe it's an issue with the eventfd mutex in the read function. I would investigate if the mutex lock is the blocking call and check what other thread did not call the unlock. Also check a commented snippet in the write function.

SK: Could also be an issue with vfs core, related to multiple readers and writers on the same fd.

SK: Check where you block in the read function.

SK: Due to the cooperative scheduler, debug messages should be able to accurately verify the code path.

FP: Should I look into 9pfs fcntl nonblock functionality?

SK: You can do that.

## :wrench: TODOs and Decisions

TT: Look into invalid argument issue on redis.

SK: Submit the 2 PRs.

FP: Investigate causes of eventfd blocking.

FP: Look into 9pfs fcntl nonblock.
