# ZipRoute: Traffic Data Setup Guide

## Contents
1. [Overview](#1-overview)
2. [Traffic Multipliers](#2-traffic-multipliers)
3. [Location Adjustments](#3-location-adjustments)
4. [Real-Time API Integration](#4-real-time-api-integration)

## 1. Overview
ZipRoute implements dynamic traffic estimation to improve ETA accuracy. This system combines static time-based multipliers, location-based heuristics, and optional real-time API data.

## 2. Traffic Multipliers
The system applies multipliers to base travel times depending on the time of day.

| Time Period | Hours | Multiplier | Description |
| :--- | :--- | :--- | :--- |
| **Rush Hours** | 07:00-10:00, 17:00-20:00 | **2.2x** | Peak congestion |
| **Daytime** | 10:00-17:00 | **1.8x** | Standard business traffic |
| **Evening** | 20:00-23:00 | **1.5x** | Post-commute traffic |
| **Night** | 23:00-07:00 | **1.2x** | Low congestion |

## 3. Location Adjustments
Specific regions receive additional weighting based on historical density data.

| City | Adjustment | Coordinates |
| :--- | :--- | :--- |
| **Bangalore** | +10% | 12.5-13.5°N, 77.0-78.0°E |
| **Mumbai** | +20% | 18.5-19.5°N, 72.5-73.5°E |
| **Delhi** | +15% | 28.0-29.0°N, 76.5-77.5°E |

## 4. Real-Time API Integration
For production environments, integration with live traffic APIs is recommended.

### Supported Providers
1.  **MapmyIndia Traffic API**: Comprehensive data for Indian roads.
2.  **Zyla India Traffic API**: Alternative source for congestion metrics.

### Configuration
To enable real-time data, configure the API key in `backend/main.py`:

```python
MAPMYINDIA_API_KEY: str = "your_api_key_here"
# OR
TRAFFIC_API_KEY: str = "your_api_key_here"
```

### Verification
You can verify the active configuration and multipliers via the API:
```bash
curl "http://localhost:8000/traffic-config"
```
