# Copilot Instructions for Space Quiz

## Architecture & Overview
- **Zero-Dependency Single-File App**: The entire application lives inside `index.html` (markup, styles, data, and scripts). There is no build pipeline, bundler, server runtime, or external package dependency.
- **State Management**: Simple vanilla JS state machine tracked with variables `currentQuestionIndex`, `score`, and `hasAnswered`. Two primary container screens (`#quiz-view` and `#results-view`) are toggled via inline style visibility.
- **Data Model**: Questions are declared in the in-memory array `quizData` with the structure:
  ```js
  {
    question: string,
    options: string[], // 4 items (A-D)
    answer: number,    // 0-3 index corresponding to options
    fact: string       // Educational takeaway revealed upon answer
  }
  ```
- **Feedback & Visual FX**:
  - CSS custom properties handle colors and support dark/light modes via `@media (prefers-color-scheme: light)`.
  - Wrong answers trigger a CSS keyframe shake animation (`shake`); correct answers trigger emerald glowing animations (`popIn`).
  - Score updates trigger a pulse badge animation (`scoreBump`).
  - Correct answers and high results trigger a canvas-based particle confetti system (`#confetti-canvas`).

## Development & Testing Workflow
- **Preview / Execution**: Open `index.html` directly in a browser or local previewer (e.g., `file:///path/to/space-quiz/index.html` or Python's `python3 -m http.server 8000`).
- **Headless / Browser Testing**: Testable directly via DOM automation or headless browser tools (such as Playwright or Puppeteer) by evaluating keyboard events and element states.

## Key Conventions & UX Patterns
- **Keyboard-First Accessibility**:
  - Options use roving `tabIndex` (active is `0`, siblings are `-1`) and support `ArrowUp`, `ArrowDown`, `ArrowLeft`, and `ArrowRight`.
  - Hotkeys `A`–`D` or `1`–`4` instantly select the corresponding option while an answer is pending.
  - Buttons (`.option-btn`, `.action-btn`) use high-contrast `:focus-visible` / `:focus` rings.
  - Advancing (`handleNext()`) and restarting (`initQuiz()`) bind to `Enter` and `Space`. When an interactive button currently has DOM focus, native button activation handles the event without double-firing.
- **Single-File Discipline**: Keep additional features, assets, and styling self-contained inside `index.html` unless a build system is explicitly requested. Avoid external CDN dependencies for offline resilience.
- **Theme Synchronization**: Any new UI elements must define corresponding color tokens in both dark `:root` and light `@media (prefers-color-scheme: light)` rule blocks.
