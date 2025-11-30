# Setup Guide - TDTU Wallet

This guide will walk you through setting up the TDTU Wallet Android application on your local development environment.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Android Studio** (Hedgehog | 2023.1.1 or later recommended)
- **JDK 8** or higher (JDK 11+ recommended)
- **Android SDK** (API Level 26 or higher)
- **Git** (for cloning the repository)
- **Google Account** (for Firebase and Google Maps API)

## Step 1: Clone the Repository

```bash
git clone <repository-url>
cd TDTU-Walleet-Final-main
```

## Step 2: Firebase Setup

### 2.1 Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Add project"** or select an existing project
3. Follow the setup wizard to create your Firebase project
4. Enable **Google Analytics** (optional but recommended)

### 2.2 Add Android App to Firebase

1. In Firebase Console, click the **Android icon** to add an Android app
2. Enter your package name: `com.example.login`
3. Register the app and download `google-services.json`
4. Place the downloaded `google-services.json` file in the `app/` directory:
   ```
   TDTU-Walleet-Final-main/
   └── app/
       └── google-services.json
   ```

### 2.3 Enable Firebase Services

In Firebase Console, enable the following services:

#### Authentication
1. Go to **Authentication** → **Sign-in method**
2. Enable **Email/Password** authentication
3. Save the changes

#### Realtime Database
1. Go to **Realtime Database**
2. Click **"Create Database"**
3. Choose your preferred location (e.g., `us-central1`)
4. Start in **test mode** for development (you can secure it later)
5. Copy the database URL (you'll need this if it's different from the default)

### 2.4 Configure Database Rules (Optional)

For development, you can use these rules in **Realtime Database** → **Rules**:

```json
{
  "rules": {
    ".read": "auth != null",
    ".write": "auth != null"
  }
}
```

**⚠️ Warning**: These rules allow authenticated users full access. For production, implement proper security rules.

## Step 3: Google Maps API Setup

### 3.1 Get Google Maps API Key

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Select your Firebase project (or create a new one)
3. Navigate to **APIs & Services** → **Library**
4. Search for **"Maps SDK for Android"** and enable it
5. Go to **APIs & Services** → **Credentials**
6. Click **"Create Credentials"** → **"API Key"**
7. Copy the generated API key

### 3.2 Configure API Key in Project

1. Open `app/src/main/AndroidManifest.xml`
2. Find the meta-data tag for Google Maps API:
   ```xml
   <meta-data
       android:name="com.google.android.geo.API_KEY"
       android:value="YOUR_API_KEY_HERE" />
   ```
3. Replace `YOUR_API_KEY_HERE` with your actual API key:
   ```xml
   <meta-data
       android:name="com.google.android.geo.API_KEY"
       android:value="AIzaSyXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" />
   ```

### 3.3 Restrict API Key (Recommended for Production)

1. In Google Cloud Console, go to **APIs & Services** → **Credentials**
2. Click on your API key
3. Under **Application restrictions**, select **Android apps**
4. Click **"Add an item"** and enter:
   - Package name: `com.example.login`
   - SHA-1 certificate fingerprint (get it using the command below)

#### Get SHA-1 Fingerprint

**For Windows (PowerShell):**
```powershell
cd $env:USERPROFILE\.android
keytool -list -v -keystore debug.keystore -alias androiddebugkey -storepass android -keypass android
```

**For macOS/Linux:**
```bash
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

Copy the SHA-1 fingerprint and add it to the API key restrictions.

## Step 4: Configure Local Properties

### 4.1 Create local.properties (if not exists)

The `local.properties` file should contain your Android SDK path:

**Windows:**
```properties
sdk.dir=C\:\\Users\\YourUsername\\AppData\\Local\\Android\\Sdk
```

**macOS:**
```properties
sdk.dir=/Users/YourUsername/Library/Android/sdk
```

**Linux:**
```properties
sdk.dir=/home/YourUsername/Android/Sdk
```

Android Studio usually creates this file automatically, but verify it exists in both:
- Root directory: `TDTU-Walleet-Final-main/local.properties`
- App directory: `TDTU-Walleet-Final-main/app/local.properties`

## Step 5: Open Project in Android Studio

1. Launch **Android Studio**
2. Click **"Open"** or **"File"** → **"Open"**
3. Navigate to the `TDTU-Walleet-Final-main` directory
4. Click **"OK"** to open the project
5. Android Studio will automatically sync Gradle files

## Step 6: Sync and Build

1. Wait for Gradle sync to complete (check the bottom status bar)
2. If prompted, click **"Sync Now"** to sync project files
3. Resolve any dependency issues if they appear
4. Build the project: **Build** → **"Make Project"** (Ctrl+F9 / Cmd+F9)

## Step 7: Run the Application

### Option 1: Using Android Studio

1. Connect an Android device via USB (with USB debugging enabled) or start an emulator
2. Click the **"Run"** button (green play icon) or press **Shift+F10** (Windows/Linux) / **Ctrl+R** (macOS)
3. Select your device/emulator
4. The app will install and launch automatically

### Option 2: Using Command Line

```bash
# Windows
gradlew.bat installDebug

# macOS/Linux
./gradlew installDebug
```

## Step 8: Verify Setup

After the app launches:

1. **Test Authentication**: Try creating a new account or logging in
2. **Test Transactions**: Add a sample income/expense transaction
3. **Test Analysis**: Navigate to the analysis section to view charts
4. **Test Maps**: Open the maps activity (if configured)

## Troubleshooting

### Issue: "google-services.json not found"

**Solution:**
- Ensure `google-services.json` is in the `app/` directory (not the root)
- Verify the package name in `google-services.json` matches `com.example.login`
- Clean and rebuild: **Build** → **"Clean Project"**, then **Build** → **"Rebuild Project"**

### Issue: "Google Maps API key error"

**Solution:**
- Verify the API key is correctly set in `AndroidManifest.xml`
- Ensure **Maps SDK for Android** is enabled in Google Cloud Console
- Check that API key restrictions allow your app's package name and SHA-1

### Issue: "Firebase Authentication failed"

**Solution:**
- Verify Email/Password authentication is enabled in Firebase Console
- Check internet connection
- Verify `google-services.json` is properly configured

### Issue: "Gradle sync failed"

**Solution:**
- Check your internet connection
- Verify `local.properties` has correct SDK path
- Try: **File** → **"Invalidate Caches"** → **"Invalidate and Restart"**
- Update Android Studio and Gradle if needed

### Issue: "Build failed - dependency errors"

**Solution:**
- Ensure you're using a stable internet connection
- Try: **File** → **"Sync Project with Gradle Files"**
- Clean project: **Build** → **"Clean Project"**
- Check that all dependencies in `libs.versions.toml` are valid

### Issue: "App crashes on launch"

**Solution:**
- Check Logcat for error messages
- Verify Firebase configuration is correct
- Ensure all required permissions are granted
- Check that minimum SDK version (26) is supported on your device/emulator

## Additional Configuration

### Enable ProGuard (For Release Builds)

1. Open `app/build.gradle.kts`
2. In the `buildTypes` section, set `isMinifyEnabled = true` for release builds
3. Configure ProGuard rules in `app/proguard-rules.pro`

### Configure App Icon

Replace the launcher icons in:
- `app/src/main/res/mipmap-*/ic_launcher*.webp`
- `app/src/main/res/mipmap-*/ic_launcher_round.webp`

## Next Steps

- Review the [README.md](README.md) for project overview
- Explore the codebase structure
- Customize categories and features as needed
- Set up proper Firebase security rules for production

## Support

If you encounter issues not covered in this guide:

1. Check the [Android Studio documentation](https://developer.android.com/studio)
2. Review [Firebase documentation](https://firebase.google.com/docs)
3. Check project issues on GitHub (if applicable)

---

**Happy Coding! 🚀**

