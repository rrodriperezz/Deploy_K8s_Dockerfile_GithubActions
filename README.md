# Deploy_K8s_Dockerfile_GithubActions

API en FastAPI empaquetada en Docker y desplegada a Kubernetes con GitHub Actions en cada push a `main`.

![Despliegue](docs/despliegue.svg)

## Correrlo

```bash
pip install -r requirements.txt
bash start.sh
```

Docs de la API: http://localhost:8080/docs. Endpoints: `GET /ping` y `POST /create`.

## Pipeline

1. **build:** instala dependencias.
2. **deploy:** construye la imagen, la sube a Docker Hub y, por SSH, aplica los manifiestos de `k8s/` con `kubectl` en una VM con Kubernetes.

Secrets necesarios: `DOCKER_USERNAME`, `DOCKER_PASSWORD`, `DOCKER_REGISTRY`, `SSH_PRIVATE_KEY`, `VM_HOST`, `VM_USER`.
