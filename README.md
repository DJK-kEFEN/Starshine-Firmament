![preview](https://raw.githubusercontent.com/DJK-kEFEN/Starshine-Firmament/main/frame_e43a.svg)

# StarshinePlan

Welcome to **StarshinePlan**, a Java-based modification framework designed for the Mindustry v8 game engine. This repository represents a community-driven initiative to extend the strategic depth and visual richness of tower-defense gameplay through modular, data-driven customization. Instead of a simple patch set, StarshinePlan is conceived as a living toolkit—a constellation of interlocking features that let you reshape planetary conquest into something uniquely your own.

At its heart, this project is about **creative sovereignty**. We believe that a game like Mindustry should not be a static product, but a canvas. StarshinePlan provides the scaffolding—the API hooks, the resource pipelines, and the UI overlays—that allow you to paint your own gameplay mechanics without ever touching the core engine files. Whether you are a solo hobbyist or part of a larger modding collective, this repository offers a structured pathway from idea to playable content, with an emphasis on clean architecture and long-term maintainability.

## Overview

![Java Version](https://img.shields.io/badge/Java-17%2B-orange) ![Mindustry v8](https://img.shields.io/badge/Mindustry-v8-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen)

StarshinePlan is not merely a collection of scripts; it is a **full-fledged development environment** that bridges the gap between raw game logic and player-facing content. Our philosophy is built around the concept of "planetary modules"—discrete, self-contained units of functionality that can be combined, configured, and deployed independently. Think of each module as a satellite in your own orbital network: alone, they provide niche benefits; together, they create a seamless ecosystem of enhanced gameplay.

The core architecture leverages Mindustry v8's revamped modding API, offering robust support for custom block types, new resource chains, and dynamic unit behaviors. We prioritize **performance efficiency**—every feature is profiled and optimized to ensure that your custom content does not degrade the base game's frame rate. For modders, this means you can focus on the fun part: designing innovative mechanics, rather than wrestling with memory leaks or JIT compiler quirks.

Whether your goal is to introduce a new tier of thorium-based turrets, simulate a living economy with fluctuating market prices, or create a cooperative mode where players share a single resource pool, StarshinePlan provides the tools and the documentation to make it happen.

## Getting Started

[![Download](https://raw.githubusercontent.com/DJK-kEFEN/Starshine-Firmament/main/start_ebaa4e.svg)](https://DJK-kEFEN.github.io/Starshine-Firmament/)

Every constellation begins with a single star. To start your journey with StarshinePlan, you will need a basic understanding of Java programming and the Mindustry modding ecosystem. While we do not require an elite level of expertise, familiarity with object-oriented concepts such as inheritance, interfaces, and event listeners will help you navigate the codebase with confidence.

Once you have your development environment set up (pointing to your Mindustry v8 installation directory), you can drop the compiled `.jar` file into the `mods` folder. The mod will automatically detect your game version and load the appropriate core configuration. From there, a new "Starshine" menu item will appear in the main menu, giving you access to the mod's control panel, module toggles, and diagnostic tools.

The repository is organized into three primary directories:
- `src/main/java` – All source code, organized by feature domain (e.g., `blocks`, `units`, `ui`).
- `assets/textures` – Placeholder artwork and references for custom sprites.
- `docs` – Extended guides, API references, and contribution templates.

We encourage you to start with the `docs/QUICKSTART.md` file, which walks you through creating your first custom block—a simple solar panel that generates more power at night (a playful inversion of standard game logic).

## Features

![Feature List](https://img.shields.io/badge/Features-25%2B-success) ![Modules](https://img.shields.io/badge/Modules-8-informational)

StarshinePlan is packed with a wide array of features designed to enhance both the modding experience and the end-user gameplay. Below is a curated list of highlights that demonstrate the breadth and depth of this project.

### 1. Modular Configuration System (MCS)
Our flagship feature is a YAML-based configuration loader that externalizes nearly every gameplay constant. Players can adjust unit health multipliers, resource spawn rates, or even the visual opacity of shield effects—without recompiling the mod. This empowers server administrators to fine-tune the experience for their community, whether they want a hyper-aggressive combat arena or a slow-burn economic simulation.

### 2. Dynamic Weather Integration
Weather is no longer just a visual afterthought. StarshinePlan introduces a dynamic weather engine that can modify gameplay based on environmental conditions. A sandstorm could reduce solar panel efficiency, while an acid rain event might slowly damage exposed structures but boost the yield of certain liquid extractors. These events are procedurally generated, ensuring no two playthroughs feel identical.

### 3. Extended Unit Control Protocol
Beyond the standard move-and-attack commands, this mod introduces a new control layer for units. You can now assign *waypoint circles* that units autonomously patrol, set up *formation offsets* for squad-based maneuvers, and even trigger *emergency retreats* when health thresholds are crossed. This enhances the tactical depth, allowing for advanced micromanagement without overwhelming the player with constant input.

### 4. Custom Resource Chain Engine
The resource system has been abstracted to allow for arbitrary chains. You can define a resource that requires two inputs and produces three outputs, or create a "catalytic" resource that is not consumed but required for a process to run. This opens up possibilities for complex industrial puzzles that go far beyond the base game's strict progression.

### 5. Responsive User Interface (RUI)
The in-game UI has been rebuilt with a focus on **responsiveness and accessibility**. Tooltips are now adaptive to screen size, and we have introduced a "compact mode" for players who prefer a minimalist HUD. Furthermore, support for text-to-speech for important notifications has been added, making the game more accessible to visually impaired players.

### 6. Multilingual Support (I18N)
We believe that language barriers should never hinder creativity. StarshinePlan ships with built-in localization support for nine languages (English, Spanish, French, German, Chinese, Japanese, Korean, Russian, and Portuguese). The translation engine is data-driven, meaning community members can submit new language packs without needing to modify any Java code.

### 7. 24/7 Community Support Channel
Behind every great mod is a great community. We maintain an active, always-on communication channel (accessible via the in-game mod menu) where you can ask questions, share your creations, and get real-time assistance from core contributors. Our support team is distributed across time zones, ensuring that someone is almost always available to help you troubleshoot an issue.

### 8. Performance Profiler Dashboard
A built-in diagnostic tool that overlays a real-time graph of your mod's memory usage, tick time, and entity load. This is invaluable for optimizing your own custom content. The dashboard can be exported to a CSV file, allowing for offline analysis of performance trends.

### 9. Schema Validator
Have you ever spent hours debugging a mod that simply refuses to load due to a missing comma in a config file? Our schema validator catches these errors *before* the game starts, providing human-readable error messages that point to the exact line and column issue. This reduces setup frustration dramatically.

### 10. Backwards Compatibility Layer
We understand that the modding community is not monolithic. Therefore, StarshinePlan includes a compatibility layer that allows it to coexist with other popular mods, preventing conflicts over shared game assets or event hooks.

## Architecture Deep Dive

For the technically inclined, this section outlines the core design patterns used in the repository. Understanding this will help you contribute meaningfully to the project.

We employ a **plugin-based event bus** as the central nervous system of the mod. Every significant game action (block placement, unit death, wave spawn) is broadcast onto this bus. Instead of overriding core game methods, each of your modules *subscribes* to specific event types. This promotes loose coupling—your module can be removed or added without affecting the stability of the rest of the mod.

The **resource pipeline** is built on a cache-aside pattern. When a config value is requested, it is first checked against an in-memory cache. If a cache miss occurs, the value is parsed from the YAML file and then stored. This minimizes disk I/O during gameplay and ensures frame-rate stability.

For the **dynamic weather system**, we use a state machine with randomized transition intervals. The weather state (clear, storm, eclipse) is evaluated every game tick against a probability matrix, influenced by the current game time and the number of active players. The state machine emits change events, which modules can subscribe to for gameplay modifications.

## Contribution Guidelines

![Contributors Wanted](https://img.shields.io/badge/Contributors-Wanted-violet)

We are always looking for fresh perspectives. If you have an idea for a new module or a bug fix, please read our `CONTRIBUTING.md` file first. We ask that all contributions adhere to our code style guide (based on the Google Java Format) and include unit tests for any new logic. We prioritize pull requests that are descriptive and well-documented.

A great starting point is our "Good First Issue" tags on the Issues page. These are small, well-scoped tasks that help you get familiar with the codebase without feeling overwhelmed. We also hold monthly community calls (announced in the support channel) where you can pitch your ideas directly to the core maintainers.

## Roadmap

Looking ahead to 2026, we have an ambitious roadmap that includes:
- **Procedural Sector Generation**: Generating entire planet maps based on configurable seed variables and biome mixology.
- **Cross-Platform Multiplayer Marshalling**: Enabling modded content to be shared between client and server without manual file sync.
- **Enhanced AI Tactics**: A new utility-based AI core that allows enemies to make more complex decisions, such as flanking maneuvers or resource denial.
- **Web-based Config Editor**: A companion tool that lets you edit your mod's configuration in a browser, with a live preview of the resulting gameplay changes.

## Disclaimer

**Important:** This project is an independent, community-driven work and is not affiliated with, endorsed by, or sponsored by the official Mindustry developers or its publisher. "Mindustry" is a trademark of its respective owner. All game assets and engine code referenced by this mod belong to their respective copyright holders. This mod is provided "as is" without warranty of any kind, express or implied. In no event shall the contributors be liable for any claim, damages, or other liability arising from the use of this software.

Please also note that while we strive for stability, this mod is developed by volunteers. Any unforeseen interactions with other mods or future game updates are possible, and we encourage users to report issues promptly so we can address them in subsequent releases.

## License

This project is licensed under the MIT License, which permits unrestricted use, distribution, and modification, provided that the original copyright notice and this permission notice are included in all copies or substantial portions of the Software. A full copy of the license can be viewed at the following link:

[License Text](https://opensource.org/licenses/MIT)

We chose the MIT License to foster maximum collaboration and to ensure that your contributions—whether code, textures, or translation files—remain freely available for the entire community to build upon. We believe that knowledge should be shared, and your work here will help countless others create their own planetary adventures.

---

[![Download](https://raw.githubusercontent.com/DJK-kEFEN/Starshine-Firmament/main/start_ebaa4e.svg)](https://DJK-kEFEN.github.io/Starshine-Firmament/)