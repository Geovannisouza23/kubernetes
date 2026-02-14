# 🧪 Kubernetes Prático – Pods, ReplicaSet, Deployment e Helm Charts

Este repositório contém exemplos práticos para estudo de Kubernetes “puro” com `kubectl` e Helm, utilizando a seguinte estrutura de diretórios:

```
kubernetes/
├── pod.yaml
├── rs.yaml
├── deploy.yaml
└── charts/
    └── nginx-chart/
        ├── Chart.yaml
        ├── values.yaml
        └── templates/
            ├── deployment.yaml
            ├── service.yaml
            └── _helpers.tpl
```

O objetivo é aprender na prática:

* Criação de Pods
* ReplicaSets
* Deployments
* Helm Charts (templates e values)

---

# 📋 Pré-requisitos

Instale as ferramentas abaixo:

* kubectl
* Minikube ou Kind
* Helm

## 🚀 Iniciar cluster local (exemplo com Minikube)

```bash
minikube start
kubectl get nodes
```

---

# 📦 1. Pod (kubernetes/pod.yaml)

Um Pod é a menor unidade do Kubernetes e executa um ou mais containers.

## 📄 Aplicar o Pod

```bash
kubectl apply -f kubernetes/pod.yaml
```

## 🔍 Verificar

```bash
kubectl get pods
kubectl describe pod nginx-pod
```

## 🧹 Remover

```bash
kubectl delete -f kubernetes/pod.yaml
```

---

# 🔁 2. ReplicaSet (kubernetes/rs.yaml)

O ReplicaSet garante que um número específico de Pods esteja sempre em execução.

## 📄 Aplicar ReplicaSet

```bash
kubectl apply -f kubernetes/rs.yaml
```

## 🔍 Verificar réplicas

```bash
kubectl get rs
kubectl get pods
```

## 📈 Escalar manualmente

```bash
kubectl scale rs nginx-rs --replicas=5
```

## 🧹 Remover

```bash
kubectl delete -f kubernetes/rs.yaml
```

---

# 🚀 3. Deployment (kubernetes/deploy.yaml)

Deployment gerencia ReplicaSets e permite atualizações e rollback de versão.

## 📄 Aplicar Deployment

```bash
kubectl apply -f kubernetes/deploy.yaml
```

## 🔍 Verificar

```bash
kubectl get deployments
kubectl get pods
```

## 🔄 Atualizar imagem do container

```bash
kubectl set image deployment/nginx-deploy nginx=nginx:latest
```

## ⏪ Rollback

```bash
kubectl rollout undo deployment/nginx-deploy
```

## 🧹 Remover

```bash
kubectl delete -f kubernetes/deploy.yaml
```

---

# 📦 4. Helm Chart (charts/nginx-chart)

O Helm é o gerenciador de pacotes do Kubernetes.
Aqui utilizamos um chart localizado em:

```
kubernetes/charts/nginx-chart/
```

### Estrutura do Chart

```
nginx-chart/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    └── _helpers.tpl
```

---

## ▶️ Instalar o Chart

```bash
cd kubernetes/charts/nginx-chart
helm install nginx-release .
```

## 🔍 Verificar recursos criados

```bash
kubectl get all
```

## 🔄 Atualizar Chart após mudanças

```bash
helm upgrade nginx-release .
```

## 🧹 Remover Chart

```bash
helm uninstall nginx-release
```

---

# 📊 Comandos Úteis para Debug

```bash
kubectl get all
kubectl get pods -o wide
kubectl logs <pod-name>
kubectl exec -it <pod-name> -- /bin/bash
kubectl describe pod <pod-name>
```

---

# 🧠 Exercícios Práticos

1. Criar o Pod com `pod.yaml`
2. Substituir por ReplicaSet com 3 réplicas
3. Migrar para Deployment
4. Atualizar versão do Nginx com rollout
5. Fazer rollback da aplicação
6. Instalar o Helm Chart
7. Alterar `values.yaml` e aplicar upgrade

---

# 🎯 Objetivo do Projeto

Ao concluir estes testes você terá domínio prático sobre:

* Pods
* ReplicaSets
* Deployments
* Rollout e Rollback
* Helm Charts (Chart.yaml, values.yaml e templates)

---

## 👨‍💻 Autor

**Geovanni Souza** 🚀
Laboratório prático de Kubernetes para estudos e testes hands-on.
