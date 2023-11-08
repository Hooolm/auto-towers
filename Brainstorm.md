# Auto-towers
*Tower Defense Autochess Game Mechanics*

## Overall
A autochess game which rotates between combat phases and shop phases. Starting with a shop phase. In the shop phase you buy towers to defend against incomming monsters. A buy phase and combat phase we is called a round.

## Combat Units
**Towers**: Defensive units that aim to keep all monsters at bay, attacking the nearest enemy minion within range. Basic towers are stationary.
**Monsters**: Offensive units with the goal of crumbling towers. Basic monsters will move each tick.

### Stats
- **Range**: The maximum distance (in hexagons) a unit can engage enemies with attacks. (Default: 1)
- **Damage**: The amount of damage a unit inflicts upon an enemy with each attack. (Default: 1)
- **Health**: The total amount of damage a unit can endure before being destroyed.
  - *Regen*: Some units may slowly recover health over time. (Default: 0 per tick)
- **Shield**: A protective layer on a unit that takes damage prior to health.
  - *Regen*: Some units may slowly regenerate their shield over time. (Default: 1 per tick)
- **Speed**: The number of hexagons a unit can move per tick.  (Default: 0 for towers, 1 for monsters)
- **Cooldown**: The number of ticks a unit must wait between attacks. (Default: 0)
- **Armor**: Each attack is reduced by this number. (Default: 0)

### Effects and Conditions
- **Aura**: Bestows additional stats or effects to adjacent allied or enemy units. (Default: range 1)
- **Splash**: A unit's attack affects not only the primary target but also nearby enemies. (Default: 0)
- **Disarmed**: Prevents units from attacking.
- **Stealth**: Keeps a unit hidden from enemy attacks until it initiates an attack.
- **Stealth Detection**: Enables a unit to remove stealth from enemy units within range.
- **Stun**: Stops enemy units from moving or attacking. (Default: duration 1 tick)
- **Disarm**: Inhibits enemy units from attacking. (Default: duration 1 tick)
- **Root**: Restricts enemy units from moving. (Default: duration 1 tick)
- **Slow**: Decreases the speed of an enemy unit upon impact.
  - *Duration*: The number of ticks the enemy unit's speed is reduced. (Default: 4 ticks)
  - *Reduction*: The proportion by which the speed is decreased, expressed as a ratio (y/x). The slow is resolved as follows:
    1. 1 tick rooted
    2. `y-x * base speed` ticks with reduced movement
    3. `x * base speed - 1` ticks rooted
- **Chain Attack**: Allows a unit's attack to jump to additional enemies within range. (Default: 1 enemy within range 1)
- **On Shield Drained**: Triggers when a unit's shield is depleted.
- **On Death**: Activates when a unit is destroyed.
- **On Spawn**: Occurs when a unit is deployed or resurrected.
- **Targeting**: Determines the enemy unit a tower will prioritize.
  - *Priorities*: Dictates the first target for a unit when multiple enemies are in range. (Monster default: highest health first, Tower default: none)
  - *Except*: Specifies any targets that the unit will not target. (Default: none)
  - *Only*: Dictates exclusive targeting parameters for a unit. (Default: all)
- **Respawn**: After a dispawn commonly death a unit can respawn. (Default: no)
  - *Delay*: Amount of ticks before respawning. (Default: 1)
  - *Times*: Amount of times the unit can respawn. (Default: 1)
  - *Placement*: A respawn might specify another location than dispawn. (Default: dispawn location)
- **Banish**: WHen banished the unit disappears from the board and respawns. See respawn for details. 

### Further ideas:
Mana, energy?
Types: conditions on types, efficiency against other unit types

## Shop/currency questions:
- How do you do get currency for your shop, only one currency?
- What type of items can you buy?
  - Towers
  - Spells for augmenting towers
  - Spells for augmenting monsters in the map
    Spells for affecting other players
- Can you save items bought between rounds, in your ivnentory?
- How do you build your board?
  - Can you move your towers around without cost?
- Can you freeze items in the shop?

## Game modes ideas

### PvP
One combat, everything resets after each battle.
You can affect each others monsters and towers aswell as your own towers.
- 1v1
- XvX (Like hearthstone battlegrounds, compete untill you are last man standing)

### PvE
Minimum crangle: Outside of a battle you have access to another shop where you can modify overall properties "talents" and affect the maps your are playing.
Even more crangle: You have character with classes and talents.

Endlessmode: Monsters will keep spawning in respect to your map modifications, for ever.
Dungeons: Monsters will keep spawning in respect to your map modifications, for x amount of rounds.

## Implementation:

#### Player Client
The client features multiple views:
- **Combat View**: Where the battles unfold, really just a combat-video-player.
- **Shop View**: Where players purchase towers and spells.
- **Menu View**: For navigating the game and accessing different modes.

#### Server
- Manages game sessions through a RESTful API.
- Coordinates the shop phase and synchronizes transactions between players.
- Pre-determines combat outcomes, providing the client with a sequence of events to render, allowing for accelerated playback or total skipping of battles.


