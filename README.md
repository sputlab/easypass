# EasyPass 🔐

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PWA Ready](https://img.shields.io/badge/PWA-Ready-purple.svg)](manifest.json)
[![Security: Web Crypto](https://img.shields.io/badge/Security-Web%20Crypto%20API-success.svg)](#security--cryptography)
[![Dependencies: 0](https://img.shields.io/badge/Dependencies-0-brightgreen.svg)](#technology-stack)

> **EasyPass** is a modern, fast, privacy-focused Password & Passphrase Generator built as a standalone, offline-first Progressive Web App (PWA).

Developed with privacy and security as top priorities: **100% client-side execution, zero external network dependencies, zero telemetry, and zero tracking**.

---

## 🌟 Key Features

### 🔑 Dual Generation Modes
- **Classic Password Generator**:
  - Configurable length (4 to 64 characters).
  - Fine-grained control over character classes (lowercase, uppercase, numbers, special symbols).
  - Guaranteed minimum counts per selected character set.
  - Extra random characters automatically filled.
- **Memorable Passphrase Generator**:
  - Generates human-friendly, memorable passphrases using dictionary words.
  - Configurable word count (3 to 10 words).
  - Customizable separators (hyphens `-`, underscores `_`, dots `.`, spaces, slashes `/`).
  - Options for word capitalization and appending numeric digits.

### 🛡️ Security & Cryptography
- **Native Web Crypto API**: Uses `crypto.getRandomValues()` with cryptographic rejection sampling (`getSecureRandomInt`) for true zero-modulo-bias pseudo-random generation (CSPRNG).
- **Accurate Entropy Calculation**: Real-time entropy computation based on character set pool size for passwords and dictionary power-of-two size for passphrases ($~8$ bits/word).
- **Content Security Policy (CSP)**: Built-in strict CSP meta policy preventing cross-site scripting and external network leakage.
- **Encrypted Local History**: Stores recent passwords in `localStorage` encrypted with PBKDF2 derivation and confirmation prompt before deletion.
- **Ninja Mode (Privacy)**: Mask passwords on screen (`-webkit-text-security: disc`) to prevent shoulder-surfing in public environments.
- **Zero Third-Party CDNs**: No external fonts, no external scripts, and no analytics calls.

### ⚙️ Advanced Customization & Usability
- **Ambiguous Character Filter**: Exclude confusing characters like `0/O`, `1/l/I`, `8/B`.
- **Consecutive Character Filter**: Prevent repeated identical characters from appearing adjacently.
- **Custom Character Exclusions**: Specify exact characters to exclude based on your company's password policy.
- **Bilingual Interface**: Seamless instant toggle between Italian (**IT**) and English (**EN**) with synchronized separator labels and HTML language tags.
- **Dark / Light Theme**: Automatic OS preference detection (`prefers-color-scheme`) with manual toggle and OLED-friendly dark palette.
- **Haptic & Audio Feedback**: Tactile vibration and clean synthesizer tone using a cached, leak-free AudioContext.
- **Accessible & Responsive**: Keyboard shortcuts (`G` to regenerate, `Escape` to close modals, click/Enter on password box to copy), visible focus rings, ARIA live announcement, and safe area insets for iOS notches and dynamic islands.

### 📱 Progressive Web App (PWA)
- Fully installable on iOS (Safari Add to Home Screen), Android (Chrome PWA prompt), macOS, Windows, and Linux.
- **Service Worker Offline Cache**: Built-in `sw.js` Cache-First service worker enabling 100% offline functionality.

---

## 📁 Repository Structure

```text
EasyPass/
├── .github/
│   └── workflows/
│       └── deploy.yml        # Automated GitHub Pages deployment
├── archive/                  # Historical release snapshots (v1.0 to v2.0.0)
│   ├── easypass_v1.html
│   ├── ...
│   ├── easypass_v197.html
│   └── easypass_v2.0.0.html
├── favicon/                  # Favicon icons across multiple resolutions
│   ├── apple-touch-icon.png
│   ├── favicon-16x16.png
│   ├── favicon-32x32.png
│   ├── favicon-48x48.png
│   └── favicon.ico
├── graphics/                 # Source design assets (SVG vector icons, branding)
│   ├── AppAssets_2026-05-03/ # App assets for iOS, Android, and Web
│   ├── easypass-app-icon...svg
│   └── logo.png
├── icons/                    # PWA launcher icons (48x48 to 512x512)
│   ├── icon-192x192.png
│   ├── icon-512x512.png
│   └── ...
├── .gitignore                # Git ignore rules for OS and temp files
├── index.html                # Main application entry point (EasyPass v2.0.0)
├── LICENSE                   # MIT License
├── logo.png                  # EasyPass primary logo
├── manifest.json             # PWA Web App Manifest
├── README.md                 # Project documentation
└── sw.js                     # Offline Service Worker (PWA Cache-First)
```

---

## 🚀 Quick Start & Local Development

Because EasyPass is a self-contained, zero-dependency web application, there are no build steps, compilers, or package managers required.

### Option 1: Direct File
Simply open `index.html` in your favorite web browser:
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 2: Local HTTP Server
To test PWA features and Service Worker / Web App Manifest locally:

```bash
# Using Python 3
python3 -m http.server 8000

# Or using Node.js / npx
npx serve .
```

Then navigate to `http://localhost:8000` in your browser.

---

## 🌐 Deploying to GitHub Pages

EasyPass is ready for 1-click deployment on GitHub Pages:

### Method A: Automated GitHub Actions (Recommended)
1. Push this repository to GitHub.
2. In your repository on GitHub, navigate to **Settings** > **Pages**.
3. Under **Build and deployment** > **Source**, select **GitHub Actions**.
4. The included `.github/workflows/deploy.yml` workflow will automatically deploy the site whenever you push to `main`.

### Method B: Classic Branch Deployment
1. Go to **Settings** > **Pages**.
2. Under **Build and deployment** > **Source**, choose **Deploy from a branch**.
3. Under **Branch**, select `main` and folder `/ (root)`.
4. Click **Save**. Your site will be live within seconds!

---

## 📜 Changelog

- **v2.0.0** (Latest)
  - Upgraded random generation to native Web Crypto API (`crypto.getRandomValues()`).
  - Added full multi-language support (Italian & English).
  - Improved accessibility (expanded interactive hitboxes, ARIA roles/labels).
  - Enhanced layout, modal animations, and bug fixes.
- **v1.97**
  - Added PWA Web App Manifest and complete multi-resolution icon set.
- **v1.96**
  - Passphrase layout alignment, white indicators, inverted changelog order.
- **v1.95**
  - Mobile modal navigation optimization, Ninja privacy mode, Settings modal.
- **v1.9**
  - Local history security hardening with HTML entity escaping, new word separators.
- **v1.0**
  - Initial public release of classic password generator.

---

## 🛠️ Technology Stack

- **HTML5 & CSS3**: Modern CSS variables, glassmorphism UI, flexible grid & flexbox layouts.
- **Vanilla JavaScript (ES6+)**: Zero external frameworks, libraries, or dependencies.
- **Web Crypto API**: High-entropy cryptographic pseudo-random number generation.
- **Web App Manifest**: Full compliance with Progressive Web App standards.

---

## 📄 License

This project is open-source and licensed under the [MIT License](LICENSE).

---

## 👤 Author & Support

- **Created by**: Stefano Soranzio ([sputlab.com](https://www.sputlab.com))
- **Support the Project**: [PayPal Donation](https://www.sputlab.com/donate)
