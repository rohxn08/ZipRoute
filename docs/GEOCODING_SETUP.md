# ZipRoute: Geocoding Setup Guide

## Contents
1. [Overview](#1-overview)
2. [Option 1: Google Geocoding API (Recommended)](#2-option-1-google-geocoding-api-recommended)
3. [Option 2: Mapbox (Free Alternative)](#3-option-2-mapbox-free-alternative)

## 1. Overview
ZipRoute requires a geocoding service to convert human-readable addresses into latitude/longitude coordinates. You can choose between Google (highest accuracy) or Mapbox (generous free tier).

## 2. Option 1: Google Geocoding API (Recommended)
Best for production apps requiring >99% accuracy globally.

### Setup
1.  **Enable API**: Enable "Geocoding API" in [Google Cloud Console](https://console.cloud.google.com/).
2.  **Get Key**: Create an API Key in **Credentials**.
3.  **Configure**: Update `backend/main.py`:
    ```python
    GOOGLE_GEOCODING_API_KEY: str = "YOUR_GOOGLE_KEY"
    ```

### Pros/Cons
*   **Pros**: Industry-standard accuracy.
*   **Cons**: Paid after $200 free credit (~40k requests).

---

## 3. Option 2: Mapbox (Free Alternative)
Best for development and projects with zero budget.

### Setup
1.  **Get Token**: Sign up at [Mapbox](https://account.mapbox.com/) and copy the "Default Public Token".
2.  **Configure**: Update `backend/main.py`:
    ```python
    MAPBOX_ACCESS_TOKEN: str = "pk.eyJ1I..."
    ```

### Pros/Cons
*   **Pros**: 50,000 free requests/month.
*   **Cons**: Slightly lower accuracy for unstructured Indian addresses compared to Google.
