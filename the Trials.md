
## Core loop

Every round a randomly generated trial starts, built from preset obstacles. When you reach the end of an obstacle you climb a stair placed at its end. Obstacles are stacked on top of each other, so the trial is a tower you ascend.

## Obstacle Rules

Obstacles are **challenges, not platforming**. Each one is a self-contained arena with its own rule you have to survive — Red Light Green Light and similar. Falling is not the fail state.

- Obstacles are pre-built prefabs, not procedurally shaped. The randomness is in **which ones appear and in what order**.
- Each round picks a **random number of obstacles within a range**. Range TBD.
- One shared tower per server. Everyone climbs the same structure at the same time.
- A staircase at the end of each obstacle leads up to the next one.

## Players are spread across the tower

Players climb at their own pace. The fast ones are several floors up while others are still working on a floor below, so **no obstacle can assume who else is in the room**.

- **Never soft lock a floor behind you.** An obstacle you have already cleared keeps running for whoever is still on it. Floors do not shut down, lock, or reset out from under a straggler, and arriving late is never an instant loss.
- **Every obstacle must be beatable alone.** No obstacle may require a second player to be present — no simultaneous levers, no passing something between players, no "fewer slots than players".
- **Rules run on a loop, not as a one-shot event.** A floor cycles its rule continuously so a player who walks in at any moment gets a fresh, full attempt at it.
- Other players in the room may make a floor *easier or harder to read* — that is fine and good. They may never be **required** for it to be solvable.
## Obstacles
  - tower, a npc is on a high ground at the end of the obstacle and whne playes enter the obstacle at the start they have to hide behind diff objects while the npc shoots at them.
  - red light green light, basically the players start at the start and make their way to the end while a light that turns red and green, if player moves while light is red they die.
  - glass bridge, two rows of panels span a gap to the exit. one panel of each pair holds, the other shatters. players pick a side and step across, and a wrong panel drops them out. broken panels stay broken, so whoever goes first pays for information everyone behind them gets. the pattern reshuffles on a timer so a late arrival still gets a real bridge to solve.
  - color call, the floor is a grid of colored tiles. a color is called out, a few seconds later every tile that is not that color falls away and then the floor rebuilds. be standing on the called color when the buzzer hits or you go down with it. runs on a loop forever.
  - quiz gates, a question shows on a screen at the start and a row of gates at the far end, one per answer. run for the gate you think is right before the timer runs out. wrong gate or no gate and you are out. a new question comes up every cycle, so whenever you walk in you get a whole one.
  - minefield, the safe path across a tiled floor lights up for a few seconds and then goes dark. memorize it and walk it. stepping on a wrong tile kills. the path relights on a cycle and picks a new route each time it does.
  - searchlights, the arena is dark and sweeping lights roam the floor on a fixed patrol. get caught in a beam and you are out. time the gaps to reach the far side. the patrol never stops, so it is the same problem whenever you arrive.
  - dodge pads, a floor of pads that light up in warning and then fire whoever is standing on them. the lit set changes every beat and speeds up the longer you are in the room. survive to the exit. one player or ten, the floor does not care.
  - gas room, gas rises from the floor while the exit stays locked behind a lever. the lever is across the room and pulling it opens the exit for a few seconds before it shuts again. get there and back through the door before the gas takes you. the room vents and resets itself after each cycle.
  - sweeper, a rotating arm circles the arena alternating between low and high passes. duck or jump it and survive a set number of rotations before the exit opens. the arm never stops turning.
    
## Failure

**Fail a challenge and you are eliminated for the round.** No retries, no checkpoints. The field thins as the tower goes up.

## Round end

A round ends one of two ways:

1. **Everyone is eliminated** — nobody reaches the top.
2. **Survivors reach the summit and fight it out** — the players who clear every obstacle face each other, and that decides the winner.

## Technical direction

Built on **Fremy**. Each obstacle should be a swappable module behind a shared interface — start, stop, eliminate a player, report completion — so the round generator can stack them without special-casing any one challenge.



