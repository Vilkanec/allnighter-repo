# Practice exams

Default output = an **interactive auto-graded exam** (multiple choice). File/printable version on request.

## Question format (strict)
- **Every question has exactly 4 options (A–D) and exactly 1 correct answer.**
- The 3 wrong options (distractors) are **plausible-but-wrong from the material itself** — a real term from the material used in the wrong place, a common confusion, an off-by-one/near-miss. Never arbitrary or obviously silly.
- Every question **and** every distractor is grounded in the source material. No outside facts.
- Vary which letter is correct — don't make it C every time.
- One line per question in the answer key explaining **why** the right answer is right (and, when useful, why a tempting distractor is wrong).

## Difficulty
- **Easy** — direct recall, single concept, definition-matching.
- **Standard** (default) — mix of recall and application.
- **Exam-level** — multi-concept, apply-to-scenario, "which is NOT / EXCEPT", compare/contrast.

## How many
Default ~10 questions. Scale to material: ~1 question per 3–5 slides, cap ~25 unless asked for more.

## Interactive exam (default in chat)
Build with the visualizer if available (`visualize:read_me` with `interactive` module → `visualize:show_widget`). Requirements:
- Show one question at a time **or** a scrollable list; the student clicks one option per question.
- **Do not reveal correctness until they hit "Check answers" / "Submit."**
- On submit: show a **score (X / N and %)**, mark each question ✅/❌, reveal the correct option, and show the one-line explanation under each.
- Include a **"Retry wrong ones"** and a **"Restart"** button if feasible. Shuffle option order on restart.
- Keep all questions/answers in a JS data array in the widget — no external calls needed for grading (grading is pure client-side comparison).
- No `localStorage`/`sessionStorage` — hold state in memory only.

Data shape to embed:
```js
const questions = [
  { q: "…", options: ["…","…","…","…"], correct: 2, why: "…" },
  // correct = 0-based index of the right option
];
```

## Printable / file version (on request: "make me a test", Word, PDF, print)
- Questions section first (A–D under each), then a clearly separated **Answer key** at the very end so it doesn't spoil self-testing.
- Answer key lists: question number → correct letter → one-line reason.
- Markdown by default; Word/PDF only if explicitly asked (see the docx/pdf skills then).