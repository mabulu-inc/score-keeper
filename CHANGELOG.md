# Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

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
- Remembered players, sorted so the people you play with most often are first, with an
  edit mode for clearing out typos.
- Saved games with their full record, and a **Play again** button that re-seats the same
  four players and moves the first deal on one place. Seats can be swapped before
  starting, for when the partnerships change.
- Seating by tapping two players to swap them, with partners shown opposite each other
  so the teams are visible before the first card is dealt.
- Any player can take the first deal; the deal then moves clockwise on its own.
- Works fully offline and installs to the home screen, so a table with no signal is not
  a problem. The game in progress survives closing the app.
