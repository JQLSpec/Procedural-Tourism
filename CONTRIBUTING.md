# Contributing

Procedural Tourism is a private prototype of a cooperative, print-and-play travel game. Contributions should support memorable discovery, cooperation, accessibility and low-stakes experimentation.

## Before contributing

Read the relevant project documents before changing content:

- [`README.md`](README.md)
- [`AGENTS.md`](AGENTS.md)
- [`docs/game-design-document.md`](docs/game-design-document.md)
- [`docs/player-rulebook.md`](docs/player-rulebook.md)
- [`sets/registry.md`](sets/registry.md)
- [`docs/authoring/card-schema.md`](docs/authoring/card-schema.md)
- [`docs/authoring/expansion-guidelines.md`](docs/authoring/expansion-guidelines.md)

Discuss broad rule changes, new mechanics, new namespaces and major layout changes with the maintainer before implementation.

## Sources of truth

Markdown files are authoritative.

- Shared design rules belong in `docs/game-design-document.md`.
- Player-facing rules belong in `docs/player-rulebook.md`.
- Card text belongs in `sets/<NAMESPACE>/*.md`.
- PDFs under `sets/<NAMESPACE>/assets/` are derived print assets.
- Do not manually edit a PDF as a substitute for updating its source Markdown.

Keep changes focused. Do not create duplicate sources or silently resolve conflicts between the design document, rulebook and card sources.

## Adding or changing cards

1. Identify the intended discovery, decision or interaction.
2. Follow the appropriate card schema.
3. Use clear, observable requirements and plain language.
4. Include effort, scope, duration, exceptions and fallback options where applicable.
5. Check safety, accessibility, consent, privacy, budget and local-law concerns.
6. Test the card against representative cards from all relevant decks.
7. Preserve existing card IDs for copy edits, translations and balance changes that retain the card's identity.
8. Assign a new ID for a substantively different or replacement card.
9. Never recycle retired IDs or renumber existing cards.

Core identifiers use the form:

```text
CORE-Q-EX-01
CORE-C-TR-01
CORE-U-MN-01
```

New sets must be registered in [`sets/registry.md`](sets/registry.md) before IDs are assigned.

## Adding an expansion set

Create a directory under `sets/` using its registered namespace:

```text
sets/JPN/
├── set.md
├── quests.md
├── conditions.md
├── curses.md
└── assets/
    ├── cards/
    ├── rulebook.pdf
    └── templates/
```

A set may contain only the decks required by its product model. Document its intended mixing rules, destination or theme, release status, category rationale and relevant sources in `set.md`.

Unchanged CORE cards retain their `CORE` identifiers. Destination adaptations with changed objectives or effects receive IDs in the new set namespace.

## Design expectations

Preserve these principles:

- Safety, local law, health, accessibility, consent, privacy and essential communication take precedence over card effects.
- Quests should require meaningful effort without becoming exhaustive itineraries.
- Conditions should shape the adventure, not become additional quests.
- Curses should be manageable complications, not punishments.
- Do not require expensive purchases, unwilling strangers, public embarrassment or unsafe conduct.
- Avoid assumptions about mobility, transport, technology, language, diet or alcohol use.
- Do not add scoring, campaign progression or mandatory decks without an explicit design decision.

Destination-specific claims should use reliable sources and include practical alternatives for closures, seasonal changes, access barriers and infrastructure differences.

## Documentation and assets

Update document versions and revision histories when appropriate. Keep relative links valid.

When changing printable content:

- Update the Markdown source first.
- Regenerate affected PDFs when a reproducible generator exists.
- If no generator exists, document the method used.
- Check page dimensions, page counts, duplex pairing, complete text and dense-card readability.
- Do not claim print alignment or field playtesting has been verified without evidence.

## Validation checklist

Before proposing a change, check:

- Card IDs match the canonical format and are unique.
- Namespaces and category codes are registered.
- Required card fields are present.
- Counts and category distributions are intentional.
- Cross-deck interactions do not create deadlocks or excessive effort.
- Accessibility and universal safety exemptions remain intact.
- Relative links resolve.
- `git diff --check` passes.
- Tests, playtesting and PDF checks that were not performed are clearly identified.

## Project boundaries

This project is private prototype work. Do not publish the repository, create a public release, add a license, grant distribution rights or introduce commercial branding without explicit maintainer approval.

Do not include secrets, private traveler information or unverified personal data in cards, tests or documentation.
