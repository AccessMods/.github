\# Accessibility Modding Workflow



This document outlines the techniques, libraries, and philosophies we use to make mainstream video games accessible to blind and visually impaired players.



Whether you are an indie developer curious about making your game accessible natively, or a modder looking to patch an existing title, this guide serves as your roadmap.



\## 📜 Table of Contents

\*   \[Defining Accessibility in Games](#defining-accessibility-in-games)

\*   \[Further Reading: The Rabbit Hole](#further-reading-the-rabbit-hole)

\*   \[How It Works Under the Hood](#how-it-works-under-the-hood)

\*   \[The Tech Stack and Tools](#the-tech-stack-and-tools)

\*   \[Engine-Specific Workflows](#engine-specific-workflows)

\*   \[Growing the Knowledge Base](#growing-the-knowledge-base)



---



\## Defining Accessibility in Games



\*\*Accessibility\*\* (n): The quality of being able to be reached or entered; easy to obtain or use.



In the context of video games for the blind, accessibility does not mean "auto-playing the game." It means providing the necessary sensory information so that a player can make informed decisions.



\### Translation, Not Transformation

Our goal is to translate visual output into audio output.

\*   \*\*Visual:\*\* A red bar above an enemy's head indicates health.

\*   \*\*Translation:\*\* A screen reader announces "Enemy Health: 50 percent," or a pitch-shifted beep lowers in tone as health drops.



We generally avoid mechanical enhancements (like aim-bots or god-mode) unless the physics of the game make it impossible to react in time via audio alone (e.g., the "Speed of Sound" rule, where we may slow down a timer to account for the time it takes to listen to a prompt).



---



\## Further Reading: The Rabbit Hole



\*\*A Note for Developers:\*\*

This document focuses on the \*technical implementation\* of \*\*mods\*\*. As such, if you are a developer wishing to have accessibility baked into your game from the start, you may not find \*\*everything\*\* you are looking for here.



While the logic is largely similar (e.g., sending text to a screen reader), the implementation differs between native development and external modification. Therefore, to keep this document focused, we have linked further reading below on the broader topic of accessible game design.



We hope that combining those resources with the technical knowledge in this doc provides a solid starting point for adding accessibility to your own games. Beyond that, should you have specific questions or require \*\*Accessibility Testing\*\* and consultation for your project, please feel free to reach out to us on Discord.



\*   \*\*\[Game Accessibility Guidelines](http://gameaccessibilityguidelines.com/):\*\* A comprehensive list of best practices for developers.

\*   \*\*\[AudioGames.net](https://forum.audiogames.net/):\*\* The central hub for the blind gaming community.

\*   \*\*\[Accessible Player Experiences (APX)](https://accessible.games/apx/):\*\* Design patterns for accessibility from the AbleGamers charity.



---



\## How It Works Under the Hood



How do we actually get a game to "speak"? Regardless of the engine, the concept usually relies on three core technologies.



\### 1. Screen Reader Abstraction

Most blind users utilize a Screen Reader (like NVDA, JAWS, or Narrator) to navigate their computer. We do not want to write code for each specific reader.

\*   \*\*Solution:\*\* We use libraries like \*\*\[Tolk](https://github.com/dkager/Tolk)\*\* or \*\*\[Universal Speech](https://github.com/qtnc/UniversalSpeech)\*\*. These are "wrapper" libraries. You send text to them (e.g., `Speak("Game Started")`), and they automatically detect which screen reader the user has running and pass the message along.



\### 2. Input Hooking

Sometimes we need to trigger accessibility features (like "Read current objective") using keys that the game doesn't use.

\*   \*\*Solution:\*\* We hook into the game's input loop to listen for specific key combinations without interfering with the game's native controls.



\### 3. Memory Reading \& Reflection

In many cases, the game doesn't "know" it needs to send text to us.

\*   \*\*Solution:\*\* We use \*\*Reflection\*\* (in C# games) or \*\*Memory Reading\*\* (in C++ games) to watch the game's internal state. When the variable `EnemyCount` changes, we detect it and trigger an audio cue.



---



\## The Tech Stack and Tools



We don't expect you to reinvent the wheel. Here are the tools we use to bridge the gap between the game engine and the screen reader.



\### General Modding Frameworks

These are the industry-standard tools used by modders everywhere (sighted or blind) to inject code into games.

\*   \*\*\[BepInEx](https://github.com/BepInEx/BepInEx):\*\* The go-to framework for Unity (and some .NET) games. It handles loading your DLLs into the game.

\*   \*\*\[MelonLoader](https://github.com/LavaGang/MelonLoader):\*\* Another popular alternative for Unity, particularly useful for games using IL2CPP.

\*   \*\*\[RE-UE4SS](https://github.com/UE4SS-RE/RE-UE4SS):\*\* A powerful scripting system and C++ modding API for Unreal Engine games.



\### Community Accessibility Tools

Over time, our community realized we were writing the same code over and over again—code to find the screen reader, code to clean up text tags, code to manage audio queues. So, we abstracted it.



\#### UnityAccessibilityLib

This is a specialized library maintained by this organization. It is designed to work alongside BepInEx or MelonLoader to handle the heavy lifting of accessibility.



It simplifies the workflow by handling:

\*   \*\*Universal Speech Integration:\*\* Automatic fallback between NVDA, JAWS, SAPI, etc.

\*   \*\*Text Cleaning:\*\* Strips out Unity rich text tags (like color codes) so the screen reader speaks clearly.

\*   \*\*Speech Management:\*\* Prevents audio spam when multiple events happen at once.



If you are modding a Unity game, we highly encourage you to use this rather than writing your own screen reader wrapper.

👉 \*\*\[View the UnityAccessibilityLib Repository](https://github.com/AccessMods/UnityAccessibilityLib)\*\*



---



\## Engine-Specific Workflows



Different game engines require different approaches. Here is how we typically attack a project.



\### Unity Games

Unity is currently the most accessible engine for modders due to its use of C# and Mono/IL2CPP.

\*   \*\*Tools:\*\* BepInEx or MelonLoader (Mod Loaders), dnSpy or ILSpy (Decompilers).

\*   \*\*Strategy:\*\* We inject code that listens to UI events. Because Unity UI is standardized, we can often write a script that says, "Whenever a text box appears, send its content to UnityAccessibilityLib."



\### Unreal Engine

Unreal compiles to native C++, making it harder to interpret.

\*   \*\*Tools:\*\* Unreal Mod Loader, RE-UE4SS.

\*   \*\*Strategy:\*\* We often have to rely on the Unreal Reflection system to find "UObjects" (game objects) and read their properties. In older Unreal games, we may fallback to memory scanning or OCR (Optical Character Recognition) if the game is heavily obfuscated.



---



\## Growing the Knowledge Base



This document is a living guide.



More additions will be coming to this page soon as the community gathers more information. Whether that is new workflows for different engines (like Godot), new libraries, or better techniques for memory reading, we rely on \*\*you\*\* to help us document it.



What we have achieved so far would not have been possible without the resilience of a few dedicated modders. They modded a game, figured out it worked, modded another, and then realized: \*"Hey, I can abstract this part and make it easier for others."\* That is exactly how tools like `UnityAccessibilityLib` were born.



We want more people to join us—to try modding different types of games, to fail, to succeed, and then to come back here and share what they learned so the next person has an easier time.



---



\## Join the Discussion



Discussion, support, and development chat happen on our Discord server.



\[ \*\*Join the Discord Server\*\* ]( PUT\_YOUR\_DISCORD\_LINK\_HERE )

