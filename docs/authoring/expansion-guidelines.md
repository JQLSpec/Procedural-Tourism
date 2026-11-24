# Expansion Guidelines

Use one directory under `sets/` for each registered namespace. Start with `set.md` and add only the decks supplied by that product.

1. Register the namespace in [`sets/registry.md`](../../sets/registry.md).
2. Document the product model, destination or theme, intended deck mixing and release status in `set.md`.
3. Add deck sources using `quests.md`, `conditions.md` and `curses.md` as applicable.
4. Allocate stable IDs in the form `<SET>-<DECK>-<CATEGORY>-<NUMBER>`.
5. Reuse unchanged CORE cards by their existing `CORE` IDs; do not copy them under a new namespace.
6. Give substantively different destination adaptations new IDs in the new namespace.
7. Record sources, dates checked and fallback options for destination-specific claims.
8. Test interactions with the CORE decks and document intentional category-ratio or rules variations.

Generated PDFs belong under `sets/<SET>/assets/` and are never the source of card rules.
