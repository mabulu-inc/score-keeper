# Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- **Flip 7**, alongside bid euchre. Everyone plays for themselves, there is no limit on
  how many are round the table, and the game goes to 200. Pick which game you are
  playing on the home screen; both share the same list of players and the same record of
  finished games.
- A quick tally at the end of each Flip 7 hand: tap a player, tap the cards sitting in
  front of them, and their score appears as you go. Every card is a toggle, so a mis-tap
  is fixed by tapping it again rather than starting over.
- The seven-card bonus counts itself. Seven different numbers adds 15 automatically, and
  the numbers you didn't take go dead — there is no eighth card to tap, because the hand
  would have ended.
- The line under the running total shows the sum being done rather than just its answer,
  so it is visible that ×2 doubles the number cards only and the + cards land after it —
  the rule tables most often get wrong.
- **Busted** is one tap and scores the hand at nothing, however far it got, clearing the
  cards with it instead of leaving them on screen to be read as a score.
- The button that ends a Flip 7 hand won't fire until every player has been tallied, and
  says how many are still to do rather than leaving you to hunt for who was missed.
- Standings that sort themselves as the game moves, and a hand-by-hand log with a column
  per player, each running total under what they scored, and the hands somebody flipped
  seven marked.
- Bid euchre scoring for four players in two teams, played to 40 points. Each hand is
  three taps — the bidding, the trump, and the number of tricks the bidding team took —
  and the running score keeps itself.
- A guided bidding round that opens to the left of the dealer and offers only the bids
  that are actually legal, so nobody has to hold the current bid in their head. When
  the round reaches the dealer with no bid on the table, passing is not offered:
  *screw the dealer* enforces itself rather than needing to be remembered.
- Trick entry where every button shows, before you press it, what that result scores
  for both teams — so the gap between making the bid and going set is on screen instead
  of being worked out at the table.
- A table diagram that carries the state of the hand: who is dealing, whose turn it is
  to bid, and what each player has already done this round. Team colours are shared by
  the seats, the scoreboard, the trick buttons and the log, so no number is ambiguous.
- Trump calling for hearts, diamonds, clubs, spades, high and low, with high and low
  unavailable below a bid of 4.
- Partner's best and alone as all-or-nothing bids worth 12 and 24 points, which score
  their full value only on all six tricks and lose it otherwise.
- A hand-by-hand log under the score — dealer, bid, trump, tricks and each team's
  running total — replacing the scratchpad it was written on.
- Undo that steps back through everything, including a mis-tapped trick count, a wrong
  trump, a bid recorded against the wrong player, and a game that has already finished.
- Remembered players, sorted so the people you play with most often are first.
- Names can be corrected wherever you notice the mistake: **✎ Fix a name** under the table
  during a game, or **Edit** in the players list while setting one up. Names are shown as
  plain text fields, so fixing a spelling is just typing it — no rename button, nothing to
  save — and the correction reaches the seats, the scoreboard, the hand log and every game
  already finished, because a player is stored once and referred to everywhere else.
- Forgetting a player now also clears them out of any seat they were filling, and no longer
  blanks out the games they played in — old scores keep the names they were won under
  instead of turning into question marks. Adding the same name again brings that player
  back with their history.
- Saved games with their full record, and a **Play again** button that re-seats the same
  four players and moves the first deal on one place. Seats can be swapped before
  starting, for when the partnerships change.
- Seating by tapping two players to swap them, with partners shown opposite each other
  so the teams are visible before the first card is dealt.
- Any player can take the first deal; the deal then moves clockwise on its own.
- Either game is won by whoever is ahead once the target is passed, not by whoever
  passed it first, so a hand that carries two teams or two players over at the same time
  is settled on the higher score. Level at the top is not over — the app says so and
  deals on until someone leads.
- Works fully offline and installs to the home screen, so a table with no signal is not
  a problem. The game in progress survives closing the app.
