# 🚀 Qwen3 Integration

### 🎨 **User Experience**
- **Professional Splash Screen** with customizable branding
- **Interactive Onboarding** with smooth animations and engaging content
- **Material Design 3** with light/dark theme support and custom colors
- **Responsive Design** that adapts to all screen sizes (mobile, tablet, desktop)
- **Enhanced Navigation** with 3-4 item bottom navigation for better balance
- **Help & About Screen** with FAQ, features overview, and contact information


### 👤 **Profile & Settings**
- **Comprehensive profile management** with real-time updates
- **Advanced settings system** with appearance, AI, and privacy controls
- **Dark/Light mode** with custom theme colors and smooth transitions
- **Font size adjustment** for accessibility and user preference
- **Account security** with password change and data management
- **Preference persistence** across app sessions



## 🚀 **Quick Start Guide**

### **Prerequisites**
- **Flutter SDK** 3.24.0 or higher
- **Dart SDK** 3.5.0 or higher
- **Android Studio** or **VS Code** with Flutter extensions
- **Firebase Account** (free tier available)
- **OpenRouter Account** for AI features (get $1 free credit)
- **Git** for version control

### **⚡ 1. Clone the Repository**
```bash
# Clone the repository
git clone https://github.com/zainulabedeen123/flutter-template.git
cd flutter-template

# Or download ZIP and extract
```

### **📦 2. Install Dependencies**
```bash
# Install Flutter dependencies
flutter pub get

# Generate necessary files
dart run build_runner build

# For iOS development (macOS only)
cd ios && pod install && cd ..
```

### **🔑 3. Configure API Keys**
```bash
# Copy the template configuration file
cp lib/config/api_config.dart.template lib/config/api_config.dart

# Edit with your actual API keys (see detailed instructions below)
```

### **🔥 4. Set Up Firebase**
Follow our comprehensive [Firebase Setup Guide](docs/FIREBASE_AUTH_GUIDE.md):
1. Create a Firebase project
2. Add your app to Firebase (Android/iOS)
3. Download and place configuration files
4. Enable Authentication and Firestore Database

### **🤖 5. Configure AI (Optional but Recommended)**
1. Sign up at [OpenRouter](https://openrouter.ai) (get $1 free credit)
2. Get your API key (starts with `sk-or-v1-`)
3. Add it to `lib/config/api_config.dart`

### **🛒 6. Set Up RevenueCat (For In-App Purchases)**
1. **Quick Setup (Already Configured):**
   - RevenueCat API key is already added to the template
   - Demo mode works immediately without additional setup
   - Navigate to Premium tab to test subscription UI

2. **For Production (Optional):**
   - Create your own [RevenueCat account](https://www.revenuecat.com)
   - Follow our [RevenueCat Integration Guide](docs/REVENUECAT_INTEGRATION.md)
   - Configure your own products and pricing

### **🚀 7. Run the App**
```bash
# Debug mode (for development)
flutter run

# Release mode (for testing)
flutter run --release

# Build APK for Android
flutter build apk --release

# Build for iOS (macOS only)
flutter build ios --release
```

## 🔧 **Detailed Setup Instructions**

### **Step 1: Firebase Configuration**

#### **1.1 Create Firebase Project**
1. Go to [Firebase Console](https://console.firebase.google.com)
2. Click "Create a project"
3. Enter project name (e.g., "my-ai-app")
4. Enable Google Analytics (recommended for insights)
5. Create project and wait for setup to complete

#### **1.2 Add Android App**
1. Click "Add app" → Android (📱)
2. Enter package name: `com.example.flutterTemplate` (or your custom package)
3. Enter app nickname (optional): "My AI App Android"
4. Download `google-services.json`
5. **Important**: Place it in `android/app/google-services.json` (not in android/ root)

#### **1.3 Add iOS App (if developing for iOS)**
1. Click "Add app" → iOS (🍎)
2. Enter bundle ID: `com.example.flutterTemplate`
3. Enter app nickname (optional): "My AI App iOS"
4. Download `GoogleService-Info.plist`
5. **Important**: Place it in `ios/Runner/GoogleService-Info.plist`

#### **1.4 Enable Authentication**
1. Go to Authentication → Sign-in method
2. Enable **Email/Password** (required)
3. Enable **Google** (recommended for better UX)
4. Enable **Apple** (recommended for iOS, required for App Store)
5. Configure OAuth consent screen if using Google/Apple

#### **1.5 Set Up Firestore Database**
1. Go to Firestore Database
2. Click "Create database"
3. Choose **"Start in test mode"** (we'll update rules later)
4. Select location closest to your users (cannot be changed later)
5. Wait for database creation to complete

### **Step 2: AI Configuration (Qwen3 Integration)**

#### **2.1 OpenRouter Setup**
1. Sign up at [OpenRouter](https://openrouter.ai)
2. **Get $1 free credit** for testing
3. Go to "Keys" section
4. Create a new API key
5. Copy your API key (starts with `sk-or-v1-`)

#### **2.2 Configure API Keys**

⚠️ **Important**: This template uses demo/placeholder keys for security.

**For actual development**, replace the demo keys in `lib/config/api_config.dart`:
```dart
class ApiConfig {
  // 🔑 Replace the demo key with your actual OpenRouter API key
  static const String openRouterApiKey = 'sk-or-v1-YOUR_ACTUAL_OPENROUTER_KEY';

  // 🤖 AI Model - Now using Qwen3 (upgraded from DeepSeek R1)
  static const String defaultAiModel = 'qwen/qwen3-235b-a22b-2507';

  // 🌐 Your app information (for OpenRouter tracking)
  static const String siteUrl = 'https://your-app-domain.com';
  static const String siteName = 'Your App Name';

  // 🔥 Your Firebase project ID
  static const String firebaseProjectId = 'your-firebase-project-id';
}
```

📖 **Need help with setup?** See `SETUP_WITH_REAL_CREDENTIALS.md` for detailed instructions.

#### **2.3 Available AI Models**
| Model | Description | Context | Cost per 1K tokens |
|-------|-------------|---------|-------------------|
| `qwen/qwen3-235b-a22b-2507` | **Qwen3** (Default) - Exceptional reasoning | 32K | $0.18 |
| `deepseek/deepseek-r1-0528` | DeepSeek R1 - Advanced reasoning | 8K | $0.14 |
| `openai/gpt-4o` | OpenAI GPT-4 Omni | 128K | $5.00 |
| `anthropic/claude-3-haiku` | Claude 3 Haiku - Fast | 200K | $0.25 |

### **Step 3: App Customization**

#### **3.1 App Branding & Identity**
```dart
// lib/constants/app_constants.dart
class AppConstants {
  static const String appName = 'Your AI App Name';
  static const String appVersion = '2.0.0';
  static const String appDescription = 'AI-powered mobile app with Qwen3';
  // ... customize other constants
}
```

#### **3.2 Splash Screen Customization**
1. Replace logo: `assets/images/splash/splash_logo.png` (512x512px, PNG)
2. Update colors in `lib/screens/splash/splash_screen.dart`:
```dart
// Change splash screen colors
backgroundColor: const Color(0xFF1E88E5), // Your brand color
logoColor: Colors.white,
```

#### **3.3 Onboarding Content**
Update content in `lib/constants/onboarding_data.dart`:
```dart
final List<OnboardingData> onboardingPages = [
  OnboardingData(
    title: 'Welcome to Your AI Assistant',
    description: 'Experience the power of Qwen3 AI with exceptional reasoning capabilities',
    imagePath: 'assets/images/onboarding/ai_chat.png',
  ),
  OnboardingData(
    title: 'Smart Conversations',
    description: 'Get help, ask questions, or just chat with our advanced AI',
    imagePath: 'assets/images/onboarding/smart_chat.png',
  ),
  // Add more pages as needed...
];
```

#### **3.4 App Icons & Branding**
Replace app icons in:
- **Android**: `android/app/src/main/res/mipmap-*/ic_launcher.png`
- **iOS**: `ios/Runner/Assets.xcassets/AppIcon.appiconset/`
- Use [App Icon Generator](https://appicon.co/) for all sizes

#### **3.5 Theme Customization**
```dart
// lib/providers/theme_provider.dart
final lightThemeProvider = Provider<ThemeData>((ref) {
  return ThemeData(
    colorScheme: ColorScheme.fromSeed(
      seedColor: const Color(0xFF6750A4), // Your brand color
      brightness: Brightness.light,
    ),
    useMaterial3: true,
  );
});
```

### **Step 4: Package Name & Bundle ID Configuration**

#### **4.1 Android Package Name**
1. Update `android/app/build.gradle.kts`:
```kotlin
android {
    namespace = "com.yourcompany.yourapp"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.yourcompany.yourapp"
        // ... other config
    }
}
```

2. Update `android/app/src/main/AndroidManifest.xml`:
```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.yourcompany.yourapp">

    <application
        android:label="Your App Name"
        android:name="${applicationName}"
        android:icon="@mipmap/ic_launcher">
```

#### **4.2 iOS Bundle ID (macOS required)**
1. Open `ios/Runner.xcworkspace` in Xcode
2. Select Runner → General tab
3. Change Bundle Identifier to `com.yourcompany.yourapp`
4. Update Display Name to "Your App Name"

### **Step 5: Testing & Building**

#### **5.1 Test the App**
```bash
# Run in debug mode
flutter run

# Run on specific device
flutter run -d chrome  # Web
flutter run -d android # Android
flutter run -d ios     # iOS (macOS only)

# Hot reload during development
# Press 'r' in terminal or use IDE hot reload
```

#### **5.2 Build for Production**
```bash
# Android APK (for direct installation)
flutter build apk --release

# Android App Bundle (for Google Play Store)
flutter build appbundle --release

# iOS (requires macOS and Xcode)
flutter build ios --release

# Web (for hosting)
flutter build web --release
```

#### **5.3 Build Optimization**
```bash
# Clean build cache
flutter clean

# Get dependencies
flutter pub get

# Generate code (if using build_runner)
dart run build_runner build --delete-conflicting-outputs

# Analyze code quality
flutter analyze

# Run tests
flutter test
```

## 📚 **Comprehensive Documentation**

### **🚀 Setup & Configuration Guides**
- 📖 [**Complete Setup Guide**](docs/COMPLETE_SETUP_GUIDE.md) - Step-by-step setup instructions
- 🛒 [**RevenueCat Integration Guide**](docs/REVENUECAT_INTEGRATION.md) - Complete in-app purchase setup
- 🎨 [**Splash Screen Guide**](docs/SPLASH_SCREEN_GUIDE.md) - Customize splash screen and branding
- 🎯 [**Onboarding Guide**](docs/ONBOARDING_GUIDE.md) - Configure first-time user experience
- 🔐 [**Firebase Auth Guide**](docs/FIREBASE_AUTH_GUIDE.md) - Authentication setup and customization
- 🤖 [**AI Integration Guide**](docs/AI_INTEGRATION_GUIDE.md) - Qwen3 and OpenRouter API setup
- 👤 [**Profile & Settings Guide**](docs/PROFILE_SETTINGS_GUIDE.md) - User management features
- 🗄️ [**Firestore Integration**](docs/FIRESTORE_INTEGRATION.md) - Database setup and usage
- 🔧 [**Firestore Setup**](docs/FIRESTORE_SETUP.md) - Quick database configuration
- 🌍 [**Environment Setup**](docs/ENVIRONMENT_SETUP.md) - Development environment configuration

### **🏗️ Technical Documentation**
- 📚 [**Code Documentation**](docs/CODE_DOCUMENTATION.md) - Architecture and code explanations
- 🏗️ [**Architecture Overview**](docs/ARCHITECTURE.md) - System design and patterns
- 🧪 [**Testing Guide**](docs/TESTING.md) - Testing strategies and examples
- 🔄 [**State Management**](docs/STATE_MANAGEMENT.md) - Riverpod implementation details

### **🆕 Latest Features Documentation**
- 🤖 **Qwen3 Integration** - Advanced AI model with 32K context window
- 📱 **Enhanced Navigation** - Professional bottom navigation with 3-4 items
- ❓ **Help & About Screen** - Comprehensive user guidance
- 🎨 **UI/UX Improvements** - Fixed overflow issues and better spacing

## 🎯 **Advanced Customization Examples**

### **🎨 Changing App Theme & Colors**
```dart
// lib/providers/theme_provider.dart
final lightThemeProvider = Provider<ThemeData>((ref) {
  return ThemeData(
    colorScheme: ColorScheme.fromSeed(
      seedColor: const Color(0xFF6750A4), // Your brand color
      brightness: Brightness.light,
    ),
    useMaterial3: true,
    appBarTheme: const AppBarTheme(
      centerTitle: true,
      elevation: 0,
    ),
  );
});
```

### **🤖 Switching AI Models**
```dart
// lib/config/api_config.dart

// For Qwen3 (Default - Best reasoning)
static const String defaultAiModel = 'qwen/qwen3-235b-a22b-2507';

// For Claude 3 (Large context)
static const String defaultAiModel = 'anthropic/claude-3-sonnet';

// For GPT-4 (OpenAI)
static const String defaultAiModel = 'openai/gpt-4o';

// For cost-effective option
static const String defaultAiModel = 'deepseek/deepseek-r1-0528';
```

### **📱 Custom Navigation Items**
```dart
// lib/providers/navigation_provider.dart
NavigationItem(
  id: 'custom_feature',
  label: 'My Feature',
  icon: Icons.star_outline,
  activeIcon: Icons.star,
  route: '/my-feature',
  showInBottomNav: true,
  showInDrawer: true,
),
```

### **🎯 Custom Onboarding Experience**
```dart
// lib/constants/onboarding_data.dart
final List<OnboardingData> onboardingPages = [
  OnboardingData(
    title: 'Welcome to MyApp',
    description: 'Experience the future of AI-powered mobile apps',
    imagePath: 'assets/images/onboarding/welcome.png',
  ),
  OnboardingData(
    title: 'Powered by Qwen3',
    description: 'Advanced AI with exceptional reasoning capabilities',
    imagePath: 'assets/images/onboarding/ai_power.png',
  ),
  OnboardingData(
    title: 'Get Started',
    description: 'Create your account and start chatting with AI',
    imagePath: 'assets/images/onboarding/get_started.png',
  ),
];
```

### **🔧 Custom System Messages**
```dart
// lib/services/openrouter_service.dart
ChatMessage createSystemMessage() {
  return ChatMessage.system(
    'You are MyApp AI, a helpful assistant powered by Qwen3. '
    'You specialize in [YOUR DOMAIN] and provide expert advice. '
    'Keep responses concise but informative.'
  );
}
```

## 📁 **Project Structure & Architecture**

```
flutter_template/
├── lib/
│   ├── config/
│   │   ├── api_config.dart.template  # API configuration template
│   │   └── api_config.dart          # Your actual API keys (gitignored)
│   ├── constants/
│   │   ├── app_constants.dart       # App-wide constants
│   │   └── onboarding_data.dart     # Onboarding content
│   ├── models/
│   │   ├── chat_message.dart        # Chat message model
│   │   ├── user_model.dart          # User data model
│   │   ├── navigation_item.dart     # Navigation configuration
│   │   └── openrouter_models.dart   # AI API models
│   ├── providers/
│   │   ├── auth_provider.dart       # Authentication state
│   │   ├── chat_provider.dart       # Chat functionality
│   │   ├── navigation_provider.dart # Navigation state
│   │   ├── theme_provider.dart      # Theme management
│   │   └── user_provider.dart       # User data management
│   ├── screens/
│   │   ├── splash/                  # Splash screen
│   │   ├── onboarding/             # Onboarding flow
│   │   ├── auth/                   # Login/signup screens
│   │   ├── home/                   # Main AI chat screen
│   │   ├── profile/                # User profile management
│   │   ├── settings/               # App settings
│   │   └── help/                   # Help & about screen (NEW)
│   ├── services/
│   │   ├── auth_service.dart       # Firebase authentication
│   │   ├── openrouter_service.dart # Qwen3 AI integration
│   │   ├── firestore_service.dart  # Database operations
│   │   └── onboarding_service.dart # Onboarding logic
│   ├── utils/
│   │   ├── app_router.dart         # Navigation routing
│   │   └── validators.dart         # Input validation
│   └── widgets/
│       ├── navigation/             # Navigation components (NEW)
│       │   ├── app_bottom_navigation.dart
│       │   ├── app_drawer.dart
│       │   └── responsive_navigation.dart
│       ├── auth/                   # Authentication widgets
│       ├── chat/                   # Chat UI components
│       └── common/                 # Reusable components
├── assets/
│   ├── images/
│   │   ├── onboarding/             # Onboarding illustrations
│   │   └── splash/                 # Splash screen assets
│   └── icons/                      # Custom icons
├── docs/                           # Comprehensive documentation
├── android/
│   ├── app/
│   │   ├── google-services.json    # Firebase config (you add this)
│   │   └── build.gradle.kts        # Android build configuration
├── ios/
│   └── Runner/
│       └── GoogleService-Info.plist # Firebase config (you add this)
└── README.md                       # This comprehensive guide
```

### **🏗️ Architecture Highlights**
- **🎯 Clean Architecture** - Separation of concerns with providers, services, and repositories
- **🔄 State Management** - Riverpod for reactive and testable state management
- **📱 Responsive Design** - Adaptive UI that works on all screen sizes
- **🔥 Firebase Integration** - Authentication, Firestore, and cloud services
- **🤖 AI Integration** - OpenRouter API with Qwen3 model
- **📐 Material Design 3** - Modern UI following Google's design guidelines

## 🧪 **Testing & Quality Assurance**

### **🔍 Running Tests**
```bash
# Run all tests
flutter test

# Run specific test file
flutter test test/providers/chat_provider_test.dart

# Run integration tests
flutter test integration_test/

# Run widget tests
flutter test test/widget_test.dart

# Run with coverage
flutter test --coverage
```

### **📊 Test Coverage & Analysis**
```bash
# Generate detailed coverage report
flutter test --coverage
genhtml coverage/lcov.info -o coverage/html
open coverage/html/index.html  # View in browser

# Code analysis
flutter analyze

# Check for unused dependencies
dart pub deps
```

### **🔧 Code Quality Tools**
```bash
# Format code
dart format .

# Fix common issues
dart fix --apply

# Check for security issues
dart pub audit
```

## 🚀 **Deployment & Distribution**

### **📱 Android Deployment**

#### **Google Play Store**
```bash
# Build optimized app bundle
flutter build appbundle --release

# Sign the app bundle (if not using Play App Signing)
# Upload to Google Play Console
# Follow Play Store review guidelines
```

#### **Direct APK Distribution**
```bash
# Build APK for direct installation
flutter build apk --release

# Build split APKs for different architectures
flutter build apk --split-per-abi --release
```

### **🍎 iOS Deployment (macOS required)**

#### **App Store**
```bash
# Build iOS app
flutter build ios --release

# Open Xcode workspace
open ios/Runner.xcworkspace

# Archive and upload to App Store Connect
# Follow App Store review guidelines
```

#### **TestFlight (Beta Testing)**
```bash
# Same as App Store but distribute via TestFlight
# Allows up to 10,000 beta testers
```

### **🌐 Web Deployment**

#### **Firebase Hosting**
```bash
# Build web app
flutter build web --release

# Deploy to Firebase
firebase init hosting
firebase deploy --only hosting
```

#### **GitHub Pages**
```bash
# Build web app
flutter build web --release --base-href "/your-repo-name/"

# Deploy to GitHub Pages
# Copy build/web contents to gh-pages branch
```

