# Hello from FastAPI — Simple App

## Overview
This is a minimal example showing a FastAPI backend that returns “Hello from FastAPI” and a small HTML page that calls it and displays the result. The endpoint is:

- GET /api/hello → returns plain text: Hello from FastAPI

The frontend (index.html) can be opened directly in your browser. It calls the FastAPI server running locally.

## Setup
Prerequisites:
- Python 3.8+ (3.10+ recommended)
- pip

Steps:
1. Create and activate a virtual environment (optional but recommended)
   - macOS/Linux:
     - python3 -m venv .venv
     - source .venv/bin/activate
   - Windows (PowerShell):
     - python -m venv .venv
     - .\.venv\Scripts\Activate.ps1

2. Install dependencies:
   - pip install fastapi uvicorn

3. Create a file named app.py with the following content:
   - from fastapi import FastAPI
     from fastapi.middleware.cors import CORSMiddleware
     from fastapi.responses import PlainTextResponse

     app = FastAPI(title="Hello from FastAPI")

     app.add_middleware(
         CORSMiddleware,
         allow_origins=["*"],
         allow_credentials=True,
         allow_methods=["*"],
         allow_headers=["*"],
     )

     @app.get("/api/hello", response_class=PlainTextResponse)
     async def hello():
         return "Hello from FastAPI"

4. Run the FastAPI server:
   - uvicorn app:app --reload --host 127.0.0.1 --port 8000

5. Open the frontend:
   - Double-click index.html to open it in your browser, or serve it from any static file server.
   - The page will automatically call GET http://127.0.0.1:8000/api/hello and display the result.
   - You can change the API base URL in the input field and click “Save” if your server runs elsewhere.

## Usage
- Start the backend server: uvicorn app:app --reload
- Open index.html in your browser.
- The app will automatically call the API and show the response “Hello from FastAPI”.
- Click “Call API” to retry, or change the API base URL if needed.