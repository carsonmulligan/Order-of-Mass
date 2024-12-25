# agent_backend.md

## Backend Approach (For Later Expansion)
- **Local Data**:
  - Currently, content is stored in a static array or a local JSON file.
  - No user authentication or remote DB in MVP.

## Potential Future Backend Stack
1. **Firebase** or **Supabase** for user sign-up, progress tracking.
2. **API** to store user quiz results, flashcard data, audio references.
3. **Push Notifications** for daily reminders to practice.

### Data Model
- **`MassSection`**: `id`, `title`, `content`.
- **`FlashcardItem`**: `id`, `question`, `answer`.
- **`QuizQuestion`**: `id`, `prompt`, `options`, `correctIndex`.

In the MVP, these can be simply arrays. For future expansions, place them in a structured online database (e.g., Firestore) if needed.

```markdown
# agent_flashcard.md

## Flashcard Mode
- **Goal**: Rapid memorization of key prayers or lines.
- **Mechanics**:
  1. Show **prompt** (e.g., partial prayer text, or just the name).
  2. Tap to reveal the full text.
  3. Swipe left/right or use “Next” / “Previous” buttons.
- **Data Source**: Local array (e.g., `[FlashcardItem]`), each with front/back text.

### Possible Enhancements
- **Spaced Repetition**: Track which cards need more review.  
- **Audio**: Play a line, user repeats it, toggles to show correct version.

```markdown
# agent_quiz.md

## Quiz Mode
- **Goal**: Test user recall of specific lines or missing words.
- **Type**:
  1. **Multiple-Choice** – Choose the correct phrase to complete the prayer.
  2. **Fill-in-the-Blank** (later) – Type in missing words.

### Example Flow
1. User sees: “Complete the phrase: ‘Glory to God in the ____.’”
2. Options: `[“highest”, “lowest”, “heavens”, “temple”]`
3. If correct, show “Correct!” in green. If wrong, show “Try again.”

### Future: Progress & Tracking
- Tally correct vs. attempted for a user’s overall progress.  
- Potentially store data locally or in a remote database if expanded.

```markdown
# agent.index.md

## Architectural Index

### 1. Objective
- Found in **agent_objective.md**  
- Explains the main focus, constraints, and user goals.

### 2. Frontend
- Found in **agent_frontend.md**  
- Summarizes SwiftUI approach, color scheme, layout details.

### 3. Backend
- Found in **agent_backend.md**  
- Details future expansions for data storage, user accounts, etc.

### 4. Flashcards
- Found in **agent_flashcard.md**  
- Outlines flashcard design, data structure, potential expansions.

### 5. Quiz
- Found in **agent_quiz.md**  
- Explains quiz design, types of questions, future progress tracking.

**Summary**  
Each file addresses a critical slice of the “Order of Mass” memorization app. They collectively form the blueprint for a streamlined iOS SwiftUI application that can be built and tested incrementally, with future expansions for greater interactivity and personalization.
