# Copilot instructions

## Build, test, and lint

- The app is a standalone `index.html`; open it directly in a browser to run it.
- No build, lint, or automated test commands are configured. There is no test runner or single-test command.
- Test every app change in the integrated browser before finishing; check affected behavior, including score/progress and results when relevant.

## Architecture

- The quiz is intentionally self-contained in `index.html`: markup, CSS, question data, and browser-side JavaScript all live in that file. There is no server or dependency setup.
- The `questions` array is the source of truth for quiz content. Each entry contains a topic, question, four answers, the zero-based correct-answer index, and an explanatory fact.
- Quiz state (`currentQuestion`, `score`, and `answered`) is managed in the inline script. `renderQuestion`, `selectAnswer`, `showResults`, and `restart` drive the question, feedback, results, and replay views.
- The initial quiz markup is in the document; the results and replay flows update the quiz card and rebind its controls. Keep element references in sync when changing that generated markup.

## Project conventions

- Keep all app code in the single `index.html`; it must remain dependency-free and directly runnable as a local file.
- Use clear camelCase names and modern JavaScript (`const`, `let`, and arrow functions; never `var`).
- Make small, focused changes; do not modify unrelated code. Add short comments only for non-obvious logic.
- Keep the app responsive on mobile and accessible with keyboard controls, visible focus, and sufficient contrast.
- Define visual tokens as CSS custom properties on `:root`, and provide dark-theme overrides with `prefers-color-scheme: dark`.
- Honor `prefers-reduced-motion` for animation and transitions.
- Use native `button` controls for answers and actions, and maintain the progress bar's accessible label and `aria-valuenow` as questions advance.
- Keep question content in the `questions` array rather than duplicating it in the markup or quiz logic.
