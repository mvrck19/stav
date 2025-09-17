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
- **Responsive Layout**: Use CSS Flexbox (or CSS Grid if more appropriate) to create a fully fluid, content-driven layout. Do not use fixed pixel values; use relative units such as %, rem, em, vw/vh, and fr. Avoid media queries and device-specific breakpoints; let components wrap and reflow naturally. Prefer gap for spacing; use flex-grow/shrink/basis or grid minmax() for sizing; add sensible min/max constraints for readability. Avoid absolute positioning unless necessary.

## Responsive Layout Guidelines

- Use Flexbox for layout management to ensure elements stack properly on different screen sizes.
- Utilize CSS variables for spacing and colors to maintain consistency across the application.
- Ensure that all interactive elements, such as buttons, are easily accessible and have sufficient touch targets for mobile users.
- Test the layout on various devices to confirm responsiveness and usability.

## Developer Workflows
- **Edit/Add Questions**: Update `questions.json` (structure is flat, no references).
- **SVG Changes**: Ensure SVGs have the required HTML structure for dynamic updates. Test with both categories.
- **Styling**: Edit `styles.css`. Use CSS variables for color and spacing.
- **Debugging**: Use browser dev tools. No custom debug commands.
- **Testing**: Manual only. Open `index.html` in a browser.

## Testing Guidelines

### Overview
This project does not currently have automated tests. However, manual testing is essential to ensure functionality and usability.

### Manual Testing Steps
1. Open `index.html` in a web browser.
2. Navigate through the quiz categories and select questions.
3. Verify that all questions display correctly and that the choices are selectable.
4. Check that the submit button functions as expected and displays the correct feedback.
5. Test the high score functionality by completing the quiz and checking local storage.
6. Ensure that the layout is responsive on various screen sizes.

### Future Considerations
- Consider implementing automated tests using a framework like Jest or Mocha for unit testing.
- Explore end-to-end testing tools like Cypress for comprehensive testing of user interactions.

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