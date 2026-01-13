# TP DevSecOps avec Docker

[![Build and Scan](https://github.com/Maxime-Mathieu/devops-tp-docker-Maxime-MATHIEU/actions/workflows/docker-deploy.yml/badge.svg)](https://github.com/Maxime-MATHIEU/devops-tp-docker-Maxime-MATHIEU/actions/workflows/docker-deploy.yml)
[![CodeQL](https://github.com/Maxime-MATHIEU/devops-tp-docker-Maxime-MATHIEU/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/Maxime-MATHIEU/devops-tp-docker-Maxime-MATHIEU/actions/workflows/codeql-analysis.yml)
[![Dependabot](https://img.shields.io/badge/Dependabot-enabled-brightgreen)](https://dependabot.com/)
[![Secret Scanning](https://img.shields.io/badge/Secret_Scanning-enabled-brightgreen)](https://docs.github.com/en/code-security/secret-scanning)
[![SBOM](https://img.shields.io/badge/SBOM-generated-blue)](https://github.com/Maxime-MATHIEU/devops-tp-docker-Maxime-MATHIEU/security/dependabot)

---

## 📌 Pipeline DevSecOps

Ce projet met en œuvre un **pipeline CI/CD sécurisé** pour Docker, intégrant les meilleures pratiques DevSecOps :

- **Analyse statique du code** (CodeQL)
- **Lint du Dockerfile** (Hadolint)
- **Scan des images Docker** (Trivy)
- **Scan des dépendances** (Dependabot)
- **Détection de secrets** (GitHub Secret Scanning)
- **Portes de sécurité** (blocage sur vulnérabilités critiques)
- **Génération de SBOM** (Software Bill of Materials)

---

## 🔐 Architecture de Sécurité

Voici un exemple de README.md structuré, clair et professionnel pour ton TP DevSecOps avec Docker, incluant les badges, les instructions et les résultats attendus :

markdown
Copier

# TP DevSecOps avec Docker

[![Build and Scan](https://github.com/Maxime-Mathieu/devops-tp-docker-Maxime-Mathieu/actions/workflows/docker-deploy.yml/badge.svg)](https://github.com/Maxime-Mathieu/devops-tp-docker-[nom]/actions/workflows/docker-deploy.yml)
[![CodeQL](https://github.com/[username]/devops-tp-docker-[nom]/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/[username]/devops-tp-docker-[nom]/actions/workflows/codeql-analysis.yml)
[![Dependabot](https://img.shields.io/badge/Dependabot-enabled-brightgreen)](https://dependabot.com/)
[![Secret Scanning](https://img.shields.io/badge/Secret_Scanning-enabled-brightgreen)](https://docs.github.com/en/code-security/secret-scanning)
[![SBOM](https://img.shields.io/badge/SBOM-generated-blue)](https://github.com/[username]/devops-tp-docker-[nom]/security/dependabot)

---

## 📌 Pipeline DevSecOps

Ce projet met en œuvre un **pipeline CI/CD sécurisé** pour Docker, intégrant les meilleures pratiques DevSecOps :

- **Analyse statique du code** (CodeQL)
- **Lint du Dockerfile** (Hadolint)
- **Scan des images Docker** (Trivy)
- **Scan des dépendances** (Dependabot)
- **Détection de secrets** (GitHub Secret Scanning)
- **Portes de sécurité** (blocage sur vulnérabilités critiques)
- **Génération de SBOM** (Software Bill of Materials)

---

## 🔐 Architecture de Sécurité

Code → SAST (CodeQL) → Hadolint → Build → Trivy → Security Gates → GHCR

## Sécurité de l'Image

- Image de base : nginx:alpine (version spécifique)
- Utilisateur non-root
- Headers de sécurité renforcés
- Health checks
- Pas de secrets dans l'image

## Exécution Locale

```bash
docker pull ghcr.io/[username]/devops-tp-docker-[nom]:main
docker run -p 8080:8080 ghcr.io/[username]/devops-tp-docker-[nom]:main
```
Accéder à : http://localhost:8080

Scan de Sécurité Local
trivy image ghcr.io/[username]/devops-tp-docker-[nom]:main

---

## Résultats Attendus

À la fin de ce TP, vous devez avoir :

**Pipeline DevSecOps complet :**
- CodeQL pour l'analyse du code source
- Hadolint pour le lint du Dockerfile
- Trivy pour le scan des images
- Dependabot pour les dépendances
- Secret Scanning activé
- Security Gates fonctionnels

**Image Docker sécurisée :**
- Utilisateur non-root
- Image de base à jour
- Dépendances corrigées
- Headers de sécurité
- Pas de vulnérabilités HIGH/CRITICAL

**Visibilité :**
- Dashboard Security complet
- Alertes automatiques
- SBOM généré
- Badges dans README

---

## Commandes Trivy Avancées

```bash
# Scan d'un filesystem
trivy fs .

# Scan avec ignoré des unfixed
trivy image --ignore-unfixed nginx:alpine

# Scan de config Kubernetes
trivy config k8s-manifest.yaml

# Scan avec template personnalisé
trivy image --format template --template "@contrib/html.tpl" -o report.html nginx:alpine

# Liste des vulnérabilités par package
trivy image --list-all-pkgs nginx:alpine
