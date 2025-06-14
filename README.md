# Proyecto Kubernetes con Minikube

Este proyecto contiene una aplicación desplegada en un clúster Kubernetes usando Minikube y Docker como driver.

---

## Requisitos previos

- Minikube instalado (https://minikube.sigs.k8s.io/docs/start/)
- Docker instalado y corriendo
- kubectl instalado y configurado

---

## Pasos para iniciar el clúster

###  Usuarios de Bash (Linux/macOS/Git Bash)

1. Iniciar Minikube con Docker como driver:

   ```bash
   minikube start --driver=docker
   ```

2. Configurar Docker para usar el daemon de Minikube:

   ```bash
   eval $(minikube docker-env)
   ```

3. Aplicar los manifiestos de Kubernetes:

   ```bash
   kubectl apply -f k8s/
   ```

4. Ver Pods:

   ```bash
   kubectl get pods
   ```

---

###  Usuarios de PowerShell (Windows)

1. Iniciar Minikube con Docker como driver:

   ```powershell
   minikube start --driver=docker
   ```

2. Configurar Docker para usar el daemon de Minikube:

   ```powershell
   minikube -p minikube docker-env | Invoke-Expression
   ```

3. Aplicar los manifiestos de Kubernetes:

   ```powershell
   kubectl apply -f k8s/
   ```

4. Ver Pods:

   ```powershell
   kubectl get pods
   ```

---

## Exposición de servicios con LoadBalancer

Para exponer servicios y obtener una IP accesible desde tu máquina:

- En Bash o PowerShell, en otra terminal ejecutá:

   ```bash
   minikube tunnel
   kubectl get svc
   ```

- Luego abrí la IP que aparece en `EXTERNAL-IP` en tu navegador.

---

## Comandos útiles

- Listar nodos:

   ```bash
   kubectl get nodes
   ```

- Ver pods en todos los namespaces:

   ```bash
   kubectl get pods -A
   ```

- Ver detalles de un pod:

   ```bash
   kubectl describe pod <nombre-pod>
   ```

- Ver logs de un pod:

   ```bash
   kubectl logs <nombre-pod>
   ```

---

## Notas adicionales

- Minikube está diseñado para desarrollo local y pruebas.
- Para entornos reales se recomienda usar clústers en la nube (EKS, GKE, o AKS).
- Si cambiás de driver (por ej. Hyper-V a Docker), eliminá el clúster anterior con:

   ```bash
   minikube delete
   ```

---

## Autor

**Martín Giménez** – martinchogimenez@gmail.com
