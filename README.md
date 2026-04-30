# Professional Dashboard with Google Calendar Integration

A clean, professional dashboard application that integrates with Google Calendar to help you manage your day.

## 🌐 Live Demo

**Dashboard URL:** https://scottmedvin.github.io/dashboard/

## ✨ Features

- **Today's Focus**: Set and track your main focus for the day
- **Live Clock**: Real-time clock display in the navigation bar
- **Calendar Integration**: View upcoming events from your Google Calendar (requires setup)
- **Tasks**: Manage your daily tasks (placeholder for future implementation)
- **Notes**: Quick note-taking area with local storage
- **Responsive Design**: Works on desktop and mobile devices
- **Clean Professional UI**: Modern, distraction-free interface

## 🚀 Quick Start

1. Visit https://scottmedvin.github.io/dashboard/
2. You can immediately use the Focus and Notes sections
3. To enable Google Calendar integration, follow the setup instructions below

## 🔐 Google Calendar API Setup

To connect your Google Calendar, you need to create API credentials:

### Step 1: Create a Google Cloud Project

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Click "Select a project" → "New Project"
3. Enter a project name (e.g., "My Dashboard")
4. Click "Create"

### Step 2: Enable Google Calendar API

1. In your project, go to "APIs & Services" → "Library"
2. Search for "Google Calendar API"
3. Click on it and press "Enable"

### Step 3: Create OAuth 2.0 Credentials

1. Go to "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "OAuth client ID"
3. If prompted, configure the OAuth consent screen:
   - User Type: External
   - App name: My Dashboard
   - User support email: your email
   - Developer contact: your email
   - Click "Save and Continue"
   - Scopes: Click "Add or Remove Scopes", select `.../auth/calendar.readonly`
   - Test users: Add your email address
4. Back in Credentials, click "Create Credentials" → "OAuth client ID"
5. Application type: Web application
6. Name: Dashboard OAuth Client
7. Authorized JavaScript origins:
   - Add: `https://scottmedvin.github.io`
8. Authorized redirect URIs:
   - Add: `https://scottmedvin.github.io/dashboard/`
9. Click "Create"
10. **Copy your Client ID** (you'll need this)

### Step 4: Create API Key

1. Click "Create Credentials" → "API key"
2. **Copy your API Key** (you'll need this)
3. Click "Restrict Key" (recommended)
4. Under "API restrictions", select "Restrict key"
5. Select "Google Calendar API"
6. Under "Website restrictions", add: `https://scottmedvin.github.io/*`
7. Click "Save"

### Step 5: Update the Dashboard Code

1. Go to your GitHub repository: https://github.com/scottmedvin/dashboard
2. Click on `index.html`
3. Click the pencil icon to edit
4. Find these lines (around line 144-145):
   ```javascript
   const CLIENT_ID = 'YOUR_CLIENT_ID_HERE';
   const API_KEY = 'YOUR_API_KEY_HERE';
   ```
5. Replace `YOUR_CLIENT_ID_HERE` with your actual Client ID
6. Replace `YOUR_API_KEY_HERE` with your actual API Key
7. Scroll down and click "Commit changes"
8. Add a commit message like "Add Google Calendar credentials"
9. Click "Commit changes"

### Step 6: Wait for Deployment

GitHub Pages will automatically rebuild your site (takes 1-2 minutes). You can check the progress in the "Actions" tab.

### Step 7: Test the Integration

1. Visit https://scottmedvin.github.io/dashboard/
2. Click the "Sign In" button
3. Authorize access to your Google Calendar
4. Your upcoming events should now appear in the Calendar card!

## 📝 Usage Tips

- **Focus Input**: Your daily focus is saved automatically in your browser
- **Notes**: Notes are also saved locally in your browser
- **Calendar**: Shows your next 10 upcoming events from today
- **Sign Out**: Click "Sign Out" to disconnect from Google Calendar

## 🛠️ Technical Details

- **Framework**: Vanilla JavaScript (no dependencies)
- **Styling**: Custom CSS with CSS variables for theming
- **Storage**: LocalStorage for focus text and notes
- **Calendar API**: Google Calendar API v3
- **Authentication**: Google Identity Services (GIS)
- **Hosting**: GitHub Pages (free HTTPS hosting)

## 📱 Browser Support

Works on all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari
- Mobile browsers

## 🔒 Privacy & Security

- Your calendar data is fetched directly from Google - nothing is stored on any server
- Focus and notes are stored locally in your browser only
- OAuth 2.0 ensures secure authentication
- The app requests read-only access to your calendar

## 🎨 Customization

You can customize colors by editing the CSS variables in `index.html`:

```css
:root {
    --bg: #f4f6f9;        /* Background color */
    --surface: #ffffff;    /* Card background */
    --border: #e2e6ea;     /* Border color */
    --accent: #2563eb;     /* Primary accent color */
    --text: #1e293b;       /* Text color */
    --sub: #64748b;        /* Subtle text color */
}
```

## 🚧 Future Enhancements

- Task management with add/remove functionality
- Weather widget
- News feed integration
- Custom themes
- More calendar views (week, month)
- Task sync with Google Tasks

## 🧰 Troubleshooting

If sign-in fails:

1. Open browser DevTools (F12) → Console tab → look for red errors
2. Test the API key directly:
   `https://www.googleapis.com/discovery/v1/apis/calendar/v3/rest?key=YOUR_KEY`
   - Long JSON response = key works
   - `400 API_KEY_INVALID` = key is stale or wrong; create a new one
   - `403 API_KEY_HTTP_REFERRER_BLOCKED` from a direct browser tab = restrictions working correctly (this is expected)
3. Verify Cloud Console settings:
   - Project number matches Client ID prefix in `index.html`
   - Google Calendar API is enabled
   - API key restrictions: Application = `https://scottmedvin.github.io/*`, API = Google Calendar API
   - OAuth consent screen: your email is a test user (or app is in production)

## 📄 License

Free to use and modify for personal use.

## 🐛 Issues or Questions?

Create an issue in this repository or contact the maintainer.

---

**Enjoy your new dashboard!** 🎉
