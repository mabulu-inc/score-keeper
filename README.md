# Score Keeper

A card game score keeper that runs in the browser, works offline, and is built to be
put down. The point is not to use it — it's to stop the table arguing about whether
that was 3 or 4 tricks, in one tap, and get back to the game.

Three games so far: **bid euchre**, **Flip 7** and **Farkle**. Tap one on the home
screen. Everything that is not the game in front of you — the player list, the rules, and
every game you've ever finished — is behind **☰ Menu**, in the same place on every screen.

Picking a game shows you what you picked before it asks who is playing: the objective, the
rules, the scoring, and a few things worth knowing that no screen can tell you while you
play. It is a page you pass through rather than a gate — **Pick the players** is pinned to
the bottom of the screen from the moment it appears, so skipping it is one tap from a
standing start and never a scroll. A rematch doesn't pass this way at all.

No build step, no dependencies, no server, no accounts. One HTML file, a service
worker, and three icons.

# Bid euchre

Four players, two teams, first to 40.

## Using it

1. **New game.** Type the four names, or tap them from the list of people you've
   played with before.
2. **Seat them.** Partners sit opposite each other on the diagram. **Drag a player by the ⠿ handle to
   the chair you want them in.** Nobody is traded: the players in between shuffle along by one
   and a chair opens up under your finger, so the seating you'd get is the seating you're
   looking at while you decide.

   The chairs are a ring, so the shuffle takes the shorter way round. Moving somebody to
   the chair beside them moves one person; straight across the table moves two. It can
   never move three. Aim rather than land — the chair you're nearest is the chair you
   mean, so a drag toward one counts well before you get there. Carry them off the table,
   or back to where they started, and nobody moves at all.

   Pick who deals first; after that the deal moves clockwise on its own.
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

### The table diagram

The table diagram carries the live state, so the answer is a glance rather than a read:
the current player is the highlighted seat, the dealer is tagged, and each seat shows
what that player did this round. Team colours are the same everywhere — on the seats,
on the scoreboard, on the trick buttons, in the log — so you never have to work out
which number belongs to whom.

## Scoring

Six tricks in a hand. First team to **40** wins.

| Bid | Made | Set |
|---|---|---|
| 3, 4 or 5 | every trick taken, overtricks included | your score docked by the bid: **−3**, **−4** or **−5** |
| Partner's best (12) | all six tricks: **+12** | **−12** |
| Alone (24) | all six tricks: **+24** | **−24** |

The non-bidding team banks **a point per trick** every hand, whether or not the bid was
made. Scores can go negative, and the app will show it.

Bids run 3 → 4 → 5 → partner's best → alone, and each must beat the last. High and low
(no trump) need a bid of at least 4. Partner's best and alone are all or nothing —
anything less than all six tricks loses the full value.

# Flip 7

Everyone for themselves, as many players as are round the table, first to 200.

## Using it

1. **New game → Flip 7.** Tap in everyone playing — there is no upper limit. They appear
   as a **Seating** list in the order you tapped them; drag anyone by the **⠿** handle to
   match how you're actually sitting. Only the handle drags — the rest of the row scrolls,
   so a long list can be swiped through without moving anybody. The deal starts at the top and works down, then round again.
2. **Play the hand** on the table, not in the app. Nothing to press while cards are
   being flipped.
3. **Tally it.** When the hand is over, tap a player's name and then tap the cards
   sitting in front of them. Their score appears as you go. Move on to the next player,
   and when everyone is done, **Score the hand**.

### Whose deal, and who starts

Above the tally: *Hand 3 · Ray deals · first card to Bea*. That second half is the thing
a distracted table actually loses, and it is the only thing the app knows about a hand in
progress — nobody has to tell it about each card as it lands.

**Seating**, in the same card as **Scores** at the top, opens the order. Drag anyone up or down to put it right when two
people swap chairs. **✕** takes a player out of a game in progress and **+ name** puts one
in: people turn up late and people give up. A hand records what each player scored against
that player rather than against their place in the list, so a hand played before somebody
joined, or after they left, still says exactly who scored what. A leaver keeps everything
they scored and stays on the final board; a joiner starts from the next hand. Come back
later and you pick up the score you left with.

### Not watching the score

The running totals are behind **Scores** at the top, closed by default. Knowing exactly
where everyone stands changes how the cards get played, and the question during a hand is
whose turn it is, not who is winning. A finished game shows them without being asked —
then it is the whole point.

### The tally

Tapping a card is the whole interaction. Every card is a toggle, so a mis-tap is fixed
by tapping it again, and the total updates as you go instead of at the end:

```
  0   1   2   3   4   5   6
  7   8   9  10  11  12
 +2  +4  +6  +8 +10  ×2

              69
 7 cards · 27 × 2 + 15 for the flip 7 = 69
```

The line under the total shows the sum being done, not just its answer — because **×2
doubles the number cards only**, and the + cards land after it. That is the rule tables
get wrong most often, and here it is in front of you rather than in an argument.

**Seven different numbers** is a flip 7: the +15 goes on automatically, and the number
cards you didn't take go dead, because there is no eighth card to tap.

**Busted** is one tap and scores the hand at nothing, however far it got. It clears the
cards with it rather than leaving them on screen to be read as a score.

Freeze, Flip Three and Second Chance are not on the grid. They are worth nothing, so
there is nothing to tally.

The button at the bottom won't score the hand until every player has been dealt with,
and it says how many are still to do rather than making you hunt for who was missed.

## Scoring

First to **200** wins.

| | |
|---|---|
| Number cards | add up the ones in front of you |
| **×2** | doubles that number total — and nothing else |
| **+2 +4 +6 +8 +10** | added on afterwards |
| Seven different numbers | **+15** |
| Bust | **0**, whatever was on the table |

The 0 card counts as one of your seven.

# Farkle

Six dice, one player at a time, first past 10,000. A turn lasts exactly as long as the
nerve holds, and the app's whole job is to hold the running total while it does.

## Using it

1. **New game → Farkle.** Tap in everyone playing and drag the **⠿** handles until the
   list matches how you are sitting. Play starts at the top and works down.
2. **Roll the dice on the table.** The app has no dice in it and never asks for a roll —
   only for what came out of one.
3. **Tap the dice taken out for scoring**, one at a time, as they are set aside. The
   total is on screen as you go.
4. **Roll again**, or **Bank** it. If the roll had nothing in it, **Farkled** — and the
   button says what that costs before you press it.

### Tapping what was set aside

The six faces along the top are drawn rather than typed, because the Unicode dice come out
of a phone's font too small to read at arm's length. Tap a face and that die joins the row
below it; tap one in that row and it goes back. Nothing about a roll is committed until
the turn rolls on, banks or farkles.

```
   ⚀   ⚁   ⚂   ⚃   ⚄   ⚅        ← the dice on the table

   [⚀] [⚀] [⚄]                   ← taken out of this roll

              250
        two 1s · 200 + a 5 · 50
```

**Every die you take out has to score**, and the app holds you to it: keep a 3 and it is
outlined in red, the line underneath names it, and both Roll again and Bank grey out until
it goes back. A die that scores nothing is not counted quietly as nought — it is the roll
being read wrong, and the app says so.

Combinations only count **within the roll they came out of**, so each roll is scored on its
own and the ones already put by are listed above the total with what each was worth.

### Hot dice

Take out all six and the row of faces lights up again with all six on the table, the turn
total intact. The app works it out from the count — there is nothing to tell it, and no
limit to how many times round a turn can go.

### How much am I risking?

**If you roll again**, at the foot of the turn, is the only question a Farkle table ever
asks. It is asked rather than shown, because a running commentary on the odds plays the
dice for you:

```
 If you roll again                                        hide

 Roll again and 750 goes back on the table. A farkle takes all of it.
 Rolling 3 dice: about 28% of rolls come up with nothing at all, or one roll in 4.
 Bank instead and Ann is on 3,150, 6,850 short of 10,000.
```

Three things, because they are the three halves of the decision: what is at stake, how
likely it is to go, and what stopping now is actually worth. The chance is the real one for
the number of dice about to be rolled — a hair over 2% on six, two rolls in three on one —
and it accounts for hot dice, so the six you would get back are the six it quotes.

### Passing the post

First past 10,000 does not end it. Anyone who has had fewer turns gets one more, and the
highest score at the end of that round wins — a turn at Farkle is worth thousands, and
ending on the leader's own turn would hand the game to whoever sat down first. The banner
says whose lead is being chased and that there is one turn each left to answer it.

## Scoring

| | |
|---|---|
| Each **1** | **100** |
| Each **5** | **50** |
| Three of a number | its face **× 100** — three 1s are **1000** |
| Four alike, five, six | **1000**, **2000**, **3000** — whatever the number |
| A run of **1 to 6** | **1500** |
| **Three pairs** | **1500** |
| **Two triplets** | **2500** |
| A roll with none of the above | **farkle** — the whole turn goes |

Nothing else scores on its own: a lone 2, 3, 4 or 6 is worth nothing and cannot be taken
out. Four alike being flat means four 1s are worth no more than three of them — that is the
printed rule, quirk and all.

Tables play a dozen variants of the four-, five- and six-of-a-kind rules. The whole table is
written out in **☰ Menu → Rules**, so nobody has to remember which house they are in.

# The menu

**☰ Menu**, top right, on every screen — and it says ☰ Menu whether it is open or not,
because a menu with a Close button on it is a strange object.

Tapping it drops a short panel over whatever you were doing, which stays visible and dimmed
behind. Tap anywhere off the panel and it goes. Tap one of its three rows and it also goes,
replaced by what you picked — the menu is somewhere you pass through, so it does not sit
there after you have passed through it. **Back** does the same as tapping away.

What you picked is then an ordinary screen with **DONE** on it, and one press of Back
returns you to your game.

### Players

Every player you've ever entered, as a text field. Correct a spelling and it is right
everywhere at once — the seats, the scoreboard, the hand log, and every game already
finished — because a player is stored once and referred to by id everywhere else. There
is no rename button and nothing to press to save it.

**✕ forgets a player**, taking them out of the pick list. Games they played in keep their
name, so old scores never turn into question marks, and adding the same name again brings
them back with their history attached. Anyone sitting in the game being played can't be
forgotten out from under it — their ✕ is greyed until the game is over. Their name is
still theirs to correct.

### Rules

The same two tables the briefing shows when you pick a game: the rules, and **Worth
knowing** under them, so the hints are there mid-game and not only at the start.

Every game explains itself, and the app refuses to start if one doesn't — see *Adding a
fourth game*. A reminder, not the rulebook, though: deliberately only the things the screen
doesn't already say. The trick buttons, the Flip 7 tally and the Farkle turn all show you
the arithmetic as you play, so the rules card covers what they leave out: the bidding
ladder and screw-the-dealer for euchre; for Flip 7 the action cards, which sit on the table
but score nothing and so never appear in the tally; and for Farkle the scoring table
itself, which is the one thing every table plays a little differently.

The menu row says how many games are in there. **One game at a time**
is how the card itself behaves: Stacking every game onto one page turns a reminder you were
meant to skim into something you have to search. The card opens on the game the screen
implies — the one you're playing, or the one you're setting up — and a row of chips at the
top switches to another. On the home screen, where nothing is implied, it opens on the
first game.

### Past games

Every finished game was always recorded hand by hand. This is where it gets read.

**Standings** across everything played: games, wins, and win rate per player. A euchre win
counts for both partners.

**Head to head** — who beats whom, as a grid. Read across the row: their wins first.
Partners never meet each other, so a partnership shows no result between them.

**Games**, newest first. Tap one to unfold its full hand-by-hand log, exactly as it looked
when it finished. **Play again** brings the same people back with the deal moved on one
place, and **✕** deletes the record.

### Back

The back button moves **within** the app, not out of it. Each press closes one thing,
innermost first:

```
 the menu panel        →  whatever it was covering
 a past game's hands   →  the list it was opened from
 Players, Rules, a board  →  whatever you were doing
 the setup screen      →  home
 a game in progress    →  home, with the game kept
```

Backing out of a game is the same as *Leave this game for now* — it keeps its place, it
does not end it.

Every layer you can be inside has a history entry behind it, pushed during the tap that
opened it. Nothing is pushed from inside the `popstate` handler: an installed app does not
honour that, and depending on it meant the first Back press worked and the second closed
the app outright.

Only at home, with nothing left above it, does back mean leave, and it asks first. The
answer is another press: a web page cannot close itself, so going is the browser's to do
and the app does not pretend otherwise. Nothing is lost either way — everything is saved
as you go.

### Which build you are running

At the foot of the menu: **Score Keeper v10**. It is there because a phone can hold a
stale page and a fresh service worker at the same time, and from the outside that state
looks exactly like a bug — the app behaving in a way the code says it should not.

When the worker has a newer build than the page you are looking at, the line says so
(*v10 · v11 ready*) and offers **Reload to finish updating**. The new page is already
cached by then, so reloading is all that stands between it and being the one you are
using — no second launch, no removing it from the home screen.

If you ever report something odd, this line says which copy you saw it in.

### Leaving a game

Both ways out are in the menu, together, with the one you almost always want first.

**Leave this game for now** keeps the game exactly where it is; the home screen offers it
back and says which hand it reached. **End game** below it, in red, discards it — and asks
first, on the game screen, so you can see what you are about to throw away.

The footer holds Undo and nothing else. End game used to sit there, which put the only
destructive control in the app under the thumb of somebody reaching for Undo, and left the
gentler exit hidden in a menu. Back does the gentle one too.

# Every game

## Staying out of the way

The screen answers the two questions a table actually asks — *whose turn is it?* and
*what's the score?* — and then stops. No sound, no confetti, no notifications, nothing
that moves to be admired.

Three things move, and each one answers a question rather than decorating an answer. The
menu **grows from the button you tapped**, so it reads as covering your game rather than
replacing it. The two questions the app asks — *Discard this game?*, *Leave Score
Keeper?* — **arrive** rather than shoving the page down. And when a hand is scored the
standings **re-sort in front of you**, because who went past whom is the story of the
game and is worth seeing happen rather than finding already done.

Everything is under 250ms, and all of it is off for anyone whose device asks for reduced
motion. Scores never count up: a number you have to watch move is a number you can't
read.

Under the running score, every hand is listed the way you'd have written it down, with
each player's running total beside what they scored. That's the scratchpad, kept for
you.

A game is won by whoever is **ahead** once the target is passed — a hand can push two
players or two teams past the post at once, and the higher score takes it. If that leaves
them level, nobody has won: the app says so and deals the next hand. Farkle adds one
condition on top: the round has to finish first, so everyone has had the same number of
turns.

## Between games

Players are remembered as you use them; the ones you played with most recently sort to
the front, and the same list serves both games. Setting a game up is only picking who is
playing — correcting and forgetting live under **☰ Menu → Players**, on every screen, so
the setup screen does one thing.

Finished games are kept with their full hand-by-hand record, under **☰ Menu → Past
games**. **Play again** on any of them brings the same people back and moves the first
deal on one place — so a rematch is two taps. Euchre players can still be dragged into
different chairs before you start, for when the partnerships change; in Flip 7 and Farkle
the order comes back as it was, carried on from where the last game stopped.

Everything lives in browser storage on that device. Nothing is uploaded, there is no
account, and the app makes no network requests once it has loaded.

## On your phone

Open the hosted URL in Safari or Chrome, then **Share → Add to Home Screen**. It gets
its own icon, opens without browser chrome, and works with no signal after the first
load — including at a kitchen table with bad reception.

If you change any file, bump `CACHE` in `sw.js` **and `BUILD` in `index.html`** together,
or phones will keep serving the old version from cache. The menu shows both and says so
when they disagree, and a test asserts they match.

## Running it locally

Open `index.html` in a browser — the app itself needs no server.

Offline caching and Add to Home Screen need a real origin, so for those:

```sh
python3 -m http.server 8000
# then http://localhost:8000
```

## Adding a fourth game

Each game is a `RULES`-shaped block at the top of the script — `RULES` for bid euchre,
`FLIP7` for Flip 7, `FARKLE` for Farkle — plus the handful of views that draw it. A block
carries its own `rules` and `strategy` copy, so a new game explains itself — in the menu
and on the briefing you get when you pick it — without touching either. It also carries
the words its screens need — what the first player does, what
one round is called, the line it gets on the home screen — so the shared views read them
rather than asking which game they are drawing.

**A game without rules is not a finished game**, and that isn't left to memory: a check at
load throws if any block in `KINDS` has no `rules` or no `strategy`, so the app won't start
at all. It fails at your desk or not at all — there is no version of this where a game ships
that the menu can't explain, or that hands a new player a screen and no idea what to do with
it.

Having written three, what they actually share turns out to be small, and only that much
is shared: a **name**, a **target**, a **way of scoring one hand**, and that `rules` list.
`finish()` ends any of them the same way, `rosterCard()` picks the players, `logTable()`
prints the hands for the live scoreboard and the board alike, and `footer()` and the
storage, undo and history behind them never had to know which game was being played.

The third game paid that back. Farkle records a **turn as a hand of one** — scored against
the player who took it, in the shape Flip 7 already used — so the totals, the standings,
the past-games board, and players joining and leaving mid-game all worked on the day they
were written, without being told that dice existed. What Farkle needed of its own was one
screen and one predicate: `ready()`, which holds the end of a game back until the round is
finished, and which the other two simply do not have.

Everything else — seats against a flat list, teams against individuals, three guided taps
against a card grid against a turn that does not end — stayed separate, because pushing
them together would have cost more than it saved. A fourth game means a fourth block, and
another look at where the line falls.

## Licence

MIT. See [LICENSE](LICENSE).
