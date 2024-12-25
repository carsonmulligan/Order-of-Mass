# agent_frontend.md

## Frontend Approach (SwiftUI)
- **Single `ContentView`** with a dark background (`.black` or `.darkGray`).
- **Custom Font** usage, e.g., `Font.custom("Claude", size: 16)`.
- **Expandable Sections** (list or custom `VStack`) for the Mass text.
- **Navigation**: 
  - **Home**: Contains the “Order of Mass” overview.
  - **FlashcardView**: A secondary screen for flashcard practice.
  - **QuizView**: A tertiary screen for short quizzes.

### Dark UI & Typography
- Primary color: `Color.black` background.
- Text color: `Color.white` or `Color(white: 0.9)`.
- Accent color for buttons: `Color.white` backgrounds with black text, or vice versa.

### Layout Components
1. **Header** – Title: “Order of Mass”.
2. **Expandable List** – A vertical stack of sections:
   - Tap on a section title to reveal/hide the content.
3. **Bottom Buttons** – “Flashcards” / “Quiz Mode” as `NavigationLink`s.

## Example SwiftUI Snippet
```swift
struct ContentView: View {
    var body: some View {
        NavigationView {
            ZStack {
                Color.black.edgesIgnoringSafeArea(.all)
                VStack {
                    Text("Order of Mass")
                        .font(.custom("Claude", size: 24))
                        .foregroundColor(.white)
                        .padding()

                    // Expandable list, etc.

                    HStack {
                        NavigationLink(destination: FlashcardView()) {
                            Text("Flashcards")
                        }
                        NavigationLink(destination: QuizView()) {
                            Text("Quiz Mode")
                        }
                    }
                    .padding()
                }
            }
            .navigationBarHidden(true)
        }
    }
}
