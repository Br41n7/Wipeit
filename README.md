# wipeit

_An Android-based self-defense and anti-forensics application._

**wipeit** is an Android application designed to monitor the device for unauthorized extraction attempts and signs of forensic imaging tools (such as Cellebrite UFED). Upon detecting physical, logical, or file-system extraction attempts or exploit staging, **wipeit** automatically initiates defensive measures, such as locking or factory resetting the device.

---

## Features

- **Forensic Extraction Detection:** Detects ADB-based Logical Extractions, File System Extractions, and Physical Extractions.
- **Real-Time Event Monitoring:** Monitors USB events (`ACTION_USB_DEVICE`), package installations, and known exploit staging directories or file hashes on the filesystem.
- **Plausible Deniability:** Supports triggering defensive responses via entry of a configurable plausible deniability password monitored through an AccessibilityService.
- **Automated Response:** Leverages Android's `DeviceAdminReceiver` policy to lock and wipe/factory-reset the device when unauthorized activity or threats are detected.
- **Boot Persistence:** Configured to launch on boot (`RECEIVE_BOOT_COMPLETED`) to ensure continuous background defense.

---

## Prerequisites

- **Java Development Kit (JDK):** JDK 17 or higher
- **Android SDK:**
  - `compileSdk`: 34
  - `minSdk`: 26 (Android 8.0+)
  - `targetSdk`: 34
- **Gradle:** Gradle 8.x

---

## Building & Compilation

You can compile, test, and build the project using Gradle commands from the project root directory.

### Build Commands

- **Build the entire project:**
  ```bash
  gradle build
  ```

- **Compile Debug APK:**
  ```bash
  gradle assembleDebug
  ```
  The generated APK will be located at:
  `app/build/outputs/apk/debug/app-debug.apk`

- **Compile Release APK:**
  ```bash
  gradle assembleRelease
  ```
  The generated APK will be located at:
  `app/build/outputs/apk/release/app-release.apk`

- **Run Unit Tests:**
  ```bash
  gradle test
  ```

- **Clean Build Artifacts:**
  ```bash
  gradle clean
  ```

---

## Installation & Configuration

1. **Build the APK:** Compile the debug or release APK using `gradle assembleDebug`.
2. **Install on Device:**
   ```bash
   adb install app/build/outputs/apk/debug/app-debug.apk
   ```
3. **Grant Device Administrator Privileges:**
   Open the application settings and grant Device Administrator rights to enable automated device lock/wipe functionality upon trigger detection.
4. **Enable Accessibility Service (Optional):**
   Enable the accessibility service in Android Settings if you wish to utilize plausible deniability trigger features.

---

## License

This project is licensed under the [Creative Commons Zero v1.0 Universal](LICENSE) license.
