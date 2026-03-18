# Safe Zone: E-Commerce Microservices Security Integration

This project is a dedicated security and quality assurance workspace for a microservices-based e-commerce platform. It focuses on integrating **SonarQube** into the CI/CD pipeline to ensure high code quality, detect vulnerabilities, and enforce robust quality gates across multiple services.

## Architecture & Repositories

The platform consists of several independent microservices:

*   **User Service**: [User Service Microservice](https://github.com/johneliud/user-service)
*   **Product Service**: [Product Service Microservice](https://github.com/johneliud/product-service)
*   **Media Service**: [Media Service Microservice](https://github.com/johneliud/media-service)
*   **API Gateway**: [API Gateway](https://github.com/johneliud/api-gateway)
*   **Frontend**: [Frontend Microservice](https://github.com/johneliud/frontend)

## Getting Started

### Prerequisites

*   **Docker**: To run the SonarQube container.
*   **Ngrok**: To expose the local SonarQube instance to GitHub Actions.
*   **Java 17+ & Maven**: For service builds and analysis.

### Installation

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/johneliud/safe-zone.git
    cd safe-zone
    ```

2.  **Start SonarQube**:
    Follow the instructions in `docs/sonarqube-setup.md` to run the SonarQube container via Docker.

3.  **Expose the Dashboard**:
    If testing with GitHub Actions locally:
    ```bash
    ngrok http 9000
    ```

## Project Objectives

1.  **Automated Static Analysis**: Every push and PR triggers a SonarQube scan.
2.  **Vulnerability Detection**: Early identification of OWASP Top 10 and other security risks.
3.  **Quality Gates**: Automated blocks on merging code that does not meet coverage or quality standards.
4.  **Continuous Monitoring**: Real-time dashboard for cross-service health metrics.

---
*For detailed setup guides, see the `/docs` directory.*
