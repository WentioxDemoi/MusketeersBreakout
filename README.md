### MusketeersBreakout

MusketeersBreakout est un Battle Royale multijoueur en vue TPS, inspiré de l’univers des mousquetaires. Les joueurs s’affrontent en PVP et PVE, doivent survivre, accumuler du butin et atteindre une zone d’extraction pour conserver leurs gains.

Ce projet est réalisé dans le cadre de nos études (travail d’équipe à 5), avec une organisation en sprints sur 3 à 4 mois (Kickoff, Follow‑up, Delivery) et un rythme de 4 jours de production par mois (le week‑end, en parallèle des cours).


## Fonctionnalités

- **Multijoueur en ligne**: création de parties, paramètres de salle, synchronisation via PUN2.
- **Vue et contrôle isométriques**: caméra isométrique, visée et tirs à distance avec laser d’aide.
- **Carte générative**: nouvelle carte à chaque partie (procédural) pour un gameplay renouvelé.
- **Boucle BR extraction**: survivre, combattre IA/joueurs, looter, puis s’extraire dans la zone d’extraction pour sécuriser le butin.
- **Combat PVP et PVE**: armes de mêlée et à distance, bouclier avec blocage, projectiles synchronisés réseau.
- **Inventaire et loot**: coffres/ennemis, gestion de slots, swap rapide d’objets, équipements persistants via PlayFab.
- **HUD et menus**: HUD en jeu, menu principal fonctionnel, gestion d’amis et chat textuel.
- **Chat de proximité**: communication proche des joueurs (voix/texte selon contexte de build).


## État du projet (MVP atteint)

- **Jouer en multijoueur**
- **Contrôler la caméra isométrique**
- **Carte générative** (nouvelle carte à chaque partie)
- **Combattre et récupérer l’équipement** (coffres + ennemis)
- **Chat de proximité**
- **Menu fonctionnel, amis, chat textuel**
- **Création de parties et réglages**
- **S’extraire** (mécanique d’extraction opérationnelle)


## Stack technique

- **Moteur**: Unity 2021.3.28f1
- **Langage**: C#
- **Réseau**: Photon PUN 2
- **Backend/BDD**: PlayFab (inventaire, persistance, CloudScript)
- **Organisation**: GitHub, Notion


## Démarrage rapide

1) **Prérequis**
- Unity Hub + **Unity 2021.3.28f1** (LTS 2021.3.x recommandé)
- Compte **Photon** (AppId PUN)
- Compte **PlayFab** (TitleId)

2) **Cloner et ouvrir**
- Cloner le repo puis ouvrir le dossier du projet dans Unity 2021.3.28f1.

3) **Configurer PUN2**
- Window → Photon Unity Networking → PUN Wizard.
- Renseigner votre **AppId** Photon.

4) **Configurer PlayFab**
- Importer/activer le SDK PlayFab si nécessaire.
- Renseigner le **TitleId** dans les settings PlayFab.

5) **Lancer**
- Ouvrir une scène dans `Assets/Scenes` (ex: Menu ou niveau principal) et Play.
- Pour tester le multijoueur en local: lancer 2 instances (Editor + Build) et rejoindre la même salle.


## Contrôles (par défaut)

- **Déplacement**: ZQSD / WASD
- **Saut / Double saut**: Espace
- **Sprint**: Maj gauche
- **Esquive**: F
- **Attaque**: Clic gauche
- **Visée longue portée**: Maintenir clic droit (laser ON/OFF au clic droit)
- **Ouvrir/Fermer HUD**: U
- **Interaction/loot**: E

## Réseau et persistance

- **Photon PUN2**: RPC et `OnPhotonSerializeView` pour synchroniser position/rotation joueur et état d’objets (activation d’armes, tags temporaires de loot, projectiles avec shooter id, etc.).
- **PlayFab**: persistance côté client/CloudScript (inventaire joueur, victoire/défaite via `PlayFabInventory` utilisé par `Player`).


## Boucle de gameplay

1. Rejoindre/créer une partie (paramètres de salle disponibles).
2. Explorer une carte générée procéduralement, combattre IA et joueurs.
3. Looter coffres/ennemis, gérer l’inventaire et l’équipement.
4. Se diriger vers la **zone d’extraction**, s’extraire pour sécuriser les gains.


## Construction (Build)

- File → Build Settings…
- Ajouter les scènes nécessaires (Menu, niveau principal, etc.).
- Platform ciblée (Windows/macOS), puis Build. Pour tests réseau locaux, lancer plusieurs builds.

