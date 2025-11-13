# Challenge - Inspection et Analyse d'un Repository GIT

## Consignes générales

Ce challenge a pour but d'évaluer votre capacité à **explorer, comprendre et analyser l'historique d'un projet GIT**.

### Règles

- **Aucune interface graphique n'est autorisée**, vous devez travailler **exclusivement en ligne de commande** (sauf pour le FORK depuis Github)
- **L'utilisation d'outils d'intelligence artificielle est strictement interdite.**
- Vous pouvez utiliser la documentation à l'adresse suivante: https://git-scm.com/book/fr/v2
- **Objectif : comprendre l'évolution du code et reconstituer les décisions prises.**

## Travail à effectuer

Le dépôt d'origine à utiliser est disponible à l'adresse suivante :
```bash
https://github.com/ETML-RRY/324_inspection_git.git
```

### Partie 1 - Préparation

1. Faites un *FORK* du dépôt sur votre compte GitHub (Attention il faut copier toutes les branches donc il faut **décocher** la case "Copy the main branch only" sur l'interface de Github)
2. Ajoutez votre enseignant comme collaborateur à votre dépôt forké.
3. Vous trouverez une réplique de ces instructions dans le fichier README.md de votre dépôt.
4. Répondez directement aux questions dans le fichier README.md qui est au format **Markdown**
5. Pour chaque points, veuillez noter la ou les commandes `git` utilisées vous permettant de répondre à la question.
6. Pour chaque partie, effectuez au minimum un commit et un push lorsque vous avez complété les réponses de la partie correspondante.

> Le format Markdown: [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)


### Partie 2 — Exploration de base

1. Combien de branches existent dans le dépôt ? Citez-les.
```
git branch --all
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/experiment/dark-mode
  remotes/origin/feature/header
  remotes/origin/feature/login
  remotes/origin/hotfix/typo
  remotes/origin/main
```    
2. Quels sont les **tags** disponibles ? A quoi correspondent-ils ?
```
git tag
v0.1
v0.2
```    
3. Quelle est la **branche principale** du projet ?
refaire : 
```
git branch --all
```
et la première branch est la branche principal

### Partie 3 — Historique et commits

4. Quel est le message du **premier commit** du projet ?  
```
git log
message : Initial commit: structure HTML/CSS/JS + README + docs
```
5. Trouvez le commit où une **clé API** a été ajoutée par erreur. Quel est son identifiant (hash court) ?  
```
git log --online | grep -i api
```
bea2d1aeaecd11
6. Quel commit a ensuite corrigé cette erreur ?
```
git log --online | grep -i api
```
le suivant
7. Trouvez le commit où le **titre de la page d'accueil** a été corrigé.
```
git log --online | grep -i titre
```
commit 6317c073f7514d580522c90fa1f0f0402066a48f (origin/hotfix/typo)
Author: Romain Rosay <romain.rosay@eduvaud.ch>
Date:   Wed Nov 5 22:15:21 2025 +0100

    hotfix: corrige la typo 'Wolrd' dans le titre

8. Quel est le message du commit qui a **ajouté le fichier `CHANGELOG.md`** et quelle commande avez-vous utilisé ?
```
commit ed62890417d8c8fb880e55a2b8933b80b00ea1bd
Author: Romain Rosay <romain.rosay@eduvaud.ch>
Date:   Wed Nov 5 22:15:30 2025 +0100

    docs: ajoute un changelog de base
```
J'ai recherché manuellement

### Partie 4 — Branches et fusions

9. Quelles branches ont été fusionnées dans `main` ?  
```
git branch --all --merge
* main
  remotes/origin/HEAD -> origin/main
  remotes/origin/feature/header
  remotes/origin/feature/login
  remotes/origin/hotfix/typo
  remotes/origin/main
```
donc aucune branche
10. Quelle branche **n'a pas été fusionnée** ? Pourquoi, selon vous ? 
```
git branch -a --no-merged
  remotes/origin/experiment/dark-mode
```
c'est une branche expérimental
### Partie 5 — Analyse du contenu

11. Quelle est la **différence principale** entre les fichiers `index.html` dans les versions `v0.1` et `v0.2` et quelle commande permet de le voir rapidement ?  
```
git diff v0.1 v0.2 index.html
```
la différence principal est : 
```
<header><nav><a href="/">Accueil</a> | <a href="#">Contact</a></nav></header>
```

12. Que contient la branche `feature/login` ?  
```
git switch feature/login
git show
ou git branch -v
```

13. Dans quelle branche a été ajouté le code pour le **mode sombre** ?  
```
  remotes/origin/experiment/dark-mode
```

14. Quelle bonne pratique de sécurité est évoquée dans les commits du fichier `config.js` ?
chore(config): retire la clé API et documente la bonne pratique
git log --oneline config.js
### Partie 6 — Réflexion

15. Pourquoi est-il important de **taguer** des versions dans un projet ?  
Pour connaitre s'il y a eu des changements majeurs, correction de bug et petit changement.
16. Que peut-on déduire du style de travail de l'équipe à partir de cet historique GIT ?
L'équipe de sait pas trop quoi commit dans les fichiers, le nommage est bon

Bonne chance, et surtout... **ne vous perdez pas dans le log !** 😉
