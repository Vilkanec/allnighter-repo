---
name: allnighter
description: "Turns provided study material (lecture slides, PDFs, textbook chapters, notes, photos of slides/whiteboards) into clear, structured, exam-ready summaries — what students call a \"konspektas\" or study guide. Use this skill whenever a student uploads or pastes course material and asks to summarize, condense, explain, make notes/konspektas from, or \"make this easier to understand,\" even without the word \"summary.\" Supports quick mode keywords: max, full, quick, sheet (cheat sheet), cards (flashcards), anki, test, exam. Also covers flashcards (incl. Anki export), interactive multiple-choice practice exams (4 options, 1 correct, auto-graded), cheat sheets, and — only on request — a polished Word (.docx) study guide. Trigger for exam prep, revision, or any request to turn dense course material into something study-friendly."
---

# AllNighter

Turn raw study material into a study guide, flashcards, an auto-graded practice exam, or a cheat sheet. Built for the night before the exam. **Fast and cheap by default.**

## The one rule about cost
Default output is **Markdown, shown in chat** (or saved as `.md`). It's cheap, reads fine on a phone, and prints. **Only make a Word (.docx) file when the student explicitly asks** ("Word", "docx", "for printing/handing in"). Word costs many more tokens — never the silent default.

## Workflow

1. **Read the material.** Use the input type's skill (`file-reading` / `pdf-reading` / `pptx`). Prefer text extraction (`pdftotext`, `pandoc`) over rendering pages as images — far cheaper; render visually only for genuine diagrams/scans/handwriting. Photos and pasted text are valid input.
2. **Many files = one course.** Merge overlapping topics, deduplicate, organize by topic (not by file) unless per-lecture is requested. Tag which lecture each section came from.
3. **Match the source language** in the output. Keep terms students are tested on in their original form (an English term in Lithuanian slides stays English).
4. **Pick the mode — hard gate, never generate until it's known.**
   - **Keyword in the message** (case-insensitive, combinable like "quick + cards") → do exactly that, no questions:

     | keyword | produces |
     |---|---|
     | `full` | full study guide |
     | `quick` | key concepts only, ~1 page / 30–40 slides |
     | `sheet` | cheat sheet, 1–2 dense pages |
     | `cards` / `anki` | flashcards / flashcards as Anki file |
     | `test` / `exam` | practice exam, standard / exam-level |
     | `max` | full guide + flashcards + exam + cheat sheet |

   - **No keyword but a format is clearly stated in their words** ("padaryk konspektą", "quiz me", "TL;DR") → treat as that mode.
   - **Neither** (even if material was uploaded) → **ask, don't default.** Show the menu below and wait.
   - **No material** → show the menu, ask them to upload, wait.
5. **Draft as Markdown**, then show it in chat (or save `.md` to `/mnt/user-data/outputs/` + `present_files`). Word only on explicit request → then read `/mnt/skills/public/docx/SKILL.md` and follow it exactly.
6. **Offer next steps** with the same menu (once per guide; drop it if they picked "Done").

## The menu (used both before generating and after)
Use an option/elicitation tool if available; otherwise one short text block. Always spell out what each does:
- **Full guide** — all topics, key terms highlighted, tables, glossary, exam callouts
- **Quick** — key concepts only, ~1 page / 30–40 slides
- **Cheat sheet** — 1–2 dense pages: formulas, definitions, lists
- **Flashcards** — Q&A cards for self-testing (in-chat or Anki file)
- **Practice exam** — multiple choice, 4 options each, 1 correct, auto-graded (standard or exam-level)
- **Max** — all of the above
- **Word file** — output as .docx instead of chat/markdown (costs more, for printing/handing in)
- **Done**

## Length calibration (Full guide)
~30 slides / ~10 pages → ~2–3 guide pages. ~100 slides / full course → ~8–12 pages. If a huge input would balloon (200 slides → 30 pages), summarize section by section or ask for a prioritized subset. Never silently truncate.

## Study-guide content rules
- **Hierarchical**: headings by topic, never a wall of text.
- **Key terms bold** (colored runs too, if Word).
- **Precise definitions** — simplify the explanation around a term, never the term itself.
- **Comparison tables** wherever the material implicitly compares things.
- **Exam callouts** only where the source signals importance (repeated, "svarbu"/"important", lecturer hints) — never fabricated.
- **"Don't confuse" notes** for easily-mixed pairs (2NF vs 3NF, TCP vs UDP).
- **Glossary** at the end: term → one-line definition (also feeds flashcards).
- **Everything traces to the source.** No outside facts unless asked, and then marked "beyond the material."

## Flashcards & exams
Read the reference file **only when that output is requested**:
- Flashcards → `references/flashcards.md`
- Practice exam / quiz / test → `references/tests.md`

## Notes
- Condensing copyrighted/scanned chapters into a transformative study guide is fine — paraphrase, don't reproduce long passages.
- If the material contradicts itself or has errors, flag it briefly rather than silently picking one version.