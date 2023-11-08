# Auto-towers
*Tower Defense Autochess Game Mechanics*

## Towers
Wants to keep all monsters out, always attacks the closest minion (random) when in range. Basic towers cant move.

## Monsters
Wants to crumble all towers. Basic towers will move.

### States
- **Range**: The maximum distance (in hexagons) a tower can reach to attack or apply effects.
- **Damage**: The amount of damage a tower deals to a target with each attack.
- **Health**: The total amount of damage a tower can sustain before it crumbles.
  - *Regen*: Certain towers may slowly recover health over time. (Default: 0 per tick)
- **Shield**: A protective layer that absorbs damage before health is affected.
  - *Regen*: Certrain towers may slowly recover sheild over time: (Default: 1 per tick)
- **Speed**: TODO (Default: 0 for towers, default 1 for mosnters)
- **Cooldown**: TODO (Default: 0)

## Effects and conditions
- **Aura**: Can add extra stats or effects to nearby towers/monsters. (Default: range 1)
- **Splash**: Damage also hit nearby entites. (Default: 0)
- **Disarmed**:  Preventing units attack
- **Stelath**: Preventing enemy units from attacking you untill you have attacked.
- **Stealth Detection**: Can remove stealth on enemy units when in range.
- **Stun**: Preventing enemy units movement or attack. (Default: durattion 1)
- **Disarm**:  Preventing enemy units attack. (Default: durattion 1)
- **Root**:  Preventing enemy units movement. (Default: durattion 1)
- **Slow**: Reducing speed of enemy unit on hit.
  - *Duration*: Amount of ticks unit is slowed for (Default: 4 ticks)
  - *Reduction*: Ratio of which the speed is reduced. Always stated on y/x. (Default: 1/4) Its resolved as:
    1. 1 tick rooted
    1. `y-x * base-speed` tick(s) with movement
    2. `x * base-speed - 1` tick(s) rooted
- **Chain Attack**: Attack jumps to additional enemies. (Default: 1 enemyu within 1 range)
- **On Shield Drained**: Activates when sheild is drained to 0.
- **On Death**: Activated when unit dies.
- **On Spawn**: Activates when unit spawns/respawns.
- **Targetting**: Specifies what enemy unit it targets.
  - *Priorities*: What will the tower try to target first if there are multiple. (Monster default: highest health first, Tower default: none).
  - *Except*: Targetting can specify what towers will exclude from its targetting. (Default: none).
  - *Only*: Targetting can specify what towers to include. (Default: all).
  
  




