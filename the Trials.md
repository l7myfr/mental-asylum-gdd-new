
## Core loop

Every round a randomly generated trial starts, built from preset obstacles. When you reach the end of an obstacle you climb a stair placed at its end. Obstacles are stacked on top of each other, so the trial is a tower you ascend.

## Obstacle Rules

Obstacles are **challenges, not platforming**. Each one is a self-contained arena with its own rule you have to survive — Red Light Green Light and similar. Falling is not the fail state.

- Obstacles are pre-built prefabs, not procedurally shaped. The randomness is in **which ones appear and in what order**.
- Each round picks a **random number of obstacles within a range**. Range TBD.
- One shared tower per server. Everyone climbs the same structure at the same time.
- A staircase at the end of each obstacle leads up to the next one.
## Obstacles
  - tower, a npc is on a high ground at the end of the obstacle and whne playes enter the obstacle at the start they have to hide behind diff objects while the npc shoots at them.
  - red light green light, basically the players start at the start and make their way to the end while a light that turns red and green, if player moves while light is red they die.
  - glass bridge, two rows of panels span a gap to the exit. one panel of each pair holds, the other shatters. players pick a side and step across, and a wrong panel drops them out. whoever goes first pays for the information everyone behind them gets.
  - color call, the floor is a grid of colored tiles. a color is called out, a few seconds later every tile that is not that color falls away. be standing on the called color when the buzzer hits or you go down with the floor.
  - quiz gates, a question shows on a screen at the start and a row of gates at the far end, one per answer. everyone runs for the gate they think is right before the timer runs out. wrong gate or no gate and you are out.
  - minefield, the safe path across a tiled floor lights up for a few seconds at the start and then goes dark. players have to memorize it and walk it. stepping on a wrong tile kills.
  - searchlights, the arena is dark and sweeping lights roam the floor. get caught in a beam and you are out. players have to time the gaps to reach the far side.
  - musical pads, a ring of safe pads with fewer pads than players. a buzzer goes off at random intervals and anyone not standing on a pad is eliminated, then pads are removed and it runs again until the count is thin enough.
  - hot potato, one player starts marked with a bomb and passes it by touching another player. when the timer hits zero whoever is holding it is eliminated. runs several times in a row.
  - gas room, gas rises from the floor while the exit door stays locked behind several levers spread around the arena that have to be held at the same time. players either cooperate or drown in it.
  - sweeper, a rotating arm circles the arena alternating between low and high passes. players duck or jump it and have to survive a set number of rotations before the exit opens.
    
## Failure

**Fail a challenge and you are eliminated for the round.** No retries, no checkpoints. The field thins as the tower goes up.

## Round end

A round ends one of two ways:

1. **Everyone is eliminated** — nobody reaches the top.
2. **Survivors reach the summit and fight it out** — the players who clear every obstacle face each other, and that decides the winner.

## Technical direction

Built on **Fremy**. Each obstacle should be a swappable module behind a shared interface — start, stop, eliminate a player, report completion — so the round generator can stack them without special-casing any one challenge.



