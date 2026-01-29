# Backend - Delivery Route Optimizer

This directory contains the Python FastAPI backend for the project.

## Prerequisites
- Python 3.9+
- pip

## Setup
1. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Windows: venv\\Scripts\\activate
   ```
2. Install dependencies:
   ```bash
   pip install -r ../requirements.txt
   ```
3. Set up Environment Variables:
   - Create a `.env` file referencing `.env.example`.
   - See [Google API Setup](../docs/GOOGLE_API_SETUP.md) for API keys.
   - See [Gmail Setup](../docs/GMAIL_SETUP.md) for email features.

## Running the Server
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

## Documentation
- [Testing Guide](../docs/BACKEND_TESTING_GUIDE.md)
- [Ngrok Setup](../docs/NGROK_SETUP_GUIDE.md)
