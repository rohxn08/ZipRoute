# ZipRoute: Ngrok Setup Guide

## Contents
1. [Overview](#1-overview)
2. [Ngrok Configuration](#2-ngrok-configuration)
3. [Frontend Integration](#3-frontend-integration)
4. [Troubleshooting](#4-troubleshooting)
5. [Production Alternatives](#5-production-alternatives)

## 1. Overview
Ngrok exposes your local backend server to the internet, allowing the mobile application (running on a physical device or emulator) to communicate with your localhost.

## 2. Ngrok Configuration
### Usage Options
#### Option 1: Free Tier (Ephemeral URL)
Generates a random URL that changes every session.
```bash
ngrok http 8000
# Output: https://abc1234.ngrok.io
```

#### Option 2: Paid Tier (Reserved Domain)
Provides a consistent URL.
```bash
ngrok http 8000 --domain=ziproute-backend.ngrok.io
```

## 3. Frontend Integration
### Step 1: Update Configuration
Modify `frontend/lib/config.dart` to include your Ngrok URL.

```dart
static const List<String> ngrokUrls = [
  'https://ziproute-backend.ngrok.io',
  'https://your-random-id.ngrok.io',
];
```

### Step 2: Handle Network Security
The `network_security_config.xml` is pre-configured to trust user certificates and system CAs, allowing cleartext traffic if needed, though HTTPS is recommended.

### Step 3: Connection Logic
The app implements retry logic (`api_client.dart`) to handle potential latency from the tunnel:
*   **Timeout**: 30 seconds.
*   **Retries**: 3 attempts with exponential backoff.

## 4. Troubleshooting
### Connection Refused
*   **Verify Backend**: Ensure `python main.py` is running on port 8000.
*   **Verify Tunnel**: Ensure `ngrok` is active.
*   **Check Health**: Run `curl https://your-url.ngrok.io/health`.

### CORS Issues
The backend is configured with `CORSMiddleware` to allow all origins (`*`) for development simplicity. Ensure this is present in `main.py`.

## 5. Production Alternatives
For permanent deployment, consider:
*   **Render / Railway**: Free tiers available for Python/FastAPI.
*   **DigitalOcean / AWS**: VPS solutions for full control (`$5/mo` range).
