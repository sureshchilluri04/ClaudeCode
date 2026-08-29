# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-module Android app (`app`) built with Kotlin and Jetpack Compose, currently at the stock
Android Studio "Empty Activity" template stage: `MainActivity.kt` hosts one `Greeting` composable
inside a `Scaffold`. `namespace`/`applicationId` is `com.example.claudecode`.

## Commands

Run all commands from the repo root using the Gradle wrapper.

- Build debug APK: `./gradlew assembleDebug`
- Build release APK: `./gradlew assembleRelease`
- Run unit tests (JVM, `app/src/test`): `./gradlew testDebugUnitTest`
- Run a single unit test: `./gradlew testDebugUnitTest --tests "com.example.claudecode.ExampleUnitTest.methodName"`
- Run instrumented tests (`app/src/androidTest`, requires a connected device/emulator): `./gradlew connectedDebugAndroidTest`
- Lint: `./gradlew lint`
- Clean: `./gradlew clean`

## Architecture notes

- `compileSdk`/`targetSdk`/`minSdk` are all 36; Java/Kotlin target compatibility is 11.
- The version catalog (`gradle/libs.versions.toml`) already declares dependencies not yet wired
  into `app/build.gradle.kts` — Navigation Compose, kotlinx-serialization, and DataStore
  Preferences. These are present for future use; add the corresponding `implementation(...)`
  lines and apply the `jetbrains-kotlin-serialization` plugin when actually introducing that
  functionality.
- Compose BOM version is pinned in the catalog (`composeBom`); use `libs.androidx.compose.bom`
  rather than pinning individual Compose library versions.
- Theming lives in `app/src/main/java/com/example/claudecode/ui/theme/` (`Color.kt`, `Theme.kt`,
  `Type.kt`) following the standard generated Material3 theme structure.
- Implement unit tests cases for every source code implementation. 
