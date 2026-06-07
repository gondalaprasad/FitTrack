# 🏋️ FitTrack Community

A mobile-first fitness & nutrition tracking platform. GitHub Pages hostable, PWA-ready, Android-convertible.

## Features
- 🔐 User accounts with password protection (SHA-256 hashed)
- 📋 20+ question health questionnaire
- 🧍 Visual body type selector (current & target)
- 📊 BMI, calorie targets, water intake calculator
- 🍽️ Daily meal log with auto macro calculation
- 🤖 Ollama AI integration for custom food items
- 👥 Community view — see all members' plans
- ⚙️ Admin panel — edit/delete any user
- 📱 Mobile-first, PWA-ready, Capacitor-convertible to APK

## Quick Start

```bash
git clone <your-repo>
cd fittrack
npm install
cp .env.example .env
# Edit .env with your admin password hash
npm run dev
```

## Environment Variables

| Variable | Description | Default |
|---|---|---|
| `VITE_ADMIN_USERNAME` | Admin login username | `admin` |
| `VITE_ADMIN_PASSWORD_HASH` | SHA-256 hash of admin password | hash of `admin` |
| `VITE_OLLAMA_API_URL` | Ollama server URL | `http://localhost:11434` |
| `VITE_OLLAMA_MODEL` | Ollama model name | `llama3` |

### Generate a Password Hash
```javascript
// In browser console:
const hash = await crypto.subtle.digest('SHA-256', new TextEncoder().encode('yourpassword'));
console.log(Array.from(new Uint8Array(hash)).map(b => b.toString(16).padStart(2,'0')).join(''));
```

## GitHub Pages Deployment

1. Push to GitHub
2. Go to Settings → Pages → Source: GitHub Actions
3. Add secrets in Settings → Secrets → Actions:
   - `ADMIN_PASSWORD_HASH`
   - `ADMIN_USERNAME`
   - `OLLAMA_API_URL` (optional)
4. Push to `main` branch — auto deploys!

## Android App Conversion

### Option A: PWABuilder (easiest, free)
1. Deploy to GitHub Pages
2. Visit [pwabuilder.com](https://pwabuilder.com)
3. Enter your GitHub Pages URL
4. Download APK package

### Option B: Capacitor (more control)
```bash
npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init FitTrack com.fittrack.app
npm run build
npx cap add android
npx cap copy
npx cap open android
# Build APK in Android Studio
```

## Default Admin Login
- Username: `admin`
- Password: `admin`
**⚠️ Change this before deploying!**