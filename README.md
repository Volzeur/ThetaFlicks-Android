# ThetaFlicks-Android

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Platform](https://img.shields.io/badge/Platform-Android-3DDC84.svg)](https://www.android.com/)
[![Built with](https://img.shields.io/badge/Built%20with-Kodular-orange.svg)](https://kodular.io/)

Desktop app for Thetaflicks, built using Kodular.

---

## Features

- WebView-based Android client for the ThetaFlicks streaming service
- Internet connectivity checking with automatic error handling
- Orientation control (landscape/portrait) via URL parameters
- Double-back press to exit functionality
- System UI visibility toggling (immersive mode)
- Offline error page with retry mechanism
- Auto-reload functionality via floating action button

---

## Components

The application uses the following Kodular components:

| Component | Purpose |
|-----------|---------|
| `Web_Viewer1` | Loads the ThetaFlicks web application |
| `InternetChecker1` | Monitors internet connectivity status |
| `Floating_Action_Button1` | Manual reload trigger |
| `Floating_Action_Button2` | Internet recheck trigger |
| `Label1`, `Label2`, `Label3` | Display connection error messages |
| `Notifier1` | Shows alert dialogs and notifications |
| `Clock1` | 2000ms timer for exit reset |
| `Clock2` | 15000ms timer for UI state management |
| `TaifunTools1` | Controls system UI visibility (immersive mode) |

---

## How It Works

### 1. Initialization
- On app start, `InternetChecker1` verifies connectivity
- If online: Loads `https://thetaflicks.vercel.app` in the WebView
- If offline: Displays error labels with retry option

### 2. Orientation Control
The WebView monitors URL changes for orientation commands:
- URL contains `"orientation"` → Sets landscape mode, hides system UI
- URL contains `"orientations"` → Sets portrait mode, shows system UI

### 3. Internet Connectivity
- **Success**: Hides error labels, shows WebView, displays notification
- **Failed**: Shows error labels (Label1, Label2, Label3), hides WebView

### 4. Exit Behavior
- First back press: Shows "Press again to exit" notification, sets exit flag
- Second back press (within 2 seconds): Closes application
- Clock1 (2000ms) resets the exit flag

### 5. User Controls
- **Floating_Action_Button1**: Reloads the WebView
- **Floating_Action_Button2**: Rechecks internet connectivity

---

## Project Structure

```text
ThetaFlicks-Android/
├── ThetaFlicks.aia    # Kodular project file
└── README.md          # Project documentation
```

---

## Getting Started

### Prerequisites

- Kodular account (or compatible MIT App Inventor fork)
- Android device or emulator for testing

### Importing and Building

1. **Clone or download the repository**
   ```bash
   git clone https://github.com/Volzeur/ThetaFlicks-Android.git
   ```

2. **Import the Project**
   - Log in to your Kodular Creator account
   - Navigate to "Projects" → "Import project (.aia)"
   - Upload the `ThetaFlicks.aia` file

3. **Configure and Build**
   - Update any necessary settings (package name, version, etc.)
   - Use "Export" → "Android app (.apk)" to build
   - Install the APK on your Android device

---

## Tech Stack

| Category         | Technology |
|------------------|------------|
| **Platform**     | Android |
| **Development**  | Kodular (Visual block-based programming) |
| **Core WebView** | Android WebView component |
| **Project Format** | `.aia` (App Inventor Archive) |

---

## Contributing

1. Fork the Project
2. Import the `.aia` file into your Kodular environment
3. Make your changes to the blocks or components
4. Export the updated `.aia` file
5. Commit the changes and open a Pull Request

---

## License

Distributed under the **GNU AGPLv3 License**. See `LICENSE` for more information.

---

Created by [Volzeur](https://github.com/Volzeur)
