# MLflow Projects Repository

## Overview

This repository provides a comprehensive implementation of machine learning experiment tracking, model management, and deployment workflows using **MLflow**. It demonstrates best practices for managing machine learning lifecycles, from initial experimentation through production deployment.

The repository comprises two complementary modules:

- **mlflow/** - Foundational tutorials and utilities for MLflow core concepts
- **MLFlow Project/** - Production-ready churn detection pipeline featuring multiple classification algorithms

---

## Table of Contents

- [Overview](#overview)
- [Quick Start](#quick-start)
- [System Requirements](#system-requirements)
- [Project Structure](#project-structure)
- [Installation Guide](#installation-guide)
- [Module Documentation](#module-documentation)
  - [MLflow Fundamentals Module](#mlflow-fundamentals-module)
  - [MLflow Project Module](#mlflow-project-module)
- [Experiment Execution](#experiment-execution)
- [Model Deployment](#model-deployment)
- [API Reference](#api-reference)
- [Dependencies](#dependencies)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [Resources](#resources)

---

## Quick Start

### Prerequisites Verification

```bash
# Verify Python installation
python --version  # Should be 3.8 or higher

# Navigate to project root
cd mlflow
```

### 1. Environment Setup

```bash
# Install all dependencies
pip install -r requirements.txt

# Verify MLflow installation
mlflow --version
```

### 2. Launch MLflow Tracking Server

```bash
# Start the MLflow UI for experiment monitoring
mlflow ui
```

The tracking server will be available at `http://localhost:5000`

### 3. Execute Your First Experiment

```bash
# Run a fundamental MLflow tutorial
python 01_create_experiment.py

# Or run the complete churn detection pipeline
cd "MLFlow Project"
mlflow run -e forest . --experiment-name churn-detection
```

---

## System Requirements

| Component            | Requirement                               |
| -------------------- | ----------------------------------------- |
| **Python**           | 3.8 or higher                             |
| **Operating System** | Windows, macOS, or Linux                  |
| **RAM**              | Minimum 4 GB (8 GB recommended)           |
| **Disk Space**       | 2 GB for dependencies and model artifacts |
| **Package Manager**  | pip 20.0+ or conda 4.8+                   |

---

## Project Structure

```
mlflow/
├── 01_create_experiment.py          # MLflow Experiment creation and management
├── 02_retrieve_experiments.py       # Experiment retrieval and introspection
├── 03_deleting_experiments.py       # Experiment lifecycle management
├── 04_mlflow_runs.py                # Run creation and tracking
├── 05_mflow_runs2.py                # Advanced run operations
├── 06_mlflow_runs3.py               # Run management and persistence
├── 07_logging_parameters.py         # Hyperparameter logging utilities
├── 08_logging_metrics.py            # Model evaluation metrics logging
├── 09_logging_artifacts.py          # Artifact storage and versioning
├── 10_logging_artifacts2.py         # Advanced artifact management
├── 11_logging_images.py             # Visualization and image logging
├── 12_logging_models.py             # Model registration and packaging
├── 13_logging_models.py             # Model versioning and metadata
├── 14_inference.py                  # Model inference implementation
├── 15_inference2.py                 # Production inference patterns
├── mlflow_utils.py                  # Shared utility functions
├── requirements.txt                 # Dependency specifications
├── README.md                        # This file
└── hello_world.txt                  # Sample reference file

MLFlow Project/
├── conda.yaml                       # Conda environment configuration
├── MLproject                        # MLflow project manifest and entry points
├── requirements.txt                 # Project-specific dependencies
├── README.md                        # Project documentation
├── forest_script.py                 # Random Forest classifier implementation
├── logistic_script.py               # Logistic Regression classifier
├── xgboost_script.py                # XGBoost gradient boosting implementation
├── utils.py                         # Project utilities and helpers
├── predict.ipynb                    # Interactive prediction demonstrations
├── mlflow-e2e-evaluation.ipynb      # End-to-end evaluation pipeline
├── X_test_prcoessed.csv             # Preprocessed test dataset
└── mlruns/                          # MLflow run artifacts (auto-generated)
```

---

## Installation Guide

### Option 1: Using pip (Recommended)

```bash
# Clone/navigate to the project
cd mlflow

# Create a Python virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install all dependencies
pip install --upgrade pip
pip install -r requirements.txt

# Verify installation
mlflow --version
```

### Option 2: Using Conda

```bash
# Create a new conda environment
conda create -n mlflow-env python=3.9

# Activate the environment
conda activate mlflow-env

# Install dependencies
conda install -c conda-forge mlflow scikit-learn xgboost matplotlib seaborn

# Or install from requirements
pip install -r requirements.txt
```

### Option 3: Development Installation

```bash
# For development with editable installation
cd mlflow
pip install -e ".[dev]"  # If setup.py is configured
pip install -r requirements.txt
```

### Verify Installation

```bash
# Test MLflow
python -c "import mlflow; print(f'MLflow version: {mlflow.__version__}')"

# Test scikit-learn
python -c "import sklearn; print(f'Scikit-learn version: {sklearn.__version__}')"

# Test XGBoost
python -c "import xgboost; print(f'XGBoost version: {xgboost.__version__}')"
```

---

## Module Documentation

### MLflow Fundamentals Module

This module provides step-by-step tutorials covering core MLflow concepts and best practices.

#### Experiment Management

| Script                       | Purpose                                | Key Concepts                                  |
| ---------------------------- | -------------------------------------- | --------------------------------------------- |
| `01_create_experiment.py`    | Create and manage MLflow experiments   | Experiment initialization, naming conventions |
| `02_retrieve_experiments.py` | Query and retrieve experiment metadata | Experiment introspection, filtering           |
| `03_deleting_experiments.py` | Delete experiments and cleanup         | Lifecycle management                          |

#### Run Operations

| Script               | Purpose                         | Key Concepts                            |
| -------------------- | ------------------------------- | --------------------------------------- |
| `04_mlflow_runs.py`  | Basic run creation and tracking | Run context, active run management      |
| `05_mflow_runs2.py`  | Advanced run operations         | Run nesting, parent-child relationships |
| `06_mlflow_runs3.py` | Run lifecycle and persistence   | Run state management, query operations  |

#### Logging Operations

| Script                     | Purpose                             | Key Concepts                               |
| -------------------------- | ----------------------------------- | ------------------------------------------ |
| `07_logging_parameters.py` | Log hyperparameters                 | Parameter types, best practices            |
| `08_logging_metrics.py`    | Log training and evaluation metrics | Metric tracking, time-series data          |
| `09_logging_artifacts.py`  | Store model artifacts and files     | Artifact versioning, artifact paths        |
| `10_logging_artifacts2.py` | Advanced artifact management        | Large file handling, artifact organization |
| `11_logging_images.py`     | Log visualizations and plots        | Image logging, matplotlib integration      |

#### Model Management

| Script                 | Purpose                       | Key Concepts                          |
| ---------------------- | ----------------------------- | ------------------------------------- |
| `12_logging_models.py` | Register and log ML models    | Model packaging, flavor specification |
| `13_logging_models.py` | Model versioning and metadata | Version control, model staging        |

#### Inference

| Script             | Purpose                       | Key Concepts                        |
| ------------------ | ----------------------------- | ----------------------------------- |
| `14_inference.py`  | Load and run model inference  | Model loading, prediction API       |
| `15_inference2.py` | Production inference patterns | Batch prediction, real-time serving |

#### Utilities

- **mlflow_utils.py** - Shared helper functions for logging, tracking, and model management

---

### MLflow Project Module

A production-grade machine learning pipeline for churn prediction with multiple classification algorithms.

#### Project Configuration

**MLproject** - Defines the project structure and entry points:

```yaml
name: churn-detection
conda_env: conda.yaml

entry_points:
  forest:
    command: python forest_script.py
    parameters:
      n_estimators: { type: int, default: 100 }
      max_depth: { type: int, default: 10 }

  logistic:
    command: python logistic_script.py
    parameters:
      c: { type: float, default: 1.0 }
      penalty: { type: str, default: 'l2' }

  xgboost:
    command: python xgboost_script.py
    parameters:
      n_estimators: { type: int, default: 100 }
      learning_rate: { type: float, default: 0.1 }
      max_depth: { type: int, default: 5 }
```

#### Implemented Algorithms

##### 1. Random Forest Classification

**File:** `forest_script.py`

**Characteristics:**

- Ensemble method using multiple decision trees
- Robust to outliers and non-linear relationships
- Provides feature importance insights
- Suitable for both classification and regression tasks

**Recommended for:** Large datasets with mixed feature types, importance explainability needed

**Hyperparameters:**

- `n_estimators` - Number of trees in forest (default: 100)
- `max_depth` - Maximum tree depth (default: 10)

##### 2. Logistic Regression

**File:** `logistic_script.py`

**Characteristics:**

- Linear classification model with probabilistic interpretation
- Fast training and inference
- Highly interpretable coefficients
- Scales well with feature dimensionality

**Recommended for:** Fast baseline models, interpretability critical, imbalanced datasets

**Hyperparameters:**

- `c` - Inverse regularization strength (default: 1.0)
- `penalty` - Regularization type: 'l1', 'l2' (default: 'l2')

##### 3. XGBoost Gradient Boosting

**File:** `xgboost_script.py`

**Characteristics:**

- State-of-the-art gradient boosting framework
- Handles non-linear relationships effectively
- Built-in feature importance calculation
- Excellent performance on structured/tabular data

**Recommended for:** Maximum accuracy needed, tabular data, competitive datasets

**Hyperparameters:**

- `n_estimators` - Number of boosting rounds (default: 100)
- `learning_rate` - Shrinkage parameter (default: 0.1)
- `max_depth` - Maximum tree depth (default: 5)

#### Notebooks

- **predict.ipynb** - Interactive demonstrations of model predictions and interpretations
- **mlflow-e2e-evaluation.ipynb** - Complete end-to-end evaluation pipeline with visualizations

---

## Experiment Execution

### Starting the MLflow Tracking Server

```bash
# Launch MLflow UI (runs on http://localhost:5000)
mlflow ui

# Or with custom configuration
mlflow ui --host 0.0.0.0 --port 5000 --backend-store-uri sqlite:///mlflow.db

# For production deployments, use a remote backend
mlflow ui --backend-store-uri postgresql://user:password@localhost/mlflow_db
```

### Running Fundamental Tutorials

Execute the MLflow basics tutorials sequentially:

```bash
# Experiment management
python 01_create_experiment.py
python 02_retrieve_experiments.py
python 03_deleting_experiments.py

# Run tracking
python 04_mlflow_runs.py
python 05_mflow_runs2.py
python 06_mlflow_runs3.py

# Logging operations
python 07_logging_parameters.py
python 08_logging_metrics.py
python 09_logging_artifacts.py
python 10_logging_artifacts2.py
python 11_logging_images.py

# Model management
python 12_logging_models.py
python 13_logging_models.py

# Inference
python 14_inference.py
python 15_inference2.py
```

### Running the Churn Detection Pipeline

#### Execute Single Algorithm

```bash
cd "MLFlow Project"

# Random Forest with default parameters
mlflow run -e forest . --experiment-name churn-detection

# Logistic Regression with default parameters
mlflow run -e logistic . --experiment-name churn-detection

# XGBoost with default parameters
mlflow run -e xgboost . --experiment-name churn-detection
```

#### Execute with Custom Hyperparameters

```bash
cd "MLFlow Project"

# Random Forest with custom parameters
mlflow run -e forest . --experiment-name churn-detection \
  -P n_estimators=450 \
  -P max_depth=10

# Logistic Regression with custom regularization
mlflow run -e logistic . --experiment-name churn-detection \
  -P c=3.5 \
  -P penalty="l2"

# XGBoost with optimized parameters
mlflow run -e xgboost . --experiment-name churn-detection \
  -P n_estimators=250 \
  -P learning_rate=0.15 \
  -P max_depth=22
```

#### Hyperparameter Sweep

```bash
# Run multiple experiments with different parameters
for estimators in 100 200 300; do
  mlflow run -e forest . --experiment-name churn-detection \
    -P n_estimators=$estimators
done

# Compare results in MLflow UI
```

### Monitoring Experiments

1. Open `http://localhost:5000` in your browser
2. Select your experiment from the list
3. Compare metrics, parameters, and artifacts across runs
4. Analyze feature importance and model performance

---

## Model Deployment

### Starting the Model Serving Server

The MLflow model serving provides a RESTful API for real-time predictions.

```bash
# Serve a specific model version
mlflow models serve -m "<model-uri>" --port 8000 --env-manager=local

# Example with actual model path
mlflow models serve -m "file:///path/to/model/artifacts/RandomForestClassifier" \
  --port 8000 \
  --env-manager=local \
  --host 0.0.0.0

# Alternative: using registered model
mlflow models serve -m "models:/RandomForestClassifier/Production" --port 8000
```

### Locating Model Artifacts

Models are saved in the `mlruns/` directory after successful training:

```
MLFlow Project/mlruns/
├── <experiment_id>/
│   ├── <run_id>/
│   │   ├── artifacts/
│   │   │   └── <model_type>/  # (e.g., RandomForestClassifier)
│   │   ├── params/
│   │   ├── metrics/
│   │   └── meta.yaml
```

Navigate to the MLflow UI to find the exact path of your model.

---

## API Reference

### Making Predictions via REST API

#### Request Format

The MLflow model server expects JSON requests following the dataframe split convention:

```bash
curl -X POST http://localhost:8000/invocations \
  -H 'Content-Type: application/json' \
  -d '{"dataframe_split": {"columns": [...], "data": [...]}}'
```

#### Request Body Structure

```json
{
  "dataframe_split": {
    "columns": [
      "Age",
      "CreditScore",
      "Balance",
      "EstimatedSalary",
      "Gender_Male",
      "Geography_Germany",
      "Geography_Spain",
      "HasCrCard",
      "Tenure",
      "IsActiveMember",
      "NumOfProducts"
    ],
    "data": [
      [45, 750, 50000, 75000, 1, 0, 0, 1, 5, 1, 2],
      [35, 680, 25000, 65000, 0, 1, 0, 1, 3, 0, 1]
    ]
  }
}
```

#### Response Format

```json
{
  "predictions": [0, 1]
}
```

Or with probabilities:

```json
{
  "predictions": [
    [0.85, 0.15],
    [0.42, 0.58]
  ]
}
```

#### Python Client Example

```python
import requests
import json

url = "http://localhost:8000/invocations"

data = {
    "dataframe_split": {
        "columns": ["Age", "CreditScore", "Balance", ...],
        "data": [[45, 750, 50000, ...]]
    }
}

response = requests.post(url, json=data)
predictions = response.json()
print(predictions)
```

---

## Dependencies

### Core Dependencies

| Package          | Version | Purpose                                     |
| ---------------- | ------- | ------------------------------------------- |
| **mlflow**       | 2.11.3  | ML experiment tracking and model management |
| **scikit-learn** | 1.2.2   | Machine learning algorithms library         |
| **xgboost**      | Latest  | Gradient boosting framework                 |
| **imblearn**     | Latest  | Imbalanced dataset handling                 |
| **matplotlib**   | Latest  | Data visualization                          |
| **seaborn**      | Latest  | Statistical data visualization              |

### Installing Dependencies

```bash
# From requirements.txt
pip install -r requirements.txt

# Individual package installation
pip install mlflow==2.11.3
pip install scikit-learn==1.2.2
pip install xgboost
pip install imbalanced-learn
pip install matplotlib
pip install seaborn

# With specific version pins (production)
pip install -r requirements.txt --no-deps
```

### Optional Dependencies

For advanced usage, consider installing:

```bash
# Database backends for tracking server
pip install psycopg2-binary  # PostgreSQL support
pip install PyMySQL          # MySQL support

# Cloud storage integration
pip install s3fs             # AWS S3 support
pip install gcsfs            # Google Cloud Storage support
pip install adlfs            # Azure Blob Storage support

# Jupyter integration
pip install jupyter
pip install jupyterlab
```

---

## Best Practices

### Experiment Organization

1. **Use descriptive experiment names**

   ```python
   mlflow.set_experiment("churn-detection-v2-imbalance-handling")
   ```

2. **Tag runs for better organization**

   ```python
   mlflow.set_tags({
       "team": "data-science",
       "project": "churn-detection",
       "phase": "experimentation"
   })
   ```

3. **Document parameters and metrics**
   ```python
   mlflow.log_param("train_size", 0.8)
   mlflow.log_metric("accuracy", 0.92)
   mlflow.log_artifact("confusion_matrix.png")
   ```

### Model Management

1. **Register production models**

   ```python
   mlflow.register_model(
       model_uri=f"runs:/{run_id}/model",
       name="RandomForestClassifier"
   )
   ```

2. **Use model stages for deployment**

   - **Staging**: For model testing
   - **Production**: For serving to end users
   - **Archived**: For deprecated models

3. **Version control your artifacts**
   - Log all trained models
   - Store preprocessing pipelines
   - Save feature engineering code

### Performance Monitoring

1. **Log comprehensive metrics**

   - Precision, Recall, F1-Score
   - ROC-AUC, PR-AUC
   - Confusion matrices
   - Feature importances

2. **Compare model performance**

   - Use MLflow UI for visual comparison
   - Export results for analysis
   - Track improvements over time

3. **Monitor production models**
   - Set up data drift detection
   - Log prediction distributions
   - Alert on performance degradation

---

## Troubleshooting

### Common Issues and Solutions

#### Issue: "Port 5000 is already in use"

```bash
# Use a different port for MLflow UI
mlflow ui --port 5001

# Or find and terminate the process using port 5000
# Windows: netstat -ano | findstr :5000
# Linux/Mac: lsof -i :5000
```

#### Issue: "Database locked" error

```bash
# Delete corrupted MLflow database and restart
rm -rf mlruns/
mlflow ui
```

#### Issue: Model serving fails to find model

```bash
# Verify model path exists
ls -la "path/to/model"

# Check MLflow run directory structure
find mlruns/ -type f -name "MLmodel"
```

#### Issue: Python package import errors

```bash
# Upgrade pip and install dependencies from scratch
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall
```

#### Issue: Memory errors with large models

```bash
# Increase available RAM or use batching
# Reduce batch size in inference scripts
batch_size = 1000  # Process in chunks
```

### Getting Help

- MLflow Documentation: https://mlflow.org/docs/latest/
- Stack Overflow: Tag questions with `mlflow`
- GitHub Issues: https://github.com/mlflow/mlflow/issues

---

## Resources

### Official Documentation

- [MLflow Official Documentation](https://mlflow.org/docs/latest/)
- [MLflow GitHub Repository](https://github.com/mlflow/mlflow)
- [MLflow Community](https://mlflow.org/community/)

### Machine Learning Frameworks

- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
- [Imbalanced-learn Documentation](https://imbalanced-learn.org/)

### Related Tutorials

- [MLflow Quickstart](https://mlflow.org/docs/latest/quickstart.html)
- [MLflow Projects](https://mlflow.org/docs/latest/projects.html)
- [MLflow Model Registry](https://mlflow.org/docs/latest/model-registry.html)
- [Hyperparameter Tuning with Optuna](https://optuna.readthedocs.io/)

### Industry Best Practices

- [ML Ops Best Practices](https://ml-ops.systems/)
- [Feature Store Design Patterns](https://www.featurestore.org/)
- [Model Monitoring and Drift Detection](https://arize.com/model-monitoring/)

---

## Performance Considerations

### Optimization Tips

1. **Parameter tuning**

   - Use GridSearchCV for small parameter spaces
   - Use RandomizedSearchCV for larger spaces
   - Consider Bayesian optimization for expensive models

2. **Data handling**

   - Use stratified sampling for imbalanced datasets
   - Preprocess data before logging
   - Cache preprocessed datasets

3. **Model serving**
   - Use connection pooling for REST API
   - Implement model warming for faster inference
   - Monitor latency and throughput

### Scalability

For production deployments:

```bash
# Use remote MLflow tracking server
export MLFLOW_TRACKING_URI=http://mlflow-server.example.com:5000

# Store artifacts in cloud storage
export MLFLOW_ARTIFACT_ROOT=s3://my-bucket/mlflow-artifacts

# Run experiments with distributed computing
mlflow run . --backend kubernetes
```

---

## Support and Contribution

### Reporting Issues

When reporting issues, include:

1. Python version and OS
2. Installed package versions
3. Minimal reproduction script
4. Full error traceback

### Contributing

To contribute improvements:

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Submit a pull request

---

## License

This project is provided for educational and research purposes.

---

**Last Updated:** January 2026  
**Python Version:** 3.8+  
**MLflow Version:** 2.11.3+
