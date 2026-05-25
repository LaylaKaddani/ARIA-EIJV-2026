# Projet ARIA  École d'Ingénieurs Jules Verne 2025/2026

## L'IA peut-elle prendre des décisions qui impactent la santé humaine ou l'environnement ?

Ce projet a été réalisé dans le cadre du projet de fin d'année à l'École d'Ingénieurs Jules Verne, par quatre étudiantes venant de spécialités différentes : TIPS, GEE et Cybersécurité.

---

## L'équipe

Ouazari Assya : TIPS, coordination générale et IA en santé

Elyabouri Marwa : GEE, environnement et impacts systémiques

Kaddani Layla : Cybersécurité, défense, éthique et réglementation

Naji Fatima Zahra : Cybersécurité, analyse et démonstration des attaques

---

## Ce qu'est ARIA

ARIA est une intelligence artificielle médicale conçue pour détecter les risques cardiaques à partir des paramètres cliniques d'un patient. Elle s'appuie sur le dataset Heart Disease UCI, qui contient les données de 1025 patients réels avec 13 variables chacun. Le modèle Random Forest utilisé atteint 98,5% de précision.

L'objectif du projet n'était pas seulement de construire une IA médicale fonctionnelle, mais de démontrer concrètement ce qu'il se passe quand elle est attaquée, et ce qu'on peut faire pour la défendre.

---

## Ce qu'on a démontré

On a construit ARIA, puis on l'a délibérément piratée en utilisant une attaque de type model swap : remplacer silencieusement le fichier du modèle par une version malveillante dont les prédictions sont entièrement inversées. L'interface ne change pas. Le médecin ne voit rien. Mais tous les diagnostics sont faux.

On a ensuite intégré une défense basée sur le hachage cryptographique SHA-256. A chaque prédiction, le serveur vérifie que le modèle n'a pas été modifié. Si c'est le cas, il bloque tout diagnostic et déclenche une alerte visible sur l'interface.

---

## Structure du projet

Le dossier backend contient le modèle, le serveur, le système de défense et les scripts d'entraînement. Le dossier frontend contient l'interface React. Le dossier attack contient le script de démonstration de l'attaque.

---

## Comment lancer le projet

Placer le fichier heart.csv dans le dossier backend. Ce fichier est disponible sur Kaggle : Heart Disease Dataset de johnsmith88.

Installer les dépendances Python avec la commande suivante depuis la racine du projet :

    py -3.11 -m pip install -r backend/requirements.txt

Entraîner le modèle légitime :

    py -3.11 backend/train_model.py

Entraîner le modèle empoisonné pour la démonstration :

    py -3.11 backend/train_poisoned.py

Lancer le serveur :

    py -3.11 backend/app.py

Dans un autre terminal, lancer l'interface :

    cd frontend
    npm install
    npm start

Pour tester l'attaque et voir la défense en action, ouvrir un troisième terminal et lancer :

    py -3.11 attack/model_swap.py

Puis cliquer sur Lancer le diagnostic dans le navigateur avant que les 60 secondes ne s'écoulent.

---

## Comment on a travaillé

On s'est réparti les rôles selon les spécialités de chacune dès le début. Chaque membre a travaillé de façon autonome sur sa partie, et on a mis en commun régulièrement pour s'assurer que tout s'emboitait. 

La difficulté principale n'était pas technique. C'était de faire travailler ensemble trois spécialités qui ne parlent pas toujours le même langage. Ce projet nous a appris autant sur la collaboration que sur l'intelligence artificielle.

