# Test Déploiement – Calculatrice

## Contexte

### Description
Une petite application de calculatrice déployée avec **Docker** et testée automatiquement via **GitHub Actions**.

---

## Structure du projet
Pour que l’application fonctionne à la fois dans le navigateur et avec Jest pour les tests, deux versions de la classe Calculatrice sont utilisé :

1. Navigateur (Docker/Nginx)

- Fichier : App/calculatrice.js
- Contient la classe Calculatrice sans require ni module.exports.
- Est chargé dans index.html via <script src="calculatrice.js"></script>.
- Utilisé par app.js pour manipuler le DOM et afficher les résultats dans le navigateur.

2. Tests Node/Jest

- Fichier : App/tests/calculatrice.node.js
- Contient la même logique, mais exportée avec CommonJS : module.exports = Calculatrice;
- Permet à Jest d’importer la classe et d’exécuter les tests unitaires.

---

## Prérequis Docker

Avant de lancer l’application avec Docker, s'assurer que :

- **Docker Desktop est installé et démarré**  
  Sur Windows/Mac, ouvrir l’application Docker Desktop avant toute commande.  

- **Une connexion Internet est disponible** pour télécharger les images.  
  Attention : certains VPN/pare-feux peuvent bloquer l’accès à Docker Hub. Les désactiver si nécessaire.  

- **Docker Compose est installé** (il est inclus dans Docker Desktop). 

---

## Installation et Lancement

### 1. Cloner le projet
```bash
    git clone <url-du-repo>
    cd <nom-du-dossier>
```

### 2. Lancement
#### Option 1 : Lancer en local (sans Docker)
Possible d'utiliser un simple serveur web pour tester l’application localement.

```bash
    cd App
    npx http-server .
```
Puis ouvrir : http://localhost:8080 dans le navigateur

#### Option 2 : Lancer avec Docker Compose
Construir et lancer le conteneur :
```bash
    docker-compose up --build
```
Puis ouvrir : http://localhost:8080 dans le navigateur

---

## Tests Automatisés (GitHub Actions)
Le projet contient un workflow GitHub Actions (.github/workflows/autoTest.yml) qui s’exécute à chaque pull request vers la branche main.

Il exécute les étapes suivantes :

- Installe les dépendances (npm ci).
- Construit le projet (npm run build si présent).
- Lance les tests (npm test).

**Résultat** : chaque PR est automatiquement validée ou rejetée selon les tests.

---

## Fonctionnalités

- Addition, soustraction, multiplication et division (avec gestion de la division par zéro).
- Interface web simple en **HTML + CSS + JavaScript**.
- Déploiement avec **Docker** et **Nginx**.
- Tests automatisés via **GitHub Actions**.
