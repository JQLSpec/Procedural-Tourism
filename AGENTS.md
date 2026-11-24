# AGENTS.md

## Project overview

**Procedural Tourism: A Cooperative Travel Game** is a cooperative, print-and-play travel exploration game. The goal is to create memorable discoveries, not competition, punishment, or an exhaustive itinerary. The project is in private prototype development; field playtesting is pending.

## Sources of truth

Read the relevant source documents before making changes. The Game Design Document is the canonical design reference; the Player Rulebook is the player-facing implementation of its rules. Deck Markdown files are the authoritative sources for individual card text. PDFs are derived print assets, not independent sources of game rules.

| File | Responsibility |
| --- | --- |
| `procedural-tourism-game-design-document.md` | Design pillars, core mechanics, expansion rules, namespace registry |
| `procedural-tourism-player-rulebook.md` | Rules and instructions for players |
| `procedural-tourism-quest-deck.md` | Quest design and cards |
| `procedural-tourism-conditions-deck.md` | Condition design and cards |
| `procedural-tourism-curse-deck.md` | Curse design and cards |
| `procedural-tourism-player-rulebook.pdf` | Printable rulebook |
| `procedural-tourism-*-cards-avery-95272.pdf` | Printable card decks |
| `avery-95272-alignment-test.pdf` | Print alignment test |

These paths reflect the current flat file layout. If the repository is reorganized, resolve the actual paths and update references rather than creating duplicate sources. Do not assume generation scripts or a build system exist; inspect the repository first.

## Design invariants

Preserve these unless the maintainer explicitly requests a rule change:

- One round lasts 12 consecutive hours, with a start time chosen by the group.
- Draw one Quest per traveler, one collective Condition, then one Curse per traveler. Follow explicit card exceptions, such as resolving Fresh Start before curse draws.
- Base quests require 90–240 minutes of meaningful effort, including relevant local travel, research and documentation.
- Conditions apply collectively; curses apply individually. Curses are mandatory every round, not triggered by failure.
- Only one active curse per traveler. No stacking, transfer, carryover, or failure penalties. Effects expire no later than round end.
- Curses should add no more than approximately 30 minutes of effort, including optional redemption. Conditions should not become additional quests.
- No formal competitive scoring or campaign progression in the current core rules.
- Safety, local laws, consent, privacy, accessibility, health, dietary needs, essential communication, and existing commitments override game effects without penalty.
- Favor cooperation, firsthand learning, modest costs, light physical activity, and meaningful choices over busywork, public embarrassment, or reliance on unwilling strangers.

Consult the canonical documents for detailed adjudication. In particular, exchange intrinsically infeasible quests first, redraw incompatible conditions second, and redraw redundant or incompatible curses third. Recheck after exchanges. Mere inconvenience is not sufficient reason for a redraw.

## Card authoring and balance

Use the existing card schemas and formatting. A new card must state clear, observable requirements or effects, appropriate scope, and necessary exceptions. Do not silently change a card's effect when shortening text for print.

### Core deck composition

| Quest category | Code | Count |
| --- | --- | ---: |
| Exploration | EX | 15 |
| History | HI | 10 |
| Culinary | FD | 10 |
| Cultural | CU | 10 |
| Creative | CR | 8 |
| Journey | JO | 7 |

| Condition category | Code | Count |
| --- | --- | ---: |
| Transportation | TR | 6 |
| Navigation & Geography | NG | 6 |
| Economics & Consumption | EC | 4 |
| Technology & Information | TI | 5 |
| Language & Social Interaction | LS | 4 |
| Food & Dining | FD | 3 |
| Time & Pace | TP | 4 |
| Cooperation & Decision-Making | CD | 4 |
| Chance & Serendipity | CS | 4 |

Condition mechanical types: 20 restrictive, 14 prescriptive, 6 beneficial. Scope is either Full Round or Quest Activities.

| Curse category | Code | Count |
| --- | --- | ---: |
| Mobility & Navigation | MN | 10 |
| Information & Resource Deprivation | IR | 10 |
| Quest Complications | QC | 10 |
| Dependency & Loss of Autonomy | DA | 10 |
| Chaos & Compulsions | CC | 10 |

Curse duration types are Persistent, Conditional, and Quest-bound. Duration is separate from scope. A conditional curse must specify its optional redemption. The initial duration mix is a playtest baseline, not an immutable expansion requirement.

Quests need an objective, effort estimate, and measurable completion requirements. Conditions need a mechanical type, scope, and explicit rule. Curses need an effect, duration type, scope, and redemption or clarification when applicable. Preserve category diversity and test card interactions rather than evaluating cards only in isolation.

## Card identifiers and expansions

Use the canonical format `<SET>-<DECK>-<CATEGORY>-<NUMBER>`; for example, `CORE-Q-EX-01`, `CORE-C-TR-01`, and `CORE-U-MN-01`.

- `CORE` is reserved for the original game. Only CORE is currently allocated; register new expansion namespaces in the Game Design Document before assigning identifiers.
- Deck codes are `Q` (Quest), `C` (Condition), and `U` (Curse). Category codes are scoped to their deck.
- Validate identifiers against `^[A-Z][A-Z0-9]*-[QCU]-[A-Z]{2}-[0-9]{2,}$`, the registry, positive canonical numbering, and uniqueness.
- Allocate the next unused number in a set/deck/category sequence. Never recycle retired IDs or renumber existing cards. Preserve legacy Quest aliases for historical records only.
- Translations, corrections, and minor balance changes retain IDs; substantively different cards receive new IDs. Unchanged core cards reused in an expansion retain their CORE IDs.
- Destination packs and thematic modules may intentionally vary category ratios with a documented rationale. Do not silently alter core mechanics for a localized edition.
- Verify destination-specific factual claims when relevant, record sources and dates checked, and provide practical alternatives for seasonal closures, accessibility, or infrastructure differences. Avoid stereotypes and single-site dependencies where possible.

## Print and visual standards

Use the official title **Procedural Tourism: A Cooperative Travel Game**. Preserve the minimalist, white-background, toner-friendly card design and existing deck colors:

| Deck | Color |
| --- | --- |
| Quest | Forest green `#285F4B` |
| Condition | Slate blue `#355B82` |
| Curse | Plum purple `#714D7E` |

Maintain distinct deck icons, labeled backs, and readable canonical identifiers. Do not rely solely on color to distinguish decks.

- Finished card size: 2.5 × 3.5 inches, portrait.
- Home print target: Avery 95272, US Letter portrait, six cards per sheet, alternating front/back PDF pages, long-edge duplex, 100% scale.
- Preserve existing sheet geometry unless corrected using a verified template or physical alignment test. Do not claim exact perforation alignment is verified without evidence.
- Professional production target: poker-size cards, 0.125-inch bleed and safe margin as a starting point, 300 DPI for raster artwork. Check actual manufacturer specifications before export.
- Prefer vector text and artwork, embedded fonts, legible text, and consistent layouts. Check the longest cards for clipping and avoid reducing text to unreadable sizes.
- The core decks require 10 Quest sheets, 7 Condition sheets, and 9 Curse sheets (26 sheets, 52 PDF pages total). Keep unused positions on partial sheets correctly paired on backs.
- The rulebook uses US Letter paper and the same visual palette.

## Change workflow and validation

1. Inspect the current files and identify which rules, source cards, and derived assets are affected. Keep changes focused on the requested scope.
2. Modify Markdown sources first. For rule changes, reconcile the Game Design Document, Player Rulebook, relevant deck references, and affected cards. Flag conflicts rather than silently choosing a new rule.
3. Update document versions and revision history where appropriate. Preserve IDs, unchanged card text, and established naming conventions.
4. Regenerate affected PDFs from the authoritative content when possible. If no generator exists, document the method used; do not invent commands or claim assets were regenerated without doing so.
5. Validate card counts, registered categories, canonical ID uniqueness (count actual card definitions rather than references), mechanical type totals, duration and scope fields, and references to other cards. Check for stale 24-hour or failure-triggered curse rules.
6. Test representative and adversarial combinations: overlapping resource restrictions, reciprocal dependencies, transport and timing constraints, evidence requirements, beneficial conditions, and accessibility exemptions. Avoid deadlocks and excessive cumulative effort.
7. For changed PDFs, verify page dimensions, counts, duplex pairing, complete card text, and visual rendering, especially dense cards and partial sheets. Distinguish software validation from physical print testing and field playtesting.
8. Check relative links, summarize changes and validation performed, and explicitly identify unresolved issues or tests not run.

## Repository and release boundaries

- Do not publish the repository, create a public release, choose a license, add a LICENSE file, or grant distribution rights without explicit maintainer approval. Licensing is undecided.
- Do not introduce commercial branding, scoring, mandatory decks, or new game mechanics as incidental changes.
- Avoid unnecessary dependencies and broad file reorganizations. If adding generation tooling, document reproducible commands and dependencies and keep source content separate from derived output.
- Do not invent playtest results, release status, or verification claims. Preserve existing work and avoid destructive operations unrelated to the task.
