
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
## Winning a floor

Because a floor never stops running, its completion condition has to belong to the **individual player**, not to the room. Every obstacle is one of two shapes:

**Traversal floors** — the win is physical. Get from the entry to the exit alive, and the staircase *is* the exit. Nothing to track: standing on the stairs means you cleared it. Most obstacles are this.

**Endurance floors** — the rule has no finish line, so the win is a count. Survive a set number of cycles of the rule and the staircase opens for you. The count starts the moment **you** walked in, so someone who entered three cycles after you still has three cycles left when you leave.

Endurance floors need a **personal gate** at the staircase — a barrier that only lets through players who have met their own count. Without it a late arrival just tails someone who earned it and skips the floor. Players should be able to see their own progress toward the count while they are in the room, otherwise surviving feels aimless.

Traversal floors need no gate, but their exit must stay open permanently — it is never "the door closes after the first group".

## Obstacles
  - tower, a npc is on a high ground at the end of the obstacle and whne playes enter the obstacle at the start they have to hide behind diff objects while the npc shoots at them. traversal, win by reaching the stairs at the far end alive.
  - red light green light, basically the players start at the start and make their way to the end while a light that turns red and green, if player moves while light is red they die. traversal, win by crossing the finish line.
  - glass bridge, two rows of panels span a gap to the exit. one panel of each pair holds, the other shatters. players pick a side and step across, and a wrong panel drops them out. broken panels stay broken, so whoever goes first pays for information everyone behind them gets. the pattern reshuffles on a timer so a late arrival still gets a real bridge to solve. traversal, win by reaching the far platform.
  - color call, the floor is a grid of colored tiles. a color is called out, a few seconds later every tile that is not that color falls away and then the floor rebuilds. be standing on the called color when the buzzer hits or you go down with it. runs on a loop forever. endurance, survive a set number of calls from when you entered and the gate to the stairs opens for you.
  - quiz gates, a short series of gates leads to the stairs, each one a question on a screen with a gate per answer. pick the right gate before the timer runs out to move to the next question. wrong gate or no gate and you are out. traversal, win by clearing the whole series. questions are drawn fresh for each player so nobody can just copy the crowd.
  - minefield, the safe path across a tiled floor lights up for a few seconds and then goes dark. memorize it and walk it. stepping on a wrong tile kills. the path relights on a cycle and picks a new route each time it does. traversal, win by reaching the far side.
  - searchlights, the arena is dark and sweeping lights roam the floor on a fixed patrol. get caught in a beam and you are out. time the gaps to reach the far side. the patrol never stops, so it is the same problem whenever you arrive. traversal, win by reaching the far side.
  - dodge pads, a floor of pads that light up in warning and then fire whoever is standing on them. the lit set changes every beat and speeds up the longer you are in the room. one player or ten, the floor does not care. traversal, win by crossing the pad floor to the exit.
  - gas room, gas rises from the floor while the exit stays locked behind a lever. the lever is across the room and pulling it opens the exit for a few seconds before it shuts again. get there and back through the door before the gas takes you. the room vents and resets itself after each cycle. traversal, win by getting through the door while it is open.
  - sweeper, a rotating arm circles the arena alternating between low and high passes. duck or jump it. the arm never stops turning. endurance, survive a set number of rotations counted from when you entered and your gate to the stairs opens.
    
## Failure

**Fail a challenge and you are eliminated for the round.** No retries, no checkpoints. The field thins as the tower goes up.

## Round end

A round ends one of two ways:

1. **Everyone is eliminated** — nobody reaches the top.
2. **Survivors reach the summit and fight it out** — the players who clear every obstacle face each other, and that decides the winner.

## Technical direction

Built on **Fremy**. Each obstacle should be a swappable module behind a shared interface — start, stop, a player entered, a player cleared it, eliminate a player — so the round generator can stack them without special-casing any one challenge.

"A player entered" matters as much as the rest of it: endurance floors start that player's count from there, and the floor has to hold per-player state for everyone currently inside rather than one global state for the room.



