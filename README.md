from zipfile import ZipFile

# Paths
existing_zip_path = "/mnt/data/packtrack_v2_sqlite.zip"
updated_zip_path = "/mnt/data/packtrack_v2_sqlite_with_readme.zip"

# README content
readme_content = """# 🛰️ PackTrack v2 (SQLite)
### Multi-User Device Tracker with Flutter & Node.js Backend

**PackTrack** is a lightweight, fast, and secure tracking system that helps users locate their devices using GPS, IP address, and IMEI data.  
It’s designed for both **mobile and desktop** users — simple, powerful, and reliable.  

---

## ⚙️ Features
- 🔐 Admin & user authentication (JWT + bcrypt)
- 🌍 Real-time location posting and retrieval
- 📦 SQLite database for simplicity and speed
- 🗺️ Leaflet.js map visualization (admin dashboard)
- 📱 API-ready for Flutter mobile integration
- ⚙️ Auto-creates admin user on first launch

---

## 🧰 Tech Stack
| Component | Technology |
|------------|-------------|
| Backend | Node.js + Express |
| Database | SQLite (Knex ORM) |
| Auth | JWT + bcrypt |
| Frontend | EJS (Admin UI) + Leaflet |
| Mobile | Flutter |
| Deployment | Railway |

---

## 🧑‍💻 Admin Access

| Role | Username | Password |
|------|-----------|----------|
| Admin | **Harryspack** | **Changeme@Matteo** |

> The admin can manage users, pair devices, and view location data on the dashboard.

---

## 🚀 Setup (Local Installation)

### 1️⃣ Clone Repository
```bash
git clone https://github.com/Harryspack/packtrack-v2-sqlite.git
cd packtrack-v2-sqlite
```

### 2️⃣ Install Dependencies
```bash
npm install
```

### 3️⃣ Create `.env` File
Create a `.env` file in the project root:

```
PORT=4000
JWT_SECRET=packtrack_secret_2025
PAIRING_CODE=PACK123
ADMIN_USERNAME=Harryspack
ADMIN_PASSWORD=Changeme@Matteo
SESSION_SECRET=packtrack_session_key_2025
```

### 4️⃣ Start Server
```bash
npm start
```

### 5️⃣ Access Admin Dashboard
Visit:  
👉 [http://localhost:4000/admin](http://localhost:4000/admin)

Login using your admin credentials above.

---

## 🌐 Deployment on Railway

1. Go to [https://railway.app](https://railway.app)
2. Create a new project → **Deploy from GitHub**
3. Select this repository (`packtrack-v2-sqlite`)
4. Add environment variables:

| Key | Value |
|------|--------|
| `PORT` | `8080` |
| `JWT_SECRET` | `packtrack_secret_2025` |
| `PAIRING_CODE` | `PACK123` |
| `ADMIN_USERNAME` | `Harryspack` |
| `ADMIN_PASSWORD` | `Changeme@Matteo` |
| `SESSION_SECRET` | `packtrack_session_key_2025` |

5. Deploy 🚀

You’ll get a public URL like:
```
https://packtrack-v2-production.up.railway.app
```

Visit:
👉 `https://packtrack-v2-production.up.railway.app/admin`

---

## 📱 Flutter API Configuration

Update your `api_client.dart` base URL:
```dart
static const String baseUrl = "https://packtrack-v2-production.up.railway.app";
```

Your app will now connect directly to the cloud backend.

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|---------|-----------|-------------|
| POST | `/auth/login` | Login with username/password |
| POST | `/auth/register` | Admin creates new user |
| POST | `/devices/pair` | Pair device using pairing code |
| POST | `/devices/:id/location` | Update device location |
| GET | `/devices/my` | List devices for logged-in user |
| GET | `/admin` | Admin dashboard UI |

---

## 🧭 Admin Dashboard
Access all registered devices and users from a central panel.  
- View real-time GPS positions on a map  
- Manage users  
- Track devices  
- Export location history (coming soon)

---

## 🛡️ Security
- All routes protected via JWT authentication  
- Passwords hashed with bcrypt  
- Admin-only endpoints require elevated permissions  
- SQLite DB stored locally or in Railway persistent volume (optional)

---

## 🏗️ Next Roadmap
- [ ] User management UI (add/edit/delete users)
- [ ] Device history export (CSV/PDF)
- [ ] Offline sync for mobile app
- [ ] Push notifications via Firebase

---

## 📜 License
MIT License © 2025 **Harryspack (Udeh Harrison Obinwanne)**
"""

# Create README.md and update ZIP
readme_path = "/mnt/data/README.md"
with open(readme_path, "w") as f:
    f.write(readme_content)

with ZipFile(existing_zip_path, "r") as existing_zip:
    with ZipFile(updated_zip_path, "w") as new_zip:
        for item in existing_zip.infolist():
            new_zip.writestr(item, existing_zip.read(item.filename))
        new_zip.write(readme_path, "README.md")

updated_zip_path
