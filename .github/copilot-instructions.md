# Copilot instructions

## Build, test, and lint

- Run the standalone app by opening `index.html` directly in a browser.
- No build, lint, or automated test commands are configured. Test each app change in the integrated browser; for quiz-flow changes, check feedback, score, progress, results, and restart as relevant.

## Architecture

- Keep the app in the single, dependency-free `index.html`; its markup, CSS, question data, and JavaScript run locally without a server.
- The `questions` array is the source for each question, four answers, the zero-based correct-answer index, and its feedback fact. Quiz state is managed by `renderQuestion`, `selectAnswer`, `showResults`, and `restart`.
- Results and replay replace quiz-card markup and rebind controls. Keep element references and event handlers aligned with generated markup.

## Conventions

- Keep changes small and focused; do not modify unrelated code. Use clear camelCase names, `const`/`let`, and arrow functions; never use `var`. Comment only non-obvious logic.
- Keep the quiz responsive and accessible: use native buttons, preserve visible keyboard focus and sufficient contrast, and update the progress bar's accessible value as questions advance.
- Define visual tokens on `:root`; preserve dark-mode overrides via `prefers-color-scheme: dark` and honor `prefers-reduced-motion`.
