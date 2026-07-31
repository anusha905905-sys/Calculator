# Calculator App

A simple, attractive Material Design calculator for Android, built with **Java** and **XML**.

## Features

- ➕ Addition
- ➖ Subtraction
- ✖️ Multiplication
- ➗ Division (with divide-by-zero protection)
- 🧹 Clear button to reset inputs and result
- ✅ Input validation (empty fields / non-numeric input)
- 🎯 Result displayed with exactly two decimal places (e.g. `12.50`)
- 🎨 Material Design UI with a result card and colour-coded operation buttons

## Tech Stack / Project Configuration

| Item                  | Value                          |
|------------------------|---------------------------------|
| Language               | Java (no Kotlin source code)   |
| UI                      | XML layouts                    |
| Build configuration     | Kotlin DSL (`build.gradle.kts`)|
| Base Activity           | `AppCompatActivity`            |
| Minimum SDK             | API 23 (Android 6.0 Marshmallow)|
| Target / Compile SDK    | API 34                         |
| IDE                     | Android Studio (Hedgehog or later recommended) |

## Project Structure

```
CalculatorApp/
├── build.gradle.kts                     # Root build script (Kotlin DSL)
├── settings.gradle.kts                  # Module/repository settings
├── gradle.properties
├── gradle/wrapper/gradle-wrapper.properties
└── app/
    ├── build.gradle.kts                 # App module build script (Kotlin DSL)
    ├── proguard-rules.pro
    └── src/main/
        ├── AndroidManifest.xml
        ├── java/com/example/calculatorapp/
        │   └── MainActivity.java
        └── res/
            ├── layout/
            │   └── activity_main.xml
            ├── values/
            │   ├── colors.xml
            │   ├── strings.xml
            │   └── themes.xml
            ├── drawable/
            │   ├── bg_edittext.xml
            │   ├── bg_result_card.xml
            │   ├── btn_add.xml
            │   ├── btn_subtract.xml
            │   ├── btn_multiply.xml
            │   ├── btn_divide.xml
            │   ├── btn_clear.xml
            │   └── ic_launcher_foreground.xml
            └── mipmap-anydpi-v26/
                ├── ic_launcher.xml
                └── ic_launcher_round.xml
```

## How to Open the Project in Android Studio

1. Launch **Android Studio**.
2. Select **File → Open** (or **Open** on the welcome screen).
3. Navigate to the `CalculatorApp` folder (the folder containing `settings.gradle.kts`) and select it.
4. Wait for Gradle to sync. Android Studio will automatically download the correct Gradle distribution and the Android Gradle Plugin (`8.2.2`) the first time you sync, provided you have an internet connection.
5. Once the sync finishes, click **Run ▶** (or press `Shift + F10`) with an emulator or physical device (API 23+) selected.

> **Note:** The `gradle-wrapper.jar` binary is not included in this text-based delivery. Android Studio will regenerate it automatically on first sync/open (`File → Sync Project with Gradle Files`), or you can run `gradle wrapper` once from a terminal inside the project if you have Gradle installed locally.

## How It Works

- **`MainActivity.java`** reads the two numbers entered in `etNumber1` / `etNumber2`.
- Input is validated:
  - Both fields must be non-empty.
  - Both fields must contain parseable numeric values.
- Depending on which button is tapped, the corresponding arithmetic operation is performed.
- For division, if the second number is `0`, an error Toast ("Cannot divide by zero") is shown and no crash occurs.
- The result is formatted using `String.format(Locale.US, "%.2f", result)` so it always displays with two decimal places (e.g. `7.00`, `-3.50`).
- The **Clear** button resets both input fields and the result back to `0.00`.

## Validation & Error Handling Summary

| Scenario                        | Behavior                                      |
|----------------------------------|------------------------------------------------|
| Empty input field(s)             | Toast: "Please enter both numbers", result unchanged (reset to `0.00`) |
| Non-numeric input                | Toast: "Please enter valid numbers"           |
| Division by zero                 | Toast: "Cannot divide by zero", no crash      |
| Valid input                      | Result shown with 2 decimal places            |

## Customization Ideas

- Add a decimal-point-aware `InputFilter` to further restrict keyboard input.
- Add haptic feedback on button press.
- Add dark mode color values in `res/values-night/`.
- Add unit tests for the arithmetic logic by extracting it into a separate `Calculator` utility class.

## License

This sample project is provided as-is for educational purposes. Feel free to use and modify it freely.
