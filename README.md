# ⚔️ Discord RPG - Projet Jeu de rôle communautaire

## 🧩 Présentation

**Discord RPG** est un jeu de rôle textuel interactif entièrement intégré à Discord.  
Chaque serveur Discord dispose de sa propre progression, son propre boss, et sa propre aventure.  
Les joueurs créent un personnage, gagnent de l’expérience, collectent des objets et affrontent des boss épiques au fil d’un **lore évolutif**.

Le jeu mêle **combat, exploration, gestion d’inventaire et progression narrative** dans un univers inspiré des RPG classiques et des mécaniques de jeux.

---

## 🏗️ Fonctionnalités principales

### 🔹 Joueurs
- Création de personnage
- Système d’expérience et de niveau
- Points d’action limités par jour
- Choix d’une **spécialité élémentaire** (Air / Terre / Eau / Feu) débloquée via l’histoire
- Actions possibles :
  - **Attaquer** le boss
  - **Utiliser** une compétence
  - **Partir en aventure**
  - **Se reposer**

---

### 🔹 Boss
- Un **boss unique par serveur**, avec points de vie, attaque et défense
- Timer de 24h pour vaincre le boss
- Le boss réplique à chaque action du joueur :
  - Attaque de base
  - Utilisation d’une compétence
  - Repos pour récupérer des PV
- Récompenses : XP + Or pour tous les participants

---

### 🔹 Compétences (Skills)
- Débloquées automatiquement selon le **niveau du joueur**
- Chaque compétence possède :
  - Un coût en points d’action
  - Un effet (dégâts, soin, buff, debuff)
  - Un élément associé
- Gérée via `PlayerSkill` et `BossSkill`
- Système extensible (effets paramétrables depuis la base de données)

---

### 🔹 Inventaire et Objets
- 20 emplacements maximum par joueur
- Types d’objets : arme, armure, accessoire, consommable
- Bonus sur les statistiques
- Possibilité d’équiper ou déséquiper des objets
- Affichage visuel avec **images ou GIFs** dans les embeds Discord

---

### 🔹 Économie
- Gagner de l’or via combats et aventures
- Dépenser de l’or en boutique
- Coût pour se reposer ou acheter des objets
- Gestion des prix et reventes

---

### 🔹 Lore (histoire)
- Progression scénarisée débloquée au fil des boss
- Chaque étape du lore est associée à un boss
- Exemples de progression :
  - Lvl 1 : Brigand
  - Lvl 2 : Bras droit du brigand
  - Lvl 3 : Chef des brigands
  - Lvl 4 : Assassin du roi
  - ...
  - Lvl 50 : Dragons primordiaux (débloque les spécialités)
- Le lore est propre à chaque serveur et évolue collectivement

---

### 🔹 Journal d’actions
- Suivi complet de toutes les actions des joueurs :
  - Attaque, compétence, aventure, repos
- Sert à générer des statistiques, logs ou événements spéciaux

---

## 🧱 Structure de la base de données (MySQL)

Les principales tables :
- `Server` : informations du serveur Discord
- `Player` : données de chaque joueur
- `Specialty` : spécialités élémentaires débloquées par le lore
- `Boss` : boss actif lié à un lore
- `Skill` : compétences disponibles selon le niveau
- `PlayerSkill` / `BossSkill` : liens entre entités et compétences
- `Item` : objets du jeu
- `Inventory` : inventaire du joueur (20 slots max)
- `Lore` : chapitres de l’histoire
- `ActionLog` : journal des actions du joueur

---

## ⚙️ Technologies utilisées

- **Langage** : Python 3.12+  
- **Framework Discord** : [discord.py](https://github.com/Rapptz/discord.py)
- **Base de données** : MySQL 8+
- **ORM recommandé** : SQLAlchemy ou asyncmy
- **Autres dépendances** :
  - dotenv (variables d’environnement)
  - aiohttp (si API externes)
  - PIL ou Pillow (affichage d’images/GIFs dans les embeds)

---


