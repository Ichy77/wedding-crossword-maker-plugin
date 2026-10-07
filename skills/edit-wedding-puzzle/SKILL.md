---
name: edit-wedding-puzzle
description: Change an existing wedding crossword, stationery or guest game by its 6-character share code, including questions, names, date, design template, colours, fonts and print size. Use when someone shares a code from Wedding Crossword Maker, says they made a wedding puzzle earlier, or wants to change the look or content of one.
---

# Edit a wedding puzzle

Every puzzle from Wedding Crossword Maker has a 6-character share code such as `A7K2Q9`. All products of one wedding (crossword, stationery and games) live under the same code.

## Read before you change

If you didn't create the puzzle in this conversation, call `get_wedding_puzzle` with the code first. It returns the stored content and design, so you change what is there instead of guessing. A code that isn't found has either been mistyped or expired: puzzles are kept for 180 days after the last save.

## Pick the narrowest tool

| The user wants to change | Tool |
|---|---|
| Crossword questions, names, title, date, solution word, design template, paper size or orientation | `update_wedding_crossword`. Pass only the fields that change. `entries` replaces **all** questions, so send the complete list. |
| The look of everything: template, colours, fonts, sizes, bold/italic/underline of the text blocks, corner decoration | `customize_design`. Call `list_designs` first for the valid template, colour-token and font ids. |
| One stationery or game product: size, card background, per-block fonts and colours, product options | `customize_product` |
| Which games guests can play online | `set_play_games` |
| A stored field no other tool covers | `update_puzzle_payload`, after reading the structure with `get_wedding_puzzle` |

These tools change the saved puzzle in place, and the change is visible to everyone who has the code. Before a larger change such as replacing all questions, briefly confirm with the user what will be overwritten.

Colours must be hex values such as `#7a8b6f` or plain colour names such as `navy`; `rgb()` and other functions are not accepted. If a value is rejected, the tool says so; pick another and retry.

## After a crossword change

Check the result for warnings about unplaced answers or a solution word the grid can't provide, fix them, and update again. See the `wedding-crossword` skill for the answer rules.

## Present the result

Confirm the change in one sentence, then give the **download link** for the updated PDF and offer the **editor link**. The share code stays the same.

Some things are only possible on the website, not through the connector: uploading a background photo and receiving the PDF by email. For those, point the user to the editor or download page.
