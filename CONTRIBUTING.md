# Contributing to AccessMods

So, you want to help make games playable? You've come to the right place.

Whether you are a veteran developer with a finished mod or a student looking to fix a typo in a README, we are happy to have you. This document outlines the technical workflow we use to keep things organized and, most importantly, stable for the players.

It is our hope to keep this organization neat, clean, and adherent to technical standards, but we also want to make it friendly to people from all levels of experience. We understand that learning Git involves a learning curve. However, this community effort requires that we all be willing to step out of our comfort zones to an extent. By respecting everyone's time and following these constraints, we improve the general experience for everyone—whether they are developers or players.

---

## 🏗️ The Core Philosophy: "Main is for Players"

We follow standard professional software development practices to ensure safety and stability. The `main` branch of any repository must always be stable.

Instead of working directly on `main`, please create branches for your specific tasks.
    **Examples:** `feature/new-menu-sounds`, `fix/broken-pathfinding`, or `docs/update-readme`.

When you are ready and have thoroughly tested your code, you merge it into `main`.

### Our Preference: Pull Requests
We strongly prefer that everyone—whether you are the repository owner, a collaborator, or an outside contributor—opens a Pull Request (PR) to merge their code. This allows for a clean history and a moment of review.

### For Repo Owners
If you own the repository, you technically have the permissions to merge branches locally or push code directly to the `main` branch (via the command line or the GitHub web upload).

However, we strongly discourage pushing to `main` without a branch or a PR review process.
*   It bypasses safety checks.
*   It makes it harder to track when a bug was introduced.

If you are new to Git and find Pull Requests difficult, you may merge locally, but please ensure you have tested thoroughly before pushing.

### For Outside Contributors
If you are contributing to a repo you do not own, opening a Pull Request is the only way to contribute.

---

## 🆕 Bringing a New Mod to the Org

If you have created a mod and want to host it here, welcome! Here is the standard "Onboarding Ritual":

### 1. The Stability Phase
Before moving here, your mod should be "battle-tested."
*   Publish your mod on your personal GitHub.
*   Post about it in the community (e.g., on the AudioGames.net forum or our Discord).
*   Get Feedback: Let people play it. Fix the initial bugs.
*   Consensus: Once the community agrees "Yes, this works and is playable," it is ready for the Org.

### 2. The Transfer
*   Contact us on Discord to request a move.
*   You will transfer the repository ownership to `AccessMods`.
*   *Don't Panic:* For about 60 seconds, you will lose admin access.
*   We immediately add you back as an Admin on that specific repository.

### 3. You Are In Control
You now have full control again. You can manage settings, add your own collaborators, and even transfer the repo back out if you ever decide to leave.

---

## 🏷️ Setup: Tags and Releases

Once your repo is moved, please do these two things. It might sound like extra homework, but it makes a huge difference for the end-user.

### 1. Add Topics (Tags)
To help users find your mod, go to your repository settings (or the "About" section on the main page) and add the appropriate tags:
*   `game-mod`: If it is a playable mod.
*   `dev-tool`: If it is a utility.
*   `library`: If it is code for other devs.
*   `stable` or `beta`: To indicate status.

### 2. Create Releases
Please use the GitHub Releases feature to upload your compiled mod.

*   Why: Most players do not know how to use Git, nor do they have compilers installed. They just want a `.zip` file they can extract.
*   The Benefit:
    *   If you use Releases, users can download your mod without cloning the repo.
    *   Our future Automated Mod Installer will rely on these releases to auto-install mods for players.

---

## 🛠️ Contributing to Existing Mods

If you want to improve a mod that is already hosted here (and you aren't the primary owner), please use the standard **Fork and Pull** workflow.

### 1. Fork the Repository
Create a copy of the repository on your own account.
*   *Navigation Hint:* The "Fork" button is usually located in the top-right section of the page (often inside a "Fork" link or split button within the 'repository actions' landmark, for screen reader users).

### 2. Create a Branch
Do not work on your default branch. Create a feature branch with a descriptive name using the conventions mentioned above (e.g., `fix/descriptive-name`).

### 3. Make Your Changes
Write your code. Please adhere to the coding style of the original repository (e.g., if they use K&R braces, you use K&R braces).

*   *Note for AI Users:* If you are using an LLM coding agent (like Cursor, Copilot, or ChatGPT), most will detect the style automatically. However, it is good practice to explicitly instruct the agent to "follow the existing coding style and indentation of the file" in your system prompt or instruction file (e.g., `.cursorrules`).

### 4. Test with Screen Readers
Before submitting, test your changes.
*   Does the game still launch?
*   Does NVDA/JAWS actually speak the new text?
*   If you added a sound cue, is the stereo panning correct?

### 5. Submit a Pull Request (PR)
Open a PR to the original repository. You can do this via the GitHub website or by using the GitHub CLI (`gh pr create`).

*   *Navigation Hint:* Navigate to the "Pull Requests" tab and look for the "New Pull Request" button.
*   **Description:** Explain what you changed and why.
*   **Link Issues:** If your PR resolves an already open issue (by yourself or someone else), say "Fixes #123" in the description. This tells GitHub to automatically close the issue when your code is merged.

The repository owner will review your code. Be open to feedback—code review is how we all get better.

---

## 🧹 Housekeeping Standards

To keep the organization clean, we ask for a few small things:

*   **Descriptive Commits:** Please write commit messages that explain what happened.
    *   Good: `fix: resolve crash when opening inventory`
    *   Bad: `fixed bug` or `update`
*   **No Binary Bloat:** Do not commit large `.exe` or `.dll` files directly to the git history if you can avoid it. Use Releases for binaries.
*   **Update Documentation:** If you add a feature, please update the mod's specific README so players know how to use it.

---

## ❓ Getting Help

If you are stuck with Git, confused about a Transfer, or just want to ask about the best way to hook into a Unity function, ask in the **#development** channel on Discord. We are here to help you ship code, not to judge your git history.