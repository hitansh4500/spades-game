# Spades Web Edition (Offline Games Style)

An interactive web recreation of the **Spades** card game from the popular Offline Games app, designed to support flexible even-numbered multiplayer groups (2, 4, 6, or 8 players).

## Features & Implementation

### 1. Lobby & Player Configuration (First Interface)
- **Default 2 Players**: The page opens immediately to the player setup interface initialized to 2 players.
- **Even Player Rule**: Enforces that only even numbers of players (2, 4, 6, 8) can join. Steppers and quick preset chips keep the player count even.
- **Dynamic Player Names**: As players are added, personalized name fields are dynamically generated. Existing typed names are preserved.
- **Team Assignment**: Automatically pairs players into **Team 1 (Red)** and **Team 2 (Blue)** with teammates positioned opposite each other.
- **Form Validation**: 
  - Prevents game start if player count is odd.
  - Checks that **all player names are filled**. If any name is left blank, the card highlights with a red outline and shake animation, and displays a friendly error banner.
- **Game Modes**: Supports **Solo with Smart AI Bots** or **Pass & Play** on a single device.

### 2. Spades Table & In-Game Badges (Screenshots 6, 7 & 8)
- **"Bid Met" Dynamic Badges**:
  - When a team reaches or surpasses their contract, their bid pill transforms into an animated green badge: **`Bid Met 8/5 ✓`**!
  - When still striving for their contract: shows **`Our Bid 3/5`** / **`Their Bid 6/5`**.
- **Player Pill Avatars**: Displays each player's name and tricks won vs bid (e.g. `4/2`, `3/3`, `0/0` for NIL).
- **Goal 500 Scoreboard**: Displays real-time match scores (including negative scores if penalized).

### 3. Comprehensive Official Rules & Regulations Engine
Implemented strictly according to the game screenshots:
1. **Making Contract (Slide 6)**:
   - If `Team Tricks >= Team Bid`: Earns `10 points per trick bid` + `1 point per excess trick (bag)`.
2. **Failing Contract / "Set" (Slide 7)**:
   - If `Team Tricks < Team Bid`: Loses `10 points per trick bid` (e.g. a bid of 5 results in `-50 points`).
3. **Bag Accumulation & Penalty (Slide 8)**:
   - Excess tricks across rounds accumulate as bags (tracked as `X/10`).
   - Every time a team reaches **10 bags**, they suffer a **-100 points penalty**, and their bag count resets by 10.
4. **NIL Bidding (Slide 9)**:
   - Any player bidding **NIL** (0 tricks):
     - Successfully winning 0 tricks: **+100 bonus points**!
     - Failing (taking 1 or more tricks): **-100 penalty points**!
5. **Round Summary Modal (Slide 10)**:
   - Modeled directly on Screenshot 10:
     - Header: `Round X`
     - Columns: `US` (Blue Pill) and `THEM` (Blue Pill)
     - Rows: `Bags (X/10)`, `This Round (+/- pts)`, and `Total`
     - Subtext: `Reach 500 to Win!`
     - Left circular red restart button (`↺`) and right green `CONTINUE` button.

### 4. 10-Slide Interactive Tutorial ("HOW TO PLAY")
- Slide 1: 4 players in 2 teams, race to 500 points.
- Slide 2: Partners sit opposite each other and combine bids/tricks.
- Slide 3: Bidding phase (Nil and 1–13 tricks expected).
- Slide 4: Must follow suit; highest card of lead suit wins if no spade.
- Slide 5: Spades are trump: beats all other suits; highest spade wins.
- Slide 6: Meeting bid gives 10 pts per bid + 1 pt per bag.
- Slide 7: Failing bid loses 10 pts per bid.
- Slide 8: 10 bags penalty (-100 points).
- Slide 9: NIL bidding (+100 bonus if made, -100 if failed).
- Slide 10: Round summary score sheet and progression towards 500 points.

## How to Run

Simply open `index.html` in any modern web browser:
```bash
open /Users/hitansh/.gemini/antigravity/scratch/spades-game/index.html
```

Or run a local static server:
```bash
cd /Users/hitansh/.gemini/antigravity/scratch/spades-game
ruby -run -ehttpd . -p8000
# Then visit http://localhost:8000 in your browser
```
