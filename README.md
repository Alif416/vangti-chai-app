# Vangti Chai

A lightweight Flutter app that tells you how to break an amount of money into the fewest Bangladeshi Taka (৳) notes. *Vangti chai* (ভাংতি চাই) means "I need change" in Bengali.

Type an amount on the on-screen keypad and the app instantly shows how many notes of each denomination you need.

## Features

- **Instant results**: the breakdown updates on every key press, with no "calculate" button.
- **Greedy note breakdown**: uses the denominations ৳500, ৳100, ৳50, ৳20, ৳10, ৳5, ৳2 and ৳1, largest first.
- **Custom keypad**: a read-only amount field with a 0–9 keypad and a Clear button, so no system keyboard pops up.
- **Responsive layout**: the keypad grid shows 3 or 4 columns depending on screen width.

## Example

| Input | Output |
|-------|--------|
| `1786` | 3 × ৳500, 2 × ৳100, 1 × ৳50, 1 × ৳20, 1 × ৳10, 1 × ৳5, 0 × ৳2, 1 × ৳1 |

## Tech Stack

- [Flutter](https://flutter.dev) (Dart)
- Material Design widgets

## Project Structure

```
vangti-chai-app/
├── main.dart    # App entry point, HomeScreen, calculation logic and UI
└── README.md
```

Key pieces in [main.dart](main.dart):

| Component | Role |
|-----------|------|
| `MyApp` | Root `MaterialApp` |
| `HomeScreen` | Stateful screen holding the input and note counts |
| `_updateCalculation()` | Greedy algorithm that computes the note counts |
| `_buildKeyButton()` | Builds the keypad buttons |

## Getting Started

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install) (stable channel)
- An Android emulator or a physical device with USB debugging enabled

### Run the app

This repository currently contains only the Dart source, not the full Flutter project scaffolding (`pubspec.yaml`, `android/`, and so on). To run it:

```bash
# 1. Create a new Flutter project
flutter create vangti_chai
cd vangti_chai

# 2. Replace the generated entry point with this repo's main.dart
cp /path/to/vangti-chai-app/main.dart lib/main.dart

# 3. Run
flutter run
```

## Known Limitations

- Very large amounts overflow `int` parsing only at extreme lengths, and there is no input length cap.
- The note counts are displayed as a fixed list; the unused `result` string is computed but not shown.
- There is no backspace key, only a full Clear.
- No automated tests yet.

## Roadmap

- Add a backspace button
- Hide denominations with a zero count (or highlight the used ones)
- Add widget and unit tests for the breakdown logic
- Commit the full Flutter project scaffold so the app runs straight after cloning

## Author

Labibul Ahsan Alif
