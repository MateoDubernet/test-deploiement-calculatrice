# Test Déploiement – Calculatrice

## Présentation
Ce projet à été réaliser durant mon alternance dans le cadre d'un devoir maison, il s'agit d'une petite application de calculatrice développer en javascript, déployée avec **Docker** et testée automatiquement via **GitHub Actions**.

Pour que l’application fonctionne à la fois dans le navigateur et avec Jest pour les tests, deux versions de la classe Calculatrice sont utilisé.

---

## Installation et Lancement
### 1. Clonage du dépôt
```bash
    git clone https://github.com/MateoDubernet/test-deploiement-calculatrice.git
```

### 2. Lancement (Docker)
**Prérequis :** [Docker Desktop](https://www.docker.com/products/docker-desktop) installé et lancé.

[!IMPORTANT]
Assurez-vous que le port 8080 n'est pas déjà utilisé par une autre application sur votre machine avant de lancer le conteneur.

```bash
    cd ./test-deploiement-calculatrice
    docker-compose up --build
```

### 3. Accès
Ouvrir un navigateur web et aller à l'adresse: http://localhost:8080

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
