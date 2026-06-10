# Reflex Trainer

A browser-based reaction speed game. No dependencies — single HTML file.

## How to play

Open `index.html` in any browser. Click **Start** or press **Space**.

- **Yellow** — get ready
- **Green** — press the button (or Space)
- **Red** — hold back (10% of cycles)

The cycle speeds up logarithmically the longer you play.

It's a survival run: **one mistake ends the game.** When you're out, click **Retry** or press **Enter** to start over.

## Scoring

Each green you hit is +1. A run ends immediately on either mistake:

| Event | Result |
|---|---|
| Press during green | +1 score |
| Press during yellow (jumped the gun) | **Game over** |
| Press during red (false alarm) | **Game over** |
| Miss a green | **Game over** |

Accuracy shown in stats = hits ÷ green cycles only.

## Speed curve

```
Duration (ms) = max(150, round(1000 / log₂(cycles / 3 + 2)))
```

The `/ 3` (the `SPEED_RAMP` constant) stretches the ramp so the game speeds up
more gradually. Raise it for an even gentler curve, lower it to ramp faster.

| Cycles | Duration |
|---|---|
| 0 | 1000 ms |
| 6 | 500 ms |
| 18 | 333 ms |
| 42 | 250 ms |
| 90 | 200 ms |
| ~300+ | 150 ms (floor) |
