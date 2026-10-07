---
name: wedding-crossword
description: Create a personalised wedding crossword about a couple. Use when someone wants a crossword, puzzle or "how well do you know the couple" game for a wedding, engagement party, bridal shower or wedding anniversary, whether they are the couple themselves, a maid of honour, best man, friend or family member.
---

# Wedding crossword

Turn a relaxed conversation about the couple into a crossword the guests solve at the wedding. The Wedding Crossword Maker connector stores it and renders the print-ready PDF. Everything is free and needs no account.

## 1. Interview, one question at a time

The facts make or break the puzzle, so collect them in a conversation, not with a form.

- Ask **exactly one question per message**. React briefly and genuinely to the last answer first, then ask the next question. No lists of questions and no enumerated options.
- Write in the user's language. The connector supports German (`locale: "de"`) and English (`locale: "en"`). Use `"de"` for a German conversation and `"en"` for every other one.
- Early on, find out whether the user **is part of the couple** or is making the puzzle **for someone else**. Address them accordingly for the rest of the conversation ("where did you two meet?" vs. "where did they meet?").
- Collect the couple's names (for `names`, e.g. "Anna & Paul") and the wedding date (for `date`, free text such as "14 June 2027").
- Ask openly about the style or colour scheme of the wedding and pick a `themeId` from the answer (see the table below). If nothing fits, leave it out.
- Ask once whether the clues should be **funny and cheeky** or **warm and heartfelt**, and keep that tone for every clue.
- Then gather stories: how they met, first date, the proposal, trips, hobbies, pets, quirks, who is always late, what friends say about them. Follow the conversation and stay tactful around sensitive topics.

If the user pastes a ready list of facts or questions, skip the interview and work with what you have.

## 2. Write the entries

Collect **8 to 12** usable facts, then turn each into a clue for the guests (`question`) and a solution (`answer`).

Answer rules, enforced by the grid:

- **One word, letters only.** No spaces, hyphens, digits or punctuation. German umlauts become AE/OE/UE and ß becomes SS automatically, but other accents should be avoided.
- **3 to 12 letters** works best. Very short answers give the grid nothing to cross.
- **Answers must share letters** so they can cross. A set of answers with common letters (E, A, N, R, S, T, …) produces a dense grid; an answer that shares no letter with the rest stays unplaced.
- Clues are normal sentences in the chosen tone, e.g. "Where did Anna spill her coffee over Paul on their first date?" → `CAFE`.

Pick a short `title` such as "How well do you know Anna & Paul?" or the German "Wie gut kennt ihr das Brautpaar?".

### Optional: solution word

A hidden `solutionWord` (e.g. `JAWORT`, `LIEBE`, `FOREVER`) is highlighted in the grid. Every one of its letters must appear somewhere in the answers. Offer it once; don't insist.

### Design templates

| The couple describes | `themeId` |
|---|---|
| Natural, greenery, eucalyptus, fresh | `eukalyptus` |
| Boho, earthy, linen, desert | `boho` |
| Simple, minimalist, modern | `minimal` |
| Romantic, blush, soft, playful | `romantisch` |
| Glamorous, gold, Gatsby, Art Deco | `artdeco` |
| Classic, navy, blue and gold | `blau-gold` |
| Sage green and terracotta | `salbei-terrakotta` |
| Ink, black and white, calligraphy | `tinte` |
| Lavender, lilac, Provence | `lavendel` |
| Emerald and gold, jewel tones | `smaragd-gold` |
| Pampas grass, beige, neutral | `pampas` |

`list_designs` returns the current list with descriptions if you are unsure.

## 3. Create it

Call `create_wedding_crossword` with `names`, `title`, `date`, `entries`, the optional `themeId`, `solutionWord`, `paperFormat` (A4 by default) and `paperOrientation` (portrait by default), and `locale`.

The result can contain **warnings**: answers that could not be placed, answers with too few letters, or solution-word letters the grid cannot provide. Don't hide them. Fix the entries yourself (swap an answer for one that shares letters, or change the solution word) and call `update_wedding_crossword` with the share code, then tell the user briefly what you changed.

## 4. Present the result

Keep the reply short and lead with what people want:

1. The **download link** for the print-ready PDF, as the main result.
2. The **editor link**, for anyone who wants to change questions, fonts or paper size themselves.
3. In words only: guests can also solve the puzzle online on their phones. Share that link only if the user asks (see the `wedding-guest-games` skill).

Mention the share code once and say that anyone who has it can open and change the puzzle, so it belongs with the couple and their helpers, not in a public post. Saved puzzles expire 180 days after the last change.

Don't paste the full tool output or every link it contains. The connector cannot send email: on the download page the user can enter an address to receive the PDF by mail.

## 5. Offer more in the same design

Once the crossword exists, offer **once** and casually to make matching pieces in the same design: welcome sign, menu card, place cards (`wedding-stationery` skill) or guest games such as bingo, a quiz or a word search (`wedding-guest-games` skill). Always pass the existing share code so everything stays together.
