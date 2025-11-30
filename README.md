# TDTU Wallet - Personal Finance Management App

A comprehensive Android application for managing personal finances, tracking expenses, and analyzing spending patterns. Built with Java and Firebase, this app provides users with an intuitive interface to monitor their financial health.

TDTU Wallet helps users take control of their finances by providing a complete solution for tracking income, expenses, and financial goals. With real-time data synchronization, beautiful visualizations, and a user-friendly interface, managing money has never been easier.

## Features

### 💰 Transaction Management
- Add and categorize income and expenses with detailed information
- Track transactions with custom notes and descriptions
- View complete transaction history with filtering and search capabilities
- Organize transactions by multiple accounts and custom categories
- Date-based transaction organization with calendar integration
- Quick transaction entry with saved preferences

### 📊 Financial Analysis
- Visual spending analysis with interactive charts and graphs
- Standard and specific analysis views for different time periods
- Expense breakdown by categories with percentage calculations
- Income vs. expense tracking with balance summaries
- Trend analysis to identify spending patterns
- Export capabilities for financial reports

### 🔐 User Authentication
- Secure login and signup functionality with email/password
- Firebase Authentication integration for reliable user management
- User account management with profile customization
- Session persistence for seamless user experience
- Password recovery and account security features

### 🗺️ Additional Tools
- **Maps Integration**: Location-based features with Google Maps API for transaction location tracking
- **Calculator**: Built-in calculator for quick financial calculations
- **News Feed**: Financial news integration to stay updated with market trends
- **Account Management**: Multiple account support for different financial sources
- **Debt Tracking**: Monitor and manage debts and loans
- **Goal Setting**: Set and track financial goals with progress visualization

### 🎨 User Experience
- Material Design UI components for modern, intuitive interface
- Navigation drawer for easy access to all features
- Dark theme support for comfortable viewing in low-light conditions
- Customizable categories and accounts for personalized organization
- Responsive design that adapts to different screen sizes
- Smooth animations and transitions for better user experience

## Technology Stack

### Core Technologies
- **Language**: Java 8+
- **Platform**: Android (minSdk 26, targetSdk 34)
- **Build System**: Gradle with Kotlin DSL
- **Architecture**: MVC (Model-View-Controller) pattern

### Backend & Services
- **Backend**: Firebase (Authentication & Realtime Database)
- **Authentication**: Firebase Authentication (Email/Password)
- **Database**: Firebase Realtime Database for real-time data synchronization
- **Maps**: Google Maps API for location services

### Libraries & Dependencies
- **Charts**: MPAndroidChart v3.1.0 - Interactive chart visualization
- **Networking**: Retrofit 2.9.0 & Gson - REST API communication
- **Image Loading**: Glide 4.15.1 - Efficient image loading and caching
- **UI Components**: Material Design Components 1.12.0
- **RecyclerView**: AndroidX RecyclerView 1.3.0 - Efficient list rendering

## Project Structure

```
app/src/main/
├── java/com/example/login/
│   ├── MainActivity.java              # Main dashboard
│   ├── LoginActivity.java             # User authentication
│   ├── AddTransactionActivity.java    # Transaction entry
│   ├── TransactionHistoryActivity.java # Transaction list
│   ├── AnalysisActivity.java          # Financial analysis
│   ├── MapsActivity.java              # Maps integration
│   ├── Calculator_activity.java       # Calculator
│   └── newsActivity/                  # News feed module
└── res/
    ├── layout/                        # UI layouts
    ├── drawable/                      # Icons and graphics
    └── values/                        # Strings and themes
```

## Getting Started

### Quick Start

1. Clone the repository
   ```bash
   git clone <repository-url>
   cd TDTU-Walleet-Final-main
   ```

2. Open the project in Android Studio (Hedgehog or later)

3. Configure Firebase:
   - Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
   - Download `google-services.json` and place it in the `app/` directory
   - Enable Email/Password authentication in Firebase Console
   - Set up Realtime Database

4. Configure Google Maps API:
   - Get API key from [Google Cloud Console](https://console.cloud.google.com/)
   - Replace `YOUR_API_KEY_HERE` in `AndroidManifest.xml`

5. Sync Gradle files and build the project

### Detailed Setup

For comprehensive setup instructions, including Firebase configuration, API key setup, and troubleshooting, please refer to [SETUP.md](SETUP.md).

## Requirements

### Development Environment
- **Android Studio**: Hedgehog (2023.1.1) or later
- **JDK**: 8 or higher (JDK 11+ recommended)
- **Android SDK**: API Level 26 (Android 8.0) or higher
- **Gradle**: 8.7.3 (included in project)

### External Services
- **Firebase Account**: Required for authentication and database
  - Firebase Authentication (Email/Password enabled)
  - Firebase Realtime Database
- **Google Cloud Account**: Required for Maps functionality
  - Google Maps SDK for Android API key

### Device Requirements
- **Minimum Android Version**: Android 8.0 (API 26)
- **Target Android Version**: Android 14 (API 34)
- **Internet Connection**: Required for Firebase and Maps services

## Architecture

The application follows the MVC (Model-View-Controller) architecture pattern:

- **Model**: Data classes (`Transaction.java`, `HelperClass.java`) and Firebase database interactions
- **View**: XML layout files in `res/layout/` directory
- **Controller**: Activity classes that handle user interactions and business logic

### Key Components

- **Activities**: Handle UI and user interactions
- **Adapters**: Manage RecyclerView data binding (`TransactionAdapter.java`, `NewsAdapter.java`)
- **Helper Classes**: Utility functions and data models
- **Firebase Integration**: Real-time data synchronization and authentication

## Dependencies

The project uses the following major dependencies (see `gradle/libs.versions.toml` for complete list):

```gradle
// Firebase
- Firebase Authentication: 23.0.0
- Firebase Realtime Database: 21.0.0

// UI & Charts
- Material Design Components: 1.12.0
- MPAndroidChart: 3.1.0

// Networking
- Retrofit: 2.9.0
- Gson Converter: 2.9.0

// Image Loading
- Glide: 4.15.1
```

## Usage

### Creating an Account
1. Launch the app and tap "Sign Up"
2. Enter your email and password
3. Complete the registration process

### Adding Transactions
1. Navigate to the main dashboard
2. Tap the transaction icon or use the navigation drawer
3. Select transaction type (Income/Expense)
4. Enter amount, category, account, and optional notes
5. Save the transaction

### Viewing Analysis
1. Open the Analysis section from the navigation drawer
2. View standard analysis for overall spending patterns
3. Access specific analysis for detailed category breakdowns
4. Review interactive charts and graphs

## Screenshots

<!-- Add screenshots of your app here -->
<!-- Example:
![Login Screen](screenshots/login.png)
![Dashboard](screenshots/dashboard.png)
![Transaction History](screenshots/transactions.png)
![Analysis](screenshots/analysis.png)
-->

## Contributing

Contributions are welcome! If you'd like to contribute to this project:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style
- Follow Java coding conventions
- Use meaningful variable and method names
- Add comments for complex logic
- Maintain consistent indentation

## Known Issues

- Maps functionality requires valid Google Maps API key
- Some features may require internet connection
- Database rules should be configured for production use

## Troubleshooting

Common issues and solutions:

- **App crashes on launch**: Check Firebase configuration and API keys
- **Login fails**: Verify Firebase Authentication is enabled
- **Maps not loading**: Ensure Google Maps API key is correctly configured
- **Data not syncing**: Check internet connection and Firebase database rules

For detailed troubleshooting, see [SETUP.md](SETUP.md).

## License

This project is developed for educational purposes as part of TDTU (Ton Duc Thang University) coursework.

## Acknowledgments

- **TDTU (Ton Duc Thang University)** - Educational institution
- **Firebase** - Backend services and authentication
- **Google Maps** - Location services
- **MPAndroidChart** - Chart visualization library
- **Material Design** - UI component guidelines

---

**Note**: Remember to configure your Firebase credentials and Google Maps API key before running the application. For detailed setup instructions, refer to [SETUP.md](SETUP.md).

