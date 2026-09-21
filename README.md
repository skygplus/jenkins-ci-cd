README.md# Jenkins CI/CD Pipeline

## Project Overview

This project demonstrates a Continuous Integration and Continuous Delivery
pipeline using Jenkins, GitHub, Python and automated testing.

## Technologies

- Jenkins
- Git
- GitHub
- Python
- Pytest
- Docker
- WSL2
- Ubuntu

## Pipeline Stages

The Jenkins pipeline contains the following stages:

1. Build
2. Test
3. Package
4. Deploy

## Build

The Build stage installs the required Python dependencies.

## Test

The Test stage executes automated unit tests using pytest.

The pipeline fails if any test fails.

## Package

The Package stage creates a build directory and copies the application
files into it.

## Deploy

The Deploy stage simulates deployment by copying the packaged application
into a deployment directory.

## Jenkinsfile

The Jenkins pipeline is defined using a Jenkinsfile stored in the root
of the Git repository.

## How to Run Locally

Run:

```bash
python3 app.py