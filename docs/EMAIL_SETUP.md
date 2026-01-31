# ZipRoute: Email Service Setup

## Contents
1. [Overview](#1-overview)
2. [Option 1: SMTP (Simpler)](#2-option-1-smtp-simpler)
3. [Option 2: OAuth2 (More Secure)](#3-option-2-oauth2-more-secure)

## 1. Overview
ZipRoute supports two methods for sending verification emails: standard SMTP (easier to set up) and OAuth2 (more secure, recommended for production). Choose the method that best fits your needs.

## 2. Option 1: SMTP (Simpler)
This method uses Gmail's SMTP server with an App Password.

### Prerequisites
1.  **2-Factor Authentication**: Enable it in [Google Account Security](https://myaccount.google.com/security).
2.  **App Password**:
    *   Go to **2-Step Verification** > **App passwords**.
    *   Create a new pass for "Mail" / "Other (ZipRoute)".
    *   Copy the 16-char password.

### Configuration
Update `backend/main.py`:
```python
GMAIL_USER = "your-email@gmail.com"
GMAIL_APP_PASSWORD = "your-16-char-app-password"
```

---

## 3. Option 2: OAuth2 (More Secure)
This method authenticates via a secure token without hardcoding passwords.

### Cloud Console Setup
1.  Create a project in [Google Cloud Console](https://console.cloud.google.com/).
2.  Enable the **Gmail API**.
3.  Create **OAuth Client ID** credentials (Application Type: Desktop).
4.  Download the JSON and save as `backend/credentials.json`.

### First Run Authentication
1.  Run the backend: `python main.py`
2.  A browser window will open. Login and grant permissions.
3.  A `token.json` file will be generated automatically for future use.
