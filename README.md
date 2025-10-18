
# PackTrack 📱🌍

**PackTrack** is a mobile and web application that helps users **locate and protect their devices** using GPS, IP address, and IMEI-based tracking.  
Built for speed, security, and accessibility, PackTrack lets users track stolen or lost devices in real time using another phone or PC.

## 🔐 Features
- Real-time device location tracking (GPS + IP)
- Admin panel (for Harryspack)
- User login and registration
- Secure authentication with JWT
- SQLite database for local and lightweight data storage
- Easy deployment on Railway and Firebase integration support

## 👤 Admin Login
- **Username:** `Harryspack`  
- **Password:** `Changeme@Matteo`

## 🧰 Tech Stack
- Node.js + Express
- SQLite database
- Railway (Cloud hosting)
- Flutter (for the mobile app frontend)

## 🚀 Deployment
Deploy easily using Railway:
1. Connect your GitHub repo to Railway
2. Add environment variables:
   - `PORT=8080`
   - `JWT_SECRET=packtrack_secret_2025`
   - `SESSION_SECRET=packtrack_session_key_2025`
   - `PAIRING_CODE=PACK123`
   - `ADMIN_USERNAME=Harryspack`
   - `ADMIN_PASSWORD=Changeme@Matteo`
3. Click **Deploy** and get your live URL.

## 🌟 Developer
Built by **Udeh Harrison (Harryspack)** — passionate about helping people protect and recover their devices.

---

> “PackTrack — Protecting your device, wherever it goes.”
