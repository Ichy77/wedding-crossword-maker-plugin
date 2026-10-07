# Wedding Crossword Maker

Create a personalised wedding crossword with Claude, straight from the couple's story, and matching stationery and guest games in the same design. Everything is free and needs no account.

## What it does

Tell Claude who is getting married. It interviews you one question at a time (how the couple met, the proposal, their quirks), writes the clues in the tone you choose and builds the crossword. You get a link to the print-ready PDF and a link to the web editor for further changes.

In the same design, Claude can also create:

- **Stationery:** welcome sign (A2), menu card (A5) and place cards (10 per A4 sheet)
- **Guest games:** wedding bingo, a quiz about the couple and a word search
- **Online play mode:** guests solve the crossword and games on their phones, with an optional live leaderboard

Give Claude a share code from an earlier session to change questions, colours, fonts or paper size.

Works in German and English.

## Use it

After installing, ask in any conversation, for example:

- "Make a wedding crossword for my best friend Anna and her fiancé Paul."
- "Erstelle ein Hochzeits-Kreuzworträtsel für uns, wir heiraten im Juni."
- "Add place cards for our guests to puzzle A7K2Q9."
- "Make bingo cards for the wedding in the same design."

## Contents

| Component | Purpose |
|---|---|
| `.mcp.json` | Connects the Wedding Crossword Maker MCP server at `https://www.wedding-crossword-maker.com/api/mcp` (remote, no sign-in) |
| `skills/wedding-crossword` | Interview, clue and answer rules, creating the crossword |
| `skills/wedding-stationery` | Welcome sign, menu card and place cards |
| `skills/wedding-guest-games` | Bingo, quiz, word search and the online play mode |
| `skills/edit-wedding-puzzle` | Changing an existing puzzle by its share code |

The plugin contains only Markdown and JSON. It runs no local code, scripts or hooks.

## Data

The plugin sends only what you ask Claude to put on the puzzle to the Wedding Crossword Maker server (`www.wedding-crossword-maker.com`): the couple's names, the wedding date, questions and answers, menu items, guest names for place cards, game content and design choices. It sends no other conversation content and no files.

The server stores each puzzle under a random 6-character share code and deletes it 180 days after the last change. Anyone who knows the code can open, download and edit that puzzle, so share it only with the couple and their helpers. For product analytics the server records which tool ran, whether it succeeded, how long it took and the share code, but not the puzzle content. The request IP address (for remote connectors, Claude's servers) is used only for rate limiting. The connector cannot send email and has no access to photos or uploads.

Privacy policy: https://www.wedding-crossword-maker.com/datenschutz

## Support

Questions and feedback: https://www.wedding-crossword-maker.com/kontakt

## License

MIT, see [LICENSE](LICENSE).
