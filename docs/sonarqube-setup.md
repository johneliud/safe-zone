# SonarQube Setup Documentation

## Docker Run Command

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube:latest
```

## Configuration

| Parameter | Value | Description |
|-----------|-------|-------------|
| `-d` | - | Run in detached mode |
| `--name` | sonarqube | Container name |
| `-p` | 9000:9000 | Port mapping (host:container) |
| Image | sonarqube:latest | Official SonarQube Community Edition |

## Access

- **Local URL**: http://localhost:9000
- **Public URL (via Ngrok)**: [Your Ngrok URL]
- **Default credentials**: admin / admin

## Project Details

| Parameter | Value |
|-----------|-------|
| Project Name | ecommerce-microservices |
| Project Key | ecommerce-microservices |
| Build Tool | Maven |

## Remote Integration (Ngrok)

To allow GitHub Actions to reach your local SonarQube instance:
1. Start Ngrok: `ngrok http 9000`
2. Update `SONAR_HOST_URL` in GitHub Secrets with the provided HTTPS URL.
3. Ensure `SONAR_TOKEN` is also added to GitHub Secrets.

## Notes

- SonarQube requires adequate memory for Elasticsearch
- Initial startup takes ~1-2 minutes
- Data is stored in the container (not persistent by default)
- For production, add volume mounts for data persistence:
  ```bash
  docker run -d --name sonarqube -p 9000:9000 \
    -v sonarqube_data:/opt/sonarqube/data \
    -v sonarqube_logs:/opt/sonarqube/logs \
    -v sonarqube_extensions:/opt/sonarqube/extensions \
    sonarqube:latest
  ```
