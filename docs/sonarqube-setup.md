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

- **URL**: http://localhost:9000
- **Default credentials**: admin / admin

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
