# Gemini AI – Project Skill File
## RMA (Return Merchandise Authorization) Android App

---

## 🧠 Project Overview

This is an Android application for **Return Merchandise Authorization (RMA) management**. It handles the workflow of logging, tracking, and processing product returns — including creating RMA requests, updating their status, and managing related data.

- **Package:** `com.example.rma`
- **Language:** Kotlin
- **Build system:** Gradle (Kotlin DSL — `build.gradle.kts`)
- **UI framework:** Jetpack Compose (exclusively)
- **Entry point:** `MainActivity.kt`
- **Theme files:** `Color.kt`, `Theme.kt`, `Type.kt`

---

## ✅ What You SHOULD Do

### Language & Code Style
- Write **Kotlin only**. Never suggest or generate Java code.
- Use idiomatic Kotlin: data classes, sealed classes, extension functions, coroutines, `StateFlow`/`Flow`, etc.
- Follow **MVVM (Model-View-ViewModel)** architecture for all features.
    - `ViewModel` handles UI state and business logic.
    - `Repository` abstracts data sources.
    - `UI layer` (Composables) only observes state — no business logic in Composables.

### UI
- Use **Jetpack Compose exclusively** for all UI. Never generate XML layouts, `View`-based widgets, or `Fragment`-based navigation unless explicitly asked.
- Use `Navigation Compose` for screen navigation.
- Follow Material 3 design conventions where applicable.
- Use `Scaffold`, `TopAppBar`, `LazyColumn`, `Card`, etc. from Compose material3.

### Architecture
- Structure code in layers: `ui/`, `viewmodel/`, `repository/`, `model/`, `data/`.
- Use `UiState` sealed classes or data classes to represent screen state.
- Use `viewModelScope` with coroutines for async work.
- Hoist state appropriately — keep Composables stateless where possible.

### RMA Domain Logic
- Understand that RMA entities typically have: an ID, product info, customer info, status (e.g. Pending, Approved, Rejected, In Transit, Resolved), and timestamps.
- When generating models, use `data class` with sensible defaults.
- Status transitions should be handled in the ViewModel or Repository, not in the UI.

### General
- When suggesting file or class names, follow the existing naming convention: PascalCase for classes/files, camelCase for functions/variables.
- Respect the existing theme setup in `Color.kt`, `Theme.kt`, and `Type.kt` — don't redefine theme colors inline.
- Always add meaningful comments to non-obvious code.

---

## ❌ What You MUST NOT Do

### Libraries
- **Do NOT add any third-party dependencies** (e.g. Retrofit, Room, Hilt, Coil, Timber, etc.) without explicitly asking the user first and getting approval.
- If a feature would benefit from a library, **suggest it and explain why**, then wait for confirmation before writing code that depends on it.

### UI
- **Never use XML layouts** (`res/layout/*.xml`), `View`, `Fragment`, or `AppCompatActivity` patterns.
- Do not use the legacy View system: no `RecyclerView`, `TextView`, `LinearLayout`, etc.
- Do not use `DataBinding` or `ViewBinding`.

### Code Style
- Do not write Java code under any circumstances.
- Do not mix Compose and XML UI code.
- Do not put business logic inside Composable functions.
- Do not use `LiveData` — prefer `StateFlow` / `Flow`.

### Architecture
- Do not put data fetching or business logic directly in `MainActivity` or any Composable.
- Do not skip the Repository layer for data access.

---

## 📁 Current Project Structure (Source)

```
app/src/main/
├── AndroidManifest.xml
└── java/com/example/rma/
    ├── MainActivity.kt
    └── ui/
        └── theme/
            ├── Color.kt
            ├── Theme.kt
            └── Type.kt
```

When adding new code, suggest placing files in appropriate new packages, for example:
- `com.example.rma.model` — data models (e.g. `RmaRequest.kt`)
- `com.example.rma.ui.screens` — Composable screens
- `com.example.rma.ui.components` — reusable Composable components
- `com.example.rma.viewmodel` — ViewModels
- `com.example.rma.repository` — Repositories
- `com.example.rma.data` — data sources (local DB, network, etc.)

---

## 🔧 Build & Gradle

- The project uses **Kotlin DSL** (`build.gradle.kts`) — always write Gradle snippets in Kotlin DSL, not Groovy.
- Version catalog is at `gradle/libs.versions.toml` — suggest adding dependencies there rather than hardcoding version strings.
- Target is a standard Android app module under `/app`.

---

## 💬 How to Communicate

- When proposing a solution involving a new library, **always ask first**.
- When multiple approaches exist, briefly explain the trade-offs and recommend one.
- When generating new files, state clearly **where the file should be placed**.
- Keep responses focused — don't rewrite unrelated parts of the codebase unnecessarily.