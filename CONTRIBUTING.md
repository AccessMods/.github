\# Contributing to AccessMods



So, you want to help make games playable? You've come to the right place.



Whether you are a veteran developer with a finished mod or a student looking to fix a typo in a README, we are happy to have you. This document outlines the technical workflow we use to keep things organized and, most importantly, \*\*stable for the players\*\*.



---



\## 🏗️ The Core Philosophy: "Main is for Players"



The most important rule in this organization is simple:

\*\*The `main` branch of any repository must always be stable.\*\*



In many dev environments, `main` (or `master`) is where development happens. \*\*Not here.\*\*

Because our end-users are blind gamers downloading mods directly (and eventually via an automated installer), we cannot risk a broken build on the default branch.



\*   \*\*Do:\*\* Push tested, working code to `main`.

\*   \*\*Don't:\*\* Push "work in progress" code that crashes the game to `main`. Use a feature branch for that.



---



\## 🆕 Bringing a New Mod to the Org



If you have created a mod and want to host it here, welcome! Here is the "Onboarding Ritual":



1\.  \*\*Develop \& Test:\*\* Build your mod in your personal repository first. Ensure it is stable.

2\.  \*\*Contact Us:\*\* Reach out on Discord to request a move.

3\.  \*\*The Transfer:\*\*

&nbsp;   \*   You will transfer the repository ownership to `AccessMods`.

&nbsp;   \*   \*Don't Panic:\* For about 60 seconds, you will lose admin access.

&nbsp;   \*   \*\*The Restoration:\*\* We immediately add you back as an \*\*Admin\*\* on that specific repository.

4\.  \*\*You Are In Control:\*\* You now have full control again. You can manage settings, add your own collaborators, and even transfer the repo back out if you decide to leave.



\### Required Setup for New Repos

Once your repo is moved, please ensure the following:



\*\*1. Add Topics (Tags)\*\*

To help users find your mod, go to your repository settings (or the "About" section on the main page) and add the appropriate tags:

\*   `game-mod` (If it is a playable mod)

\*   `dev-tool` (If it is a utility)

\*   `library` (If it is code for other devs)

\*   `stable` or `beta` (To indicate status)



\*\*2. Create a Release\*\*

Please use the \*\*GitHub Releases\*\* feature to tag your binaries.

\*   Tag your release (e.g., `v1.0`).

\*   Upload the compiled zip/exe as an \*\*Asset\*\*.

\*   \*Why?\* Our future Mod Installer will rely on these "Assets" to automatically download the mod for players.



---



\## 🛠️ Contributing to Existing Mods



If you want to improve a mod that is already hosted here (and you aren't the primary owner), please use the standard \*\*Fork and Pull\*\* workflow.



\### 1. Fork the Repository

Click the "Fork" button in the top right. This creates a copy of the mod on your personal account.



\### 2. Create a Branch

Do not work on your default branch. Create a feature branch with a descriptive name:

\*   `fix/menu-crash`

\*   `feat/sonar-system`

\*   `docs/update-readme`



\### 3. Make Your Changes

Write your code. Please adhere to the coding style of the original repository (e.g., if they use K\&R braces, you use K\&R braces).



\### 4. Test with Screen Readers

Before submitting, \*\*test your changes\*\*.

\*   Does the game still launch?

\*   Does NVDA/JAWS actually speak the new text?

\*   If you added a sound cue, is the stereo panning correct?



\### 5. Submit a Pull Request (PR)

Open a PR to the original repository.

\*   \*\*Description:\*\* Explain \*what\* you changed and \*why\*.

\*   \*\*Link Issues:\*\* If you are fixing a bug, say "Fixes #123".



The repository owner will review your code. Be open to feedback—code review is how we all get better.



---



\## 🧹 Housekeeping Standards



To keep the organization clean, we ask for a few small things:



\*   \*\*Descriptive Commits:\*\* Please write commit messages that explain \*what\* happened.

&nbsp;   \*   Good: `fix: resolve crash when opening inventory`

&nbsp;   \*   Bad: `fixed bug` or `update`

\*   \*\*No Binary Bloat:\*\* Do not commit large `.exe` or `.dll` files directly to the git history if you can avoid it. Use \*\*Releases\*\* for binaries.

\*   \*\*Update Documentation:\*\* If you add a feature, please update the mod's specific README so players know how to use it.



---



\## ❓ Getting Help



If you are stuck with Git, confused about a Transfer, or just want to ask about the best way to hook into a Unity function, ask in the \*\*#development\*\* channel on Discord. We are here to help you ship code, not to judge your git history.

