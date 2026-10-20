# rcloneDrive &mdash; Personal Google Drive Client for Rclone

<p align="center">
  <img src="assets/logo-120.png" width="120" height="120" alt="rcloneDrive Logo" style="border-radius: 24px; box-shadow: 0 4px 20px rgba(0,0,0,0.15);" />
</p>

<p align="center">
  <strong>Secure, transparent personal OAuth client &amp; compliance site for Google Drive with Rclone.</strong>
</p>

<p align="center">
  <a href="#quick-start">Quick Start</a> &bull;
  <a href="#oauth-consent-screen-fields">OAuth Fields</a> &bull;
  <a href="#features">Features</a> &bull;
  <a href="#google-policy-compliance">Google Policy</a> &bull;
  <a href="DEPLOYMENT.md">Deployment Guide</a>
</p>

---

## Overview

This repository contains the complete static website and legal documentation needed to set up a personal **Google Drive OAuth 2.0 Client** for [Rclone](https://rclone.org) and publish it to **GitHub Pages**.

It fulfills all requirements shown in the **Google Cloud Console OAuth consent screen**:
- **Application Home Page** (`index.html`)
- **Application Privacy Policy** (`privacy.html`)
- **Application Terms of Service** (`terms.html`)
- **App Logo** (`assets/logo-120.png` &amp; `assets/logo.svg`)
- **404 Handling &amp; GitHub Pages Configuration** (`404.html`, `.nojekyll`)
- **Interactive OAuth Link Generator Widget** built directly into the homepage for instant copy-pasting.

---

## OAuth Consent Screen Fields

Once deployed to GitHub Pages at `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO>/`:

| Google Cloud Console Field | Value to Enter |
| :--- | :--- |
| **App logo** | Upload [`assets/logo-120.png`](assets/logo-120.png) *(120&times;120px)* |
| **App name** | `rcloneDrive` |
| **Application home page** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO>/` |
| **Application privacy policy link** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO>/privacy.html` |
| **Application Terms of Service link** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO>/terms.html` |
| **Authorised domains** | `github.io` |

---

## Features

- **100% Client-Side Privacy:** No external servers, no tracking, no middleman. All API queries occur directly between your local machine and `https://www.googleapis.com`.
- **Local Credential Storage:** Tokens and client secrets are stored strictly on your local disk in `~/.config/rclone/rclone.conf`.
- **Google Limited Use Compliant:** Fully adheres to the [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy).
- **Interactive Link Generator:** Enter your GitHub username and repository name on the home page to instantly generate and copy all Google Cloud Console fields.

---

## Quick Start (Deploying to your GitHub Account)

To deploy to your own GitHub account without pushing from this environment:

```bash
# 1. Stage and commit
git add .
git commit -m "Configure rcloneDrive OAuth pages and logo"

# 2. Add your repository remote
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO>.git

# 3. Push to main branch
git push -u origin main
```

Then enable GitHub Pages under **Repository Settings &gt; Pages &gt; Deploy from a branch (`main` / root)**.

Detailed instructions are available in [DEPLOYMENT.md](DEPLOYMENT.md).

---

## License

MIT License. Open-source personal client configuration.
