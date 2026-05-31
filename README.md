# getxtra_storage

[![pub package](https://img.shields.io/pub/v/getxtra_storage.svg)](https://pub.dev)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

A fast, lightweight, synchronous key-value storage solution for Flutter and Dart applications, built for the **GetXtra ecosystem**.

`getxtra_storage` is the community-maintained continuation of the original `get_storage` package, modernized for current Flutter and Dart releases, enhanced Web/WASM compatibility, and future AI-assisted application development.

It preserves the familiar GetStorage API while replacing legacy GetX dependencies with **GetXtra** and incorporating modern platform support improvements.

---

## Why getxtra_storage?

The original GetStorage became one of the most widely used lightweight storage solutions in the Flutter ecosystem because of its simplicity:

```dart
box.write('username', 'tabitha');
print(box.read('username'));
```

No database.
No schema.
No migrations.
Just fast in-memory storage with persistent disk backup.

`getxtra_storage` continues that philosophy while adding:

* ✅ GetXtra compatibility
* ✅ Modern Dart and Flutter support
* ✅ WebAssembly (WASM) compatibility
* ✅ Cross-platform storage implementations
* ✅ Backward-compatible GetStorage APIs
* ✅ Community-driven maintenance
* ✅ AI-first ecosystem alignment

---

## Features

### Fast Memory Access

Values are written immediately to memory and become available synchronously:

```dart
box.write('theme', 'dark');
final theme = box.read('theme');
```

### Persistent Storage

Changes are automatically persisted to the platform storage backend.

### Multiple Containers

Create isolated storage areas:

```dart
final userBox = GetStorage('user');
final cacheBox = GetStorage('cache');
```

### Reactive Listeners

Listen to storage changes:

```dart
box.listen(() {
  print('Storage changed');
});
```

Or listen to a specific key:

```dart
box.listenKey('username', (value) {
  print('Username updated: $value');
});
```

### Web & WASM Ready

Supports Flutter Web and modern WebAssembly compilation targets:

```bash
flutter build web --release --wasm
```

### AI-Friendly Architecture

Designed to integrate naturally into:

* AI-generated Flutter applications
* Agentic development workflows
* Code generation systems
* Runtime configuration platforms
* The Tabitha and GetXtra ecosystems

---

# Installation

Add the package to your `pubspec.yaml`:

```yaml
dependencies:
  getxtra_storage:
```

Then run:

```bash
flutter pub get
```

---

# Import

```dart
import 'package:getxtra_storage/getxtra_storage.dart';
```

---

# Initialization

Initialize storage before using it:

```dart
Future<void> main() async {
  await GetStorage.init();

  runApp(const MyApp());
}
```

---

# Basic Usage

Create a storage instance:

```dart
final box = GetStorage();
```

Write a value:

```dart
await box.write('quote', 'GetXtra is awesome');
```

Read a value:

```dart
final quote = box.read<String>('quote');
```

Remove a value:

```dart
await box.remove('quote');
```

Erase an entire container:

```dart
await box.erase();
```

Check if data exists:

```dart
if (box.hasData('quote')) {
  print('Found quote');
}
```

---

# Multiple Containers

```dart
await GetStorage.init('settings');

final settings = GetStorage('settings');

await settings.write('theme', 'dark');
```

---

# ReadWriteValue Helper

```dart
class Preferences {
  final username = ''.val('username');
  final age = 0.val('age');
}
```

Usage:

```dart
final prefs = Preferences();

prefs.username.val = 'Tabitha';

print(prefs.username.val);
```

---

# Supported Platforms

| Platform | Supported |
| -------- | --------- |
| Android  | ✅         |
| iOS      | ✅         |
| macOS    | ✅         |
| Windows  | ✅         |
| Linux    | ✅         |
| Web      | ✅         |
| WASM     | ✅         |

---

# What getxtra_storage Is

A lightweight persistent storage layer that combines:

* Fast in-memory access
* Persistent platform storage
* Simple API surface
* Minimal dependencies
* Reactive change notifications

Perfect for:

* Application settings
* User preferences
* Local caching
* Session data
* Lightweight state persistence

---

# What getxtra_storage Is Not

`getxtra_storage` is not intended to replace a full database.

If your application requires:

* Complex querying
* Relationships
* Indexing
* Large-scale datasets
* Offline-first synchronization

Consider solutions such as:

* Drift
* Isar
* Hive
* SQLite

---

# Migration from get_storage

Most applications can migrate with minimal changes.

### Before

```yaml
dependencies:
  get_storage:
```

```dart
import 'package:get_storage/get_storage.dart';
```

### After

```yaml
dependencies:
  getxtra_storage:
```

```dart
import 'package:getxtra_storage/getxtra_storage.dart';
```

The public API remains intentionally familiar.

---

# Relationship to GetXtra

`getxtra_storage` is the official storage package for the GetXtra ecosystem.

It aims to provide a stable migration path for developers moving from GetX/GetStorage while embracing modern Flutter development practices and future ecosystem improvements.

Learn more:

* GetXtra
* Tabitha
* Fairmount & Charles

---

# Acknowledgements

This package would not exist without the work of the Flutter community members who built and maintained the projects that came before it.

Special thanks to:

### Jonny Borges (jonataslaw)

Creator of the original:

* get_storage
* GetX

### lcw99

Maintainer of:

* get_storage_wasm

whose WebAssembly work helped modernize the storage implementation for future Flutter Web targets.

### Contributors

Thank you to every contributor, tester, maintainer, issue reporter, and community member who helped evolve these projects over the years.

---

# License

MIT License.

Please retain all applicable copyright notices and attribution from upstream projects.
