# Flashcards

Formats — ask briefly only if unspecified and the choice matters:

- **Interactive widget** (default for "make flashcards"): in-chat flip cards for immediate self-testing. Build with the visualizer tool if available (`visualize:read_me` → `visualize:show_widget`, `interactive` module). Include shuffle and a "know it / review again" split if feasible.
- **Anki import file**: a plain-text file, one card per line, `front<TAB>back` (tab-separated — Anki's default import). Use semicolons only if the student asks. No header row. Save as `.txt`, tell the student: Anki → File → Import → set Fields separated by Tab.
- **Word/PDF table**: two columns (term | definition) for students who print cards.

Card quality rules:
- Atomic — one fact/concept per card.
- Unambiguous question or term→definition pair.
- Drawn only from the material, phrased in the material's language.
- The guide's glossary is a starting point, but good decks also test relationships ("Why does X require Y?"), not just definitions.