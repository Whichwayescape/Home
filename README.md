# Whichway Escape — Website

A small, classy escape-room website with one fully playable Office Escape puzzle.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The main landing page (Sherlock-Holmes / cigar-den style) |
| `style.css` | Stylesheet for the landing page |
| `office.html` | The Office Escape — the start of the puzzle |
| `office-style.css` | Stylesheet for the Office desktop |
| `inbox.html` | Email puzzle (clue: "you won't find what you are looking for here") |
| `sent.html` | Email puzzle (clue: read the second word of each line) |
| `history.html` | Meeting Notes puzzle |
| `snake.html` | Snake game (the high-score initials are part of the puzzle) |
| `ballbreaker/ballbreaker.html` | Ball Breaker game (top 3 high scores spell the password) |
| `officepass.html` | The "you won!" page |
| `IMG_6912.JPG` | Original wallpaper (kept in case you want it) |
| `email.css` | Shared stylesheet for the email/note windows |

## Puzzle solutions (don't share with players!)

| Puzzle | Password | How they figure it out |
|---|---|---|
| **Games** | `RATLOL` | Top 3 high scores in Ball Breaker spell **RAT-WOW-LOL** → take the first chunk + last chunk. Snake also has a "RAT" at the top as a hint. |
| **Email** | `IS` | Read the second word of each line in the **Sent** email vertically — it spells out a sentence ending in "IS". (Inbox email also says "you won't find what you are looking for here" → look elsewhere, in Sent.) |
| **Meeting** | `7543ing111` | The 9:27am note complains about a password and mentions IT thinks the user is mistyping. The password reads like keyboard shifts — solve to get `7543ing111`. |
| **Conference** | `PLACEHOLDER` | Currently set to `PLACEHOLDER` — change this in `office.html` once you've designed the animal-ranking puzzle's specific challenge. |

> If you want to **change a password**, edit it in `office.html` inside the `requiredPasswords` array near the top of the `<script>` block.

## Licensing & attribution (this is all copyright-free / open source)

- **XP.css** — by Jordan Scales, MIT License — https://github.com/botoxparty/XP.css
  - Loaded from a CDN: `<link rel="stylesheet" href="https://unpkg.com/xp.css" />`
  - You can use this freely in commercial projects.
- **Google Fonts** (Playfair Display, EB Garamond, Cormorant Garamond) — Open Font License, free for commercial use.
- All custom HTML/CSS/JS in this repo: written from scratch for you. Yours.

## How to update the site (the simple version)

See `HOW-TO-UPDATE.md` in this folder for plain-English instructions on editing
content, pushing changes to GitHub, and deploying with Netlify.
