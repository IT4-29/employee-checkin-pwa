# 📍 Employee Check-in PWA System

A location-based Progressive Web App for employee check-in and check-out with offline support.

## 🚀 Live Demo

**Your PWA will be deployed at:** https://guitarjak.github.io/employee-checkin-pwa

## ⚡ Quick Start

### 1. Enable GitHub Pages
1. Go to [Repository Settings](https://github.com/guitarjak/employee-checkin-pwa/settings/pages)
2. Under "Source", select "Deploy from a branch"
3. Choose "main" branch
4. Click "Save"
5. Your app will be live in a few minutes!

### 2. Configure Your n8n Webhook
1. Open `index.html`
2. Find this line: `const WEBHOOK_URL = 'YOUR_N8N_WEBHOOK_URL_HERE';`
3. Replace with your actual n8n webhook URL
4. Commit the change

### 3. Set Your Office Location
In your n8n workflow, update the office coordinates in the "Validate Location" node:
```javascript
const OFFICE_LOCATIONS = {
  'main_office': {
    lat: YOUR_OFFICE_LATITUDE,    // e.g., 13.7563
    lng: YOUR_OFFICE_LONGITUDE,   // e.g., 100.5018
    radius: 100,                  // meters
    name: 'Your Office Name'
  }
};
```

## 📱 PWA Features

✅ **Install on Mobile** - Add to home screen like a native app  
✅ **Works Offline** - Stores check-ins locally, syncs when online  
✅ **Location Validation** - GPS-based office location verification  
✅ **Background Sync** - Automatic data sync when connection restored  
✅ **Push Notifications** - Ready for future reminder features  
✅ **App Shortcuts** - Quick check-in/out from home screen  

## 🔧 How It Works

1. **Employee opens the app** (via URL or installed PWA)
2. **Location permission requested** (GPS access)
3. **Employee enters ID and selects action** (Check In/Out)
4. **Location validated** against configured office coordinates
5. **Data sent to n8n workflow** for processing and storage
6. **Offline support** - if no internet, saves locally and syncs later

## 📋 Installation Guide for Employees

### iOS (iPhone/iPad):
1. Open the app URL in Safari
2. Tap the Share button (square with arrow)
3. Scroll down and tap "Add to Home Screen"
4. Tap "Add" to confirm

### Android:
1. Open the app URL in Chrome
2. Tap the "Install" banner when it appears
3. Or tap Chrome menu → "Add to Home screen"
4. Tap "Install" to confirm

## 🛠️ Technical Details

### Files Structure:
- `index.html` - Main PWA application
- `manifest.json` - PWA configuration and metadata
- `service-worker.js` - Offline functionality and caching

### Location Accuracy:
- Uses HTML5 Geolocation API
- Requests high accuracy GPS
- Configurable radius tolerance (default: 100m)
- Indoor accuracy may vary (10-50+ meters typical)

### Data Storage:
- Online: Direct to n8n webhook
- Offline: localStorage with auto-sync
- No sensitive data stored locally

## 🔒 Security Considerations

- ✅ HTTPS required (automatically provided by GitHub Pages)
- ✅ Location permissions required
- ✅ Server-side validation in n8n workflow
- ✅ No employee credentials stored in app
- ⚠️ Basic GPS spoofing protection (deterrent level)

## 🐛 Troubleshooting

**PWA won't install?**
- Ensure you're using HTTPS
- Check that manifest.json is accessible
- Try different browser (Chrome/Safari recommended)

**Location not working?**
- Enable location permissions in browser
- Test on HTTPS (required for geolocation)
- Try outdoors for better GPS signal

**Offline sync not working?**
- Check browser developer tools for errors
- Verify service worker registration
- Test network toggle in dev tools

## 📊 Monitoring & Analytics

Track usage through:
- n8n execution logs
- Google Sheets records (if configured)
- Browser developer tools
- Service worker cache statistics

## 🔄 Updates & Maintenance

To update the app:
1. Edit files directly in GitHub
2. Changes deploy automatically
3. Service worker will update cached version
4. Users get updates on next app load

## 📞 Support

For technical issues:
- Check n8n workflow logs
- Test webhook URL directly
- Verify office coordinates
- Check browser console for errors

---

**Deployed by:** guitarjak  
**Last Updated:** August 27, 2025  
**Version:** 1.0.0
