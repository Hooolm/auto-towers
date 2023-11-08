# Auto-towers
*Tower Defense Autochess Game Mechanics*

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
