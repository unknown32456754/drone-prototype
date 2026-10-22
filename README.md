# drone-prototype
A drone flying prototype game built in Unreal Engine.
# Drone Game

## Project overview

**Drone Game** is a third-person / remote-drone survival game set in an AI-controlled apocalypse. The player is trying to survive in a world where hostile machines have taken over. The player’s main tool—and their way to explore and fight—is an attack drone that can be piloted into dangerous areas.

The central idea is to make the drone both powerful and vulnerable. It can scout, fight, collect useful materials, and complete objectives, but it can also run low on battery, lose its signal, or be damaged by enemy machines. The player must decide how far to venture, which threats to confront, what to bring back, and how to improve the drone for the next outing.

The long-term direction includes a safe hideout, scrap scavenging, drone upgrades, several mission areas, and a final confrontation with the AI core. The exact story format is still undecided. A story can be told through optional audio logs and short messages rather than relying on cinematic cutscenes.

## Current project status

This folder contains an Unreal Engine project named **Drone_Game_Copy**, configured for **Unreal Engine 5.8**. The main map and gameplay assets are present in the project''s Content folder. The project has assets whose names indicate a drone, a bullet, a target, a HUD, and Enhanced Input actions.

The project structure and asset names give a useful snapshot of the prototype, but they do not confirm every blueprint''s behavior. Unreal assets such as `.uasset` and `.umap` are binary editor files; open the project in Unreal Editor to inspect or change their nodes, properties, and level layout.

### Main gameplay assets

- `Content/Main_Level.umap` — the main playable level.
- `Content/BP_Drone.uasset` — drone blueprint.
- `Content/BP_Bullet.uasset` — bullet blueprint.
- `Content/BP_Target.uasset` — target blueprint.
- `Content/WBP_HUD.uasset` — HUD widget.
- `Content/IMC_Drone.uasset` — drone input mapping context.
- `Content/IA_MoveForward.uasset` — forward movement input.
- `Content/IA_MoveRight.uasset` — sideways movement input.
- `Content/IA-MoveUp.uasset` — vertical movement input.
- `Content/IA_Turn.uasset` — turning input.
- `Content/IA_Camera.uasset` — camera input.
- `Content/IA_Shoot.uasset` — shooting input.
- `Content/IA_Reload.uasset` — reload input.
- `Content/IA_Restart.uasset` — restart input.

### Imported asset folders

The Content folder includes Fab assets organized under names such as:

- `Fab/Animated_Drone`
- `Fab/Dirt_Bullet_caliber_9x19`
- `Fab/Some_Robot`

These appear to provide drone, projectile, and robot art assets for the project.

## Intended player experience

A typical mission could work like this:

1. The player starts at a hideout or mission launch point.
2. They deploy the drone into a dangerous area.
3. They navigate the environment, watch the drone''s condition, and fight or avoid hostile machines.
4. They collect scrap and complete a mission objective.
5. They decide whether to push farther for more supplies or return while the drone is still safe.
6. They spend recovered scrap on upgrades.
7. New routes, enemies, or mission areas become available as the player progresses.

The tension should come from balancing reward against risk. A drone that has taken damage or is approaching its signal or battery limit may need to retreat even when more scrap or an objective is nearby.

## Core design pillars

### 1. The drone is the player''s lifeline

The drone is the player''s primary way to interact with the dangerous world. Its health, battery, signal range, ammunition, and upgrades should be easy to understand. When it is threatened, the player should feel the consequences directly.

### 2. Every expedition has a cost and a reward

Scrap is collected from destroyed machines and points of interest. It supports the pickup loop and provides a reason to explore. The player should make meaningful choices about when to collect, fight, continue, and return.

### 3. Enemies encourage different responses

Enemy types can be introduced gradually:

- **Turrets** establish the basic combat challenge by firing at the drone from a fixed position.
- **Patrol robots** add a moving threat and can make routes less predictable.
- **Flying hunters** can pursue or pressure the drone, forcing the player to react while navigating.

Each new enemy should add a small, clear twist to the encounter instead of only having more health.

### 4. The world is hostile, but the hideout offers safety

A hideout can act as a safe place to review progress, spend scrap, choose upgrades, and receive the next objective. It also gives missions a clear starting and ending point.

### 5. Story supports the survival loop

The story can be delivered in short, optional pieces: audio logs, found messages, environmental clues, or mission dialogue. The player can learn what the AI did and why the world changed while staying focused on piloting and survival.

## Ideas captured from the design notes

The following are design ideas, not a claim that they are already implemented:

- **Signal range and battery:** Limit how far the drone can operate, giving the map a natural boundary and creating pressure to return.
- **AI jamming zones:** Let the hostile AI disrupt controls or the HUD in certain areas, such as causing a wobble or static.
- **A hideout base:** Provide a safe location to spend recovered scrap and continue the story.
- **Scrap as currency:** Drop scrap from destroyed machines and allow the drone to collect it by flying into it.
- **Enemy variety:** Start with turrets, then introduce patrol robots and flying hunters.
- **Audio logs:** Tell story fragments through messages found around the world, keeping production manageable.
- **The AI core:** Use the AI''s core as the intended final target and endgame encounter.

## Suggested development roadmap

### Phase 1 — Survival prototype

Build and tune the smallest complete combat loop:

- Give the drone a health value.
- Create one turret that can detect and shoot at the drone.
- Apply damage when a shot hits the drone.
- Show the drone''s remaining health clearly.
- Trigger a readable death or mission-failed screen when health reaches zero.
- Add a restart or retry flow.
- Tune movement and combat until dodging and attacking feel understandable.

**Done when:** a player can start the level, fight one turret, take damage, lose, and retry without restarting the editor.

### Phase 2 — Pickups and one upgrade

- Make a simple scrap pickup.
- Allow the drone to collect it by flying into it.
- Track the player''s scrap amount.
- Add a basic upgrade station or menu.
- Implement one upgrade, such as more health, improved movement, extra ammunition, or longer battery life.
- Make the upgrade''s effect visible in play.

**Done when:** the player can collect scrap, return to safety, buy an upgrade, and notice the difference.

### Phase 3 — Save progression

- Decide which upgrades and resources persist.
- Save progression between missions and play sessions.
- Add sensible defaults for a new save.
- Handle loading a save and starting a fresh game.

**Done when:** progress remains after closing and reopening the game.

### Phase 4 — Missions and story

- Add objectives to the HUD.
- Create a short mission dialogue or briefing.
- Place a few audio logs or messages in the level.
- Track mission completion and rewards.
- Decide how much of the story is required versus optional.

**Done when:** a player can understand why they are in a mission and what success means.

### Phase 5 — Hub and mission areas

- Build a small hub or hideout.
- Create three or four compact mission areas with distinct layouts or hazards.
- Connect missions to the hub and progression.
- Expand to larger connected zones only after the small missions work well.

**Done when:** the player can leave the hub, complete a mission, return, and choose a next step.

### Phase 6 — Art, sound, and feedback

- Replace temporary shapes with the chosen drone, robot, and environment art.
- Add clear weapon and impact effects.
- Add feedback for damage, low health, low battery, and signal loss.
- Add suitable sound effects and music.
- Keep visual effects readable so the player can understand incoming threats.

**Done when:** important gameplay events are understandable through visuals and sound, not only debug information.

### Phase 7 — Endgame

- Build a final area around the AI core.
- Reuse and combine enemy behaviors to create a final challenge.
- Make the ending respond to the player''s mission progress.
- Add a clear completion sequence and a way to continue or replay.

**Done when:** the player can reach the AI core, overcome the final encounter, and see that the game is complete.

## Important design decisions to make later

These questions can stay open while the core prototype is being tested:

- Is the player physically present at the hideout while remotely piloting, or is the drone the player''s direct point of view?
- What happens when the drone is destroyed: is it rebuilt, recovered, or does the player lose some carried scrap?
- Does battery run out over time, or mainly when using powerful abilities?
- Does signal range depend on distance from the player, a relay, or a mission boundary?
- Can the player avoid most enemies, or is combat expected in every mission?
- Are upgrades permanent, mission-specific, or a mixture?
- How linear should the story be, and how much should the player discover optionally?

## Scope advice

Keep the first playable version small. One drone, one map, one turret, one scrap pickup, one upgrade, and a retry flow are enough to test the central idea. Avoid building many enemies, levels, story sequences, or save features before the basic drone movement and combat loop feel enjoyable.

The project is large on disk partly because Unreal stores imported assets, editor-generated data, and recovery files alongside the game content. The `Content` directory contains the authored game assets. Folders such as `Saved`, `Intermediate`, and `DerivedDataCache` commonly contain editor state, autosaves, logs, temporary build files, and caches; they are not the core gameplay design.

## Opening the project

1. Install or select a compatible Unreal Engine 5.8 installation.
2. Open `Drone_Game_Copy.uproject`.
3. Open `Content/Main_Level` in the Content Browser if it does not open automatically.
4. Use Unreal Editor to inspect the blueprints, input mappings, HUD, and level.
5. Test changes in Play In Editor before expanding the feature set.

## Project tree at a glance

```text
Drone_Game - Copy/
├── Config/                 Project and input configuration
├── Content/                Maps, blueprints, UI, inputs, and imported assets
│   ├── BP_Drone.uasset
│   ├── BP_Bullet.uasset
│   ├── BP_Target.uasset
│   ├── WBP_HUD.uasset
│   ├── Main_Level.umap
│   └── Fab/                 Imported art assets
├── DerivedDataCache/        Generated editor cache
├── Intermediate/            Temporary generated project files
├── Saved/                   Logs, autosaves, crash reports, and editor state
├── Drone_Game_Copy.uproject  Unreal project descriptor
└── README.md                This project overview and roadmap
```

## Short pitch

> Survive an AI-controlled apocalypse by piloting a fragile attack drone into hostile territory. Fight machines, gather scrap, and upgrade your drone so you can venture farther toward the AI core.
 
