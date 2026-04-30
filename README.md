# Deploy Pipeline Project

Projeto Node.js com duas estratégias de deploy: Docker e Kubernetes (GCP).

## 📋 Estrutura

- **`main`** - Branch principal
- **`deploy-docker`** - Deploy em container Docker
- **`deploy-kubernetes`** - Deploy em cluster Kubernetes (GCP/GKE)

## 🐳 Branch: deploy-docker

Deploy simples da aplicação em um container Docker.

### Arquivos:

- `.gitlab-ci.yml` - Pipeline GitLab CI/CD para build e push no Docker Hub
- `docker-compose.yml` - Arquivo para testes locais
- `Dockerfile` - Imagem Docker da aplicação

### Como usar:

1. Faz push na branch `deploy-docker`
2. GitLab CI/CD faz build da imagem
3. Push automático para Docker Hub
4. Deploy do container

### Variáveis de ambiente necessárias no GitLab:

- `DOCKER_USERNAME` - Seu usuário Docker Hub
- `DOCKER_PASSWORD` - Seu token Docker Hub

## ☸️ Branch: deploy-kubernetes

Deploy da aplicação em cluster Kubernetes na GCP (Google Cloud Platform).

### Arquivos:

- `.gitlab-ci.yml` - Pipeline GitLab CI/CD para GKE
- `kubernetes/manifests/deployment.yaml` - Deployment Kubernetes
- `kubernetes/manifests/service.yaml` - Service LoadBalancer
- `kubernetes/manifests/configmap.yaml` - Variáveis de configuração

### Como usar:

1. Cria conta GCP (https://cloud.google.com)
2. Cria um cluster GKE
3. Configura as variáveis de ambiente no GitLab
4. Faz push na branch `deploy-kubernetes`
5. GitLab CI/CD faz deploy automático no GKE

### Variáveis de ambiente necessárias no GitLab:

- `DOCKER_USERNAME` - Seu usuário Docker Hub
- `DOCKER_PASSWORD` - Seu token Docker Hub
- `GCP_SERVICE_ACCOUNT_KEY` - Chave de serviço GCP (base64)
- `GCP_PROJECT_ID` - ID do projeto GCP
- `GKE_CLUSTER_NAME` - Nome do cluster GKE
- `GKE_ZONE` - Zona do cluster (ex: us-central1-a)

## 🚀 Próximos passos

1. Migrar repositório para GitLab (opcional)
2. Criar conta GCP e cluster GKE
3. Configurar variáveis de ambiente no GitLab
4. Testar pipelines em ambas as branches

## 📝 Notas

- A aplicação roda na porta 3000
- Replicas padrão no Kubernetes: 3
- LoadBalancer expõe a aplicação na porta 80
