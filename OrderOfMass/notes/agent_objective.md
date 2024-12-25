# agent_objective.md

## Objective Overview
Create a sleek iOS (SwiftUI) app with a dark-mode interface, off-white text, and a custom “Claude” font style. The app focuses on:

1. Displaying the **Order of Mass** content in an expandable layout.
2. Providing **Flashcard** and **Quiz** modes for rapid memorization.
3. Tracking user progress toward memorizing prayers in under a week (with potential expansion for voice recognition/audio).

## Features Breakdown
- **One-Page Style** with minimal navigation – large, clear sections.
- **Expandable Sections** for the Order of Mass (title + hidden text that slides down).
- **Flashcard** mode to drill partial or full prayers.
- **Quiz** mode with multiple choice or fill-in-the-blank.
- **Dark Theme** with off-white text and a distinctive typeface.
- (Later) Option for **audio playback** and speaking practice.

## Constraints
- SwiftUI approach (iOS 14+ or 15+).
- Minimal overhead, local data storage for textual content (no heavy backend).
- Potential for future expansions: user accounts, remote DB, voice recognition.

## User Goals
1. Quickly identify each section of the Mass from a single page.
2. Tap to see detailed text for each portion.
3. Launch a flashcard session to memorize specific prayers.
4. Quiz themselves on missing words or lines.

## App Scope
- **MVP** is local-only, no server dependencies.
- Later expansions can integrate analytics, user personalization, and more advanced recall tracking.
