# CI/CD Monorepo

This repository contains a monorepo for two applications, FirstApp and SecondApp, that share a common `Modules` folder.

## Directory Structure

The structure of the monorepo is as follows:

.
├── FirstApp
│ ├── file1
│ ├── file2
│ └── ...
├── SecondApp
│ ├── file1
│ ├── file2
│ └── ...
└── Modules
├── file1
├── file2
└── ...

- The `FirstApp` directory contains files specific to the FirstApp application.
- The `SecondApp` directory contains files specific to the SecondApp application.
- The `Modules` directory contains shared files that are used by both applications.

## CI/CD Pipeline

The repository is configured with a CI/CD pipeline using GitHub Actions. The pipeline is triggered on pushes to the `main` branch and performs the following actions:

- If there is a change in the `FirstApp` folder, only the FirstApp is built.
- If there is a change in the `SecondApp` folder, only the SecondApp is built.
- If there is a change in the `Modules` folder, both FirstApp and SecondApp are built.

During the build process for either FirstApp or SecondApp, the `Modules` folder is copied into the respective app's folder.

## Docker Images

The built Docker images are pushed to GitHub Container Registry (GHCR) with the following naming convention:

- FirstApp: `ghcr.io/Shahid199578/firstapp:<commit-sha>`
- SecondApp: `ghcr.io/Shahid199578/secondapp:<commit-sha>`

Replace `<commit-sha>` with the commit SHA of the corresponding build.

## Getting Started

To use this monorepo or run the CI/CD pipeline locally, you can follow these steps:

1. Clone the repository:

   ```
   git clone https://github.com/Shahid199578/CI-CD-Monorepo.git
   ```
   
Make the necessary changes or additions to the FirstApp, SecondApp, and Modules directories.

2. Commit and push your changes to the master branch:
```git add .
git commit -m "Update code"
git push origin master
```
3. Monitor the CI/CD pipeline in the "Actions" tab of the repository on GitHub.

4. Once the pipeline completes, the Docker images will be available in GHCR for use or deployment.

For more details on how the CI/CD pipeline is set up, please refer to the workflow file ci-cd.yml