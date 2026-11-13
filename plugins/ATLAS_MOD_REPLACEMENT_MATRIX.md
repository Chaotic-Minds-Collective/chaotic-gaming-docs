# ATLAS Mod Replacement Matrix

This matrix maps the 30-item local Workshop inventory to original Chaotic Minds Gaming capabilities. It is a clean-room replacement plan, not a promise that every feature can be reproduced through a server plugin. Exact behavior must be verified against the local package, available server hooks, and licensing.

## Important inventory findings

- The local inventory contains 30 Workshop packages and approximately 1.94 GB of files.
- The files are primarily cooked Unreal assets; the inventory found no obvious editable source projects.
- 28 Workshop listings were reported removed and 2 were unverified at the time of the prior audit.
- Custom Shipyards and Ship Repair Crew were reported discontinued but still working on patch 560.3.
- Ship Repair Crew was specifically flagged as discontinued/incompatible in the prior audit.
- Revy's Core is a dependency for Atlas Stables/Creature Cloud, Smart Decay, Anti PvP Chicken and Better Chat.
- Never copy third-party code, cooked assets, models, textures, UI, or other protected content into Chaotic Gaming. Build original functionality and independently created assets only.

## Replacement mapping

| Existing package | Function area to investigate | Chaotic Gaming replacement capability | Priority | Notes |
| --- | --- | --- | --- | --- |
| ATLAS Shipwright | Ship construction / shipyard workflows | Shipyard Manager | P1 | Recreate behavior, not assets or proprietary implementation |
| Custom Shipyards | Custom shipyard functionality | Shipyard Manager | P1 | Reported discontinued; verify actual feature set from local package |
| Ship Repair Crew | Ship repair workflow | Ship Repair & Maintenance | P1 | Reported discontinued/incompatible; do not rely on it |
| CG Ships | Ship content / ship features | Ship Systems Framework | P1 | Separate server logic from any new ship assets |
| ATLAS Architect | Building / construction tools | Architect & Build Utilities | P1 | One of the four previously prioritized packages |
| Rustic Buildings | Building structures/content | Building Utilities + original content pack | P2 | Structure assets cannot be recreated by a server plugin alone |
| eco's RP Decor | Decorative building content | Decor & Placement Utilities | P2 | New decorative assets require an independent asset pipeline |
| CG Structures EA | Structures / building content | Structures Framework + original content pack | P2 | Avoid importing cooked assets |
| ATLAS Beastmaster | Creature handling / management | Creature & Taming Manager | P1 | Previously prioritized; verify feature list and server hooks |
| Tame Overhaul | Taming mechanics / progression | Taming Rules & Progression | P1 | Recreate mechanics only where server hooks permit |
| CG Creatures | New creature content | Creature Framework | P2 | Largest package; 5,436 file rows / ~910 MB; cooked assets, not a plugin-only replacement |
| CG Creatures Flyers | Flying creature content | Creature Framework (later) | P2 | Requires original models/animations if new creatures are desired |
| Death Recovery | Death / recovery workflow | Death Recovery & Corpse Locator | P1 | Good server-side candidate; confirm inventory and corpse APIs |
| More Crops | Farming / crop content | Farming & Harvest Rules | P2 | New crop assets or item definitions may need content modlets |
| Better Farms 2.0 | Farming systems / farm content | Farming Utilities | P2 | Prior audit reported no copying, modification or redistribution; clean-room only |
| Smart Decay | Structure decay / upkeep | Structure Upkeep & Decay | P1 | Revy's Core dependency reported; implement independently |
| ATLAS Overseer | Server administration / oversight | Server Admin & Automation | P1 | Previously prioritized; verify commands and permission behavior |
| Master Navigator | Navigation / map utility | Navigator & Waypoint Tools | P1 | Previously identified; verify exact feature set |
| Marvelous Spyglass | Player information / spyglass QoL | Player Inspection & Spyglass Companion | P2 | May require client UI/assets; keep server-only features separate |
| Better Chat | Chat QoL / moderation | Chat Bridge & Chat Controls | P1 | Revy's Core dependency reported |
| CG Stuff | General gameplay / utility content | General Gameplay Utilities | P2 | Break down package into discrete features before implementation |
| CG Respec | Character respec / progression | Respec & Progression Manager | P1 | Validate server-side attribute/skill APIs |
| CG Custom Item Stacks | Inventory stack-size rules | Stack Rules Manager | P1 | Validate item stack hooks and persistence |
| Revys Mods - Core | Shared framework dependency | Chaotic Plugin Runtime / Shared Services | P0 | Replace the architectural role with our own framework; do not copy code |
| Atlas Stables | Creature storage / stable management | Stable & Creature Storage | P1 | Revy's Core dependency reported |
| Mythical Compass | Navigation / compass utility | Navigator & Waypoint Tools | P2 | Could share core with Master Navigator |
| Anti PvP Chicken | PvP protection / anti-abuse | PvP Safety & Zone Rules | P1 | Prior audit reported CC BY-NC-ND; no copying, modification or derivative assets |
| eco's ATLAS Foliage | Foliage / world assets | Original World Flora Content | P2 | Content/asset work, not a server plugin replacement; do not reuse cooked assets |
| Crew Goodies | Crew recipes / consumables | Crew Provisions & Recipe Utilities | P2 | Validate recipe and item hooks; original item definitions only |
| Jose's Docks | Dock / harbor building content | Dock & Harbor Utilities + original content | P2 | Prior audit described it as open source but license was unverified; do not reuse until verified |

## Replacement capability families

The 30 packages consolidate into these owned systems:

1. **Chaotic Plugin Runtime** — replaces the shared-framework role currently provided by Revy's Core.
2. **Ship Systems** — shipyard workflows, ship repair/maintenance and ship-related server rules.
3. **Architect & Structures** — construction helpers, placement validation and structure administration.
4. **Decor & World Content** — original decor, foliage and dock assets; this is a separate content pipeline, not just code.
5. **Creature & Taming** — creature management, tame progression and stable/storage features.
6. **Death Recovery** — configurable death handling and recovery tools.
7. **Server Admin & Automation** — oversight, scheduled tasks, safe admin commands and audit.
8. **Navigation & Player Information** — navigator, waypoints, compass and spyglass-like information where APIs allow.
9. **Chat & PvP Safety** — chat controls, moderation, anti-abuse and PvP protection rules.
10. **Progression & Inventory** — respec, item-stack rules and character progression.
11. **Farming & Provisions** — crop/farm systems, crew recipes and provisions.
12. **Structure Upkeep** — decay, maintenance and configurable upkeep policies.

## Technical feasibility boundaries

- **Good server-plugin candidates:** administration, announcements, chat routing, permissions, death handling, respec, stack rules, decay, taming rules, player stats and stable logic, provided the API exposes the necessary hooks.
- **Potentially mixed code + data work:** recipes, crops, shipyard definitions, structure placement rules and item definitions.
- **Not a server-plugin-only replacement:** new creatures, new ship models, buildings, foliage, decor, icons, animations and other cooked Unreal content. These require original content assets and a validated content pipeline.
- **ATLAS API dependency:** the Atlas Server API 1.71 listing is dated May 2024. No loader build or plugin has yet been validated against the target server. Keep all implementation behind an adapter until the proof-of-concept passes.
- **No DevKit assumption:** the initial plan must not depend on the user installing or operating the ATLAS DevKit.

## Implementation sequence

1. Prove the ATLAS plugin loader with a minimal startup/shutdown/logging plugin on an isolated server.
2. Build the Chaotic Plugin Runtime and permissions/audit contracts.
3. Implement low-risk server-side utilities: announcements, server status, admin audit and chat.
4. Implement death recovery, navigation, respec, stack rules and structure upkeep after hook validation.
5. Implement ship, creature, taming, stable and farming systems after game-specific API validation.
6. Plan original visual/content asset production separately; do not block server-side plugins on it.

## Audit follow-up

Before coding each replacement, capture:
- observed behavior from the local mod package or screenshots/video
- required game hooks and data structures
- client/server installation requirements
- persistence/save compatibility
- dependencies and load order
- license status of the original package
- exact parity target and known limitations

A replacement is considered complete only when it has its own implementation, tests, documentation, compatibility record and clean uninstall path.
