# Log Classification with Hybrid Approach

This repository contains a hybrid log classification system that leverages BERT embeddings, LLM (DeepSeek), and Regex-based classification for accurate log categorization. The system integrates machine learning, deep learning, and rule-based techniques to classify log messages efficiently.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Folder Structure](#folder-structure)

## Introduction

This project implements a hybrid classification approach for log messages using:

- BERT Embeddings (via Sentence Transformers) for semantic representation.
- Logistic Regression for traditional machine learning-based classification.
- Regex-based Classification for predefined pattern matching.
- LLM (DeepSeek) to enhance classification with contextual understanding.
- FastAPI for serving the model via an API interface.
  By combining these techniques, the system ensures both high accuracy and interpretability in classifying log messages.

## Features

- Hybrid classification using BERT embeddings, LLM DeepSeek, and Regex.
- Trainable ML models using Sentence Transformer and Logistic Regression.
- Regex-based classification for predefined log patterns.
- FastAPI for serving predictions via a REST API.
- Pretrained models support for quick deployment.

## Installation

1. Clone the repository to your local machine:

```
   git clone https://github.com/srijosh/Log-Classification-with-Hybrid-Approach.git
```

2. Navigate to the project directory:

```
   cd Log-Classification-with-Hybrid-Approach
```

3. Install the required dependencies:

```
   pip install -r requirements.txt
```

4. Set up environment variables by creating a .env file (Use .env.sample as a reference for setting up your .env file.)

## Usage

1. Start the FastAPI server:

```
   uvicorn server:app --host 0.0.0.0 --port 8000
```

2. Once the FastAPI server is running, you can send log classification requests using cURL, requests (Python) or Postman:

```
   curl -X POST "http://localhost:8000/classify/" -H "Content-Type: multipart/form-data" -F "file=@resources/test.csv" -o resources/output.csv

```

```
   #using requests
   import requests

   url = "http://localhost:8000/classify/"
   files = {"file": open("resources/test.csv", "rb")}
   response = requests.post(url, files=files)

   with open("resources/output.csv", "wb") as f:
      f.write(response.content)

   print("Classified logs saved as classified_logs.csv")


```

## Folder Structure

1. training/:

- Contains the code for training models using Sentence Transformer and Logistic Regression.
- Includes the regex-based classification logic.

2. models/:

- Stores the trained models, including BERT-based embeddings and the Logistic Regression model.

3. resources/:

- Contains test CSV files, output logs, and other supporting files.

4. Root Directory:

- Houses the FastAPI server code (server.py).
