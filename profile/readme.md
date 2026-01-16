# Welcome to the Accessibility Modding Hub

Hello, and welcome to the party.

If you are reading this, you are likely looking for one of three things: a way to play games that weren't built with you in mind, a place to host your work, or an answer to the question, "What on earth are these people doing with my game?"

We admit, this is a bit of a long read. However, we operate on a model of radical transparency and trust, so we hope you will read through this in full to understand if this is the right place for you.

## 📜 Table of Contents
*   [What We Are (And What We Are Not)](#-what-we-are-and-what-we-are-not)
*   [Visual Accessibility: A Primer for Outsiders](#-visual-accessibility-a-primer-for-outsiders)
*   [Code of Conduct & Transparency](#-code-of-conduct--transparency)
*   [For Contributors: The Workflow](#-for-contributors-the-workflow)
*   [Repository Structure](#-repository-structure)

---

## 🛡️ What We Are (And What We Are Not)

We are a centralized hub for **Accessibility Mods**—modifications designed specifically to enable blind and visually impaired gamers to play mainstream titles.

### To Game Developers and Publishers
We want to be clear about our intent. We are not here to pirate your games, nor are we here to break them.

Our philosophy is **Translation, Not Transformation.**
*   We do not modify core gameplay loops to provide an unfair advantage.
*   We do not bypass anti-cheat for malicious reasons.
*   We do not distribute illegal copies of game assets.

Our goal is to inject accessibility layers—screen reader support, audio cues, and navigational aids—into games that otherwise have none. We use standard modding tools where available, and where they aren't, we utilize hooks solely to read game state for accessibility.

A prime example of this philosophy in action is [Hearthstone Access](https://github.com/HearthSim/Hearthstone-Access), which opened a game to thousands of blind players without compromising the competitive integrity of the original. This project is a testament to the community's resilience: when the original developer could no longer support it, the community rallied to revive and maintain it collaboratively. It even garnered attention from Blizzard, sparking discussions about adding native accessibility features to render the mod redundant—a future we would welcome from you as well, should one of your games be featured here.

**A Note on Mechanics:**
Occasionally, a mod may slightly alter a mechanic, such as a timer. This is not to cheat, but to accommodate physics. Light travels faster than sound. It takes a sighted player a fraction of a second to glance at a UI element; it takes a blind player significantly longer for a screen reader to speak that same information. We only adjust these elements to level the playing field, ensuring the *intent* of the challenge remains intact.

---

## 👁️ Visual Accessibility: A Primer for Outsiders

If you are an indie dev or a sighted gamer stumbling upon this org, you might be wondering what "Accessibility Modding" actually looks like.

This goes beyond simply changing contrast settings or adding text-to-speech. We are often building entirely new audio-based user interfaces on top of existing visual ones. Our mods typically implement:

*   **Screen Reader Output:** Sending UI text (menus, inventory, dialogue) to screen readers like NVDA, JAWS, or SAPI.
*   **3D Audio Cues:** Using stereo or surround sound to indicate the position of enemies, objectives, or walls.
*   **Grid Navigation:** Translating visual maps into coordinate systems that can be traversed by sound.
*   **Sonar Systems:** Implementing proximity scanners that change pitch or frequency to alert players to nearby walls, traps, or interactables,or help them path-find to nearest waypoints.
*   **OCR & Hooking:** Reading the game's memory or visual buffer to detect state changes that have no audio cue.

To learn more about vision impaired accessible design, the specific libraries we use (like Tolk or Universal Speech) and how we approach different engines, check out our deep dive:
👉 **[Read the Full Accessibility Modding Workflow](https://github.com/AccessMods/.github/blob/main/ACCESSIBILITY_WORKFLOW.md)**

---

## 🤝 Code of Conduct & Transparency

This organization runs on a principle of **High Trust and Zero Ego.**

We believe that accessibility should be collaborative, not competitive. Whether you are a first-time contributor or an Organization Admin, we follow these core tenets:

1.  **Transparency:** Decisions regarding the organization are made openly. We don't do "shadow bans" or secret policies.
2.  **No Power Grabs:** Admins exist to facilitate, not to lord over others. The goal is to keep the repo clean, not to control your code.
3.  **Community Driven:** If the community decides a mod is stable, it gets hosted. If the community wants a change in workflow, we discuss it.

We are all here because we love games and we want to play them. That shared passion is our only currency.

---

## 🛠️ For Contributors: The Workflow

We know you just want to write code and not get bogged down in bureaucracy. However, to keep this hub professional and safe for users, we have a structured workflow.

**The Summary:**
1.  **You Build It:** Create and test your mod in your own repository.
2.  **We Test It:** Once the community confirms it is stable (no game-breaking bugs), you request a transfer.
3.  **You Own It:** You transfer the repo to this Org. We immediately grant you **Admin** access to it. You retain full control, including the ability to transfer it back out if you ever choose to leave.

**A Note on Admin Access:**
While Organization Admins technically retain access to repositories to assist in emergencies (simply due to how organizations function on this platform), we adhere to a strict policy: **we will never modify your code or repository settings without your explicit permission.**

**Technical Guidelines:**
*   Main branch must always be safe for a user to download and play.
*   For contributions to other people's repos, please use the standard "Fork and Pull Request" method.

For a complete guide on how to set up your repo, naming conventions, and contribution standards, please read:
👉 **[Read the Contribution Guidelines](https://github.com/AccessMods/.github/blob/main/CONTRIBUTING.md)**

---

## 📂 Repository Structure

To help you navigate, here is how our configuration is set up. You are currently viewing the **Organization Profile**.

*   **[AccessMods/.github](https://github.com/AccessMods/.github):** This is the configuration repo.
    *   `profile/README.md`: The page you are reading right now.
    *   `CONTRIBUTING.md`: The technical rules of the road.
    *   `ACCESSIBILITY_WORKFLOW.md`: Resources and guides for accessibility tech.

Feel free to explore the repositories tab to download mods, or join the discussion to help build the next one.

## Conclusion

We are thrilled to have you here, and we hope you enjoy your time.

Should you have any questions, please feel free to contact us on Discord (*Link Coming Soon*). For specific administrative concerns, you can mention the Staff role (*coming soon*), but for general ideas or proposed changes, we encourage you to post in the general discussion channel!

Since we exist to facilitate rather than dictate, most suggestions will be raised for a community vote anyway—we simply facilitate that discussion.

Happy Modding,
*- The AccessMods Team*