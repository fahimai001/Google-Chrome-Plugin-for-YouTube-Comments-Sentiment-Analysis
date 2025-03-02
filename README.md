Google Chrome Plugin For Youtube Comments Sentiment Analysis
==============================

This project provides an end-to-end solution that leverages advanced NLP techniques and state-of-the-art machine learning models for YouTube comment sentiment analysis. Utilizing multiple classification algorithms—with LightGBM proving to be the best performer—the tool accurately categorizes comments as positive, negative, or neutral. It seamlessly integrates with the YouTube API to extract comments, processes the data, and delivers actionable insights through an intuitive, real-time interface. Designed for both developers and content creators, this solution enhances the understanding of audience sentiment to drive improved engagement strategies. Moreover, it incorporates robust features such as data versioning with DVC, experiment tracking with MLflow, a dedicated Google Chrome extension for live sentiment visualization, an automated CI/CD pipeline, Docker containerization, and deployment on AWS EC2, ensuring scalability and operational efficiency.

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    │
    ├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── make_dataset.py
    │   │
    │   ├── features       <- Scripts to turn raw data into features for modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>


# YouTube Comments Sentiment Analysis

A comprehensive project that analyzes YouTube video comments to determine sentiment, using multiple classification algorithms to identify the best performer (LightGBM), integrated with state-of-the-art tools for data versioning, experiment tracking, continuous integration/deployment, containerization, and cloud deployment. Additionally, a Google Chrome extension has been created to visualize sentiment insights directly on YouTube videos.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Setup and Installation](#setup-and-installation)
- [Data Versioning with DVC](#data-versioning-with-dvc)
- [Experiment Tracking with MLflow](#experiment-tracking-with-mlflow)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Google Chrome Extension Integration](#google-chrome-extension-integration)
- [Visualization](#visualization)
- [CI/CD Pipeline](#cicd-pipeline)
- [Dockerization](#dockerization)
- [Deployment on AWS EC2](#deployment-on-aws-ec2)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project performs sentiment analysis on YouTube comments using several classification algorithms. After extensive experimentation, **LightGBM** emerged as the best performing model. The project is designed to be reproducible, maintainable, and scalable using best practices in data science and software engineering.

---

## Features

- **Multiple Classification Algorithms:** Run and compare various classifiers to find the best model. LightGBM was determined to be the top performer.
- **Data Versioning:** Integrated with [DVC](https://dvc.org/) to track data changes and manage data pipeline versions.
- **Experiment Tracking:** Utilizes [MLflow](https://mlflow.org/) for tracking hyperparameters, metrics, and model versions.
- **Google Chrome Extension:** A custom-built extension that integrates the sentiment analysis model to visualize:
  - Average counts for Positive, Negative, and Neutral comments.
  - A trend line depicting sentiment over time.
  - A word cloud showing the frequency of comment terms.
- **CI/CD Pipeline:** Automated testing and deployment pipeline ensuring consistent builds.
- **Containerization:** Dockerized for reproducible environments.
- **Cloud Deployment:** Deployed on AWS EC2 for robust hosting.

---

# Setup and Installation

## Clone the Repository

git clone https://github.com/fahimai001/Google Chrome Plugin For Youtube Comments Sentiment Analysis.git
cd Google Chrome Plugin For Youtube Comments Sentiment Analysis

# Create a Virtual Environment

python3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate


# Install Dependencies

pip install -r requirements.txt


# Data Versioning with DVC

DVC is used to track data changes and pipeline versions.

* Initialize DVC (if not already initialized):

dvc init


* Add Data Files to DVC:

dvc add data/your_dataset.csv


* Commit the Changes:

git add data/your_dataset.csv.dvc .gitignore
git commit -m "Add dataset with DVC tracking"


* Push Data to Remote Storage (ensure you have configured a remote):

dvc remote add -d myremote s3://your-bucket/path
dvc push


# Experiment Tracking with MLflow

MLflow is used to track hyperparameters, metrics, and model versions.

* Start the MLflow Tracking Server (if required):

mlflow server --backend-store-uri sqlite:///mlflow.db --default-artifact-root ./mlruns


* Run Training with MLflow Tracking:

The train.py script is integrated with MLflow. Run it as follows:

python src/train.py


# Model Training and Evaluation

python src/train.py --all-models


# Google Chrome Extension Integration

The extension integrates the sentiment analysis model to provide real-time insights on YouTube videos.

1. Load the Extension:
* Open Google Chrome and navigate to chrome://extensions/
* Enable "Developer mode"
* Click "Load unpacked" and select the extension/ folder from the project

2. Usage on YouTube:

* Open any YouTube video.

* The extension will display:

 * Average Comments: Count of Positive, Negative, and Neutral comments.
 * Trend Line: Sentiment trend over time.
 * Word Cloud: Visualization highlighting frequently occurring terms in the comments.

# Visualization

When the Chrome extension runs, it visualizes the following:
 * Average Sentiment Counts: Calculates and displays the average number of positive, negative, and neutral comments.
 * Trend Line: A dynamic graph showing the progression of sentiment across the video timeline.
 * Word Cloud: A word cloud where word size reflects the frequency of appearance in the comments.

# CI/CD Pipeline

A CI/CD pipeline is configured to automate testing, building, and deployment.

1. Configuration:

 * The pipeline configuration files are located in the ci/ folder.
 * Example (for GitHub Actions):

 name: CI/CD Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.8'
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run Tests
        run: pytest --maxfail=1 --disable-warnings -q
  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to AWS EC2
        run: |
          # Add your deployment commands here
          ssh -i "your-key.pem" ec2-user@your-ec2-instance "bash deploy.sh"


2. Triggering the Pipeline:

 * Push changes to the main branch to trigger the CI/CD workflow.

# Dockerization

The model and associated services are containerized using Docker.

1. Build the Docker Image:
 docker build -t youtube-sentiment-analysis -f docker/Dockerfile .

2. Run the Docker Container:

 docker run -p 5000:5000 youtube-sentiment-analysis

3. Docker Compose (if applicable):
 docker-compose -f docker/docker-compose.yml up --build

# Deployment on AWS EC2

1. Launch an EC2 Instance:

 * Install Docker on the EC2 Instance:

 sudo yum update -y
 sudo amazon-linux-extras install docker
 sudo service docker start
 sudo usermod -a -G docker ec2-user
 exit

# Deploy the Docker Container:

Transfer your Docker image or pull from a container registry.
Run the container as described in the Dockerization section.

## Access the Application:

 * Open your browser and navigate to http://<EC2_PUBLIC_IP>:5000 (or the configured port).

# Usage

After deployment, users can:
 * Analyze YouTube Comments: Run the analysis locally or via the deployed model.
 * Visualize Sentiment: Use the Chrome extension on any YouTube video to see sentiment trends, averages, and word clouds.
 * Monitor Experiments: Check model performance and experiment logs using MLflow.
 * Version Control Data: Keep track of data changes with DVC.

# Contributing

 Contributions are welcome! Please fork the repository and create a pull request with your changes. For major changes, please open an issue first to discuss what you would like to change.









