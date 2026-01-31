# ZipRoute: Backend Testing Guide

## Contents
1. [Introduction](#1-introduction)
2. [Available Testing Tools](#2-available-testing-tools)
3. [Quick Start](#3-quick-start)
4. [Test Coverage](#4-test-coverage)
5. [JSON Report Structure](#5-json-report-structure)
6. [Troubleshooting](#6-troubleshooting)

## 1. Introduction
This guide outlines the usage of the comprehensive testing suite designed for the ngrok backend. It provides tools for validation, performance monitoring, and detailed reporting.

## 2. Available Testing Tools
### Shell Script Test (`test_ngrok_backend.sh`)
*   **Purpose**: Quick validation of all endpoints.
*   **Output**: `ngrok_backend_test_results.json` containing status codes and response times.

### Python Comprehensive Test (`test_ngrok_comprehensive.py`)
*   **Purpose**: Advanced analysis including performance metrics and recommendations.
*   **Output**: `ngrok_backend_comprehensive_report.json` containing detailed analytics and next steps.

### Test Runner (`run_backend_tests.sh`)
*   **Purpose**: Interactive utility to execute tests easily.
*   **Function**: Allows selection between shell, Python, or combined testing modes.

## 3. Quick Start
### Running All Tests
To execute the full test suite interactively:
```bash
./run_backend_tests.sh
```

### Running Individual Tests
To run specific test scripts directly:
```bash
# Shell validation only
./test_ngrok_backend.sh

# Python comprehensive analysis
python3 test_ngrok_comprehensive.py
```

## 4. Test Coverage
The suite covers the following endpoints:
1.  **System**: Root (`/`), Health (`/health`), Docs (`/docs`, `/openapi.json`)
2.  **Auth**: User Registration (`/auth/register`)
3.  **Location**: Search Suggestions (`/search-suggestions`), Nearby Places (`/nearby-places`)
4.  **Core Features**: Route Optimization (`/plan-full-route`), ETA Prediction (`/predict-eta`), OCR (`/ocr/extract-text`)

**Metrics Collected**:
*   Response Time (Latency)
*   HTTP Status Codes
*   Response Size
*   Success/Failure Rates

## 5. JSON Report Structure
### Shell Output
The `ngrok_backend_test_results.json` file provides a flat list of test results:
```json
{
  "test_suite": "ngrok_backend_comprehensive_test",
  "tests": [
    {
      "name": "Root",
      "status_code": 200,
      "response_time": 0.245,
      "success": true
    }
  ]
}
```

### Python Output
The `ngrok_backend_comprehensive_report.json` file includes deep analysis:
```json
{
  "summary": {
    "success_rate_percent": 100.0,
    "average_response_time_seconds": 1.245
  },
  "recommendations": [
    "Backend is ready for production use"
  ]
}
```

## 6. Troubleshooting
### Common Issues
*   **Permission Denied**: Ensure scripts are executable.
    ```bash
    chmod +x test_ngrok_backend.sh test_ngrok_comprehensive.py run_backend_tests.sh
    ```
*   **Dependencies**: Ensure `requests` is installed for Python tests.
    ```bash
    pip install requests
    ```
*   **Missing `jq`**: The shell script requires `jq` for JSON processing.
    ```bash
    sudo apt install jq  # Ubuntu
    brew install jq      # macOS
    ```
