# ⏱️ Age Timer

A lightweight, client-side single-page app that displays the exact age of a person in real time — down to the second.

---

## ✨ Features

- **Live countdown** – updates every second
- **Detailed breakdown** – years, months, days, hours, minutes, seconds
- **Total overview** – age also displayed as total months, weeks, and days
- **First-run setup** – a setup dialog appears automatically on first visit
- **Persistent storage** – name and date of birth are saved in the browser's `localStorage` and survive every refresh
- **Settings** – editable at any time via the ⚙️ icon; changes are saved permanently
- **Dark mode** – toggle with one tap, preference is also persisted
- **Localization** – UI language adapts automatically to the browser's language setting (English and German supported; falls back to English)
- **Zero dependencies** – pure HTML/CSS/JavaScript, no external libraries
- **Responsive** – optimized for both mobile and desktop

---

## 🌍 Localization

The app detects the browser's language via `navigator.language` and renders all UI text in the matching language. The date and time format in the subtitle also adapts accordingly via the browser-native `toLocaleDateString` / `toLocaleTimeString` APIs.

| Browser language | UI language |
|---|---|
| `de`, `de-AT`, `de-CH`, … | German 🇩🇪 |
| anything else | English 🇬🇧 |

To add another language, extend the `TRANSLATIONS` object in `index.html` with a new key (e.g. `fr`) and the corresponding strings.

---

## 🚀 Usage

The app is a single HTML file — no build step or server required.

### Option 1 – Open directly in the browser

```bash
# Double-click the file, or:
open index.html
```

### Option 2 – Local web server (recommended)

```bash
# Python
python3 -m http.server 8080

# Node.js (npx)
npx serve .
```

Then open `http://localhost:8080` in your browser.

### Option 3 – Static hosting

Drop the file onto any web host, GitHub Pages, Netlify, or Vercel — no configuration needed.

---

## 🛠️ Setup

On the **first visit**, a setup dialog appears automatically:

1. Enter the **name** of the person
2. Select their **date and time of birth**
3. Click **Save & start**

The data is stored in the browser's `localStorage`. On every subsequent visit the timer starts immediately — no re-entry needed.

### Changing the data later

Tap the **⚙️ icon** in the bottom-right corner. The fields are pre-filled with the current values. Saving the form overwrites the stored data permanently.

---

## 💾 Data storage

All data stays **local in the browser** — nothing is sent to any server.

| localStorage key | Content |
|---|---|
| `timer_name` | Name of the person |
| `timer_birthdate` | Date of birth as an ISO 8601 string |
| `theme` | Color scheme (`light` or `dark`) |

### Resetting the data

To start from scratch, delete the keys via the browser DevTools:

```
DevTools → Application → Local Storage → delete entries
```

Or via the browser console:

```javascript
localStorage.removeItem("timer_name");
localStorage.removeItem("timer_birthdate");
localStorage.removeItem("theme");
```

---

## 🧮 Age calculation

The calculation correctly accounts for months of different lengths. If a person was born on **January 31st**, the anchor day in shorter months (February, April, …) is automatically clamped to the last day of that month — consistent with the common convention for stating ages.

```
Age = (years, months, days, hours, minutes, seconds)
      since the stored birth timestamp
```

---

## 📁 File structure

```
index.html   ← entire app (HTML + CSS + JS in one file)
README.md    ← this file
```

---

## 🌐 Browser compatibility

Works in all modern browsers:

| Browser | Support |
|---|---|
| Chrome / Edge | ✅ |
| Firefox | ✅ |
| Safari (iOS & macOS) | ✅ |
| Samsung Internet | ✅ |

---

## 📄 License

This project is released under the [MIT License](https://opensource.org/licenses/MIT) — free to use, modify, and distribute.
