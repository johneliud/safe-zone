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

| Service | Repository | Project Key |
|-----------|-------|-------------|
| User Service | [user-service](https://github.com/johneliud/user-service) | `user-service` |
| Product Service | [product-service](https://github.com/johneliud/product-service) | `product-service` |
| Media Service | [media-service](https://github.com/johneliud/media-service) | `media-service` |
| API Gateway | [api-gateway](https://github.com/johneliud/api-gateway) | `api-gateway` |
| Frontend | [frontend](https://github.com/johneliud/frontend) | `frontend` |

## GitHub Integration (Task 3)

The following configurations are applied to each repository:
1. **Secrets**:
   - `SONAR_TOKEN`: Authentication token from SonarQube.
   - `SONAR_HOST_URL`: The Ngrok public URL.
2. **Workflow**: `.github/workflows/build.yml` triggers on every push and PR.
3. **Quality Gates**: Maven builds include `-Dsonar.qualitygate.wait=true` to enforce status checks.

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
