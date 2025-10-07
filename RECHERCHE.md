# 🧭 Git Flow

## 1. 📜 Historique

Git Flow a été proposé en **2010** par **Vincent Driessen**.  
À cette époque, les équipes utilisaient Git mais manquaient d’un cadre standard pour organiser leurs branches.  
Son modèle a introduit une **méthodologie structurée** pour gérer le développement, les tests et la mise en production d’un projet logiciel.  
Il a été rapidement adopté dans les entreprises et les équipes travaillant avec des **releases planifiées**.

---

## 2. 🎯 Objectifs

Les objectifs de Git Flow sont de :

- Structurer le **cycle de vie du code** dans Git.  
- Séparer clairement les **environnements de développement** (dev / test / prod).  
- Faciliter le **travail collaboratif** entre développeurs.  
- Assurer la **stabilité du code en production**.  
- Rendre les versions du logiciel **traçables et reproductibles** grâce aux tags et à une organisation logique des branches.

---

## 3. ⚙️ Principes

Git Flow repose sur une **hiérarchie de branches** avec des rôles bien définis.

### 🔸 Branches principales

- **`main`** : contient le code **stable et en production**.  
- **`develop`** : contient le code **en cours de développement** ; c’est la base pour intégrer les nouvelles fonctionnalités.

### 🔹 Branches secondaires

- **`feature/`** : pour développer de nouvelles fonctionnalités  
  → créée à partir de `develop`, fusionnée dans `develop`.  
- **`release/`** : pour préparer une version stable  
  → créée à partir de `develop`, fusionnée dans `main` et `develop`.  
- **`hotfix/`** : pour corriger une erreur critique en production  
  → créée à partir de `main`, fusionnée dans `main` et `develop`.

---

### ✅ Avantages

- Structure **claire et rigoureuse**.  
- Facilite la **collaboration** et la **gestion des versions**.  
- Sépare proprement les étapes de **développement** et de **production**.

### ⚠️ Limites

- Méthode assez **complexe et lourde** pour les petits projets.  
- Peu adaptée aux environnements de **déploiement continu (CI/CD)**.  
- Nécessite une **discipline stricte** dans la gestion des branches.

---

# 🧩 Versionnement sémantique (SemVer)

## 📜 Définition

Le **versionnement sémantique** (*Semantic Versioning* ou **SemVer**) est une **convention de nommage des versions** d’un logiciel.  
Elle permet de comprendre rapidement le type de changements apportés entre deux versions, en utilisant un format standardisé :

MAJOR.MINOR.PATCH


**Exemple :** `2.5.1`

---

## 🔢 Signification des numéros

| Partie | Nom | Quand on l’incrémente ? | Impact |
|:-------:|:------|:--------------------------|:---------|
| **MAJOR** | Version majeure | Lorsqu’on introduit des **changements incompatibles** avec les versions précédentes | Peut **casser la compatibilité** (*breaking changes*) |
| **MINOR** | Version mineure | Lorsqu’on ajoute des **fonctionnalités nouvelles** de manière **rétrocompatible** | N’affecte pas les anciens usages |
| **PATCH** | Correctif | Lorsqu’on effectue des **corrections de bugs** ou des **améliorations mineures** | Version **compatible** avec la précédente |

---

## 🧠 Exemples

| Version | Explication |
|----------|-------------|
| `1.0.0` | Première version stable du logiciel. |
| `1.1.0` | Ajout d’une nouvelle fonctionnalité sans casser la compatibilité. |
| `1.1.1` | Correction d’un bug mineur. |
| `2.0.0` | Changement majeur, rupture de compatibilité avec la version précédente. |

---

# 📘 Le rôle du Changelog

Le **changelog** (ou *journal des modifications*) sert à **lister et décrire tous les changements** apportés au logiciel entre deux versions.  
C’est une **trace écrite de l’évolution du projet**.

## 🔹 Concrètement, il indique :

- Quelles **nouvelles fonctionnalités** ont été ajoutées.  
- Quels **bugs** ont été corrigés.  
- Quelles **améliorations ou modifications** ont été faites.  
- Et éventuellement, quelles **fonctionnalités ont été supprimées**.

L’objectif principal du changelog est de **communiquer clairement** aux utilisateurs, testeurs ou développeurs **ce qui a changé d’une version à l’autre**.  

C’est aussi un outil essentiel pour :
- **Suivre l’historique** du projet.  
- **Faciliter le débogage** (retrouver quand un changement a eu lieu).  
- **Maintenir la cohérence** entre les différentes versions.

---

# 📙 Le rôle de la Documentation de Version

La **documentation de version** complète le changelog.  
Alors que le changelog dit *« ce qui a changé »*, la documentation explique *« comment utiliser ces changements »*.

## 🔹 Elle détaille :

- Le **fonctionnement des nouvelles fonctionnalités**.  
- Les **conséquences des modifications** pour les utilisateurs ou les développeurs.  
- Les **étapes à suivre pour mettre à jour** le logiciel.  
- Et parfois les **points de compatibilité** (par exemple, si une version n’est plus compatible avec une ancienne API).

---

# 🔗 Lien entre Issues, Milestones et Releases sur GitHub

GitHub fournit trois outils complémentaires pour **organiser, suivre et publier** le développement d’un projet :

## 1️⃣ Issues

- Une **issue** représente une **tâche**, un **bug** ou une **amélioration** à réaliser.  
- Chaque issue peut contenir une description, des commentaires, des labels, et être assignée à un développeur.  
- **Exemple :** `#42 - Corriger le bug de connexion`

## 2️⃣ Milestones

- Une **milestone** regroupe plusieurs **issues** autour d’un même objectif ou d’une version spécifique.  
- Elle sert à **planifier et suivre l’avancement** d’un ensemble de tâches liées à une version.  
- **Exemple :** `v2.0 - Refonte de l’interface`

## 3️⃣ Releases

- Une **release** correspond à une **version officielle du projet**.  
- Elle inclut généralement :  
  - un **tag Git** pour identifier la version,  
  - un **changelog** ou notes de version,  
  - éventuellement des **fichiers téléchargeables**.  
- **Exemple :** `Release v2.0.0`

---

## 🧭 Schéma du flux

```text
[ Issue #101 ] ---\
[ Issue #102 ] ---->  🧩 Milestone : "Version 2.0"
[ Issue #103 ] ---/           │
                              ▼
                        🚀 Release v2.0.0
                              │
                              ▼
                   🗒️ Changelog / Notes de version

```
- Les issues décrivent les tâches individuelles.
- Les milestones regroupent ces issues vers un objectif commun (souvent une version).
- Une fois toutes les issues d’une milestone terminées, on crée une release.
- La release est ensuite documentée avec un changelog et un tag Git.