# Comprehensive React Native & Expo Windows Setup Guide

A complete, step-by-step installation and environment configuration guide for setting up the React Native development workflow on **Windows 10/11** system.

---

## 📋 Overview of the Stack

| Component           | Selected Tool                          | Description                                                                                       |
| :------------------ | :------------------------------------- | :------------------------------------------------------------------------------------------------ |
| **Framework**       | **Expo** (Managed Workflow)            | Recommended toolchain for React Native with built-in router and cloud build capabilities via EAS. |
| **Node Manager**    | **NVM for Windows** or **fnm**         | Version control for Node.js environments.                                                         |
| **IDE / Editor**    | **Visual Studio Code**                 | Standard IDE with React Native and Expo extensions.                                               |
| **SDK & Emulation** | **Android Studio (Android SDK & AVD)** | Native Android build toolchain and emulator setup.                                                |
| **Package Manager** | **npm** / **npx**                      | Default package execution and dependency management.                                              |

---

## 🚀 Step-by-Step Installation Guide

### Step 1: Set Up Node.js Isolation via NVM (`nvm-windows`)

1. Download `nvm-setup.exe` from the official [nvm-windows Releases page](https://github.com/nvm-windows/nvm/releases).
2. Run the installer executable and complete the wizard.
3. Open a **new** PowerShell window and execute:
   ```powershell
   nvm install lts
   nvm use lts
   ```

#### Verification:

Confirm that Node and NPM are accessible in your path:

```powershell
node -v # v24.20.0
npm -v # 11.19.0
```

---

### Step 2: Install & Configure Visual Studio Code

1. Install VS Code:
   ```powershell
   winget install --id Microsoft.VisualStudioCode -e
   ```
2. Install essential development extensions for React Native and Expo:
   ```powershell
   code --install-extension dbaeumer.vscode-eslint
   code --install-extension esbenp.prettier-vscode
   code --install-extension expo.vscode-expo-tools
   ```

---

### Step 3: Install Android Studio & Native Tools

1. Install Android Studio:
   ```powershell
   winget install --id Google.AndroidStudio -e
   ```
2. Launch **Android Studio** from the Windows Start Menu.
3. Complete the setup wizard using standard mode and let it download initial dependencies.

---

### Step 4: Configure Android SDK Manager Packages

1. Open Android Studio → Click **More Actions** → **SDK Manager** (or navigate to **Settings → Languages & Frameworks → Android SDK**).
2. Under the **SDK Platforms** tab:
   - Check **Android 17.0 ("CinnamonBun") - API Level 37.0** (or latest stable release).
3. Under the **SDK Tools** tab, check the following items:
   - [x] **Android SDK Build-Tools**
   - [x] **Android Emulator**
   - [x] **Android SDK Platform-Tools**
4. Click **Apply**, accept the license terms, and wait for the component installation to complete.

> **Why Google Play Images over Google APIs?**
> System images with **Google Play** include the official Google Play Store application and auto-updating Google Play Services. It enforces CTS (Compatibility Test Suite) production rules and locked root permissions, providing an accurate representation of a consumer physical device.

---

### Step 5: Create and Launch an Android Virtual Device (AVD)

1. Open **Android Studio** → Click **More Actions** → **Virtual Device Manager**.
2. Click **Create Device** (+).
3. Select Category: **Phone** → Device Model: **Pixel 10** → Click **Next**.
4. In the Virtual Device Manager list, click the **Play (▶)** button to start the emulator instance.

---

### Step 6: Launch Expo React Native App

1. Open PowerShell and navigate into your target project directory:

   ```powershell
   cd D:\Repositories\OrdinatorVitae
   ```

2. Start the Metro Development Server:
   ```powershell
   npx expo start
   ```

---

### 📱 Previewing & Developing

Once `npx expo start` is running:

- **On Android Emulator:** Press **`a`** in your PowerShell terminal window while your AVD is running. Expo will connect automatically, install **Expo Go**, and open your application.
- **On Physical iOS / Android Device:** Download the **Expo Go** app from the Apple App Store or Google Play Store. Ensure your phone is connected to the same Wi-Fi network as your PC, then scan the QR code displayed in your terminal.
- **Hot Reloading:** Open the workspace folder in VS Code (`code .`) and edit files. Save changes to view instant updates on screen.

---
