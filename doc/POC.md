# Proof of Concept: ArgoCD Deployment

Цей документ описує процес розгортання та налаштування ArgoCD на Kubernetes кластері, розгорнутому за допомогою Kind.

Створення кластера:


kind create cluster --name asciiartify-cluster
Активація Kubernetes-контексту:


kubectl cluster-info --context kind-asciiartify-cluster
Встановлення та налаштування ArgoCD
Створення простору імен ArgoCD:


kubectl create namespace argocd
Встановлення ArgoCD:


kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
Налаштування порт-форвардингу для доступу до веб-інтерфейсу ArgoCD:


kubectl port-forward svc/argocd-server -n argocd 8080:80
Отримання початкового пароля для адміністратора:


kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
Збережіть пароль для подальшого входу в систему.

Вхід до веб-інтерфейсу ArgoCD:

Адреса: http://localhost:8080
Логін: admin
Пароль:
