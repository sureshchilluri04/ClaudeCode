# ClaudeCode

A single-module Android app built with Kotlin and Jetpack Compose.

## Project Status

Currently at the stock Android Studio "Empty Activity" template stage: `MainActivity.kt` hosts one
`Greeting` composable inside a `Scaffold`.

- **Namespace / Application ID:** `com.example.claudecode`
- **compileSdk / targetSdk / minSdk:** 36
- **Java / Kotlin target compatibility:** 11

## Getting Started

Run all commands from the repo root using the Gradle wrapper.

```bash
# Build debug APK
./gradlew assembleDebug

# Build release APK
./gradlew assembleRelease

# Run unit tests (JVM)
./gradlew testDebugUnitTest

# Run a single unit test
./gradlew testDebugUnitTest --tests "com.example.claudecode.ExampleUnitTest.methodName"

# Run instrumented tests (requires a connected device/emulator)
./gradlew connectedDebugAndroidTest

# Lint
./gradlew lint

# Clean
./gradlew clean
```

## Architecture

- Theming lives in `app/src/main/java/com/example/claudecode/ui/theme/` (`Color.kt`, `Theme.kt`,
  `Type.kt`), following the standard generated Material3 theme structure.
- The version catalog (`gradle/libs.versions.toml`) already declares dependencies not yet wired
  into `app/build.gradle.kts` — Navigation Compose, kotlinx-serialization, and DataStore
  Preferences — for future use.
- Compose BOM version is pinned in the catalog (`composeBom`); library versions come from
  `libs.androidx.compose.bom` rather than being pinned individually.
