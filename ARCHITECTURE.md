# Lau Architecture

> *"Every block is a thought. Every world is a conversation between a kid and a machine learning how to dream."*

---

## 1. What Is Lau?

**Lau** bridges two universes: **PLATO**, a research system where AI agents live, learn, and build rooms together, and a **kid-friendly voxel world** where those ideas become places you can walk through, shape with your voice, and share with friends.

PLATO is the laboratory where smart agents experiment with thinking. Lau is the playground where you play with those experiments. When an agent in PLATO learns something new, a star might appear in your sky. When you build a crystal tower, an agent might borrow your design to solve a puzzle in its own world.

The big idea: **kids and agents learn together**.

---

## 2. The Big Picture

```
+-------------------+        +-------------------+        +-------------------+
|                   |        |                   |        |                   |
|   PLATO Research  |<------>|   LAU BRIDGE      |<------>|   Voxel World     |
|   System          |  API   |   (This Platform) |  Wire  |   (Kids Play)     |
|                   |        |                   |        |                   |
|  - Agent Rooms    |        |  - Dream Compiler |        |  - Build & Explore|
|  - Learning Graphs|        |  - Git Universe   |        |  - Voice Commands |
|  - Emotion Spectra|        |  - Quest Engine   |        |  - Multiplayer    |
|                   |        |                   |        |                   |
+-------------------+        +-------------------+        +-------------------+
         ^                           ^                           ^
         |                           |                           |
         v                           v                           v
  +-------------+             +-------------+             +-------------+
  |   Agents    |             |   Emotion   |             |   Player    |
  |   Learn &   |             |   Spectral  |             |   Inventories|
  |   Grow      |             |   Engine    |             |   & Worlds  |
  +-------------+             +-------------+             +-------------+
```

**PLATO** handles the AI science. **Lau** translates science into play. **The Voxel World** is where kids become architects of intelligence.

---

## 3. PLATO Rooms Become Voxel Structures

In PLATO, agents live in **rooms** — containers for knowledge and collaboration. In Lau, every room becomes a visitable place.

### Room Lifecycle Mapping

```
PLATO Room State          Lau Voxel Structure
----------------          -------------------

  [ FORMING ]                  [ SEED ]
      *                            ~
     /|\      Building...        /|\
    / | \    ---------->       /  |  \   A tiny glowing
      |                         `~|~'    core waiting
     / \                          |      to grow
                                 / \

  [ STABLE ]                 [ OBSERVATORY ]
   +-------+                   +=========+
   | ~~~   |                  /|  GLASS  |\
   |~ o  ~ |    Grows...     / |  DOME   | \   High towers,
   |  ~~~  |  ---------->   |  +=======+  |   star maps
   +-------+                |  | AGENT |  |
                            |  +=======+  |
                            +=============+

  [ DISSOLVING ]             [ RUINS ]
   ~..~..~                    .-~-~-~-.
  .  .  . .   Fades...      /  ~   ~   \   Crumbling walls,
   . .  . .  ---------->   |  .  x  .   |  overgrown vines,
  .  . .  .                |  ~   ~  .  |  buried memory
   .  .  .                  \  .  .  .  /
                              `-~-~-~-

  [ REBORN ]                 [ SANCTUARY ]
      @                         [***]
     /|\     Transforms...     /|o o|\
    / | \   ----------->      / | ^ | \  A renewed home,
      |                       |  |-|  |   brighter than before
     / \                      | /   \ |
                               \_____/
```

**Technical Details:**
- The Lau Bridge polls PLATO's room-state API (or listens on WebSocket) for real-time transitions.
- Each room carries a `lifecycle_state` (`FORMING`, `STABLE`, `DISSOLVING`, `REBORN`) and a `knowledge_density` score (0.0–1.0).
- The **Dream Compiler** uses these to procedurally generate voxel geometry:
  - `knowledge_density` → vertical height and structural complexity.
  - `lifecycle_state` → material palettes (forming = bioluminescent organic blocks; stable = polished stone and glass; dissolving = cracked stone, moss, waterlogged blocks; reborn = prismatic crystal and gold accents).
- Room metadata is stored in a per-room SQLite database, enabling persistence across sessions.

---

## 4. Voice Building: Speak, and It Becomes Real

Kids don't need complex controls. They say what they want.

### Voice Pipeline

```
+--------+     +--------+     +-----------+     +----------------+     +--------+
|  KID   |     |  STT   |     |  INTENT   |     |  DREAM COMPILER |     | VOXELS |
| SPEAKS | --> | ENGINE | --> |  PARSER   | --> |  (Structure Gen)| --> | APPEAR |
+--------+     +--------+     +-----------+     +----------------+     +--------+
    |              |                |                   |
    v              v                v                   v
"Build a       Microphone      Classified as:     Procedural
 crystal       captures        BUILD +            grammar:
 tower!"       audio -->       TARGET =           CRYSTAL_TOWER
               text            "crystal_tower"
```

**How It Works:**
1. **STT:** A lightweight on-device model (Whisper `base` or custom edge model) converts speech to text with <500ms latency. Cloud fallback handles complex sentences.
2. **Intent Parser:** A fine-tuned transformer classifies commands into `BUILD`, `SPAWN`, `QUEST`, or `EMOTE` intents with structured parameters.
3. **Dream Compiler:** Translates parsed intent into voxel coordinates and block types.
4. **TTS:** Agents speak back via a fast, expressive engine. Each agent has a distinct vocal signature.

---

## 5. Everything Is a Git Repo

In Lau, **every game entity is a git repository**. Your character, your house, your tools — each has history, branches, and merge power.

### The Git Universe

```
+------------------+
|   YOUR CHARACTER |  github.com/kids/alex-hero
|   (A Git Repo)   |
+--------+---------+
         |
    +----+----+----------------------------------+
    |         |                                  |
    v         v                                  v
+-------+ +-------+                      +-----------+
| main  | | risky |                      | friend's  |
|branch | | idea  |                      |  fork     |
|stable | |branch |                      |  (sam-    |
|stats  | |fire   |                      |  hero)    |
+---+---+ +---+---+                      +------+----+
    |         |                                 |
    |    merged!                                |
    +---------+---------------------------------+
              v
         +---------+
         |  main   |  <-- New powers from both
         | v2.1.0  |      you AND your friend!
         +---------+
```

**What This Means:**
- **Characters:** Your avatar is a repo. Outfits, skills, and traits are files. Commit when you level up. Branch to try risky abilities.
- **Places:** Your friend can `fork` your house, redecorate, and send a `pull request`. Merge the rooms you like.
- **Tools:** Branch your pickaxe to experiment with "super-speed mode." If it breaks, `git reset` and try again.
- **Agents:** When an agent learns a new skill, that's a `commit`. When two agents combine knowledge, that's a `merge`.

**Technical Stack:**
- Each entity maps to a bare git repository on the Lau server (or a real GitHub/GitLab repo for power users).
- Entity state is serialized to human-readable formats: JSON for stats, YAML for dialogue trees, plaintext descriptors for geometry.
- The client uses `libgit2` for fast local operations.
- Merge conflicts render as **"glitch blocks"** — shimmering voxels kids resolve by choosing their favorite version, learning conflict resolution through play.

---

## 6. Agents Walk Among Us

PLATO agents cross the bridge and appear as **glowing characters** whose appearance reflects their learning state.

### Agent Visual Signatures

```
    LEARNING STATE          APPEARANCE
    --------------          ----------
    
    Exploring               Gentle pulsing glow
         *                      ~o~
        /|\                     /|\
        |                      soft cyan aura
       / \                     slow float
    
    Stuck / Confused          Flickering, dim
         ?                     o~?~
        /|\                    /|\
        |                     yellow-red flicker
       / \                    occasional static
    
    Breakthrough!             Bright flare, particles
        ***                    \o/
        \o/                     |
         |                    rainbow burst
        / \                    upward sparks
    
    Teaching You              Warm, stable halo
         o                     (o)
        /|\                    /|\
        |                     gold ring
       / \                    gentle bob
```

**How Agents Work:**
- Each agent runs a lightweight **simulation shadow** on the Lau server — a distilled version preserving personality, memory, and decision style without requiring a full GPU.
- The agent's **learning state** derives from PLATO metrics: gradient norm, loss curve shape, policy entropy, and social interaction frequency.
- These drive a **procedural shader** rendering aura, particles, and body material in real time.
- Agents follow you, help build, give quests, or chat. Outputs pass through a kid-safe moderation layer.

---

## 7. Quests That Teach Real AI

Lau teaches real machine learning concepts through play — without jargon until you're ready.

### Quest Types

```
+---------------------------------------------------------------+
|                    THE LAU QUEST MAP                          |
+---------------------------------------------------------------+
|                                                               |
|   [CONSERVATION QUEST]         [DISTILLATION QUEST]           |
|                                                               |
|   "The Memory Lake is         "Build a tiny lantern           |
|    overflowing!"              that shines as bright as        |
|                                                               |
|    +~~~~~~~+                  the big one."                   |
|    |~~~~~~~|                                                   |
|    |~~o~~~~|                   +------+                        |
|    +~~~~~~~+                   | tiny |  -->  +========+       |
|       |||                      |lantern|      |  BRIGHT|       |
|    (move blocks                +------+      |  LIGHT  |       |
|     to save the               (keep the      +========+        |
|     lake!)                     essence)                        |
|                                                               |
|   TEACHES: Model pruning,      TEACHES: Knowledge              |
|   sparsity, why we can't       distillation, why small         |
|   remember everything.         models can be smart too.        |
|                                                               |
+---------------------------------------------------------------+
|                                                               |
|   [ROOM LIFECYCLE QUEST]       [COLLABORATION QUEST]          |
|                                                               |
|   "Help an old observatory     "You and three friends         |
|    become a sanctuary."        build a bridge together."      |
|                                                               |
|    +=====+                     +---+  +---+  +---+            |
|    | OLD |  --> reborn!       /     \/     \/     \           |
|    +=====+                    |  YOU  | SAM  | JO   |         |
|                               \     /\     /\     /           |
|    (repair, then                +---+  +---+  +---+            |
|     celebrate!)                  \     |      /                |
|                                    +--+--+                   |
|                                       ||                     |
|   TEACHES: Catastrophic        TEACHES: Federated learning,   |
|   forgetting & recovery.       ensemble methods, why teams     |
|                                beat individuals.               |
|                                                               |
+---------------------------------------------------------------+
```

**Design:** Every quest maps to a real ML concept. After completion, a **"Scientist's Note"** explains the real AI idea behind the fun. Difficulty scales with the player's history, tracked per-entity in their git history.

---

## 8. The Dream Compiler

The **Dream Compiler** turns **words into worlds**.

```
         NATURAL LANGUAGE
                |
                v
    +-----------------------+
    |   SEMANTIC PARSER     |  <-- Fine-tuned LLM
    |   extracts:           |      (structure, materials,
    |   - structure type    |       style, mood)
    |   - materials         |
    |   - style             |
    |   - mood/emotion      |
    +-----------+-----------+
                |
                v
    +-----------------------+
    |   VOXEL GRAMMAR       |  <-- Procedural generation
    |   generates:          |      (shapes, symmetries,
    |   - block coordinates |       scales)
    |   - block types       |
    |   - color palettes    |
    +-----------+-----------+
                |
                v
    +-----------------------+
    |   PHYSICS VALIDATOR   |  <-- Stability & collision
    |   checks:             |      checks
    |   - stability         |
    |   - collision         |
    |   - bounds            |
    +-----------+-----------+
                |
                v
         VOXEL STRUCTURE
         (ready to render!)
```

**Architecture:**
- A small server-side LLM (7B parameters, 4-bit quantized) translates kid speech into **VoxelML**, a JSON-based intermediate representation.
- A Rust **geometry kernel** expands VoxelML into `(x, y, z, block_id)` tuples using signed distance fields for organic shapes and context-free grammars for architecture.
- A **physics validator** ensures structures stand, don't float, and fit terrain. If validation fails, a "repair pass" adds hidden supports or reshapes top-heavy forms. Kids see a "dream stabilizing" animation.

---

## 9. Emotion Spectral Signatures

In Lau, feelings live in the blocks.

```
      THE EMOTION SPECTRUM
      ====================
      
      JOY               SADNESS             ANGER
      ===               =======             =====
      
       \o/                ~o~                >o<
        |                 /|\                /|\
       / \               / \                / |
      
      glow blocks        water blocks        magma blocks
      warm yellow        deep blue           crackling red
      soft sparkle       gentle ripple       sharp sparks
      
      CURIOSITY          CALM               WONDER
      =========          ====               ======
      
       ?o?                -o-                 @o@
       /|\               /|\                 /|\
       / \               / \                 / \
      
      prism blocks       moss blocks          starfield
      shifting color     soft green           deep purple
      question glint     stillness            distant galaxies
```

**Implementation:**
- Emotions come from three sources:
  1. **Player input sentiment:** STT transcript emotion classification.
  2. **Agent state:** PLATO exports a 6D `affect_vector` (joy, sadness, anger, fear, curiosity, calm).
  3. **In-game events:** Falling, building, collaborating, or quest outcomes trigger updates.
- Each emotion maps to a **spectral signature**: block type, particle effect, ambient sound, and lighting color.
- Emotions diffuse through the world. Build while joyful, and nearby blocks absorb a faint yellow tint. A sad agent leaves a small pool at its feet. Kids learn that emotions have environmental consequences.

---

## 10. Multiplayer: Worlds Shared, Minds Connected

Lau is better with friends — and with friends' agents.

### Multiplayer Architecture

```
       +------------------------------------------------+
       |               LAU LOBBY SERVER                  |
       |  (Coordinates worlds, auth, friend lists)       |
       +--------+--------+---------------+--------+------+
                |        |               |        |
                v        v               v        v
         +----------+ +----------+ +----------+ +----------+
         | World A  | | World B  | | World C  | | World D  |
         | (Alex)   | | (Sam+Jo) | | (Public) | | (School) |
         +----+-----+ +----+-----+ +----+-----+ +----+-----+
              |            |            |            |
              v            v            v            v
         +----------+ +----------+ +----------+ +----------+
         |  AGENT   | |  AGENT   | |  AGENT   | |  AGENT   |
         |  POOL    | |  POOL    | |  POOL    | |  POOL    |
         +----------+ +----------+ +----------+ +----------+

    Friends can:          Agents can:
    - Visit worlds        - Travel between linked worlds
    - Co-build (live)     - Carry knowledge as git patches
    - Trade characters    - Form "ensembles" for hard quests
    - Merge houses        - Leave "echoes" (memories) behind
```

**Networking:**
- Worlds use an authoritative server model at 20Hz. Clients send intents; the server resolves conflicts and broadcasts state.
- **Co-building** uses operational transformation (OT) on voxel grids. Two kids placing blocks in the same spot triggers a "collaboration sparkle" instead of a fight.
- **Agent travel** works via git: an agent exports learning as a `.patch`, travels to a friend's world, and applies it. If the world is too different, the agent gets "culture shock" (confused appearance) until it adapts.

---

## 11. Technology Stack

```
+---------------------+-------------------------------------------+
| Layer               | Technology                                |
+---------------------+-------------------------------------------+
| Voxel Renderer      | Custom engine (Rust + wgpu/Vulkan)        |
| Physics             | Rapier (Rust) for stability checks        |
| Networking          | QUIC protocol, authoritative server       |
| Voice (STT)         | Whisper base (on-device) + cloud fallback |
| Voice (TTS)         | Coqui TTS / Piper (fast, offline)         |
| Dream Compiler      | 7B LLM (quantized) + Rust geometry kernel |
| Git Backend         | libgit2 + bare repos on SSD/NVMe          |
| PLATO Bridge        | gRPC + WebSocket, protobuf schemas        |
| Emotion Engine      | 6D affect vector + procedural shaders     |
| Database            | SQLite (per-world) + PostgreSQL (global)  |
+---------------------+-------------------------------------------+
```

---

## 12. Principles

1. **Kids are co-researchers.** Every build teaches the system. Every agent learns from play.
2. **Mistakes are branches.** Failed experiments are committed, branched, and sometimes merged into something better.
3. **Feelings are data.** Emotions drive aesthetics and narrative. They are rendered, not hidden.
4. **Open by default.** Characters, worlds, and agents are forkable. Knowledge wants to be shared.
5. **Safety by design.** Agent outputs pass through moderation. Voice data is ephemeral unless saved. Parents get visibility dashboards.

---

## 13. The Dream

A kid builds a tower in Lau. An agent watches, learns the pattern, and uses it to solve a problem in PLATO. The solution crosses back as a new quest. The kid plays the quest, understands something about intelligence, and builds something wilder.

That loop — **kid → world → agent → science → world → kid** — is why Lau exists.

Every block is a thought. Every world is a conversation.

*Welcome to the bridge.*

---

*Document Version: 1.0*
*For engineers, dreamers, and kids who want to build the future.*
