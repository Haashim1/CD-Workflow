# CI/CD Task 2 – Docker CD Workflow

## Project Overview

This project demonstrates a simple Continuous Deployment (CD) workflow using GitHub Actions and Docker.

When changes are pushed to the `main` branch, GitHub Actions automatically:

1. Checks out the project.
2. Builds the Docker image.
3. Pushes the Docker image to GitHub Container Registry (GHCR).

## Project Structure

```text
CICD-Task2/
├── app/
│   └── app.py
├── .github/
│   └── workflows/
│       └── docker-cd.yml
├── Dockerfile
└── README.md
```

### Project Files

- [Application – `app/app.py`](https://github.com/Haashim1/CD-Workflow/blob/main/app/app.py)
- [Dockerfile](https://github.com/Haashim1/CD-Workflow/blob/main/Dockerfile)
- [CD Workflow – `docker-cd.yml`](https://github.com/Haashim1/CD-Workflow/blob/main/.github/workflows/docker-cd.yml)
- [Workflows Folder](https://github.com/Haashim1/CD-Workflow/tree/main/.github/workflows)
- [Application Folder](https://github.com/Haashim1/CD-Workflow/tree/main/app)

## Application

The application is a simple Python program that prints:

```text
Hello from my CI/CD Task 2 application!
```

The application source code can be viewed here:

[View `app.py`](https://github.com/Haashim1/CD-Workflow/blob/main/app/app.py)

## Docker

The application is packaged into a Docker image using the [Dockerfile](https://github.com/Haashim1/CD-Workflow/blob/main/Dockerfile).

To build the image locally:

```bash
docker build -t cicd-task2 .
```

To run the container:

```bash
docker run --rm cicd-task2
```

The container successfully runs the Python application and displays the expected message.

## Continuous Deployment Workflow

The GitHub Actions workflow is located at:

[`.github/workflows/docker-cd.yml`](https://github.com/Haashim1/CD-Workflow/blob/main/.github/workflows/docker-cd.yml)

The workflow runs automatically whenever code is pushed to the `main` branch.

It:

1. Checks out the repository.
2. Logs in to GitHub Container Registry.
3. Builds the Docker image.
4. Pushes the image to GitHub Container Registry.

The Docker image is published as:

```text
ghcr.io/haashim1/cd-workflow:latest
```

## Technologies Used

- Python
- Docker
- GitHub Actions
- GitHub Container Registry (GHCR)
- Git

## Result

The CD workflow was successfully implemented using GitHub Actions.

During the first workflow run, the build failed because the Docker image name contained an uppercase letter:

```text
ghcr.io/Haashim1/cd-workflow:latest
```

Docker image repository names must use lowercase characters. The workflow was therefore updated to use:

```text
ghcr.io/haashim1/cd-workflow:latest
```

After making this correction and pushing the updated workflow, the GitHub Actions workflow completed successfully.

The final workflow automatically builds the Docker image and pushes it to GitHub Container Registry whenever changes are pushed to the `main` branch.

<img width="1082" height="561" alt="Screenshot 2026-09-21 at 13 20 47" src="https://github.com/user-attachments/assets/0c86a4a1-9da1-4a57-a698-9f1b125a8cd8" />
