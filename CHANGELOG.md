# 🕘 Historique des versions

Toutes les évolutions notables du dashboard sont consignées ici, de la plus récente à la plus ancienne.

> **Règle** : ce fichier doit être mis à jour à chaque mise à jour de `poker-dashboard-LATEST.html` (voir le workflow dans [CLAUDE.md](CLAUDE.md)).

## [2026-07-05] — `poker-dashboard-2026-07-05.html`

### Ajouté
- Éditeur de QCM personnalisé : question + image collée (Ctrl+V) + réponses définies manuellement (fini les mauvaises réponses générées au hasard et trop décalées).
- Nombre de réponses flexible (2 à 4) pour un QCM perso — permet les questions type Oui/Non.
- Image d'explication optionnelle, révélée après avoir répondu (comme le verso d'une carte Anki).
- Choix d'une catégorie existante (PKO & ICM, SQZ 80bb, Exploits ICM, Maths) ou création d'une nouvelle catégorie à la volée pour un QCM perso.
- Export / Import des QCM perso au format JSON, pour les partager avec quelqu'un d'autre sans backend.
- Les QCM perso sont suivis par le même système de répétition espacée (SRS) que les flashcards existantes.
- Mise en place du dépôt Git / GitHub, avec index de navigation ([README.md](README.md)), mode d'emploi ([USAGE.md](USAGE.md)) et cet historique.

## [2026-07-01] — `poker-dashboard-2026-07-01.html`

### Ajouté
- Session 04 : *Mathématiques du Poker* (T. Sacquet) — 28 flashcards, catégorie `math` (violet).
- Total : 4 sessions, 79 flashcards (dont 21 takeaways).

### Modifié
- Passe de revue des flashcards existantes (cartes supprimées/reformulées via `REVIEW-flashcards.xlsx`).

## [2026-05-08] — `poker-dashboard-2026-05-08.html`

### Ajouté
- Session 02 : *Pots SQZ 80bb SB vs HJ* (C-Bet, textures).
- Session 03 : *Exploits ICM en Table Finale* (T. Boivin).
- Total : 3 sessions, 66 flashcards.

## [2026-05-06] — `poker-dashboard-2026-05-06.html`

### Ajouté
- Version initiale du dashboard.
- Session 01 : *PKO & ICM + Applications Postflop*.
