## HomeLabOps

Projekt homelabowy do nauki DevOps w praktyce.
Buduję właśną platformę self-hosted na Ubuntu PC
i Raspberry Pi 5, ucząc się narzędzi potrzebnych 
do pracy jako Junior DevOps.

## Infrastuktura 

- Ubuntu PC - głowny server (192.168.137.10)
- Raspberry Pi 5 - przyszły węzeł Kubernetes (192.168.178.11)
- Windows 11 - stacja robocza

## Serwisy
### Działające
- Gitea - własne repozytorium Git (192.168.137.10:3000)

### Planowane
- Nextcloud - własna chmura
- Uptime Kuma - monitoring dostępności 
- Grafana + Prometheus - monitoring metryk

## Stack technologiczny
- OS: Ubuntu 24.04 LTS, Raspberry Pi OS Lite (64-bit)
- Konteneryzacja: Docker, Docker Compose
- Wersjonowanie: Git, Gitea
- Planowane: k3s, Ansible, Prometheus, Grafana

## Status MileStonów

## M1 - Fundament - Git, SSH, Sieć

- [x] Skonfiguruj statyczne IP na Ubuntu PC i Raspberry Pi
- [x] Zainstaluj i skonfiguruj SSH: generuj klucze ed25519, wyłącz auth hasłem
- [x] Utwórz repo Git dla projektu HomeLabOps z branch strategy (main / dev / feature/*)
- [x] Naucz się: git branch, git checkout -b, git merge, git rebase, git tag
- [x] Postaw Gitea na Ubuntu PC (Docker run, pierwszy kontakt z kontenerami)
- [x] Skonfiguruj Windows 11 jako stację roboczą: VSCode + WSL2 + Git Bash
- [x] Napisz pierwszy README.md dokumentujący infrastrukturę (Markdown, diagram ASCII)
- [x] Ustaw Raspberry Pi OS Lite, podłącz przez SSH z PC i Windowsa

## M2 - Docker & Docker Compose - Konteneryzacja

- [ ] Zainstaluj Docker Engine + Docker Compose v2 na Ubuntu PC
- [ ] Rozumienie: docker run, exec, logs, inspect, stop, rm, prune
- [ ] Napisz docker-compose.yml dla Nextcloud (app + MariaDB + Redis)
- [ ] Postaw Uptime Kuma do monitorowania dostępności usług
- [ ] Skonfiguruj Nginx Proxy Manager jako reverse proxy (wszystko pod jednym portem 443)
- [ ] Zarządzaj sekretami przez pliki .env + dodaj .env do .gitignore
- [ ] Skonfiguruj Docker na Raspberry Pi (ARM64) — wdróż Uptime Kuma jako node
- [ ] Udokumentuj każdy serwis w repozytorium (README + docker-compose)

## M3 - CI/CD Pipeline - Automatyzacja Deploymentu

- [ ] Zainstaluj Gitea Actions runner na Ubuntu PC
- [ ] Napisz pipeline: on push → validate docker-compose → deploy na serwer
- [ ] Dodaj stage "lint" — walidacja plików YAML (yamllint)
- [ ] Skonfiguruj deploy przez SSH: pipeline loguje się na serwer i robi docker compose pull + up
- [ ] Przetestuj rollback: git revert + automatyczny re-deploy poprzedniej wersji
- [ ] Zautomatyzuj tagowanie wersji: git tag → pipeline tworzy "release" w Gitea
- [ ] Skonfiguruj powiadomienia pipeline (email / webhook do Uptime Kuma)

## M4 - Kubernetes (k3s) - Raspberry Pi jako klaster

- [ ] Zainstaluj k3s na Ubuntu PC (master node)
- [ ] Dołącz Raspberry Pi jako worker node do klastra
- [ ] Naucz się kubectl: get, describe, apply, delete, logs, exec, port-forward
- [ ] Wdróż Gitea na k3s używając manifestów YAML (Deployment + Service + PVC)
- [ ] Zainstaluj Helm i wdróż pierwszą aplikację przez helm install
- [ ] Skonfiguruj Traefik Ingress (wbudowany w k3s) z routingiem po hostname
- [ ] Przetestuj self-healing: usuń pod ręcznie → obserwuj jak k3s go odtworzy
- [ ] Napisz manifest dla Uptime Kuma z PersistentVolumeClaim

## M5 -  Monitoring - Prometheus + Grafana

- [ ] Wdróż Prometheus + Grafana przez docker-compose (lub Helm na k3s)
- [ ] Zainstaluj Node Exporter na Ubuntu PC i Raspberry Pi
- [ ] Zbuduj dashboard Grafana: CPU, RAM, dysk, sieć — dla obu maszyn
- [ ] Dodaj cAdvisor — metryki kontenerów Docker
- [ ] Skonfiguruj alert: wysyłaj email gdy CPU > 80% przez 5 minut
- [ ] Naucz się podstaw PromQL: rate(), avg_over_time(), histogram_quantile()
- [ ] Zrób screenshot dashboardu i dodaj do portfolio README

## M6 - Infrastructure as Code - Ansible + Backup

- [ ] Zainstaluj Ansible na Ubuntu PC, skonfiguruj inventory (PC + Pi)
- [ ] Napisz playbook: fresh install całego stacku na nowej maszynie
- [ ] Użyj Ansible Vault do szyfrowania haseł i kluczy API
- [ ] Zautomatyzuj backup Nextcloud (dane + DB) do zewnętrznego dysku / chmury
- [ ] Przetestuj disaster recovery: usuń dane, przywróć z backupu
- [ ] Zorganizuj role Ansible: osobno dla docker, monitoring, backup
- [ ] Dodaj playbook uruchamiany przez CI/CD pipeline

## M7 -  Portfolio & Demo - Przygotowanie do Rekrutacji

- [ ] Stwórz publiczne repo GitHub "homelab-ops" z profesjonalnym README
- [ ] Udokumentuj architekturę: diagram infra (draw.io / Excalidraw)
- [ ] Nagranie demo 3–5 min: pipeline uruchomiony, deploy widoczny, Grafana żywa
- [ ] Przygotuj odpowiedzi na 10 pytań rekrutacyjnych (CI/CD, Docker, K8s basics)
- [ ] Dodaj do CV sekcję "Projekty": HomeLabOps z linkiem do repo i demo
- [ ] Zgłoś się do 3 firm Junior DevOps z gotowym CV i linkiem do projektu







