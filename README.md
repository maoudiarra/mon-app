# 🚀 Atelier Pipeline as Code

## 📖 Description

Projet réalisé dans le cadre du module **Pipeline as Code** à l'EPSI.

L'objectif de cet atelier est de mettre en place une chaîne complète d'intégration et de déploiement continus (CI/CD) en utilisant :

- GitHub
- Jenkins
- Docker
- Next.js
- GitHub Pages
- Webhooks GitHub

---

## 👨‍🎓 Étudiant

**Nom :** Maou DIARRA

**Formation :** Master Ingénierie des Données - EPSI

---

## 🏗️ Architecture du projet

```text
GitHub
   ↓
Webhook GitHub
   ↓
Jenkins
   ↓
Docker (Node.js 20)
   ↓
Build Next.js
   ↓
GitHub Pages
```

---

## ⚙️ Fonctionnement du pipeline

Le pipeline Jenkins est défini dans un fichier `Jenkinsfile` versionné dans GitHub.

### Étape 1 : Installation

```bash
npm ci
```

Installation des dépendances du projet.

### Étape 2 : Build

```bash
npm run build
```

Compilation de l'application Next.js et génération du site statique.

### Étape 3 : Déploiement

Le contenu du dossier `out/` est automatiquement publié sur la branche :

```text
gh-pages
```

GitHub Pages publie ensuite le site web.

---

## 🐳 Utilisation de Docker

Le pipeline s'exécute dans un conteneur Docker :

```groovy
agent {
    docker {
        image 'node:20-alpine'
    }
}
```

Cela garantit un environnement d'exécution reproductible et indépendant de la machine hôte.

---

## 📂 Dépôt GitHub

Dépôt du projet :

```text
https://github.com/maoudiarra/mon-app
```

---

## 🌐 Site Web Déployé

Le site est accessible à l'adresse suivante :

```text
https://maoudiarra.github.io/mon-app/
```

---

## 🔄 Déclenchement Automatique

Un webhook GitHub a été configuré afin de déclencher automatiquement Jenkins lors d'un push sur le dépôt.

À chaque modification :

1. Push vers GitHub
2. GitHub envoie un webhook
3. Jenkins démarre automatiquement
4. Build de l'application
5. Déploiement GitHub Pages
6. Mise à jour du site web

---

## 📸 Captures d'écran

### Jenkins - Build SUCCESS

![Jenkins Success](captures/01-jenkins-success.png)

### Jenkinsfile dans GitHub

![Jenkinsfile](captures/02-jenkinsfile.png)

### Configuration GitHub Pages

![GitHub Pages](captures/03-github-pages.png)

### Site Web Déployé

![Site Web](captures/04-site-web.png)

### Configuration du Webhook GitHub

![Webhook](captures/05-webhook.png)

### Déclenchement Automatique Jenkins

![Webhook Trigger](captures/06-auto-build.png)

---

## ✅ Résultats obtenus

- Jenkins Pipeline as Code
- Jenkinsfile versionné dans GitHub
- Exécution dans Docker
- Build automatique Next.js
- Déploiement automatique GitHub Pages
- Site accessible publiquement
- Webhook GitHub → Jenkins
- Déclenchement automatique après chaque push
- Mise en place d'une chaîne CI/CD complète

---

## 🛠️ Technologies utilisées

- Git
- GitHub
- GitHub Pages
- Jenkins
- Docker
- Node.js 20
- Next.js 16
- Ngrok

---

## 🎯 Conclusion

Ce projet a permis de mettre en œuvre une chaîne CI/CD complète reposant sur Jenkins, Docker et GitHub Pages.

L'intégralité du processus de compilation et de déploiement est automatisée. Un simple push GitHub déclenche automatiquement la reconstruction et la publication du site web.

---

## 👤 Auteur

**Maou DIARRA**

EPSI - Master Ingénierie des Données