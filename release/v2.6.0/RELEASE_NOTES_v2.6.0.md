# Enhance-d Club Glucose - Karoo v2.6.0

## 🎉 Release Highlights

**Token Query Parameter Authentication**

This release updates the Nightscout authentication method to use token query parameters instead of API secret headers, providing better compatibility with modern Nightscout servers.

![Enhance-d Club Glucose - Karoo](app/src/main/res/drawable/ic_enhanced_club_glucose.png)

## 📋 What's New

### ✨ New Features

- **Token Query Parameter Authentication**: Updated Nightscout API authentication to use token query parameters
  - Tokens are now sent as `?token=your-token` in the URL instead of HTTP headers
  - Better compatibility with Nightscout servers that require token-based authentication
  - Example: `https://yournightscout.com/api/v1/entries/sgv.json?token=your-token`

### 🔧 Improvements

- **Simplified Authentication**: More straightforward token-based authentication flow
- **Better Server Compatibility**: Works with Nightscout servers that use token query parameters
- **Clearer Configuration**: Updated UI text to clarify token usage

## 📊 Available Data Fields

### Basic Fields (9 total)
- **Glu. mg** - Blood glucose in mg/dL
- **Glu. mmol** - Blood glucose in mmol/L (1 decimal place)
- **Time Since (s)** - Seconds since last reading
- **Time Since (m)** - Formatted time (h:m:s) since last reading
- **Direction** - Glucose trend with arrow indicators (↑↑, ↑, ↗, →, ↘, ↓, ↓↓)
- **15m Δ mg** - 15-minute glucose change in mg/dL
- **15m Δ mmol** - 15-minute glucose change in mmol/L
- **5m Δ mg** - 5-minute glucose change in mg/dL
- **5m Δ mmol** - 5-minute glucose change in mmol/L

### Combo Fields (8 total, Graphical)
Space-efficient combined fields displaying time since, delta, and direction on the left with glucose value on the right:

- **Combo 1 mg** - Left: Time since (s) and 15m delta with arrow | Right: Glucose value (mg/dL)
- **Combo 1 mmol** - Left: Time since (s) and 15m delta with arrow | Right: Glucose value (mmol/L)
- **Combo 2 mg** - Left: Time since (s) and 5m delta with arrow | Right: Glucose value (mg/dL)
- **Combo 2 mmol** - Left: Time since (s) and 5m delta with arrow | Right: Glucose value (mmol/L)
- **Combo 3 mg** - Left: Time since (m) and 15m delta with arrow | Right: Glucose value (mg/dL)
- **Combo 3 mmol** - Left: Time since (m) and 15m delta with arrow | Right: Glucose value (mmol/L)
- **Combo 4 mg** - Left: Time since (m) and 5m delta with arrow | Right: Glucose value (mg/dL)
- **Combo 4 mmol** - Left: Time since (m) and 5m delta with arrow | Right: Glucose value (mmol/L)

**Total: 17 data fields available**

## 📱 Supported Devices

- **Hammerhead Karoo**
- **Hammerhead Karoo 2**
- **Hammerhead Karoo 3**

## 🔗 Nightscout API Sources

The app supports multiple Nightscout data sources:

### 1. **Nightscout Server** (Cloud-based)

- Standard cloud-hosted Nightscout instances
- Requires internet connection
- Optional API token authentication via query parameter
- Example: `https://yournightscout.com/api/v1/entries/sgv.json?token=your-token`

### 2. **Phone Local Broadcast via Hotspot**

- xDrip+ or similar apps broadcasting glucose data
- Auto-detects gateway IP when connected to phone hotspot
- Example: `http://192.168.1.1:17580/sgv.json`
- **⚠️ Important Note**: Local broadcast from xDrip+ on a phone via hotspot may not be possible on recent Android devices due to Layer 2 Firewalls. This is a security feature in newer Android versions that prevents devices on the same network from communicating directly. If this method doesn't work, consider using a cloud-based Nightscout server or running xDrip+ locally on the Karoo device instead.

### 3. **Local Karoo Device** (xDrip+ Local)

- xDrip+ running locally on the Karoo device
- No internet required, direct local access
- Example: `http://127.0.0.1:17580/sgv.json`

## 🛠️ Installation

### Method 1: Hammerhead App Installation (Recommended)

1. Download the APK from this release
2. Install the Hammerhead app on your phone
3. Connect your Karoo device to the same WiFi network as your phone
4. Open the Hammerhead app and sign in
5. Navigate to Device Settings → Install APK
6. Upload the downloaded APK file
7. Follow the on-screen instructions

### Method 2: USB Debugging Installation

1. Download the APK from this release
2. Enable USB debugging on your Karoo device
3. Connect via USB to your computer
4. Install using: `adb install Enhance-d_Club_Glucose_Karoo_v2.6.0.apk`

## 🔄 Automatic Updates

### How It Works

1. **App Launch**: When you open the app, it automatically checks for updates after 2 seconds
2. **Update Detection**: Compares your current version with the latest GitHub release
3. **Update Prompt**: If a newer version is available, shows an update dialog
4. **One-Click Update**: Tap "Update Now" to download and install automatically
5. **Session Management**: Only prompts once per app session to avoid annoyance

### Update Features

- **Automatic Detection**: No manual checking required
- **Release Notes**: See what's new before updating
- **Progress Tracking**: Shows download progress
- **Error Recovery**: Handles network issues gracefully
- **Manual Override**: Still available in Settings menu

### Configuration

The app automatically connects to the official GitHub repository to check for updates. No additional configuration required.

## ⚙️ Configuration

### API Token Setup

If your Nightscout server requires authentication:

1. **Open Settings** in the app
2. **Tap "Configure API Token"**
3. **Enter your API token** (visible by default for easy verification)
4. **Use the toggle** to hide the token if needed for privacy
5. **Save the configuration**
6. **Restart the app** to apply changes

The API token is sent as a query parameter in the URL:
- Format: `?token=your-token`
- Example: `https://yournightscout.com/api/v1/entries/sgv.json?token=your-token`

### Token Features

- **Default Visibility**: Tokens are shown by default for easier verification
- **Privacy Toggle**: Optional switch to hide tokens when needed
- **Real-time Display**: See actual token values in Settings
- **Secure Storage**: Tokens stored securely in app preferences

### Creating Nightscout Tokens

#### **What are Nightscout Tokens?**

Nightscout tokens are authentication credentials that allow secure access to your Nightscout site. They act like a "key" that grants specific permissions to access your glucose data.

#### **When Do You Need a Token?**

**You need a token if:**

- Your Nightscout site is **not publicly accessible** (most common)
- Your site requires authentication to view data
- You want to restrict access to specific users
- Your site uses `AUTH_DEFAULT_ROLES` set to `denied`

**You don't need a token if:**

- Your Nightscout site is publicly accessible
- Your site allows anonymous read access
- You're using local xDrip+ without authentication

#### **Creating Tokens:**

To create authentication tokens for your Nightscout site, follow the official Nightscout documentation:

1. **Access Admin Tools**: Click the settings panel (three horizontal bars) in your Nightscout website and select "Admin Tools"
2. **Create Token**: Click "Add New Subject" and choose the appropriate role:
   - **`readable`**: Read-only access (recommended for this app)
   - **`careportal`**: Can view and make treatment entries
   - **`admin`**: Full access
3. **Copy Token**: Use the generated token string for authentication

_Note: If you change your API_SECRET, all tokens will change and need to be updated._

## ⚠️ Important Notes

### Medical Disclaimer

This app is for **informational purposes only**. It is NOT intended for:

- Medical diagnosis or treatment
- Emergency medical situations
- Life-critical diabetes management decisions

**Always consult qualified healthcare professionals for medical decisions.**

### System Requirements

- Android 7.0+ (API level 24)
- Active data connection (WiFi or cellular) for updates
- Nightscout server with glucose data

### Data Usage

- Estimated usage: ~1MB per hour of ride time
- Update checks: Minimal data usage (~10KB per check)
- Data charges may apply depending on your cellular plan
- WiFi recommended when available

## 🔄 Updating from Previous Versions

1. **Automatic**: The app will prompt you to update when opened
2. **Manual**: Use "Check for Updates" in Settings
3. **Manual Installation**: Download and install APK manually
4. **Your settings will be preserved** during updates

## 🐛 Known Issues

- Some deprecation warnings in the code (non-functional)
- Requires "Install from Unknown Sources" to be enabled for first-time installation
- Update checks require internet connection

## 📞 Support

- **GitHub Issues**: [Report bugs and request features](https://github.com/haspden/Enhance_d_Club_Glucose_Karoo/issues)
- **Email**: uk@club.enhance-d.com
- **Documentation**: Check the README.md file for detailed setup instructions

## 🙏 Acknowledgments

- **Enhance-d Club UK** - Community support and inspiration for active living with type 1 diabetes
- **CGM in the Cloud** - Community-driven diabetes technology
- **xDrip+** - Open source diabetes management
- **Hammerhead** - Karoo platform and extension framework
- **Nightscout** - Open source CGM data platform

## 💪 About Enhance-d Club UK

**Enhance-d Club UK** is a not-for-profit community built by and for people living with type 1 diabetes who refuse to let it hold them back. From cyclists and runners to swimmers and weekend adventurers, we support each other to stay active, healthy, and connected.

### Our Mission:

- **💪 Empower** people with type 1 diabetes to live active, fulfilling lives
- **🚴 Create safe spaces** to share experiences, challenges, and wins
- **🤝 Build community** through meetups, events, and online support
- **🌍 Break down barriers** to access, so everyone can enjoy the benefits of sport and activity

### Support the Community:

Your support helps us keep the community thriving – from hosting meetups, to creating resources, to backing initiatives that make active living with type 1 diabetes more accessible to all.

**☕ Every coffee fuels community, connection, and action.**

_Together, we're proving that diabetes doesn't define limits._

---

**Version**: 2.6.0  
**Release Date**: December 2025  
**File**: `Enhance-d_Club_Glucose_Karoo_v2.6.0.apk`  
**Size**: See file details below

---

_Brought to you by Enhance-d Club_


