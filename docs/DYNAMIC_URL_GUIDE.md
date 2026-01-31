# ZipRoute: Dynamic URL Guide

## Contents
1. [Introduction](#1-introduction)
2. [Accessing Configuration](#2-accessing-configuration)
3. [Configuration Steps](#3-configuration-steps)
4. [Features](#4-features)
5. [Troubleshooting](#5-troubleshooting)

## 1. Introduction
The Dynamic URL feature allows the mobile application to connect to variable backend endpoints (such as Ngrok or local IPs) without requiring a rebuild. This is essential for development and testing across different network environments.

## 2. Accessing Configuration
The URL configuration screen can be accessed via:
1.  **Settings Menu**: Tap the menu icon (☰) > **Backend Configuration**.
2.  **Status Indicator**: Tap the network status icon in the app bar.

## 3. Configuration Steps
### Step 1: Obtain URL
Ensure your backend is running. If using Ngrok:
```bash
ngrok http 8000
```
Copy the generated HTTPS URL (e.g., `https://abc1234.ngrok.io`).

### Step 2: Input and Test
1.  Navigate to the **Backend Configuration** screen.
2.  Enter the URL in the input field.
3.  Tap **Test** to verify connectivity.
4.  Upon success, tap **Save Configuration**.

## 4. Features
*   **Auto-Save**: Successful connections are saved to a "Favorites" list for quick switching.
*   **Auto-Detect**: The app attempts to identify the type of URL (Ngrok, Localhost, Production).
*   **Quick Buttons**: Pre-set shortcuts for common environments:
    *   **Emulator**: `http://10.0.2.2:8000`
    *   **Localhost**: `http://localhost:8000`
    *   **Local Network**: `http://192.168.0.x:8000`

## 5. Troubleshooting
### Connection Failed
*   **Check Backend**: Ensure the server is online.
*   **Check Network**: Verify mobile device and server are on the same network (for local IPs) or have internet access (for Ngrok).
*   **Auto Detect**: Use the "Auto Detect" button to attempt discovery.

### URL Persistence
URLs are stored locally on the device. If a URL is not saving, ensure that the connection test passes first.
