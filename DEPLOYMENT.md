# rcloneDrive &mdash; Deployment &amp; Google OAuth Setup Guide

This guide walks you through deploying this project to **GitHub Pages** on your other GitHub account and obtaining the exact links to fill into the **Google Cloud Console OAuth Consent Screen**.

> [!NOTE]
> As requested, this project has **NOT** been pushed to GitHub from this environment so that you can deploy it to your preferred separate GitHub account.

---

## Part 1: Push to Your Other GitHub Account

### Step 1: Create a New Repository on GitHub
1. Sign in to your other GitHub account at [github.com/new](https://github.com/new).
2. Set the repository name (e.g., `rclonedrive`).
3. Set the visibility to **Public** (required for free GitHub Pages).
4. Do **not** initialize with a README, `.gitignore`, or license (the project already has them).
5. Click **Create repository**.

### Step 2: Push Your Local Code to the Repository
In your terminal, navigate to this project folder and run:

```bash
cd rclonedrive

# Stage all files
git add .

# Commit files
git commit -m "Initial commit: rcloneDrive GitHub Pages & OAuth consent site"

# Ensure branch is named main
git branch -M main

# Add the remote repository URL for your other account
# Replace <YOUR_GITHUB_USERNAME> and <YOUR_REPO_NAME> with your actual details:
git remote add origin https://github.com/<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>.git

# Push to your repository
git push -u origin main
```

*(If you use SSH: `git remote add origin git@github.com:<YOUR_GITHUB_USERNAME>/<YOUR_REPO_NAME>.git`)*

---

## Part 2: Enable GitHub Pages

Once your code is pushed:
1. In your GitHub repository, click on **Settings** (top tab).
2. In the left sidebar, click on **Pages** (under "Code and automation").
3. Under **Build and deployment**:
   - **Source**: Select `Deploy from a branch`
   - **Branch**: Select `main` and folder `/ (root)`
4. Click **Save**.
5. Wait 60–90 seconds for GitHub Actions to publish your site.

---

## Part 3: Your Live Links for Google Cloud Console

Once deployed, your live site URL will follow the structure:
`https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO_NAME>/`

Here are the exact fields to enter into the **Google Cloud Console OAuth consent screen** (as shown in your screenshot):

| Google Cloud Console Field | What to Enter |
| :--- | :--- |
| **App logo** | Upload [`assets/logo-120.png`](assets/logo-120.png) *(Exact 120&times;120px square PNG)* |
| **App name** | `rcloneDrive` (or your preferred name) |
| **User support email** | Your personal Gmail / Google account email |
| **Application home page** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO_NAME>/` |
| **Application privacy policy link** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO_NAME>/privacy.html` |
| **Application Terms of Service link** | `https://<YOUR_GITHUB_USERNAME>.github.io/<YOUR_REPO_NAME>/terms.html` |
| **Authorised domains** | `github.io` |
| **Developer contact email** | Your personal Gmail / Google account email |

> [!TIP]
> **Authorised domains formatting:** In the Google Cloud Console "Authorised domains" input, enter just `github.io` without `https://` and without slashes. Google allows `github.io` as an authorized parent domain for GitHub Pages sites.

---

## Part 4: Personal Google Drive Client Best Practices

1. **Keep App in "Testing" Status:**
   - Under **OAuth consent screen &gt; Publishing status**, you can leave your app in **Testing**.
   - Under **Test users**, add your own Google Account email address (`you@gmail.com`).
   - This allows you to immediately authenticate Rclone without needing to go through Google's formal OAuth app verification process!

2. **Creating the OAuth 2.0 Client ID for Rclone:**
   - In Google Cloud Console, navigate to **APIs &amp; Services &gt; Credentials**.
   - Click **+ Create Credentials &gt; OAuth client ID**.
   - Application type: Select **Desktop app**.
   - Name: `rcloneDrive Desktop Client`.
   - Click **Create**.
   - Copy the **Client ID** and **Client Secret**.

3. **Configuring Rclone:**
   - Run `rclone config` in your terminal.
   - Choose `n` for New remote.
   - Name: `gdrive`
   - Storage type: `drive`
   - Paste your **Client ID** and **Client Secret**.
   - Follow the web prompt to sign into your Google account.
