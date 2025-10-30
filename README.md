# 📱 DailyPulse - Your Personal Mood Tracker

<div align="center">

![Flutter](https://img.shields.io/badge/Flutter-3.35.7-02569B?logo=flutter)
![Dart](https://img.shields.io/badge/Dart-3.9.2-0175C2?logo=dart)
![Firebase](https://img.shields.io/badge/Firebase-Enabled-FFCA28?logo=firebase)
![License](https://img.shields.io/badge/License-MIT-green)

**A modern Flutter mobile app to track your daily moods, understand emotional patterns, and improve mental wellness** 🌈

[Features](#-features) • [Screenshots](#-screenshots) • [Installation](#-installation) • [How It Works](#-how-it-works) • [Tech Stack](#-tech-stack) • [Learning Resources](#-learning-resources-for-flutter-beginners)

</div>

---

## 📖 What is DailyPulse?

DailyPulse is a **mood tracking application** built with Flutter that helps you:
- 📝 Log your daily emotions using simple emoji selections
- 📊 View statistics about your mood patterns
- 🔄 Sync your data across multiple devices using Firebase
- 🌙 Track your mental wellness journey over time

**Perfect for:** Beginners learning Flutter, mental wellness tracking, or building a portfolio project!

---

## ✨ Features

### 🔐 User Authentication
- **Email & Password Login/Signup** using Firebase Authentication
- **Secure Session Management** - Stay logged in automatically
- **User-Specific Data** - Your moods are private and only visible to you

### 😊 Mood Logging
- **20 Emoji Options** - Express exactly how you feel (😄 😊 🙂 😐 😢 😡 and more)
- **Add Notes** - Write about what made you feel this way
- **Automatic Date Tracking** - Every entry is timestamped
- **Beautiful Grid Interface** - Easy-to-use emoji picker

### 📚 Mood History
- **Chronological List** - See all your past mood entries
- **Delete Entries** - Remove individual moods or clear all
- **Pull-to-Refresh** - Sync latest data from cloud
- **Formatted Dates** - Easy-to-read date display (e.g., "Jan 15, 2025")

### 📊 Analytics Dashboard
- **Total Entries Count** - See how consistent you've been
- **Mood Breakdown** - View positive, negative, and neutral days
- **Most Common Mood** - Discover your dominant emotional state
- **Visual Statistics** - Beautiful card-based display

### ☁️ Cloud Sync & Offline Support
- **Firebase Firestore Integration** - Data syncs across all your devices
- **Local Storage (SharedPreferences)** - Works offline, syncs when online
- **Dual Persistence Strategy** - Data is always safe!

### 🎨 Beautiful UI/UX
- **Material Design 3** - Modern, clean interface
- **Dark Mode** - Toggle between light and dark themes
- **Smooth Animations** - Fade and slide effects on login/signup
- **Custom Theming** - Consistent colors and styling
- **Google Fonts** - Professional typography (Inter font family)

---

## 🖼️ Screenshots

> Add screenshots of your app here once you run it on an emulator or device!

| Login Screen | Mood Logger | History | Analytics |
|--------------|-------------|---------|-----------|
| ![Login](docs/screenshots/login.png) | ![Logger](docs/screenshots/mood_log.png) | ![History](docs/screenshots/history.png) | ![Analytics](docs/screenshots/analytics.png) |

---

## 🚀 Installation

### Prerequisites

Before you begin, make sure you have:
- **Flutter SDK** (version 3.35.7 or higher)
- **Dart** (version 3.9.2 or higher, comes with Flutter)
- **Android Studio** or **VS Code** with Flutter extensions
- **Git** for cloning the repository
- **Firebase Account** (free tier is sufficient)

### Step 1: Install Flutter

**Windows:**
```powershell
# Download Flutter from https://flutter.dev/docs/get-started/install/windows
# Extract to C:\src\flutter
# Add to PATH: C:\src\flutter\bin

# Verify installation
flutter doctor
```

**macOS/Linux:**
```bash
# Download Flutter SDK
git clone https://github.com/flutter/flutter.git -b stable
export PATH="$PATH:`pwd`/flutter/bin"

# Verify installation
flutter doctor
```

### Step 2: Clone the Repository

```bash
git clone https://github.com/rnt07s/DailyPulse.git
cd DailyPulse
```

### Step 3: Install Dependencies

```bash
# Get all Flutter packages
flutter pub get
```

This will install:
- `firebase_core` - Firebase initialization
- `firebase_auth` - User authentication
- `cloud_firestore` - Cloud database
- `shared_preferences` - Local storage
- `google_fonts` - Custom fonts
- `intl` - Date formatting
- And more!

### Step 4: Firebase Setup

1. **Create a Firebase Project**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Click "Add Project"
   - Name it "DailyPulse" (or your choice)
   - Follow the setup wizard

2. **Enable Authentication**
   - In Firebase Console → Authentication
   - Click "Get Started"
   - Enable "Email/Password" sign-in method

3. **Create Firestore Database**
   - In Firebase Console → Firestore Database
   - Click "Create Database"
   - Start in **Test Mode** (for development)
   - Choose a location closest to you

4. **Add Android App to Firebase**
   - In Firebase Console → Project Settings → Your Apps
   - Click "Add App" → Android icon
   - **Android Package Name**: `com.dailypulse.app` (matches `AndroidManifest.xml`)
   - Download `google-services.json`
   - Place it in `android/app/` folder

5. **Configure Firebase in Project**
   - The `google-services.json` file connects your app to Firebase
   - All Firebase services are already configured in the code!

### Step 5: Run the App

```bash
# List available devices (emulators or connected phones)
flutter devices

# Run on connected device/emulator
flutter run

# Or run in debug mode with hot reload
flutter run --debug
```

**First time?** It may take 5-10 minutes to build. Subsequent runs are faster!

---

## 🎯 How It Works

### For Flutter Beginners: Understanding the App Architecture

#### 1️⃣ **Project Structure**

```
lib/
├── main.dart                 # App entry point - starts here!
├── models/                   # Data structures
│   └── mood_entry.dart       # Defines what a "mood" looks like
├── services/                 # Business logic
│   ├── auth_service.dart     # Handles login/signup
│   └── mood_storage.dart     # Saves/loads mood data
└── screens/                  # What users see
    ├── login_screen.dart     # Login page
    ├── signup_screen.dart    # Registration page
    ├── mood_log_screen.dart  # Log new mood
    ├── mood_history_screen.dart  # View past moods
    └── analytics_screen.dart # Statistics page
```

#### 2️⃣ **What is Flutter?**

**Flutter** is a framework (tool) that lets you build mobile apps for Android and iOS using **one codebase**. Instead of writing separate code for Android (Java/Kotlin) and iOS (Swift), you write once in **Dart** and it works on both!

**Key Concepts:**
- **Widget**: Everything in Flutter is a widget! Buttons, text, screens - all widgets.
- **Hot Reload**: Change code and see results instantly (in ~1 second!)
- **Material Design**: Pre-built beautiful UI components from Google

#### 3️⃣ **How Data Flows in DailyPulse**

```
User Taps "Save Mood"
        ↓
mood_log_screen.dart (UI)
        ↓
mood_storage.dart (Service)
        ↓
├─ SharedPreferences (Local Storage) ✅ Saved instantly
└─ Cloud Firestore (Cloud) ☁️ Synced in background
```

**When Loading:**
```
App Opens
        ↓
mood_storage.dart tries Cloud Firestore first
        ↓
If offline → Falls back to SharedPreferences
        ↓
Data displayed in mood_history_screen.dart
```

#### 4️⃣ **Key Files Explained**

**`main.dart`** - The Starting Point
```dart
void main() async {
  await Firebase.initializeApp();  // Connect to Firebase
  runApp(MyApp());                 // Start the app!
}
```
- Initializes Firebase when app starts
- Creates the main app widget
- Sets up light/dark themes

**`models/mood_entry.dart`** - Data Structure
```dart
class MoodEntry {
  String id;          // Unique identifier
  String emoji;       // The mood emoji (😊)
  String note;        // User's note
  DateTime date;      // When it was logged
}
```
- Defines what a "mood entry" contains
- Has methods to convert to/from JSON (for saving)
- Includes helpers like `isPositive` (checks if emoji is happy)

**`services/auth_service.dart`** - Authentication Logic
```dart
Future<void> signUpWithEmailPassword(email, password) {
  // Creates new user in Firebase
}

Future<void> signInWithEmailPassword(email, password) {
  // Logs in existing user
}
```
- Handles all Firebase Authentication operations
- Converts Firebase errors to user-friendly messages
- Manages user sessions

**`services/mood_storage.dart`** - Data Persistence
```dart
Future<void> saveMoodEntry(MoodEntry entry) async {
  // 1. Save to local storage (SharedPreferences)
  // 2. Upload to Firestore if user is logged in
}
```
- **Dual Storage**: Local + Cloud for offline support
- Uses `SharedPreferences` for local data (key-value storage)
- Uses `Firestore` for cloud sync (NoSQL database)

**`screens/mood_log_screen.dart`** - Logging Interface
```dart
// Shows grid of 20 emojis
GridView.builder(
  itemCount: _emojis.length,  // 20 emojis
  itemBuilder: (context, index) {
    return GestureDetector(
      onTap: () => setState(() => _selectedEmoji = _emojis[index]),
      child: Text(_emojis[index], style: TextStyle(fontSize: 40)),
    );
  },
)
```
- `GridView`: Displays emojis in a grid (5 columns)
- `GestureDetector`: Detects taps on emojis
- `setState()`: Updates UI when emoji is selected

#### 5️⃣ **What is Firebase?**

**Firebase** is Google's backend platform that handles:
- **Authentication**: User login/signup without building your own server
- **Firestore**: Cloud database that syncs in real-time
- **Security**: Built-in protection for user data

**Why use it?**
- No need to write server code (backend)!
- Automatically scales (handles millions of users)
- Free tier includes 50,000 reads/day

#### 6️⃣ **Important Flutter Concepts Used**

**StatefulWidget vs StatelessWidget:**
```dart
// StatelessWidget - Doesn't change
class WelcomeMessage extends StatelessWidget {
  Widget build(BuildContext context) {
    return Text("Welcome!"); // Always same text
  }
}

// StatefulWidget - Can change
class MoodLogScreen extends StatefulWidget {
  _MoodLogScreenState createState() => _MoodLogScreenState();
}

class _MoodLogScreenState extends State<MoodLogScreen> {
  String _selectedEmoji = "😊"; // This can change!
  
  void _changeEmoji(String emoji) {
    setState(() {
      _selectedEmoji = emoji; // Updates UI!
    });
  }
}
```

**FutureBuilder - Handle Async Data:**
```dart
FutureBuilder<List<MoodEntry>>(
  future: _storage.getAllMoodEntries(),  // Get data
  builder: (context, snapshot) {
    if (snapshot.connectionState == ConnectionState.waiting) {
      return CircularProgressIndicator(); // Show loading
    }
    if (snapshot.hasData) {
      return ListView(...); // Show data
    }
    return Text("No moods yet"); // Empty state
  },
)
```

**StreamBuilder - Real-time Updates:**
```dart
StreamBuilder(
  stream: FirebaseAuth.instance.authStateChanges(),
  builder: (context, snapshot) {
    if (snapshot.hasData) {
      return HomeScreen(); // User logged in
    }
    return LoginScreen(); // User logged out
  },
)
```

---

## 🛠️ Tech Stack

### Frontend
- **Flutter 3.35.7** - UI framework
- **Dart 3.9.2** - Programming language
- **Material Design 3** - Design system

### Backend & Services
- **Firebase Authentication** - User management
- **Cloud Firestore** - NoSQL cloud database
- **SharedPreferences** - Local storage

### Key Packages
```yaml
dependencies:
  flutter:
    sdk: flutter
  
  # Firebase
  firebase_core: ^2.32.0          # Firebase initialization
  firebase_auth: ^4.16.0          # Authentication
  cloud_firestore: ^4.17.5        # Cloud database
  
  # Local Storage
  shared_preferences: ^2.5.3      # Key-value storage
  
  # UI/UX
  google_fonts: ^6.3.2            # Custom fonts
  intl: ^0.19.0                   # Date formatting
```

### Development Tools
- **Android Studio** - IDE with emulator
- **VS Code** - Lightweight code editor
- **Flutter DevTools** - Debugging and profiling
- **Git** - Version control

---

## 📚 Learning Resources for Flutter Beginners

### Official Documentation
- 📘 [Flutter Documentation](https://docs.flutter.dev/) - Official guide
- 🎓 [Flutter Codelabs](https://docs.flutter.dev/codelabs) - Step-by-step tutorials
- 📺 [Flutter YouTube Channel](https://www.youtube.com/c/flutterdev) - Video tutorials

### Recommended Learning Path
1. **Start Here**: [Flutter for Beginners Course](https://flutter.dev/learn)
2. **Understand Dart**: [Dart Language Tour](https://dart.dev/guides/language/language-tour)
3. **Build First App**: [Write Your First Flutter App](https://docs.flutter.dev/get-started/codelab)
4. **Learn Widgets**: [Widget Catalog](https://docs.flutter.dev/ui/widgets)
5. **Understand State**: [State Management Intro](https://docs.flutter.dev/data-and-backend/state-mgmt/intro)

### Key Concepts to Master
- **Widgets**: Building blocks of Flutter UI
- **State Management**: How data flows in your app
- **Async Programming**: Using `async/await` for network calls
- **Navigation**: Moving between screens
- **Firebase Integration**: Backend services

### DailyPulse-Specific Tutorials
- [Firebase Setup for Flutter](https://firebase.google.com/docs/flutter/setup)
- [SharedPreferences Guide](https://docs.flutter.dev/cookbook/persistence/key-value)
- [ListView.builder Tutorial](https://docs.flutter.dev/cookbook/lists/long-lists)
- [Form Validation](https://docs.flutter.dev/cookbook/forms/validation)
- ☁️ **Cloud Sync** - Access your mood data from any device

## 📋 Getting Started

### Prerequisites
- Flutter SDK (3.x or higher)
- Android Studio / VS Code with Flutter extensions
- Android emulator or physical device
- Firebase account (for cloud features)

### Installation

#### 1. Clone the Repository
```bash
git clone <your-repo-url>
cd dailypulse
```

#### 2. Install Dependencies
```bash
flutter pub get
```

#### 3. Set Up Firebase (Optional but Recommended)

See [FIREBASE_SETUP.md](FIREBASE_SETUP.md) for detailed instructions.

Quick setup:
1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Add Android app with package name: `com.dailypulse.app`
3. Download `google-services.json` and place in `android/app/`
4. Enable Authentication (Email/Password)
5. Enable Firestore Database
6. Update Firestore security rules (see FIREBASE_SETUP.md)

#### 4. Run the App
```bash
flutter run
```

> **Note**: The app works offline with local storage, but requires Firebase setup for authentication and cloud sync features.

## 📁 Project Structure

```
lib/
├── main.dart                      # App entry point, Firebase init, auth flow
├── models/
│   └── mood_entry.dart            # Mood data model with JSON serialization
├── services/
│   ├── auth_service.dart          # Firebase Authentication service
│   └── mood_storage.dart          # Dual storage (local + Firestore)
└── screens/
    ├── login_screen.dart          # User login interface
    ├── signup_screen.dart         # User registration interface
    ├── mood_log_screen.dart       # Mood logging interface
    ├── mood_history_screen.dart   # History view with ListView.builder
    └── analytics_screen.dart      # Analytics and insights

android/
└── app/
    └── google-services.json       # Firebase config (add your own)

Firebase Collections:
├── users/                         # User profiles
└── mood_entries/                  # Mood entries with userId
```

## 🔧 Technical Details

### Dependencies
- `shared_preferences: ^2.2.2` - Local data persistence
- `google_fonts: ^6.1.0` - Beautiful typography (Inter font)
- `intl: ^0.19.0` - Date/time formatting
- `firebase_core: ^2.24.2` - Firebase initialization
- `firebase_auth: ^4.16.0` - User authentication
- `cloud_firestore: ^4.13.6` - Cloud database

### State Management
- Uses `setState` for state management (as required)
- Future-proof for adding Provider, Bloc, or Riverpod if needed

### Key Implementation Details

1. **Dual Storage**: Local (SharedPreferences) + Cloud (Firestore) sync
2. **Authentication**: Firebase Auth with secure email/password login
3. **ListView.builder**: Efficient rendering of mood history with dynamic item building
4. **Emoji Selection**: Grid-based emoji picker (5x4) with visual feedback
5. **Analytics**: Real-time calculation of mood statistics from stored data
6. **Dark Mode**: System-level theme switching with Material 3 support
7. **User Isolation**: Each user only sees their own mood entries via userId filtering

## 📱 Usage

### Initial Setup
1. **Sign Up**: Create an account with email and password
2. **Login**: Sign in to access your mood data

### Daily Usage
1. **Log Your Mood**: 
   - Tap an emoji that best represents how you feel
   - Add an optional note describing your day
   - Tap "Save My Mood" to record the entry
   
2. **View History**: 
   - Navigate to History tab
   - Scroll through past mood entries
   - Delete entries by tapping the delete icon
   
3. **Check Analytics**: 
   - Open Analytics tab
   - View total entries, mood distribution, and most common mood

4. **Switch Theme**: 
   - Tap the theme icon (🌙/☀️) in app bar
   - Toggle between light and dark modes

5. **Sign Out**: 
   - Tap the logout icon in app bar
   - Data persists in cloud and local storage

## 🎨 UI/UX Design Rationale

### Emotional Logic Design
The app uses emoji-based mood selection because:
- **Universal**: Emojis transcend language barriers
- **Fast**: Quick visual selection beats text input
- **Emotional**: Symbols capture feelings better than words
- **Intuitive**: No learning curve for users

### UI Choices
1. **Emoji Grid (5x4)**: Shows all 20 options at once, reducing decision fatigue
2. **Color Coding**: Visual distinction (green=positive, red=negative) helps quick scanning
3. **Card Layout**: Provides visual hierarchy and breathing room
4. **Bottom Navigation**: Thumb-friendly, shows all main sections
5. **Material 3**: Modern design language with elevation and motion

## 🚀 Future Enhancements

Potential features for expansion:
- Calendar view with mood indicators
- Chart visualization using fl_chart
- Export mood data as CSV
- Push notifications for daily reminders
- Mood tags/categories for better tracking
- Weekly/monthly mood summaries
- Multi-device sync improvements
- Social features (optional mood sharing)

## 🧪 Testing

### Manual Testing Checklist
- [ ] Create account and login
- [ ] Log multiple mood entries
- [ ] Verify data persists after app restart
- [ ] Test analytics calculations
- [ ] Switch themes and verify UI
- [ ] Test sign out and sign in again
- [ ] Verify mood entries sync to Firestore

## 🤝 Contributing

This is an educational project, but contributions are welcome:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📝 License

This project is created for educational purposes.

## 🙏 Credits

Built with ❤️ using:
- Flutter & Dart
- Material Design 3
- Firebase
- Google Fonts (Inter)

---

**Note**: Requires Firebase setup for authentication and cloud sync features. See [FIREBASE_SETUP.md](FIREBASE_SETUP.md) for configuration instructions.

