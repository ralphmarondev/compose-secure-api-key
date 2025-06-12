# 🔐 Compose Secure Api Key

**Compose Secure Api Key** is a simple Android project demonstrating how to securely inject and
manage API keys using **Jetpack Compose Material 3** and the `local.properties` file. It follows a
modern Android setup with **Kotlin**, Gradle 8+, and `buildConfigField` for runtime access to
secrets—without exposing them in version control.

![License](https://img.shields.io/badge/license-MIT-purple)
![Platform](https://img.shields.io/badge/platform-Android-pink)
![UI](https://img.shields.io/badge/UI-Compose%20Material3-purple)
![Kotlin](https://img.shields.io/badge/kotlin-2.0%2B-7f52ff?logo=kotlin-pink)
![Gradle](https://img.shields.io/badge/gradle-8.0%2B-02303a?logo=gradle)
![Android SDK](https://img.shields.io/badge/minSdk-28-orange)

---

## 🔗 Repository

GitHub: [https://github.com/ralphmarondev/compose-secure-api-key](https://github.com/ralphmarondev/compose-secure-api-key)

---

## ✨ Features

* 🔐 Securely inject API keys using `local.properties`
* 🧪 Use `BuildConfig` to access secrets at runtime
* 💡 Jetpack Compose Material 3 setup
* 🛡️ Keeps API keys out of version control (safely ignored by `.gitignore`)
* ⚙️ Clean and modern Gradle + Kotlin DSL configuration

---

## 🛠️ Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ralphmarondev/compose-secure-api-key.git
cd compose-secure-api-key
````

### 2. Set Up `local.properties`

In the root of your project, edit or create a `local.properties` file:

```
API_KEY=YourSecureKeyHere
```

⚠️ **Do not add quotes.** The build script will wrap it properly for `BuildConfig`.

> Example:
>
> ```properties
> API_KEY=Hello
> ```

### 3. Open in Android Studio

* Open the root project folder
* Wait for Gradle to sync
* Run the app on your connected Android device or emulator

---

## 💬 Usage in Code

```kotlin
val apiKey = BuildConfig.API_KEY
```

This allows you to securely use your API key anywhere in your Compose app without hardcoding it in
source files.

---

## 🧩 Gradle Setup Snippet

To make this work, you'll need to load the API key from `local.properties` and pass it to
`BuildConfig`.
Add the following inside the `defaultConfig` block of your `build.gradle.kts` file:

```kotlin
val localProperties = java.util.Properties()
val localPropertiesFile = project.rootProject.file("local.properties")
if (localPropertiesFile.exists()) {
    localProperties.load(localPropertiesFile.inputStream())
}

buildConfigField("String", "API_KEY", "\"${localProperties.getProperty("API_KEY")}\"")
```

This reads the `API_KEY` from your local machine and injects it into the generated
`BuildConfig.java`, allowing safe access from your Kotlin code via:

```kotlin
val apiKey = BuildConfig.API_KEY
```

✅ **Bonus**: You can define multiple keys the same way:

```kotlin
buildConfigField("String", "API_KEY_ONE", "\"${localProperties.getProperty("API_KEY_ONE")}\"")
buildConfigField("String", "API_KEY_TWO", "\"${localProperties.getProperty("API_KEY_TWO")}\"")
```

---

## 📄 License

This project is licensed under the **MIT License**.
See the [LICENSE](LICENSE.txt) file for full details.

---

## 👤 Author

**Ralph Maron Eda**
GitHub: [@ralphmarondev](https://github.com/ralphmarondev)

---

## 🤝 Contributing

Suggestions, feedback, and contributions are welcome!
Feel free to fork the project or open a pull request.

---

⭐ If you found this helpful, consider starring the repo!
