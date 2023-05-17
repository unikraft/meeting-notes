---
datetime: 2023-05-17T17:30:00+01:00
location: Online, Google Meet
teams:
  - app-compat
participants:
  - RazvanD
  - Simon
  - Andra
  - Stefan
  - Tianyi Liu
---

### Discussions

TL: Which libc environment should I use for the project?

SK: There are multiple environments, depending on what we focus on.
Compiling applications together with unikraft will use musl, while using the elfloader will use the Unikraft's nolibc and use the applications libc (likely glibc).

RD: Talking about libc-test, the prime target should be musl.
Using libc-test to test the applications will eventually end up testing some internal functionalities of Unikraft, not just the libc.

SK: Use musl in principal, also have nolibc in mind, the critical items should be covered by it.

RD: The libc-test from what I recall is takes as part of musl, so it will have mainly tests from the musl libc.
More of an integration testing, also using the layers below the libc.

SK: The target of nolibc should be a libc replacement for smaller projects, or for the elfloader application, where you don't need to drag an entire libc, so the basic functionalities should work fine.

TL: I'm at the moment updating the libc-test repository to work with the latest Unikraft release.
There seem to be just simple issues, nothing complicated.

SK: Should we add more tests?

RD: There are more options, after libc-test gets ported, we can focus on extending the testing interface, cover more areas, extend existing tests, test also nolibc etc.

SK: One aspect could be also the vdso work, which we do not yes have, so that is also a way the project could go to.

TL: I think the project should be more that providing the vdso.
If I replace almost all the libc functionalities, there will be no need for vdso anymore.

SK: True, you will most likely not need the vdso anymore.

TL: I would like to also have some regression testing, since some functions may not be avalaible in Unikraft, it would be nice to have some regression testing to make sure new PRs don't break stuff.

RD: Make sure you choose a project where you have fun, enjoy yourself.

SK: In Unikraft, we are using the TLS as the application uses it on linux.
We need to switch from the "userland" to the "kernelland", so without changing anything you will have a problem when you will link the libc of the application.
There will be a TLS chain coming from the application and you will have the Unikraft TLS, this could be an aditionnal step towards the dinamic linking with the PLT GOT.

The proposal is just a stating point, we can see what tracks are also usefull, it's very important to have stuff like regression testing and others.

RD: What is your time zone?

TL: Current time is 11pm

RD: We have the Application Compatibility happening, it would be great if you can join it.
That is where the entire application compatibility people get toghether.
For Simon to decide, a periodic meeting regarding this project.
We can discuss the items in the Application Compatibility session, and see if there is need to do another meeting.

SK: Aim to use the App Compat meeting for updates, since it's 1h, create new meeting if / when needed.

TL: The Application Compatibility meeting slot is fine for me.
