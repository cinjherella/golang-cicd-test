# golang-cicd-test

A proof-of-concept Go application demonstrating CI/CD pipeline implementation using AWS CodeBuild.

## Overview

This project showcases a simple Go application with automated build and deployment using AWS CodeBuild. The application prints a custom message and serves as a foundation for understanding CI/CD workflows in AWS.

## Project Structure

```
golang-cicd-test/
├── helpers/
│   └── output.go          # Helper package with constants
├── buildspec.yml          # AWS CodeBuild configuration
├── go.mod                 # Go module definition
├── main.go                # Main application entry point
└── README.md              # Project documentation
```

## Prerequisites

- Go 1.23 or later
- AWS CLI configured (for CodeBuild deployment)
- AWS CodeBuild project setup

## Local Development

### Installation

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd golang-cicd-test
   ```

2. Install dependencies:
   ```bash
   go mod tidy
   ```

### Running Locally

```bash
go run main.go
```

Expected output:

```
CICD Test by Jaineyyy!
```

### Building

```bash
go build -o main .
./main
```

## CI/CD Pipeline

### AWS CodeBuild Configuration

The project uses AWS CodeBuild for automated building. The pipeline is configured via `buildspec.yml`:

- **Runtime**: Go 1.23
- **Build Process**:
  - Dependency resolution with `go mod tidy`
  - Cross-compilation for macOS ARM64
- **Artifacts**: Compiled binary (`main`)

### Pipeline Phases

1. **Install Phase**: Sets up Go 1.23 runtime
2. **Build Phase**:
   - Resolves dependencies
   - Compiles application for macOS ARM64
3. **Artifacts**: Outputs the compiled binary

### Deployment

To set up the CI/CD pipeline:

1. Create an AWS CodeBuild project
2. Connect to your Git repository
3. Use the included `buildspec.yml` configuration
4. Configure appropriate IAM permissions

## Architecture

- **main.go**: Entry point that imports and uses the helpers package
- **helpers/output.go**: Contains application constants and helper functions
- **buildspec.yml**: Defines the build process for AWS CodeBuild

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test locally
5. Submit a pull request

## License

This is a proof-of-concept project for learning CI/CD with AWS CodeBuild.
