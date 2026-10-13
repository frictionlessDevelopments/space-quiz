# Cosmic Quest: Space Exploration Quiz

An interactive, responsive, keyboard-accessible trivia web application testing knowledge of human spaceflight, planetary rovers, telescopes, and cosmic discoveries.

Live Website: [https://frictionlessdevelopments.github.io/space-quiz/](https://frictionlessdevelopments.github.io/space-quiz/)

---

## Features

- **Curated Mission Trivia**: 10 space exploration questions with educational facts revealed after each submission.
- **Dynamic Feedback & Visual FX**: Instant visual feedback on answers, shake animations on mistakes, score pulse animations, and particle confetti celebrations.
- **Keyboard-First Accessibility**:
  - `A`–`D` or `1`–`4` hotkeys to select options immediately.
  - Arrow keys (`Up` / `Down` / `Left` / `Right`) to navigate between options using roving `tabIndex`.
  - `Enter` / `Space` to advance to the next mission or restart the quiz.
- **Theme Synchronization**: Automatic dark and light mode adaptation based on system preference (`prefers-color-scheme`).
- **Shareable Mission Debriefing**: Results screen breaking down final score, correct answers, and mistakes, with one-click clipboard sharing.
- **Zero Dependencies**: Lightweight single-file architecture (`index.html`) with no bundlers, package managers, or runtime servers required.

---

## Running Locally

Because the application has zero external dependencies, you can run it locally with any of the following methods:

### Option 1: Direct File Open
Open `index.html` directly in any modern web browser:
- Double-click `index.html` in your file manager, or
- On macOS:
  ```bash
  open index.html
  ```
- On Linux:
  ```bash
  xdg-open index.html
  ```

### Option 2: Python HTTP Server
Run a local static file server using Python 3:
```bash
python3 -m http.server 8000
```
Then navigate to [http://localhost:8000](http://localhost:8000) in your browser.

### Option 3: Node.js `serve` / `npx`
If you have Node.js installed:
```bash
npx serve .
```
Open the provided local URL in your browser.

---

## Deployment

The application is deployed to **GitHub Pages** using GitHub Actions via `.github/workflows/deploy.yml`. Any push to the `main` branch automatically deploys the latest version to GitHub Pages.
