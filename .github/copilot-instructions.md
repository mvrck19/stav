# Copilot Instructions for stav

This project is a browser-based Greek language quiz app focused on grammar and syntax, using only static assets (HTML, CSS, SVG, JSON, JS inlined in HTML). There is no build system or backend.

## Project Structure
- `index.html`: Main app logic, UI, and all JavaScript. Handles category selection, question/answer flow, SVG integration, and high score logic.
- `questions.json`: Contains all quiz categories and questions. Each category has an `id`, `title`, `description`, and a list of questions with choices, correct answer, and explanation.
- `styles.css`: All styling for the app, including mobile optimizations and 3D card effects.
- `*_q.svg` / `*_a.svg`: SVGs for question/answer cards, swapped based on category. SVGs embed HTML via `<foreignObject>` for dynamic content.
- No build, test, or deployment scripts. All files are static and loaded directly by the browser.

## Key Patterns & Conventions
- **SVG Integration**: The app dynamically updates embedded SVGs using JavaScript. SVGs must contain a `<foreignObject>` with HTML elements (e.g., `#question-text`, `#choices-area`, `#submit-btn`). See `updateQuestionInSVG` and `updateAnswerInSVG` in `index.html` for required structure.
- **Category/Question Model**: All quiz data is in `questions.json`. To add or edit questions, update this file. Each question must have `id`, `question`, `choices`, `correctIndex`, and `explanation`.
- **High Score Persistence**: High scores are stored in `localStorage` under `quizHighScores`.
- **No Frameworks**: All logic is vanilla JS in `<script>` tags in `index.html`. No external dependencies.
- **Mobile Support**: CSS includes responsive rules for mobile. Test UI changes on small screens.
- **No State Persistence**: Quiz state resets on reload; only high scores persist.

## Developer Workflows
- **Edit/Add Questions**: Update `questions.json` (structure is flat, no references).
- **SVG Changes**: Ensure SVGs have the required HTML structure for dynamic updates. Test with both categories.
- **Styling**: Edit `styles.css`. Use CSS variables for color and spacing.
- **Debugging**: Use browser dev tools. No custom debug commands.
- **Testing**: Manual only. Open `index.html` in a browser.

## Examples
- To add a new category: Add an object to `categories` in `questions.json` and provide matching SVGs if needed.
- To add a new question: Add to the `questions` array of the relevant category in `questions.json`.
- To update SVG UI: Edit the relevant SVG file and ensure required IDs/classes are present for JS hooks.

## Limitations
- No automated tests or CI.
- No package manager, build, or deployment scripts.
- All logic is in a single HTML file; keep changes modular and well-commented.

---
For more, see the main logic in `index.html` and quiz data in `questions.json`.