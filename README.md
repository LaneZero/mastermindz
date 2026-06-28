# Fekr o Bekr / Mastermind

A bilingual, browser-based Mastermind code-breaking game built as a single HTML file.

- **Persian name:** فکر و بکر
- **English name:** Mastermind
- **Languages:** Persian (RTL) and English (LTR)
- **Deployment:** Static hosting, including Netlify
- **Build step:** None required

## Live Concept

The computer creates a secret sequence of six colored pegs. The player must crack the code within ten attempts by using the feedback after each guess.

The game is designed for desktop and mobile play, with quick color selection controls so players do not need to repeatedly scroll through the page.

## Features

- Bilingual interface: Persian and English
- Responsive layout for desktop, tablet, and mobile
- Persian UI uses the Vazirmatn font
- Dark and light themes
- Color-blind mode with symbols inside color pegs
- Ten attempts per game
- Eight available colors
- Optional repeated colors in the secret code
- Normal and Simple game modes
- In Simple mode, exact-position matches are shown directly on the matching peg
- Quick color palette for faster play, especially on mobile
- Sticky desktop color palette
- Three limited Codebreaker Assistant hints per game
- Assistant avoids suggesting colors that the player has already used
- Accurate Mastermind feedback for duplicate colors
- Score calculation based on difficulty, attempts, time, and win streak
- Local leaderboard and player statistics
- Save and resume an unfinished game with `localStorage`
- Sound effects generated with the Web Audio API
- Keyboard controls
- How-to-play modal
- Result screen with win/loss details and close button
- GitHub profile footer for LaneZero

## How to Play

1. Enter a username and start a game.
2. Select your preferred game options:
   - **Allow repeated colors:** The secret code may contain the same color more than once.
   - **Simple mode:** Exact-position matches are shown on the related peg.
3. Build a guess containing six colors.
4. Submit the guess.
5. Read the feedback:
   - **Black peg:** Correct color in the correct position.
   - **White peg:** Correct color in the wrong position.
   - **No peg:** That color does not exist in the secret code.
6. Use logic to solve the code before running out of attempts.

Feedback pegs are intentionally shown in no positional order in Normal mode. This is a core Mastermind rule and prevents the feedback from revealing too much.

## Difficulty and Scoring

The game applies a score multiplier based on the selected mode:

| Mode | Repeated Colors | Score Multiplier |
|---|---:|---:|
| Normal | Enabled | ×1.00 |
| Normal | Disabled | ×0.90 |
| Simple | Enabled | ×0.75 |
| Simple | Disabled | ×0.65 |

The final score also considers:

- Base score
- Remaining attempts
- Completion time
- First-attempt bonus
- Current win streak

Simple mode awards less because it reveals exact peg locations and is intentionally easier.

## Codebreaker Assistant

Each game includes up to three Codebreaker Assistant hints.

The assistant may:

- Suggest a color that has not been used in prior guesses
- Provide a position-related clue when all useful color suggestions have already been used
- Avoid repeating a previously guessed color as a “new” color suggestion

Hints are designed to reduce frustration without giving away the full code.

## Controls

### Mouse and Touch

- Tap or click a color to select it.
- Tap an empty slot to place the selected color.
- Tap a filled slot to remove it.
- Use the quick palette at the bottom of the game screen to add colors directly to the next empty slot.
- Use **Undo Last** to remove the latest peg.
- Use **Submit Guess** after filling all six slots.

### Keyboard

| Key | Action |
|---|---|
| `1` to `8` | Select a color |
| `Enter` | Submit the current guess |
| `Backspace` | Remove the latest peg |
| `Esc` | Close open dialogs or result screens |

## Color Palette

| Key | Color | Hex |
|---:|---|---|
| 1 | Red | `#FF4444` |
| 2 | Blue | `#4444FF` |
| 3 | Green | `#44BB44` |
| 4 | Yellow | `#FFD700` |
| 5 | Orange | `#FF8C00` |
| 6 | Purple | `#9B59B6` |
| 7 | Pink | `#FF69B4` |
| 8 | White | `#F0F0F0` |

## Local Storage

The game stores data in the browser using `localStorage`.

| Key | Purpose |
|---|---|
| `mastermind_users` | Player statistics and best scores |
| `mastermind_leaderboard` | Local top score list |
| `mastermind_current_game` | Unfinished game state for resume support |
| `mastermind_settings` | Sound, theme, language, color-blind mode, and last username |

> Local storage is device- and browser-specific. Clearing browser data removes local scores, settings, and saved games.

## Run Locally

No package manager, build system, or backend is needed.

### Option 1: Open the file

Open `index.html` in a modern browser.

### Option 2: Use a local server

Using Python:

```bash
python -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Deploy on Netlify

This project is a static website. The repository root should contain `index.html`.

### Netlify Build Settings

```text
Base directory: [leave empty]
Build command: [leave empty]
Publish directory: .
Production branch: main
```

### Deploy through GitHub

After connecting the GitHub repository to Netlify:

```bash
git add index.html README.md
git commit -m "Update game"
git push origin main
```

Netlify will automatically create a new production deployment after the push.

## Project Structure

```text
fekr-o-bekr/
├── index.html     # Complete game: HTML, CSS, and JavaScript
├── README.md      # Project documentation
└── LICENSE        # Add a license before public distribution
```

## Technical Notes

- The game is intentionally packaged as one `index.html` file.
- There is no build process and no runtime JavaScript framework.
- Game state is stored locally in the browser.
- The current game does not use a database or user authentication.
- A future Wallet, payment, or shared online leaderboard feature must use a backend or serverless functions. Do not trust `localStorage` for paid credits or account balances.

## Future Ideas

- Daily challenge with one shared code per day
- Online leaderboard with authenticated accounts
- Friends challenge mode
- Wallet-based optional purchases for hints
- Base / USDC payment support
- PWA install support
- Android app packaging with Capacitor
- Additional visual themes and sound packs

## Credits

Designed with love by [LaneZero](https://github.com/LaneZero/).

---

Enjoy cracking the code.
