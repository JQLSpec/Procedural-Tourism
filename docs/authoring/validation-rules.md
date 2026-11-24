# Validation Rules

Validate all sets together before a release or mixed-deck playtest.

- Match every card ID against `^[A-Z][A-Z0-9]*-[QCU]-[A-Z]{2}-[0-9]{2,}$`.
- Confirm that each namespace is registered in [`sets/registry.md`](../../sets/registry.md).
- Confirm that deck and category codes are valid for the card's deck.
- Confirm that IDs are unique and numbers are positive.
- Preserve retired IDs and never recycle or renumber them.
- Count card definitions, not references or examples in design documentation.
- Check required schema fields, scope, duration and compatibility notes.
- Check cross-set interactions before producing mixed-deck assets.

Derived PDFs should be checked for page dimensions, page counts, card text, duplex pairing and readable dense cards. Physical print alignment and field playtesting remain separate checks.
