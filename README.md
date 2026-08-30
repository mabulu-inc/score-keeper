# Score Keeper

A card game score keeper that runs in the browser, works offline, and is built to be
put down. The point is not to use it — it's to stop the table arguing about whether
that was 3 or 4 tricks, in one tap, and get back to the game.

First game in is **bid euchre**. The structure allows for others.

No build step, no dependencies, no server, no accounts. One HTML file, a service
worker, and three icons.

## Using it

1. **New game.** Type the four names, or tap them from the list of people you've
   played with before.
2. **Seat them.** Partners sit opposite each other on the diagram. Tap two seats to
   swap. Pick who deals first — after that the deal moves clockwise on its own.
3. **Play.** Each hand is three taps in a row: the bidding, the trump, and how many
   tricks the bidding team took. The score does itself.

Nothing needs saving. Close it mid-hand, drop the phone, come back tomorrow — the game
is exactly where you left it.

### A hand, in full

**Bidding** opens to the left of the dealer and goes round once. Each player passes or
bids higher. Only the legal bids are tappable, so nobody has to remember what the
current bid is — and if it reaches the dealer with nothing on the table, the pass
button is simply gone. *Screw the dealer* enforces itself.

**Trump** is called by whoever won the bid: hearts, diamonds, clubs, spades, high or
low. High and low grey out below a bid of 4.

**Tricks** — the only number you type. Tap how many the bidding team took, and every
button already shows what it will do to *both* scores before you press it:

```
   3         4         5         6
  -4        +4        +5        +6      ← the team that bid 4
  +3        +2        +1        +0      ← the other team
```

So the difference between making it and going set is on screen, in the two teams'
colours, without anyone doing arithmetic out loud.

**Undo** steps back through all of it — a mis-tapped trick count, a wrong trump, a bid
entered against the wrong player, even a finished game. There is no wrong tap you have
to live with.

### Staying out of the way

The screen answers the two questions a table actually asks — *whose bid is it?* and
*what's the score?* — and then stops. No animation, no sound, no confetti, no
notifications, nothing that moves while you're playing cards.

The table diagram carries the live state, so the answer is a glance rather than a read:
the current player is the highlighted seat, the dealer is tagged, and each seat shows
what that player did this round. Team colours are the same everywhere — on the seats,
on the scoreboard, on the trick buttons, in the log — so you never have to work out
which number belongs to whom.

Under the running score, every hand is listed the way you'd have written it down:
dealer, who bid what in which suit, tricks taken, and the running total for each team.
That's the scratchpad, kept for you.

## Scoring

Six tricks in a hand. First team to **40** wins.

| Bid | Made | Set |
|---|---|---|
| 3, 4 or 5 | every trick taken, overtricks included | minus the bid |
| Partner's best (12) | all six tricks: **+12** | **−12** |
| Alone (24) | all six tricks: **+24** | **−24** |

The non-bidding team banks **a point per trick** every hand, whether or not the bid was
made. Scores can go negative, and the app will show it.

Bids run 3 → 4 → 5 → partner's best → alone, and each must beat the last. High and low
(no trump) need a bid of at least 4. Partner's best and alone are all or nothing —
anything less than all six tricks loses the full value.

If a hand pushes both teams past 40 at once, the team that made its bid takes the game.

## Between games

Players are remembered as you use them; the ones you played with most recently sort to
the front. Finished games are kept with their full hand-by-hand record.

**Play again** on any previous game re-seats the same four players and moves the first
deal on one place — so a rematch is two taps. Seats can still be swapped before you
start, for when the partnerships change.

Everything lives in browser storage on that device. Nothing is uploaded, there is no
account, and the app makes no network requests once it has loaded.

## On your phone

Open the hosted URL in Safari or Chrome, then **Share → Add to Home Screen**. It gets
its own icon, opens without browser chrome, and works with no signal after the first
load — including at a kitchen table with bad reception.

If you change any file, bump `CACHE` in `sw.js`, or phones will keep serving the old
version from cache.

## Running it locally

Open `index.html` in a browser — the app itself needs no server.

Offline caching and Add to Home Screen need a real origin, so for those:

```sh
python3 -m http.server 8000
# then http://localhost:8000
```

## Adding another game

Bid euchre lives in one `RULES` block at the top of the script: the bid ladder, the
trump options, how many tricks are in a hand, the target score, and a `score()`
function that turns *tricks taken by the bidding team* into points for both sides.
Another game means another block shaped like that one. There is deliberately no
abstraction layer waiting for it — the second game can show what the two actually have
in common.

## Licence

MIT. See [LICENSE](LICENSE).
