# Explainable Customer Churn Prediction Engine

An AI-powered customer churn prediction application built with React and
FastAPI. The project uses XGBoost for churn prediction and SHAP/LIME to
help explain individual predictions.

## Features

-   Customer churn prediction
-   SHAP and LIME explanations
-   Customer risk segmentation
-   Retention recommendations
-   React and TypeScript frontend
-   FastAPI REST API
-   Model training workflow

> Verify that each feature is implemented in your current code before
> describing it as complete. If you use synthetic data, results are for
> demonstration and are not evidence of real-world performance.

## Technology Stack

-   **Frontend:** React, TypeScript, Vite
-   **Backend:** Python, FastAPI, Uvicorn
-   **Machine learning:** XGBoost, scikit-learn
-   **Explainability:** SHAP, LIME
-   **Data processing:** pandas, NumPy

## Example Project Structure

Adjust this to match your actual repository.

``` text
customer-churn-prediction/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   └── main.py
│   ├── data/
│   │   └── churn_synthetic.csv
│   ├── models/
│   │   └── churn_model.json
│   ├── requirements.txt
│   └── train_model.py
├── frontend/
│   ├── src/
│   │   └── App.tsx
│   └── package.json
├── .gitignore
└── README.md
```

## Prerequisites

-   Python 3.10 or a compatible version supported by your dependencies
-   Node.js and npm
-   Git

## Run Locally on Windows

### 1. Clone the repository

Replace `YOUR_USERNAME` with your GitHub username and update the
repository URL if needed.

``` powershell
git clone https://github.com/YOUR_USERNAME/customer-churn-prediction.git
cd customer-churn-prediction
```

### 2. Install backend dependencies

``` powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

If PowerShell blocks activation, use Command Prompt and run:

``` bat
.venv\Scripts\activate.bat
```

### 3. Start the backend

Run this from the `backend` directory:

``` powershell
python -m uvicorn app.main:app --reload --port 8000
```

-   Health endpoint: http://localhost:8000/health
-   API documentation: http://localhost:8000/docs

Keep the backend terminal open.

### 4. Install and start the frontend

Open a second terminal at the repository root:

``` powershell
cd frontend
npm install
npm run dev
```

Open the local URL printed by Vite. It is often `http://localhost:5173`,
but Vite may choose another port if the default is busy.

### 5. Configure the API URL

For local development, the backend URL is usually:

``` text
http://localhost:8000
```

If the frontend reads the URL from a Vite environment variable, create
`frontend/.env.local` containing:

``` text
VITE_API_URL=http://localhost:8000
```

Restart Vite after changing environment variables. Do not commit
credentials or private keys. The API URL itself is not a secret.

## API Testing

Open http://localhost:8000/docs to view the available endpoints and test
requests. Use the request schema shown there. Exact endpoints and input
fields depend on `backend/app/main.py`.

## Machine Learning and Explainability

### XGBoost

The classifier estimates churn risk using the features supplied during
training. Training and inference must use compatible feature names,
order, and preprocessing.

### SHAP

SHAP estimates how input features contribute to a model prediction.

### LIME

LIME explains an individual prediction by approximating model behavior
around the selected input.

### Risk Segmentation and Retention Recommendations

Risk thresholds and suggested actions should be configured and validated
for the application. Recommendations are decision-support suggestions,
not guarantees of customer behavior.

## Deployment

A typical deployment separates the frontend and backend:

1.  Push the project to GitHub.
2.  Deploy the FastAPI backend to a Python-capable hosting service.
3.  Deploy the React frontend to a frontend hosting service.
4.  Set the frontend API URL to the deployed backend URL.
5.  Configure FastAPI CORS to allow the deployed frontend's exact
    origin.
6.  Test the health, prediction, and explanation endpoints after
    deployment.

Ensure the deployed backend includes the model artifact and any runtime
data files it requires. Check hosting-provider limits and filesystem
behavior.

## Troubleshooting

-   **Connection refused:** Confirm the backend is running and the
    frontend uses the correct port.
-   **CORS error:** Allow the frontend's exact origin in FastAPI CORS
    settings.
-   **404 response:** Check the API endpoint path.
-   **422 response:** Make sure the request body matches the backend
    schema.
-   **Model not loaded:** Check backend logs, model paths, and
    dependency versions.
-   **Old API URL:** Check environment variables and restart/redeploy
    the frontend.

## Data, Privacy, and Limitations

-   Do not commit real customer personal information, credentials, API
    keys, or private datasets.
-   Clearly label synthetic data as synthetic.
-   Report performance metrics only when measured on an appropriate
    held-out dataset.
-   Review predictions and recommendations before using them for real
    customer decisions.

## Future Improvements

-   Add model evaluation metrics and validation reports.
-   Improve dashboard visualizations and explanation displays.
-   Monitor model drift and prediction quality.
-   Add controlled retraining and model versioning.
-   Evaluate retention recommendations against observed outcomes.

## Author

**YOUR NAME**

## License

Add a license file if you want to grant others permission to reuse,
modify, or distribute the project. Without a license, others should not
assume they have open-source reuse rights.
