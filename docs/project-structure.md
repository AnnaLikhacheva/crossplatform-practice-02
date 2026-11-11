# Задание 3. Структура кросс-платформенного проекта

Проект: официальный пример `platform_channels` из репозитория
[flutter/samples](https://github.com/flutter/samples/tree/main/platform_channels)
(скачан командой `git clone --depth 1 --filter=blob:none --sparse` + `git sparse-checkout set platform_channels`).

| Каталог / файл | Назначение | Общий / платформенный |
|---|---|---|
| `lib/` (`main.dart`, `lib/src/*.dart`) | UI и логика приложения на Dart, вызовы каналов платформы | Общий |
| `assets/` | Изображения, используемые приложением | Общий |
| `test/` | Виджет-тесты на Dart | Общий |
| `pubspec.yaml` | Манифест Flutter: SDK, зависимости (`go_router`), ресурсы | Общий (конфигурация) |
| `analysis_options.yaml` | Правила статического анализа Dart | Общий (конфигурация) |
| `android/` | Нативный проект Android (Gradle) | Платформенный |
| `android/app/src/main/kotlin/.../MainActivity.kt` | Обработчики MethodChannel / EventChannel / BasicMessageChannel на Kotlin | Платформенный |
| `android/app/src/main/kotlin/.../AccelerometerStreamHandler.kt` | Поток данных акселерометра (`SensorManager`) | Платформенный |
| `android/build.gradle`, `android/app/build.gradle`, `settings.gradle` | Сборка APK/AAB под Android | Платформенный (сборка) |
| `ios/` (`Runner.xcodeproj`, `Runner.xcworkspace`) | Нативный проект iOS (Xcode) | Платформенный |
| `ios/Runner/AppDelegate.swift` | Обработчики каналов на Swift | Платформенный |
| `ios/Runner/AccelerometerStreamHandler.swift` | Поток акселерометра (`CMMotionManager`) | Платформенный |

Платформозависимые места в общем коде: `MethodChannel('methodChannelDemo')`
(`lib/src/counter_method_channel.dart`), `EventChannel('eventChannelDemo')`
(`lib/src/accelerometer_event_channel.dart`), `BasicMessageChannel`
(`lib/src/pet_list_message_channel.dart`, `lib/src/platform_image_demo.dart`).

Доля общего кода: Dart — 701 строка, нативный Kotlin + Swift — 277 строк → ≈ 72 % общего кода.
