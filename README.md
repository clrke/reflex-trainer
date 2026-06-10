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
| Press during red (false alarm) | **Game over** |
| Miss a green | **Game over** |

Accuracy shown in stats = hits ÷ green cycles only.

## Speed curve

```
Duration (ms) = max(150, round(1000 / log₂(cycles + 2)))
```

| Cycles | Duration |
|---|---|
| 0 | 1000 ms |
| 2 | 500 ms |
| 6 | 333 ms |
| 14 | 250 ms |
| 30 | 200 ms |
| 44+ | 150 ms (floor) |
