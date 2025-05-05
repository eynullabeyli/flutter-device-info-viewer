# 📱 Flutter Device Info Viewer

A lightweight Flutter utility that retrieves safe and cross-platform device information using the [`device_info_plus`](https://pub.dev/packages/device_info_plus) plugin.

This tool helps you fetch and print basic device metadata such as model, brand, OS version, and whether it's a physical device — all safely accessible on both Android and iOS.

---

## ✨ Features

- ✅ Safe device info (no restricted permissions)
- ✅ Android and iOS support
- ✅ Uses `device_info_plus`
- ✅ Prints basic info to console (can be extended to UI)

---

## 🧪 Example Output

```text
Model: SM-A515F
Brand: Samsung
Device: a51
OS Version: Android 12
Is Physical: true
```

---

## 🔧 Installation

Add the dependency in your `pubspec.yaml`:

```yaml
dependencies:
  device_info_plus: ^9.0.3
```

Run:

```bash
flutter pub get
```

---

## 🚀 Usage

```dart
import 'package:device_info_plus/device_info_plus.dart';
import 'dart:io';

Future<void> printDeviceInfo() async {
  final deviceInfo = DeviceInfoPlugin();

  if (Platform.isAndroid) {
    final info = await deviceInfo.androidInfo;
    print("Model: ${info.model}");
    print("Brand: ${info.brand}");
    print("Device: ${info.device}");
    print("OS Version: ${info.version.release}");
    print("Is Physical: ${info.isPhysicalDevice}");
  } else if (Platform.isIOS) {
    final info = await deviceInfo.iosInfo;
    print("Model: ${info.model}");
    print("Name: ${info.name}");
    print("System Version: ${info.systemVersion}");
    print("Vendor ID: ${info.identifierForVendor}");
    print("Is Physical: ${info.isPhysicalDevice}");
  }
}
```

---

## 📋 Cross-Platform Device Info Reference

| Property           | Android Equivalent              | iOS Equivalent               | Description                                                          |
|--------------------|----------------------------------|-------------------------------|----------------------------------------------------------------------|
| `isPhysicalDevice` | `androidInfo.isPhysicalDevice`   | `iosInfo.isPhysicalDevice`    | Whether the device is a real one or emulator/simulator              |
| `model`            | `androidInfo.model`              | `iosInfo.model`               | Device model name (e.g., SM-A515F or iPhone13,4)                    |
| `brand`            | `androidInfo.brand`              | *Not available on iOS*        | Manufacturer brand (e.g., Samsung)                                  |
| `device`           | `androidInfo.device`             | `iosInfo.name`                | Device identifier name                                              |
| `systemVersion`    | `androidInfo.version.release`    | `iosInfo.systemVersion`       | OS version (e.g., Android 12 / iOS 16)                              |
| `identifier`       | *Not reliable*                   | `iosInfo.identifierForVendor` | Unique app installation ID (iOS only)                               |
| `product`          | `androidInfo.product`            | *Not available*               | Name of the product (Android only)                                  |
| `manufacturer`     | `androidInfo.manufacturer`       | *Not available*               | Manufacturer name (Android only)                                    |

---
