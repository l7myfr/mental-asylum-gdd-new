
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
  - red light green light, basically the players start at the start and make their way to the end while a light that turns 
## Failure

**Fail a challenge and you are eliminated for the round.** No retries, no checkpoints. The field thins as the tower goes up.

## Round end

A round ends one of two ways:

1. **Everyone is eliminated** — nobody reaches the top.
2. **Survivors reach the summit and fight it out** — the players who clear every obstacle face each other, and that decides the winner.

## Technical direction

Built on **Fremy**. Each obstacle should be a swappable module behind a shared interface — start, stop, eliminate a player, report completion — so the round generator can stack them without special-casing any one challenge.



