# Regarding QA

I've been helping the OpenMandriva project with side tasks all around for the past couple of years. While now I'm mainly relegated to infrastructure work because I'm doing too many other things, I'm particularly worried about the current state of affairs. It's too reckless, people aren't being careful, and the notion of "works for me" is abused too much.

Now, there's the notion of making Lx a rolling-release type distribution, and unfortunately, I cannot support that without improvements to the current QA system that puts in strict access control links and a project management tool that people look at. Because people don't listen.

## Rolling-release type distribution?

As I envision it, from Lx 4 and on, we have a stable and unstable branch. The unstable branch is Cooker; but the stable branch is Lx. That doesn't sound like anything spectacular, but when we build updates in Cooker and they are approved, they'll be automatically mirrored to stable on a weekly snapshot basis.

That's what we mean by rolling. (That also means we have to slow down Cooker occasionally to respin a new ISO, but if everything is stable, we shouldn't have to slow it down at all).

No more branches, in essence. I should be able to have an ISO of Lx 4 and be able to upgrade all the way to Lx 12 without issue, for example.

## What's pushing this? We just released Lx 3?

Kahinah must be deprecated by November 1st, because Persona shuts down November 30th and we don't have a replacement. __This is a hard deadline.__ Also because I don't have much motivation to work on Kahinah right now and it's falling apart because I'm thinking of too many things right now.

## Sounds simple?

No. Two major blockers have arisen:

* ABF improvements (i.e. Kahinah & ABF)
* Project management (i.e. how not to break anything)

### ABF Improvements

* We need to find a way to push 100 updates w/o causing the repositories to go inconsistent. So maybe locking/unlocking publishing, batching updates from Cooker to Lx (snapshotting), and more.
* We need ease of use. An easy way for testers to test specific updates, as well as bulk +1/-1 them. (i.e. CLI)
* We need to lock down management of updates. Devs shouldn't be able to push their own packages for a specific timeframe, or access control lists should be put in place.
* Health warnings should be put prominently - i.e. if a package is on the critical path (basesystem-minimal, etc), be more stringent on its approval and more lenient on its disapproval. If a package is a security update, it should be marked as such.
* In a way, Kahinah should be merged into ABF so that we achieve a way to put access control without having ABF put a gaping hole there where devs can push their own packages. The trust-no-one method, unfortunately.

## Project Management

* I'd like to merge all our project tracking strategies into one place. So Bugzilla and OpenProject merge into OpenProject, maybe we put it on Github, or ABF -- either way, we need _one_ central location. I personally prefer OpenProject, so migrating all our Bugzilla issues to OpenProject.
* In order to enforce it, I'd like to block Github commits/ABF builds that don't have an issue opened, especially when we're about to release a snapshot.

## Overall,
More automation is what we're seeing. Too many things done manually means there's too much room for mistakes.

## Anyway:
I'll be putting up instances of infrastructure we'll be using. That includes me looking at LDAP (maybe switching to FreeIPA to manage single sign on access?), as well as all the software we use. I'd like to consolidate the software we use and automate it as much as possible so that we can work as little as possible to maintain this distribution.

Thoughts welcome on om-cooker@.

