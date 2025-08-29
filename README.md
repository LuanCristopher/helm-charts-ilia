# Helm Charts – Desafio Ília

Este repositório contém os **Helm charts** utilizados no desafio técnico da Ília para gerenciar aplicações no cluster EKS.

### Estrutura:
- `api/` → Chart para deploy da API em Python.
- `grafana/` → Chart para deploy do Grafana, configurado com datasources (Athena, Prometheus).
- `apps/` → Chart para deploy do Prometheus e outras features.

### Destaques:
- **API**
  - Uso do **hash do commit** como tag da imagem, garantindo rastreabilidade.
  - Configuração de probes (`/healthz` e `/readyz`).
  - Requests e limits de CPU/memória.
- **Grafana**
  - Configurado com **IRSA** para acessar Athena.
  - Persistência via PVC (gp3).
  - Estratégia de deploy RollingUpdate sem downtime.
- **ArgoCD**
  - Utilizado para sincronizar automaticamente os charts com o cluster.

### CI/CD:
- Cada chart passa por validação via **GitHub Actions** antes do deploy.

---

Este repositório centraliza os manifestos Helm, integrados ao **ArgoCD**, para manter o cluster EKS atualizado conforme alterações no Git.
