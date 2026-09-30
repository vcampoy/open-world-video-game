# Tiny Fantasy Island — Game Brief

**Goal:** Make a small, complete third-person fantasy action game for personal practice. A 10–15 minute run is a playtest target, not a promised duration.

## The one complete run

Speak to the village quest giver to accept the task, defeat the **three designated melee enemies** in the clearing outside the village, then return and speak to the quest giver. The run is complete when a clear completion message appears. No other completion condition is needed.

## Controls

| Action | Keyboard / mouse |
|---|---|
| Move | W, A, S, D |
| Camera | Mouse movement |
| Simple sword attack | Left mouse button |
| Dodge | Space |
| Talk / interact with the nearby NPC | E |
| Pause | Escape |

Right mouse button and other keys are unassigned in this baseline. Keep these bindings as the reference when considering any later extension; do not add an extension that conflicts with them.

## People, enemy, and map

- **Three NPCs total:** the quest giver starts and completes the task; a local scout offers a short directional/combat hint; a villager adds one brief flavor line.
- **One enemy type:** the same simple melee foe appears as the three designated targets. No other enemy archetypes are required.
- **Village:** safe starting point, all three NPCs, and quest return point.
- **Island trail:** connects the village to the encounter area.
- **Outer clearing:** contains the three designated enemies, away from the safe village.

## Milestones and boundaries

1. Explore the village and talk to the quest giver.
2. Follow the trail, use sword attacks and dodges, and defeat the three targets.
3. Return to the quest giver and see the completion message.

Keep the island to this short route and these zones. Exclude interiors, extra quests, other weapons, magic, inventory, crafting, bosses, multiplayer, and saving. None is mandatory for a finished game.

## Failure and finish checklist

**One failure rule:** when the player dies, restart this short run at the village with the quest reset and all three enemies restored to their starting state; the player begins a fresh run.

- [ ] Exactly one completion condition: finish the accepted three-enemy task and receive the quest giver's completion message.
- [ ] Exactly one failure/restart rule: death resets the run, quest, and enemies as described above.
- [ ] Exactly three NPC roles, one enemy type, and no required optional feature.
- [ ] Controls, safe village, route, encounter area, return, and replay are understandable in playtesting.
