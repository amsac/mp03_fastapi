# MP03 FastAPI — Bike Rental Prediction API

This repository contains a FastAPI application that serves a bike rental demand prediction model. It includes the API code, a Python wheel for the trained model, and the runtime dependencies needed to run the service locally or in a container.

Table of contents
- About
- Features
- Repository structure
- Requirements
- Installation
- Running the API
- Example usage
- Development
- Contributing
- License
- Contact

About

MP03 FastAPI exposes a prediction model for bike rental demand through a simple REST API built with FastAPI. The model package (bikerental_model-0.0.1-py3-none-any.whl) is included in the repository for easy installation.

Features
- Lightweight FastAPI server for predictions
- Included model wheel for offline installation
- Requirements file to reproduce environment

Repository structure
- app/ — FastAPI application code
- bikerental_model-0.0.1-py3-none-any.whl — Pre-built model package
- requirements.txt — Python dependencies
- README.md — This file

Requirements
- Python 3.9+ (3.10+ recommended)
- pip
- (Optional) virtualenv or venv

Installation
1. Clone the repository:

   git clone https://github.com/amsac/mp03_fastapi.git
   cd mp03_fastapi

2. Create and activate a virtual environment (recommended):

   python -m venv .venv
   source .venv/bin/activate   # Linux / macOS
   .\.venv\Scripts\activate  # Windows (PowerShell)

3. Install dependencies:

   pip install --upgrade pip
   pip install -r requirements.txt

4. Install the included model wheel (optional if you want the packaged model):

   pip install ./bikerental_model-0.0.1-py3-none-any.whl

Running the API

The FastAPI app is located in the `app` package. Start the server with uvicorn. The exact module path may be `app.main:app` — if your entrypoint differs, adjust accordingly.

   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

By default the server will be available at http://127.0.0.1:8000 and the interactive API docs at:
- Swagger UI: http://127.0.0.1:8000/docs
- ReDoc: http://127.0.0.1:8000/redoc

API Endpoints (examples)
- GET / — health check or welcome message
- POST /predict — submit a JSON payload with features and receive a prediction (depends on the implementation in app/)
- GET /health or /ping — optional readiness/liveness probes

Example usage (curl)

Replace the example payload with the expected features required by the model:

curl -X POST "http://127.0.0.1:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{"feature_1": 1, "feature_2": 2}'

Development

- Edit the code under `app/`.
- Run the server with `uvicorn app.main:app --reload` for hot reload during development.
- Add unit tests and use pytest to run them.

Contributing

Contributions are welcome. Please open an issue to discuss changes before submitting a pull request. Follow these guidelines:
- Fork the repository and create a branch for your feature or fix.
- Write tests for new behavior when applicable.
- Ensure linting and formatting are consistent with the project.

License

This project does not include an explicit license. Add a LICENSE file if you wish to apply an open-source license.

Contact

Repository owner: amsac


Notes
- If the application entry point differs from `app.main:app`, update the run command accordingly.
- For containerization, add a Dockerfile that installs the requirements and runs uvicorn.
