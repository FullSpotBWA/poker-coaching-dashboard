# 🕘 Historique des versions

Toutes les évolutions notables du dashboard sont consignées ici, de la plus récente à la plus ancienne.

> **Règle** : ce fichier doit être mis à jour à chaque mise à jour de `poker-dashboard-LATEST.html` (voir le workflow dans [CLAUDE.md](CLAUDE.md)).

## [2026-08-27] — `poker-dashboard-2026-08-27.html`

### Ajouté
- Nouvelle section dédiée au coaching technique 1-to-1 avec **Alexis Taxigalloise** (catégorie `mw`, couleur or).
- Session 07 : *OR/IP/BB en Multiway* — **Part 1 (en cours, suite la semaine prochaine)** — 20 flashcards (dont 4 takeaways).
  - Écart théorie/pratique sur la fréquence de c-bet IP en SRP vs multiway, exploits côté OR (overcbet, raise IP), défense BB (no raise vs stab IP, agressivité en clos d'action), hard exploit sur les probes turn et les sizing tells de l'OR.
- Notes brutes de la séance sauvegardées dans `transcriptions/alexis-taxigalloise-or-ip-bb-multiway-part1.txt`.
- Export Anki `anki-v5-2026-08-27.txt` (147 cartes, toutes sessions confondues).
- Total : 7 sessions, 147 flashcards (dont 37 takeaways).

### Refonte
- **Sidebar entièrement redesignée** pour désencombrer la navigation :
  - Barre de **recherche** en temps réel (titre, coach, provenance, thématique).
  - **Groupes pliables/dépliables** (accordéon, état mémorisé en localStorage) — seul le groupe de la session active est déplié par défaut.
  - **3 modes de regroupement** au choix (onglets) : par **Thématique**, par **Coach**, par **Provenance** (Coaching Vidéo / Coaching 1-to-1 / Review + Solver).
  - La sidebar est désormais **générée dynamiquement** depuis un nouveau tableau `sessionsIndex` (source de vérité unique : titre, icône, thématique, coach, provenance, minutes) au lieu d'un bloc HTML codé en dur par session.
  - Les compteurs de la sidebar (sessions, minutes, takeaways, flashcards) et le total du Quiz Mode se **recalculent automatiquement** à partir de `sessionsIndex` et `quizData`.
  - Aucune modification des systèmes SRS / Mode Libre existants — uniquement la couche de navigation.
- **Nouvelle identité visuelle « Editorial Clean »** appliquée à tout le dashboard, avec **3 thèmes commutables** :
  - Toggle **Clair / Sombre / Soft** en haut de la sidebar (mémorisé en localStorage, appliqué sans flash au chargement).
  - Typographie : Source Serif 4 (titres) + Public Sans (texte/labels), en remplacement de Space Grotesk / Outfit / JetBrains Mono.
  - Thème Clair (par défaut) : fond crème chaud, encre navy, accent or — esprit plateforme de formation premium plutôt que « terminal hacker ».
  - Thème Sombre : même identité (sérif + or) sur un fond encre chaude, sans le look néon d'origine.
  - Thème Soft : version plus douce et pastel du thème clair, contrastes adoucis.
  - Toutes les couleurs de catégorie (PKO, ICM, Maths, Heads-Up, Check-Raise, Multiway...) gardent leur identité propre à travers les 3 thèmes ; refonte des tokens CSS (dont des variables `--accent-*-rgb` pour que les fonds teintés des badges/tags suivent bien le thème, plus seulement leur texte).
  - Trois maquettes de direction ont été comparées avant de choisir celle-ci (Casino Luxe / Minimal Mono / Editorial Clean).
  - Aucune modification des systèmes SRS / Mode Libre / sidebar dynamique — uniquement les couleurs, polices et le toggle.

> Cette session sera complétée la semaine prochaine (Part 2) au fil des prochains cours avec ce coach.

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
