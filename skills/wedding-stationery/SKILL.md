---
name: wedding-stationery
description: Create printable wedding stationery (a welcome sign, a menu card or place cards) in a design matching the couple's wedding crossword. Use when someone asks for a wedding welcome sign, easel sign, menu, menu card, place cards, name cards, seating cards or table cards, or wants stationery that matches a puzzle they already made.
---

# Wedding stationery

The Wedding Crossword Maker connector creates three stationery products as print-ready PDFs. They share the design, names and date of the puzzle they belong to, so a couple gets one consistent look.

## Keep it together

If the user already has a puzzle from this conversation, or gives you a 6-character share code, **pass that `code`** to every create call. Then the product joins the existing puzzle with the same design and names. Without a code, a new puzzle with its own share code is created; in that case pass `names`, `date` and a `themeId` (see the `wedding-crossword` skill for the template list).

Write in the user's language and pass `locale`: `"de"` for German, `"en"` for everything else.

## What to write yourself and what to ask for

| Product | Tool | Content |
|---|---|---|
| Welcome sign | `create_welcome_sign` | `names` is required. You **may write** `headline` (e.g. "Welcome", "Herzlich willkommen") and `subline` (e.g. "to the wedding of") in the couple's tone; check once that it fits. Default size is A2, for an easel. |
| Menu card | `create_menu_card` | `heading` plus `courses`, each with a `label` ("Starter") and `dishes` with `name` and optional `description`. **Ask for the real courses and dishes. Never invent a menu.** If the couple doesn't know it yet, suggest coming back later. Default size is A5. |
| Place cards | `create_place_cards` | `guests`, one name per entry, printed 10 cards per A4 sheet. **Ask for the real guest list. Never invent names.** Accept a pasted list and split it into one name per entry. |

Ask one question at a time, as in the crossword interview.

## Fine-tuning

`customize_product` changes one product after it exists: print size (`format`), card `backgroundColor`, product options such as `showCutLines` for place cards, and per-text-block `styles` with `font`, `size` and `color`. Its description lists every field per product. Call `list_designs` for valid font ids and colour rules before you set fonts or colours.

To change the shared design of all products at once (template, colours, fonts of the puzzle sheet), use `customize_design`, described in the `edit-wedding-puzzle` skill.

## Present the result

Lead with the **download link** for the print-ready PDF, then offer the **editor link** for changes. Keep it to a few sentences and don't paste the full tool output. Physical printing is up to the couple: the PDF works with any print shop or a home printer.
