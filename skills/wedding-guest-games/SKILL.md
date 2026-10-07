---
name: wedding-guest-games
description: Create wedding games for guests (wedding bingo, a quiz about the couple or a word search) as printable sheets and as an online play mode guests open on their phones. Use when someone wants games, activities or entertainment for wedding guests, a "how well do you know the couple" quiz, wedding bingo cards, a wedding word search, or asks how guests can play the crossword on their phones.
---

# Wedding guest games

The Wedding Crossword Maker connector creates three games next to the crossword. Each one is a printable PDF, and all of them, the crossword included, can be played online at the wedding.

## Keep it together

Pass the existing share **`code`** when the couple already has a puzzle, so the game joins it with the same design and names. Without a code, a new puzzle is created; then pass `names`, `date` and optionally a `themeId`. Pass `locale` (`"de"` for German, `"en"` otherwise).

## The games

| Game | Tool | What you can do |
|---|---|---|
| Quiz | `create_quiz` | `questions`, each with `question` and an optional `answer`. You **may derive** 8 to 14 questions yourself from what you know about the couple, in their chosen tone. Unlike crossword answers, quiz answers can be free text. |
| Word search | `create_wordsearch` | `words`: 8 to 14 short single words with a wedding link (names, places, hobbies from the conversation, or classics such as LOVE, DANCE, VOWS). Letters only, no spaces. You may compile them yourself. |
| Bingo | `create_bingo` | `terms`: typical wedding moments ("Bride cries happy tears", "First dance", "Champagne cork pops"). Use **at least 24** so the cards differ from each other. Optional `freeText` for the centre square, e.g. "I DO!". You may compile them yourself. |

Each tool also takes an optional `title`. Tailor content to what you learned about the couple; generic examples are a fallback, not the goal.

## Online play mode

Every puzzle with content can be played on phones: guests open one link and see a tab per game. A live leaderboard is available there as well.

- By default every game with content is live. `set_play_games` chooses which games guests see, for example only the crossword and the quiz.
- Tool results mention the play mode in words and include its link. **Share the play link only when the user asks for it**: most people first want the printable version, and the link is meant for the guests on the day.
- Anyone with the share code can open and edit the puzzle, so the couple should hand guests the play link, not the editor link.

## Present the result

Lead with the **download link** for the printable sheet, offer the **editor link** for changes, and mention the online play mode in a sentence. Keep it short.
