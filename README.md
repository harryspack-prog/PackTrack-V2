// server.js
require('dotenv').config();
const express = require('express');
const app = express();
const path = require('path');
const sqlite3 = require('sqlite3').verbose();

// Middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'public')));

// Database setup
const DB_PATH = path.join(__dirname, 'packtrack.db');
const db = new sqlite3.Database(DB_PATH, (err) => {
  if (err) console.error('DB Error:', err.message);
  else console.log('Connected to SQLite database.');
});

// Example route
app.get('/', (req, res) => {
  res.send('PackTrack v2 (SQLite) running ✅');
});

// Admin login route (example)
app.get('/admin', (req, res) => {
  const username = process.env.ADMIN_USERNAME || 'Harryspack';
  const password = process.env.ADMIN_PASSWORD || 'Changeme@Matteo';
  res.send(`
    <h1>PackTrack Admin Login</h1>
    <p>Username: ${username}</p>
    <p>Password: ${password}</p>
    <p>Login functionality coming soon...</p>
  `);
});

// Start server
const PORT = process.env.PORT || 4000;
const HOST = '0.0.0.0';
app.listen(PORT, HOST, () => {
  console.log(`PackTrack v2 listening on ${HOST}:${PORT}`);
});{
  "name": "packtrack-v2",
  "version": "1.0.0",
  "description": "PackTrack v2 backend (SQLite + Express) for tracking devices",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "author": "Udeh Harrison (Harryspack)",
  "license": "MIT",
  "dependencies": {
    "express": "^4.18.2",
    "sqlite3": "^5.1.6",
    "dotenv": "^16.3.1"
  },
  "devDependencies": {
    "nodemon": "^3.0.1"
  }
}
