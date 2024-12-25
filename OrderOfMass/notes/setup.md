# SwiftUI Dark-Mode “Order of Mass” App

Below is a minimal SwiftUI code snippet for a single-page iOS app that:

1. Displays the **Order of Mass** in an expandable list view.  
2. Lets users tap a prayer or section to expand/collapse content.  
3. Includes navigation to separate **Flashcard** and **Quiz** modes.  
4. Uses a **dark background** with off-white text.  
5. Demonstrates how you might integrate a custom “Claude” font (placeholder).

**Note:** In a real project, you’d import/declare your custom font in `Info.plist` and your asset catalog.

```swift
import SwiftUI

// MARK: - Simple Data Models
struct MassSection: Identifiable {
    let id = UUID()
    let title: String
    let content: String
}

// Example Data
let sampleSections: [MassSection] = [
    MassSection(title: "Introductory Rites", content: "In the name of the Father, and of the Son..."),
    MassSection(title: "Liturgy of the Word", content: "First Reading, Responsorial Psalm, Second Reading, Gospel..."),
    MassSection(title: "Liturgy of the Eucharist", content: "Preparation of the Gifts, Eucharistic Prayer, Communion Rite..."),
    MassSection(title: "Concluding Rites", content: "Final Blessing, Dismissal...")
]

// MARK: - Main App
@main
struct DarkMassApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
                // Force dark mode for demonstration
                .preferredColorScheme(.dark)
        }
    }
}

// MARK: - ContentView
struct ContentView: View {
    var body: some View {
        NavigationView {
            ZStack {
                // Dark background
                Color.black.ignoresSafeArea()
                
                VStack {
                    // Header
                    Text("Order of Mass")
                        .font(.custom("Claude", size: 24)) // Example custom font
                        .foregroundColor(.white)
                        .padding(.top, 20)
                    
                    // Expandable List
                    ScrollView {
                        VStack(spacing: 10) {
                            ForEach(sampleSections) { section in
                                ExpandableMassSection(section: section)
                            }
                        }
                        .padding()
                    }
                    
                    // Navigation Buttons
                    HStack(spacing: 20) {
                        NavigationLink(destination: FlashcardView()) {
                            Text("Flashcards")
                                .font(.custom("Claude", size: 18))
                                .foregroundColor(.black)
                                .padding()
                                .background(Color.white)
                                .cornerRadius(8)
                        }
                        
                        NavigationLink(destination: QuizView()) {
                            Text("Quiz Mode")
                                .font(.custom("Claude", size: 18))
                                .foregroundColor(.black)
                                .padding()
                                .background(Color.white)
                                .cornerRadius(8)
                        }
                    }
                    .padding(.bottom, 20)
                }
            }
            .navigationBarHidden(true)
        }
    }
}

// MARK: - Expandable Section
struct ExpandableMassSection: View {
    let section: MassSection
    @State private var isExpanded: Bool = false
    
    var body: some View {
        VStack(alignment: .leading) {
            Button(action: {
                withAnimation {
                    isExpanded.toggle()
                }
            }) {
                HStack {
                    Text(section.title)
                        .font(.custom("Claude", size: 20))
                        .foregroundColor(.white)
                    Spacer()
                    Image(systemName: isExpanded ? "chevron.up" : "chevron.down")
                        .foregroundColor(.gray)
                }
            }
            .padding(.vertical, 5)
            
            if isExpanded {
                Text(section.content)
                    .font(.custom("Claude", size: 16))
                    .foregroundColor(.white.opacity(0.8))
                    .padding(.leading, 8)
                    .transition(.slide)
            }
        }
        .padding(.horizontal, 10)
        .background(Color.gray.opacity(0.2))
        .cornerRadius(8)
    }
}

// MARK: - FlashcardView
struct FlashcardView: View {
    var body: some View {
        ZStack {
            Color.black.ignoresSafeArea()
            Text("Flashcard Mode")
                .font(.custom("Claude", size: 24))
                .foregroundColor(.white)
        }
        .navigationTitle("Flashcards")
        .navigationBarTitleDisplayMode(.inline)
    }
}

// MARK: - QuizView
struct QuizView: View {
    var body: some View {
        ZStack {
            Color.black.ignoresSafeArea()
            Text("Quiz Mode")
                .font(.custom("Claude", size: 24))
                .foregroundColor(.white)
        }
        .navigationTitle("Quiz")
        .navigationBarTitleDisplayMode(.inline)
    }
}
