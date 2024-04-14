# Dotnet Jenkins Demo

This repository contains a demo .NET application integrated with Jenkins for continuous integration and deployment.

## Usage

1. Clone this repository:


2. Set up Jenkins with the following stages in your pipeline:

- **Checkout Stage:** Check out the source code from the repository.
- **Build Stage:** Compile the solution file (`DotnetApp.sln`) using the .NET CLI.
- **Test Stage:** Run tests for the project.
- **Release Stage:** Build the solution file with specific configurations.
- **Deploy Stage:** Deploy the application on IIS.

3. Ensure you have the necessary tools installed, such as .NET CLI and Microsoft Web Deploy V3.

4. Customize the paths and configurations in the Jenkinsfile according to your environment.

5. Run the Jenkins pipeline and monitor the execution of each stage.

## Folder Structure

- **DotnetApp:** Contains the .NET application code.
- **DotnetApp/Properties/PublishProfiles:** Contains publish profiles for deployment.
