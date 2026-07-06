# 🌙 AllNighter

**Exam tomorrow? You'll be fine.**

AllNighter is a [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that turns your lecture slides, PDFs, textbook chapters — even photos of slides — into clean, exam-ready study guides. Then quizzes you on them.

## What it does

Upload your material, ask for a summary, and get:

- 📄 **A structured study guide** (Word doc) — color-highlighted key terms, comparison tables, a glossary, and "this will be on the exam" callouts (only when your material actually signals it)
- 🃏 **Flashcards** — interactive in-chat, or exported for Anki
- ✍️ **Practice tests** — easy to exam-level difficulty, with a separate answer key and grounded wrong-answers (no random distractors)
- ⚡ **Cheat sheets** — one page, maximum density, for the final hour

Works in **any language** — the output matches your material's language automatically (tested with Lithuanian and English). Handles multiple lecture files at once, merging them into one organized guide.

It never invents facts: everything in the output traces back to the material you gave it.

## Install

1. Download [`allnighter.skill`](./allnighter.skill)
2. In Claude.ai: **Settings → Capabilities → Skills** → upload the file (or open the file card in a chat and hit **Save skill**)
3. For Claude Code: copy the `allnighter/` folder into your skills directory (e.g. `~/.claude/skills/`)

## Use

Just talk naturally:

> *"Summarize these slides for my exam"*
> *"Padaryk konspektą iš šitų skaidrių"*
> *"Make a cheat sheet from this chapter"*
> *"Quiz me on this — exam level"*

After each study guide, you get tappable options: **Flashcards · Practice test · Cheat sheet**.

## Repo structure

```
allnighter/
├── SKILL.md                 # core skill (loaded when triggered)
└── references/
    ├── flashcards.md        # loaded only when flashcards are requested
    └── tests.md             # loaded only when a test is requested
```

The split keeps token usage low — details load only when actually needed (progressive disclosure).

## Contributing

Issues and PRs welcome. Keep `SKILL.md` lean; put feature detail in `references/`.

## License

MIT — see [LICENSE](./LICENSE).
